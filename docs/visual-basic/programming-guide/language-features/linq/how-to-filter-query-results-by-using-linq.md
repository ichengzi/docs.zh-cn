---
title: 'How to: Filter Query Results by Using LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- filtering [Visual Basic]
- filtering data [LINQ in Visual Basic]
- filtering [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], filtering results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- filtering data [Visual Basic]
ms.assetid: ef103092-9bed-4134-97f4-2db696e83c12
ms.openlocfilehash: 2ea8a852a2f012ddb25ec1198c66e09df880ff47
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344993"
---
# <a name="how-to-filter-query-results-by-using-linq-visual-basic"></a>如何：使用 LINQ 筛选查询结果 (Visual Basic)

Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.

The following example shows how to create a new application that performs queries against a SQL Server database and filters the results by a particular value by using the `Where` clause. For more information, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).

The examples in this topic use the Northwind sample database. If you do not have this database on your development computer, you can download it from the Microsoft Download Center. For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-connection-to-a-database"></a>To create a connection to a database

1. In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.

2. Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.

3. Specify a valid connection to the Northwind sample database.

## <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>To add a project that contains a LINQ to SQL file

1. 在 Visual Studio 中的“文件”菜单上，指向“新建”，然后单击“项目”。 Select Visual Basic **Windows Forms Application** as the project type.

2. 在 **“项目”** 菜单上，单击 **“添加新项”** 。 Select the **LINQ to SQL Classes** item template.

3. 为 `northwind.dbml` 文件命名。 单击 **添加**。 The Object Relational Designer (O/R Designer) opens for the northwind.dbml file.

## <a name="to-add-tables-to-query-to-the-or-designer"></a>To add tables to query to the O/R Designer

1. In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database. Expand the **Tables** folder.

     If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.

2. Click the Customers table and drag it to the left pane of the designer. Click the Orders table and drag it to the left pane of the designer.

     The designer creates new `Customer` and `Order` objects for your project. Notice that the designer automatically detects relationships between the tables and creates child properties for related objects. For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.

3. Save your changes and close the designer.

4. 保存你的项目。

## <a name="to-add-code-to-query-the-database-and-display-the-results"></a>To add code to query the database and display the results

1. From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.

2. Double-click Form1 to add code to the `Load` event of the form.

3. When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project. This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table. The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file. For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.

    You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.

    Add the following code to the `Load` event to query the tables that are exposed as properties of your data context. The query filters the results and returns only customers that are located in `London`.

    [!code-vb[VbLINQToSQLHowTos#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#11)]

4. Press F5 to run your project and view the results.

5. Following are some other filters that you can try.

    [!code-vb[VbLINQToSQLHowTos#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#12)]

## <a name="see-also"></a>请参阅

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [查询](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext 方法（O/R 设计器）](/visualstudio/data-tools/datacontext-methods-o-r-designer)
