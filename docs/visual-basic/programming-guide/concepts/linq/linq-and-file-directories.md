---
title: LINQ 和文件目录
ms.date: 07/20/2015
ms.assetid: 159fd5c3-3926-4071-ae78-d8e423287eb7
ms.openlocfilehash: 390d3c7a1c738aea0df8e3dcad0edb70563f8fb6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347789"
---
# <a name="linq-and-file-directories-visual-basic"></a>LINQ and File Directories (Visual Basic)
许多文件系统操作实质上是查询，因此非常适合使用 LINQ 方法。  
  
 请注意，本部分中的查询是非破坏性查询。 它们不用于更改原始文件或文件夹的内容。 这遵循了查询不应引起任何副作用这条规则。 通常，修改源数据的任何代码（包括执行创建/更新/删除运算符的查询）应与只查询数据的代码分开。  
  
 本节包含下列主题：  
  
 [How to: Query for Files with a Specified Attribute or Name (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 演示如何通过检查文件的 <xref:System.IO.FileInfo> 对象的一个或多个属性来搜索文件。  
  
 [How to: Group Files by Extension (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 演示如何根据文件扩展名返回 <xref:System.IO.FileInfo> 对象组。  
  
 [How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)  
 演示如何返回指定目录树中所有文件的总字节数。  
  
 [How to: Compare the Contents of Two Folders (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s  
 演示如何返回位于两个指定文件夹中的所有文件，以及仅位于其中一个文件夹中的所有文件。  
  
 [How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 演示如何返回目录树中的最大文件、最小文件或指定数量的文件。  
  
 [How to: Query for Duplicate Files in a Directory Tree (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 演示如何对出现在指定目录树中多个位置的所有文件名进行分组。 此外，还演示如何根据自定义比较器执行更复杂的比较。  
  
 [How to query the contents of files in a folder (LINQ) (Visual Basic)](how-to-query-the-contents-of-files-in-a-folder-linq.md)  
 演示如何循环访问树中的文件夹，打开每个文件以及查询文件的内容。  
  
## <a name="comments"></a>注释  
 创建准确表示文件系统的内容并适当处理异常的数据源，存在一定难度。 本部分中的示例创建 <xref:System.IO.FileInfo> 对象的快照集合，该集合表示指定的根文件夹及其所有子文件夹下的所有文件。 每个 <xref:System.IO.FileInfo> 的实际状态可能会在开始和结束执行查询期间发生更改。 例如，可以创建 <xref:System.IO.FileInfo> 对象的列表来用作数据源。 如果尝试通过查询访问 `Length` 属性，则 <xref:System.IO.FileInfo> 对象会尝试访问文件系统来更新 `Length` 的值。 如果该文件不再存在，则你会在查询中获得 <xref:System.IO.FileNotFoundException>，即使未直接查询文件系统也是如此。 本部分中的一些查询使用不同的方法，在某些情况下使用该方法不会出现这些特定异常。 另一种方法是使用 <xref:System.IO.FileSystemWatcher> 保持数据源动态更新。  
  
## <a name="see-also"></a>请参阅

- [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
