---
title: -nostdlib
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: db6b047f521d8ef44d2bd1b70b654a4233ebb1a7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347916"
---
# <a name="-nostdlib-visual-basic"></a>-nostdlib (Visual Basic)
Causes the compiler not to automatically reference the standard libraries.  
  
## <a name="syntax"></a>语法  
  
```console  
-nostdlib  
```  
  
## <a name="remarks"></a>备注  
 The `-nostdlib` option removes the automatic reference to the System.dll assembly and prevents the compiler from reading the Vbc.rsp file. The Vbc.rsp file, which is located in the same directory as the Vbc.exe file, references the commonly used .NET Framework assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.  
  
> [!NOTE]
> The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.  
  
> [!NOTE]
> The `-nostdlib` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.  
  
## <a name="example"></a>示例  
 The following code compiles `T2.vb` without referencing the standard libraries. You must set the `_MYTYPE` conditional-compilation constant to the string "Empty" to remove the `My` object.  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>请参阅

- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [自定义 My 中可用的对象](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
