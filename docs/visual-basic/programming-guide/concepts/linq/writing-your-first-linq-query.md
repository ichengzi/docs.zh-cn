---
title: 编写第一个 LINQ 查询
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
ms.openlocfilehash: a9fe4241972815a04ec9c6a51a45760d72a8bbb2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349336"
---
# <a name="writing-your-first-linq-query-visual-basic"></a>编写第一个 LINQ 查询 (Visual Basic)
*查询*是一种从数据源检索数据的表达式。 Queries are expressed in a dedicated query language. Over time, different languages have been developed for different types of data sources, for example, SQL for relational databases and XQuery for XML. This makes it necessary for the application developer to learn a new query language for each type of data source or data format that is supported.  
  
 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] simplifies the situation by offering a consistent model for working with data across various kinds of data sources and formats. 在 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查询中，始终会用到对象。 You use the same basic coding patterns to query and transform data in XML documents, SQL databases, ADO.NET datasets and entities, .NET Framework collections, and any other source or format for which a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider is available. This document describes the three phases of the creation and use of basic [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries.  
  
## <a name="three-stages-of-a-query-operation"></a>Three Stages of a Query Operation  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query operations consist of three actions:  
  
1. Obtain the data source or sources.  
  
2. 创建查询。  
  
3. 执行查询。  
  
 In [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], the execution of a query is distinct from the creation of the query. You do not retrieve any data just by creating a query. 这一点将在本主题后面部分进行更详细的讨论。  
  
 The following example illustrates the three parts of a query operation. The example uses an array of integers as a convenient data source for demonstration purposes. However, the same concepts also apply to other data sources.  
  
> [!NOTE]
> On the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), ensure that **Option infer** is set to **On**.  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 输出：  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a>数据源  
 Because the data source in the previous example is an array, it implicitly supports the generic <xref:System.Collections.Generic.IEnumerable%601> interface. It is this fact that enables you to use an array as a data source for a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query. 支持 <xref:System.Collections.Generic.IEnumerable%601> 或派生接口（如泛型 <xref:System.Linq.IQueryable%601>）的类型称为可查询类型。  
  
 As an implicitly queryable type, the array requires no modification or special treatment to serve as a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] data source. The same is true for any collection type that supports <xref:System.Collections.Generic.IEnumerable%601>, including the generic <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.Dictionary%602>, and other classes in the .NET Framework class library.  
  
 If the source data does not already implement <xref:System.Collections.Generic.IEnumerable%601>, a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider is needed to implement the functionality of the *standard query operators* for that data source. For example, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] handles the work of loading an XML document into a queryable <xref:System.Xml.Linq.XElement> type, as shown in the following example. For more information about standard query operators, see [Standard Query Operators Overview (Visual Basic)](standard-query-operators-overview.md).  
  
 [!code-vb[VbLINQFirstQuery#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#2)]  
  
 With [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], you first create an object-relational mapping at design time, either manually or by using the [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) in Visual Studio. 针对这些对象编写查询，然后由 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 在运行时处理与数据库的通信。 In the following example, `customers` represents a specific table in the database, and <xref:System.Data.Linq.Table%601> supports generic <xref:System.Linq.IQueryable%601>.  
  
```vb  
' Create a data source from a SQL table.  
Dim db As New DataContext("C:\Northwind\Northwnd.mdf")  
Dim customers As Table(Of Customer) = db.GetTable(Of Customer)  
```  
  
 有关如何创建特定类型的数据源的详细信息，请参阅各种 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 提供程序的文档。 (For a list of these providers, see [LINQ (Language-Integrated Query)](../../../../visual-basic/programming-guide/concepts/linq/index.md).) The basic rule is simple: a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] data source is any object that supports the generic <xref:System.Collections.Generic.IEnumerable%601> interface, or an interface that inherits from it.  
  
> [!NOTE]
> Types such as <xref:System.Collections.ArrayList> that support the non-generic <xref:System.Collections.IEnumerable> interface can also be used as [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] data sources. For an example that uses an <xref:System.Collections.ArrayList>, see [How to: Query an ArrayList with LINQ (Visual Basic)](how-to-query-an-arraylist-with-linq.md).  
  
## <a name="the-query"></a>The Query  
 In the query, you specify what information you want to retrieve from the data source or sources. You also have the option of specifying how that information should be sorted, grouped, or structured before it is returned. To enable query creation, Visual Basic has incorporated new query syntax into the language.  
  
 When it is executed, the query in the following example returns all the even numbers from an integer array, `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 The query expression contains three clauses: `From`, `Where`, and `Select`. The specific function and purpose of each query expression clause is discussed in [Basic Query Operations (Visual Basic)](basic-query-operations.md). For more information, see [Queries](../../../../visual-basic/language-reference/queries/index.md). Note that in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], a query definition often is stored in a variable and executed later. The query variable, such as `evensQuery` in the previous example, must be a queryable type. The type of `evensQuery` is `IEnumerable(Of Integer)`, assigned by the compiler using local type inference.  
  
 It is important to remember that the query variable itself takes no action and returns no data. It only stores the query definition. In the previous example, it is the `For Each` loop that executes the query.  
  
## <a name="query-execution"></a>查询执行  
 Query execution is separate from query creation. Query creation defines the query, but execution is triggered by a different mechanism. A query can be executed as soon as it is defined (*immediate execution*), or the definition can be stored and the query can be executed later (*deferred execution*).  
  
### <a name="deferred-execution"></a>延迟执行  
 A typical [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query resembles the one in the previous example, in which `evensQuery` is defined. It creates the query but does not execute it immediately. Instead, the query definition is stored in the query variable `evensQuery`. You execute the query later, typically by using a `For Each` loop, which returns a sequence of values, or by applying a standard query operator, such as `Count` or `Max`. This process is referred to as *deferred execution*.  
  
 [!code-vb[VbLINQFirstQuery#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#7)]  
  
 For a sequence of values, you access the retrieved data by using the iteration variable in the `For Each` loop (`number` in the previous example). Because the query variable, `evensQuery`, holds the query definition rather than the query results, you can execute a query as often as you want by using the query variable more than one time. For example, you might have a database in your application that is being updated continually by a separate application. After you have created a query that retrieves data from that database, you can use a `For Each` loop to execute the query repeatedly, retrieving the most recent data every time.  
  
 The following example demonstrates how deferred execution works. After `evensQuery2` is defined and executed with a `For Each` loop, as in the previous examples, some elements in the data source `numbers` are changed. Then a second `For Each` loop runs `evensQuery2` again. The results are different the second time, because the `For Each` loop executes the query again, using the new values in `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#3)]  
  
 输出：  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>立即执行  
 In deferred execution of queries, the query definition is stored in a query variable for later execution. In immediate execution, the query is executed at the time of its definition. Execution is triggered when you apply a method that requires access to individual elements of the query result. Immediate execution often is forced by using one of the standard query operators that return single values. Examples are `Count`, `Max`, `Average`, and `First`. These standard query operators execute the query as soon as they are applied in order to calculate and return a singleton result. For more information about standard query operators that return single values, see [Aggregation Operations](aggregation-operations.md), [Element Operations](element-operations.md), and [Quantifier Operations](quantifier-operations.md).  
  
 The following query returns a count of the even numbers in an array of integers. The query definition is not saved, and `numEvens` is a simple `Integer`.  
  
 [!code-vb[VbLINQFirstQuery#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#4)]  
  
 You can achieve the same result by using the `Aggregate` method.  
  
 [!code-vb[VbLINQFirstQuery#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#5)]  
  
 You can also force execution of a query by calling the `ToList` or `ToArray` method on a query (immediate) or query variable (deferred), as shown in the following code.  
  
 [!code-vb[VbLINQFirstQuery#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#6)]  
  
 In the previous examples, `evensQuery3` is a query variable, but `evensList` is a list and `evensArray` is an array.  
  
 Using `ToList` or `ToArray` to force immediate execution is especially useful in scenarios in which you want to execute the query immediately and cache the results in a single collection object. For more information about these methods, see [Converting Data Types](converting-data-types.md).  
  
 You can also cause a query to be executed by using an `IEnumerable` method such as the <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A> method.  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 中的 LINQ 入门](getting-started-with-linq.md)
- [局部类型推理](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [标准查询运算符概述 (Visual Basic)](standard-query-operators-overview.md)
- [Visual Basic 中的 LINQ 简介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [查询](../../../../visual-basic/language-reference/queries/index.md)
