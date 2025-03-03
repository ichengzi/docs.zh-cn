---
title: ReDim 语句
ms.date: 07/20/2015
f1_keywords:
- vb.ReDim
- vb.Preserve
helpviewer_keywords:
- fixed-length strings [Visual Basic], declaring
- ReDim statement [Visual Basic], syntax
- dynamic arrays [Visual Basic], ReDim statement
- arrays [Visual Basic], reallocating
- arrays [Visual Basic], reinitializing
- arrays [Visual Basic], dimensions
- scalars, and arrays
- scalars
- declarations [Visual Basic], dynamic arrays
- variables [Visual Basic], scalar
- ReDim statement [Visual Basic]
- data types [Visual Basic], assigning
- As keyword [Visual Basic], in ReDim statement
- To keyword [Visual Basic], ReDim statement
- arrays [Visual Basic], declaring
- Preserve keyword [Visual Basic], ReDim statement
- storage [Visual Basic], allocating
- arrays [Visual Basic], and scalars
- declaration statements [Visual Basic]
- scalar variables [Visual Basic]
ms.assetid: ad1c5e07-dcd7-4ae1-a79e-ad3f2dcc2083
ms.openlocfilehash: fabfd9a45d47cc1b881b3743181a03e89158f939
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346737"
---
# <a name="redim-statement-visual-basic"></a>ReDim 语句 (Visual Basic)
为数组变量重新分配存储空间。  
  
## <a name="syntax"></a>语法  
  
```vb  
ReDim [ Preserve ] name(boundlist) [ ,  name(boundlist) [, ... ] ]  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|----------|----------------|  
|`Preserve`|可选。 修饰符，当仅更改最后一个维度的大小时，用来保留现有数组中的数据。|  
|`name`|必须的。 数组变量的名称。 请参阅 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。|  
|`boundlist`|必须的。 列出重新定义的数组各个维度的边界。|  
  
## <a name="remarks"></a>备注  
 可以使用 `ReDim` 语句来更改某个已声明数组的一个或多个维度的大小。 如果数组较大，并且你不再需要它的某些元素，`ReDim`可通过减少数组大小来释放内存。 另一方面，如果数组需要更多元素，也可使用 `ReDim` 进行添加。  
  
 `ReDim` 语句仅供数组使用。 它对标量（仅包含单个值的变量）、集合或结构无效。 请注意，如果将变量声明为 `Array` 类型，则 `ReDim` 语句将没有足够的类型信息来创建新数组。  
  
 仅可在过程级别使用 `ReDim` 。 因此，变量的声明上下文必须是过程；而不能是源文件、命名空间、接口、类、结构、模块或块。 有关详细信息，请参阅[声明上下文和默认访问级别](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。  
  
## <a name="rules"></a>规则  
  
- **Multiple Variables.** You can resize several array variables in the same declaration statement and specify the `name` and `boundlist` parts for each variable. 以逗号分隔多个变量。  
  
- **Array Bounds.** Each entry in `boundlist` can specify the lower and upper bounds of that dimension. 下边界始终为 0（零）。 上边界是该维度可能的最大索引值，而不是维度的长度（即上边界加 1）。 每个维度的索引都可能在 0 到其上边界值之间变动。  
  
     `boundlist` 中的维数必须与数组的原始维数（秩）相匹配。  
  
- **Data Types.** The `ReDim` statement cannot change the data type of an array variable or its elements.  
  
- **Initialization.** The `ReDim` statement cannot provide new initialization values for the array elements.  
  
- **Rank.** `ReDim` 语句无法更改数组的秩（维数）。  
  
- **Resizing with Preserve.** If you use `Preserve`, you can resize only the last dimension of the array. 对于其他每个维度，必须指定现有数组的边界。  
  
     例如，如果数组只有一个维度，则可以重设该维度的大小并依然保留数组的所有内容，因为你更改的是最后一个也是唯一的维度。 但是，如果数组具有两个或更多维度，则使用 `Preserve` 只能重设最后一个维度的大小。  
  
- **Properties.** You can use `ReDim` on a property that holds an array of values.  
  
## <a name="behavior"></a>行为  
  
- **Array Replacement.** `ReDim` releases the existing array and creates a new array with the same rank. 新数组将替换数组变量中已释放的数组。  
  
- **Initialization without Preserve.** If you do not specify `Preserve`, `ReDim` initializes the elements of the new array by using the default value for their data type.  
  
- **Initialization with Preserve.** If you specify `Preserve`, Visual Basic copies the elements from the existing array to the new array.  
  
## <a name="example"></a>示例  
 下面的示例将增加某个动态数组最后一个维度的大小（不会丢失数组中的任何现有数据），然后减小该大小（会有部分数据丢失）。 最后，它会将大小重新减小到其原始值，并重新初始化所有数组元素。  
  
 [!code-vb[VbVbalrStatements#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#52)]  
  
 `Dim` 语句创建具有三个维度的新数组。 为每个维度声明的边界为 10，因此每个维度的数组索引的范围介于 0 到 10 之间。 在下面的讨论中，三个维度分别被称为层、行和列。  
  
 第一个 `ReDim` 创建一个新数组，该数组将替换变量 `intArray` 中的现有数组。 `ReDim` 将所有元素从现有数组复制到新数组中。 它还向每一层中每一行的末尾添加 10 列，并将这些新列中的元素初始化为 0（数组的元素类型 `Integer` 的默认值）。  
  
 第二个 `ReDim` 创建另一个新数组并复制所有适合的元素。 但是，每一层的每一行的末尾丢失了 5 列。 如果不再使用这些列，这不是问题。 减小大型数组的大小可以释放不再需要的内存。  
  
 第三个 `ReDim` 创建另一个新数组，同时从每一层中每一行的末尾删除另外 5 列。 这一次它不会复制任何现有元素。 此语句将数组恢复为其原始大小。 由于该语句不包括 `Preserve` 修饰符，因此它将所有数组元素设置为其原始默认值。  
  
 For additional examples, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="see-also"></a>请参阅

- <xref:System.IndexOutOfRangeException>
- [Const 语句](../../../visual-basic/language-reference/statements/const-statement.md)
- [Dim 语句](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Erase 语句](../../../visual-basic/language-reference/statements/erase-statement.md)
- [Nothing](../../../visual-basic/language-reference/nothing.md)
- [数组](../../../visual-basic/programming-guide/language-features/arrays/index.md)
