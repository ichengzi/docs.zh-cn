---
title: How to combine LINQ queries with regular expressions
ms.date: 07/20/2015
ms.assetid: 3da1bd10-b0d8-4d5b-a637-966891c13592
ms.openlocfilehash: 27fc46056ad78567339ca0c5818aef38d0fbb9a6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348423"
---
# <a name="how-to-combine-linq-queries-with-regular-expressions-visual-basic"></a>How to combine LINQ queries with regular expressions (Visual Basic)

此示例演示如何使用 <xref:System.Text.RegularExpressions.Regex> 类在文本字符串中为更复杂的匹配创建正则表达式。 通过 LINQ 查询可以轻松地准确筛选要用正则表达式搜索的文件，并对结果进行改良。

## <a name="example"></a>示例

```vb
Imports System.IO
Imports System.Text.RegularExpressions

Class LinqRegExVB

    Shared Sub Main()

        ' Root folder to query, along with all subfolders.
        ' Modify this path as necessary so that it accesses your Visual Studio folder.
        Dim startFolder As String = "C:\Program Files (x86)\Microsoft Visual Studio 14.0\"
        ' One of the following paths may be more appropriate on your computer.
        'Dim startFolder As String = "C:\Program Files (x86)\Microsoft Visual Studio\2017\"

        ' Take a snapshot of the file system.
        Dim fileList As IEnumerable(Of FileInfo) = GetFiles(startFolder)

        ' Create a regular expression to find all things "Visual".
        Dim searchTerm As New Regex("Visual (Basic|C#|C\+\+|Studio)")

        ' Search the contents of each .htm file.
        ' Remove the where clause to find even more matches!
        ' This query produces a list of files where a match
        ' was found, and a list of the matches in that file.
        ' Note: Explicit typing of "Match" in select clause.
        ' This is required because MatchCollection is not a
        ' generic IEnumerable collection.
        Dim queryMatchingFiles = From afile In fileList
                                Where afile.Extension = ".htm"
                                Let fileText = File.ReadAllText(afile.FullName)
                                Let matches = searchTerm.Matches(fileText)
                                Where (matches.Count > 0)
                                Select Name = afile.FullName,
                                       Matches = From match As Match In matches
                                                 Select match.Value

        ' Execute the query.
        Console.WriteLine("The term " & searchTerm.ToString() & " was found in:")

        For Each fileMatches In queryMatchingFiles
            ' Trim the path a bit, then write
            ' the file name in which a match was found.
            Dim s = fileMatches.Name.Substring(startFolder.Length - 1)
            Console.WriteLine(s)

            ' For this file, write out all the matching strings
            For Each match In fileMatches.Matches
                Console.WriteLine("  " + match)
            Next
        Next

        ' Keep the console window open in debug mode
        Console.WriteLine("Press any key to exit")
        Console.ReadKey()
    End Sub

    ' Function to retrieve a list of files. Note that this is a copy
    ' of the file information.
    Shared Function GetFiles(root As String) As IEnumerable(Of FileInfo)
        Return From file In My.Computer.FileSystem.GetFiles(
                   root, FileIO.SearchOption.SearchAllSubDirectories, "*.*")
               Select New FileInfo(file)
    End Function

End Class
```

请注意，还可以查询 `RegEx` 搜索返回的 <xref:System.Text.RegularExpressions.MatchCollection> 对象。 在本例中，只在结果中生成每个匹配项的值。 但是，也可以使用 LINQ 对集合执行筛选、排序和分组等各种操作。 由于 <xref:System.Text.RegularExpressions.MatchCollection> 为非泛型 <xref:System.Collections.IEnumerable> 集合，所以必须显式声明查询中范围变量的类型。

## <a name="compiling-the-code"></a>编译代码

Create a VB.NET console application project, copy and paste the code sample, and adjust the Startup object value in the project properties.

## <a name="see-also"></a>请参阅

- [LINQ and Strings (Visual Basic)](linq-and-strings.md)
- [LINQ 和文件目录 (Visual Basic)](linq-and-file-directories.md)
