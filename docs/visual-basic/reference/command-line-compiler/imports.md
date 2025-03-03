---
title: -imports
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 380e71e462f736d4564a37b83567007fa9461b05
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332958"
---
# <a name="-imports-visual-basic"></a>-imports (Visual Basic)
Imports namespaces from a specified assembly.  
  
## <a name="syntax"></a>语法  
  
```console  
-imports:namespaceList  
```  
  
## <a name="arguments"></a>自变量  
  
|术语|定义|  
|---|---|  
|`namespaceList`|必须的。 Comma-delimited list of namespaces to be imported.|  
  
## <a name="remarks"></a>备注  
 The `-imports` option imports any namespace defined within the current set of source files or from any referenced assembly.  
  
 The members in a namespace specified with `-imports` are available to all source-code files in the compilation. Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.  
  
|To set /imports in the Visual Studio integrated development environment|  
|---|  
|1.  Have a project selected in **Solution Explorer**. 在“项目”菜单上，单击“属性”。 <br />2.  Click the **References** tab.<br />3.  Enter the namespace name in the box beside the **Add User Import** button.<br />4.  Click the **Add User Import** button.|  
  
## <a name="example"></a>示例  
 The following code compiles when `/imports:system.globalization` is specified. Without it, successful compilation requires either that an `Imports System.Globalization` statement be included at the beginning of the source code file, or that the property be fully qualified as `System.Globalization.CultureInfo.CurrentCulture.Name`.

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [引用和 Imports 语句](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
