---
title: 计算表达式
description: 了解如何创建方便的语法，以便在中F#写入可使用控制流结构和绑定进行排序和组合的计算。
ms.date: 11/04/2019
ms.openlocfilehash: c9ac0454221782a7ccb3d41850ca6aba4e20a72a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976790"
---
# <a name="computation-expressions"></a>计算表达式

中F#的计算表达式提供了一种方便的语法，用于编写可使用控制流结构和绑定进行序列化和组合的计算。 根据计算表达式的类型，可以将其视为表示 monad、monoids、monad 转换器和 applicative 函子的一种方法。 但是，与其他语言（如 Haskell 中的 *-notation* ）不同，它们不会与单个抽象相关，也不依赖于宏或其他形式的元编程来实现方便且区分上下文的语法。

## <a name="overview"></a>概述

计算可以采用多种形式。 最常见的计算形式是单线程执行，它易于理解和修改。 但是，并非所有形式的计算都像单线程执行一样简单。 一些示例包括：

- 非确定性计算
- 异步计算
- Effectful 计算
- 生成计算

通常，在应用程序的某些部分，您必须执行*上下文相关*的计算。 编写上下文相关的代码可能会很难，因为在没有抽象的情况下，可以轻松地在给定上下文之外 "泄漏" 计算，以防您这样做。 这些抽象通常很难自行编写，这就是F#一种通用的方法来实现这种**计算表达式**。

计算表达式为区分上下文的计算提供统一的语法和抽象模型。

每个计算表达式都是由*生成器*类型支持的。 生成器类型定义可用于计算表达式的操作。 请参阅[创建新类型的计算表达式](computation-expressions.md#creating-a-new-type-of-computation-expression)，其中显示了如何创建自定义计算表达式。

### <a name="syntax-overview"></a>语法概述

所有计算表达式具有以下形式：

```fsharp
builder-expr { cexper }
```

其中 `builder-expr` 是定义计算表达式的生成器类型的名称，而 `cexper` 是计算表达式的表达式主体。 例如，`async` 计算表达式代码可能如下所示：

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

计算表达式中有一种特殊的附加语法，如前面的示例所示。 以下表达式窗体可用于计算表达式：

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

其中的每个关键字和其他标准F#关键字仅在计算表达式中可用（如果已在后备生成器类型中定义）。 唯一的例外情况是 `match!`，这本身就是使用 `let!` 后跟结果的模式匹配的语法。

生成器类型是一个对象，该对象定义控制计算表达式片段的组合方式的特殊方法;也就是说，其方法控制计算表达式的行为方式。 描述生成器类的另一种方法是，它使您能够自定义多个F#构造（如循环和绑定）的操作。

### `let!`

`let!` 关键字将调用的结果绑定到一个名称：

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

如果将对计算表达式的调用绑定到 `let`，则不会获得计算表达式的结果。 而是将未*实现*的调用的值绑定到该计算表达式。 使用 `let!` 绑定到结果。

`let!` 由生成器类型上的 `Bind(x, f)` 成员定义。

### `do!`

`do!` 关键字用于调用一个计算表达式，该表达式返回类似于 `unit`的类型（由生成器上的 `Zero` 成员定义）：

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

对于[异步工作流](asynchronous-workflows.md)，此类型为 `Async<unit>`。 对于其他计算表达式，此类型可能是 `CExpType<unit>`。

`do!` 由生成器类型上的 `Bind(x, f)` 成员定义，其中 `f` 生成一个 `unit`。

### `yield`

`yield` 关键字用于从计算表达式返回值，以便可以将其用作 <xref:System.Collections.Generic.IEnumerable%601>：

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

在大多数情况下，调用方可以省略它。 省略 `yield` 的最常见方法是 `->` 运算符：

```fsharp
let squares =
    seq {
        for i in 1..10 -> i * i
    }

for sq in squares do
    printfn "%d" sq
```

对于更复杂的表达式，可能会产生许多不同的值，并且可能有条件地省略关键字：

```fsharp
let weekdays includeWeekend =
    seq {
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then
            "Saturday"
            "Sunday"
    }
```

与[ C#中的 yield 关键字](../../csharp/language-reference/keywords/yield.md)一样，计算表达式中的每个元素都是在迭代时重新生成的。

`yield` 由生成器类型上的 `Yield(x)` 成员定义，其中 `x` 是要返回的项。

### `yield!`

`yield!` 关键字用于平展计算表达式中的值的集合：

```fsharp
let squares =
    seq {
        for i in 1..3 -> i * i
    }

let cubes =
    seq {
        for i in 1..3 -> i * i * i
    }

let squaresAndCubes =
    seq {
        yield! squares
        yield! cubes
    }

printfn "%A" squaresAndCubes // Prints - 1; 4; 9; 1; 8; 27
```

计算时，`yield!` 调用的计算表达式会将其项逐个返回，从而平展结果。

`yield!` 由生成器类型上的 `YieldFrom(x)` 成员定义，其中 `x` 是值的集合。

与 `yield`不同，必须显式指定 `yield!`。 它的行为在计算表达式中是隐式的。

### `return`

`return` 关键字包装与计算表达式对应的类型中的值。 除了使用 `yield`的计算表达式，它用于 "完成" 计算表达式：

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return` 由生成器类型上的 `Return(x)` 成员定义，其中 `x` 是要包装的项。

### `return!`

`return!` 关键字实现计算表达式的值，并将结果与计算表达式对应的类型进行包装：

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return!` 由生成器类型上的 `ReturnFrom(x)` 成员定义，其中 `x` 是另一个计算表达式。

### `match!`

从 4.5 F#开始，使用`match!`关键字可以在其结果中内联调用另一个计算表达式和模式匹配：

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

当使用 `match!`调用计算表达式时，它将实现调用的结果，如 `let!`。 这通常在调用计算表达式（其中的结果是[可选](options.md)的）时使用。

## <a name="built-in-computation-expressions"></a>内置计算表达式

核心库定义了三个内置计算表达式：[序列表达式](sequences.md)、[异步工作流](asynchronous-workflows.md)和[查询表达式。](query-expressions.md) F#

## <a name="creating-a-new-type-of-computation-expression"></a>创建新类型的计算表达式

您可以通过创建生成器类并在类上定义某些特殊方法，定义自己的计算表达式的特征。 Builder 类可以选择定义下表中列出的方法。

下表描述了可在工作流生成器类中使用的方法。

|**方法**|**典型签名**|**描述**|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|为计算表达式中的 `let!` 和 `do!` 调用。|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|将计算表达式包装为函数。|
|`Return`|`'T -> M<'T>`|为计算表达式中的 `return` 调用。|
|`ReturnFrom`|`M<'T> -> M<'T>`|为计算表达式中的 `return!` 调用。|
|`Run`|`M<'T> -> M<'T>` 或<br /><br />`M<'T> -> 'T`|执行计算表达式。|
|`Combine`|`M<'T> * M<'T> -> M<'T>` 或<br /><br />`M<unit> * M<'T> -> M<'T>`|在计算表达式中调用以进行序列化。|
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` 或<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|为计算表达式中的 `for...do` 表达式调用。|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|为计算表达式中的 `try...finally` 表达式调用。|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|为计算表达式中的 `try...with` 表达式调用。|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'T :> IDisposable`|为计算表达式中的 `use` 绑定调用。|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|为计算表达式中的 `while...do` 表达式调用。|
|`Yield`|`'T -> M<'T>`|为计算表达式中的 `yield` 表达式调用。|
|`YieldFrom`|`M<'T> -> M<'T>`|为计算表达式中的 `yield!` 表达式调用。|
|`Zero`|`unit -> M<'T>`|为计算表达式中 `if...then` 表达式的空 `else` 分支调用。|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|指示将计算表达式作为一个引号传递到 `Run` 成员。 它将计算的所有实例都转换为引号。|

生成器类中的许多方法都使用并返回 `M<'T>` 构造，这通常是一个单独定义的类型，用于确定要合并的计算种类，例如，异步工作流的 `Async<'T>` 和用于序列的 `Seq<'T>`工作. 这些方法的签名使它们相互组合起来并彼此嵌套，以便可以将从一个构造返回的工作流对象传递到下一个构造。 编译器在分析计算表达式时，通过使用上表中的方法和计算表达式中的代码，将表达式转换为一系列嵌套函数调用。

嵌套表达式的格式如下：

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

在上面的代码中，如果未在计算表达式生成器类中定义 `Run` 和 `Delay`，则将忽略这些调用。 计算表达式的主体（此处表示为 `{| cexpr |}`）将按下表中所述的翻译转换为涉及生成器类方法的调用。 根据这些转换以递归方式定义计算表达式 `{| cexpr |}`，其中 `expr` 为F#表达式，`cexpr`为计算表达式。

|Expression|转换|
|----------|-----------|
|<code>{ let binding in cexpr }</code>|<code>let binding in {&#124; cexpr &#124;}</code>|
|<code>{ let! pattern = expr in cexpr }</code>|<code>builder.Bind(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{ do! expr in cexpr }</code>|<code>builder.Bind(expr, (fun () -> {&#124; cexpr &#124;}))</code>|
|<code>{ yield expr }</code>|`builder.Yield(expr)`|
|<code>{ yield! expr }</code>|`builder.YieldFrom(expr)`|
|<code>{ return expr }</code>|`builder.Return(expr)`|
|<code>{ return! expr }</code>|`builder.ReturnFrom(expr)`|
|<code>{ use pattern = expr in cexpr }</code>|<code>builder.Using(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{ use! value = expr in cexpr }</code>|<code>builder.Bind(expr, (fun value -> builder.Using(value, (fun value -> { cexpr }))))</code>|
|<code>{ if expr then cexpr0 &#124;}</code>|<code>if expr then { cexpr0 } else binder.Zero()</code>|
|<code>{ if expr then cexpr0 else cexpr1 &#124;}</code>|<code>if expr then { cexpr0 } else { cexpr1 }</code>|
|<code>{ match expr with &#124; pattern_i -> cexpr_i }</code>|<code>match expr with &#124; pattern_i -> { cexpr_i }</code>|
|<code>{ for pattern in expr do cexpr }</code>|<code>builder.For(enumeration, (fun pattern -> { cexpr }))</code>|
|<code>{ for identifier = expr1 to expr2 do cexpr }</code>|<code>builder.For(enumeration, (fun identifier -> { cexpr }))</code>|
|<code>{ while expr do cexpr }</code>|<code>builder.While(fun () -> expr, builder.Delay({ cexpr }))</code>|
|<code>{ try cexpr with &#124; pattern_i -> expr_i }</code>|<code>builder.TryWith(builder.Delay({ cexpr }), (fun value -> match value with &#124; pattern_i -> expr_i &#124; exn -> reraise exn)))</code>|
|<code>{ try cexpr finally expr }</code>|<code>builder.TryFinally(builder.Delay( { cexpr }), (fun () -> expr))</code>|
|<code>{ cexpr1; cexpr2 }</code>|<code>builder.Combine({ cexpr1 }, { cexpr2 })</code>|
|<code>{ other-expr; cexpr }</code>|<code>expr; { cexpr }</code>|
|<code>{ other-expr }</code>|`expr; builder.Zero()`|

在上表中，`other-expr` 描述了表中未列出的表达式。 生成器类不需要实现所有方法并支持上表中列出的所有翻译。 未实现的这些构造在该类型的计算表达式中不可用。 例如，如果不想在计算表达式中支持 `use` 关键字，则可以在生成器类中省略 `Use` 的定义。

下面的代码示例演示一个计算表达式，该表达式将计算封装为一系列步骤，一次只能对一个步骤进行计算。 `OkOrException`，可区分的联合类型对该表达式的错误状态进行编码（如目前所计算）。 此代码演示了几种可在计算表达式中使用的典型模式，如某些生成器方法的样本实现。

```fsharp
// Computations that can be run step by step
type Eventually<'T> =
    | Done of 'T
    | NotYetDone of (unit -> Eventually<'T>)

module Eventually =
    // The bind for the computations. Append 'func' to the
    // computation.
    let rec bind func expr =
        match expr with
        | Done value -> func value
        | NotYetDone work -> NotYetDone (fun () -> bind func (work()))

    // Return the final value wrapped in the Eventually type.
    let result value = Done value

    type OkOrException<'T> =
        | Ok of 'T
        | Exception of System.Exception

    // The catch for the computations. Stitch try/with throughout
    // the computation, and return the overall result as an OkOrException.
    let rec catch expr =
        match expr with
        | Done value -> result (Ok value)
        | NotYetDone work ->
            NotYetDone (fun () ->
                let res = try Ok(work()) with | exn -> Exception exn
                match res with
                | Ok cont -> catch cont // note, a tailcall
                | Exception exn -> result (Exception exn))

    // The delay operator.
    let delay func = NotYetDone (fun () -> func())

    // The stepping action for the computations.
    let step expr =
        match expr with
        | Done _ -> expr
        | NotYetDone func -> func ()

    // The rest of the operations are boilerplate.
    // The tryFinally operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryFinally expr compensation =
        catch (expr)
        |> bind (fun res ->
            compensation();
            match res with
            | Ok value -> result value
            | Exception exn -> raise exn)

    // The tryWith operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryWith exn handler =
        catch exn
        |> bind (function Ok value -> result value | Exception exn -> handler exn)

    // The whileLoop operator.
    // This is boilerplate in terms of "result" and "bind".
    let rec whileLoop pred body =
        if pred() then body |> bind (fun _ -> whileLoop pred body)
        else result ()

    // The sequential composition operator.
    // This is boilerplate in terms of "result" and "bind".
    let combine expr1 expr2 =
        expr1 |> bind (fun () -> expr2)

    // The using operator.
    let using (resource: #System.IDisposable) func =
        tryFinally (func resource) (fun () -> resource.Dispose())

    // The forLoop operator.
    // This is boilerplate in terms of "catch", "result", and "bind".
    let forLoop (collection:seq<_>) func =
        let ie = collection.GetEnumerator()
        tryFinally
            (whileLoop
                (fun () -> ie.MoveNext())
                (delay (fun () -> let value = ie.Current in func value)))
            (fun () -> ie.Dispose())

// The builder class.
type EventuallyBuilder() =
    member x.Bind(comp, func) = Eventually.bind func comp
    member x.Return(value) = Eventually.result value
    member x.ReturnFrom(value) = value
    member x.Combine(expr1, expr2) = Eventually.combine expr1 expr2
    member x.Delay(func) = Eventually.delay func
    member x.Zero() = Eventually.result ()
    member x.TryWith(expr, handler) = Eventually.tryWith expr handler
    member x.TryFinally(expr, compensation) = Eventually.tryFinally expr compensation
    member x.For(coll:seq<_>, func) = Eventually.forLoop coll func
    member x.Using(resource, expr) = Eventually.using resource expr

let eventually = new EventuallyBuilder()

let comp = eventually {
    for x in 1..2 do
        printfn " x = %d" x
    return 3 + 4 }

// Try the remaining lines in F# interactive to see how this
// computation expression works in practice.
let step x = Eventually.step x

// returns "NotYetDone <closure>"
comp |> step

// prints "x = 1"
// returns "NotYetDone <closure>"
comp |> step |> step

// prints "x = 1"
// prints "x = 2"
// returns "Done 7"
comp |> step |> step |> step |> step
```

计算表达式具有表达式返回的基础类型。 基础类型可能表示可以执行的计算结果或延迟计算，或者它可能提供一种方法来循环访问某些类型的集合。 在上面的示例中，基础类型**最终**是。 对于序列表达式，基础类型是 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>。 对于查询表达式，基础类型为 <xref:System.Linq.IQueryable?displayProperty=nameWithType>。 对于异步工作流，基础类型是[`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)。 `Async` 对象表示要执行的工作来计算结果。 例如，调用[`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b)以执行计算并返回结果。

## <a name="custom-operations"></a>自定义操作

可以在计算表达式中定义自定义操作，并使用自定义操作作为计算表达式中的运算符。 例如，可以在查询表达式中包含查询运算符。 定义自定义操作时，必须在计算表达式中定义 Yield 和方法。 若要定义自定义操作，请将其放在计算表达式的 builder 类中，然后应用[`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19)。 此属性采用字符串作为参数，该参数是要在自定义操作中使用的名称。 此名称将出现在计算表达式的左大括号开头的范围内。 因此，不应使用与此块中的自定义操作名称相同的标识符。 例如，避免在查询表达式中使用标识符，如 `all` 或 `last`。

### <a name="extending-existing-builders-with-new-custom-operations"></a>利用新的自定义操作扩展现有生成器

如果已经有一个生成器类，则可以从该生成器类的外部扩展其自定义操作。 扩展必须在模块中声明。 命名空间不能包含在定义该类型的同一文件和相同的命名空间声明组中的扩展成员。

下面的示例演示现有 `Microsoft.FSharp.Linq.QueryBuilder` 类的扩展。

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member _.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a>请参阅

- [F# 语言参考](index.md)
- [异步工作流](asynchronous-workflows.md)
- [序列](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [查询表达式](query-expressions.md)
