---
title: -warnaserror
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: f9ca5575e2a042d68fc490494f2e86991d58b80c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351711"
---
# <a name="-warnaserror-visual-basic"></a>-warnaserror (Visual Basic)
使编译器将第一次出现的警告视为错误。  
  
## <a name="syntax"></a>语法  
  
```console  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a>自变量  
  
|术语|定义|  
|---|---|  
|+ &#124; -|可选。 默认情况下，`-warnaserror-` 生效；警告不会阻止编译器生成输出文件。 `-warnaserror` 选项与 `-warnaserror+` 相同，会导致将警告视为错误。|  
|`numberList`|可选。 `-warnaserror` 选项适用的警告 ID 编号列表，以逗号分隔。 如果未指定警告 ID，则 `-warnaserror` 选项适用于所有警告。|  
  
## <a name="remarks"></a>备注  
 `-warnaserror` 选项将所有警告视为错误。 通常将报告为警告的任何消息都报告为错误。 编译器将随后出现的相同警告报告为警告。  
  
 默认情况下，`-warnaserror-` 生效，导致警告仅提供信息。 `-warnaserror` 选项与 `-warnaserror+` 相同，会导致将警告视为错误。  
  
 如果希望仅将一些特定警告视为错误，则可以指定视为错误的警告编号的逗号分隔列表。  
  
> [!NOTE]
> `-warnaserror` 选项不控制警告的显示方式。 使用 [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) 选项来禁用警告。  
  
|设置 -warnaserror 以将所有警告视为 Visual Studio IDE 中的错误|  
|---|  
|1.  Have a project selected in **Solution Explorer**. 在“项目”菜单上，单击“属性”。 <br />2.  Click the **Compile** tab.<br />3.  Make sure the **Disable all warnings** check box is unchecked.<br />4.  Check the **Treat all warnings as errors** check box.|  
  
|设置 -warnaserror 以将特定警告视为 Visual Studio IDE 中的错误|  
|---|  
|1.  Have a project selected in **Solution Explorer**. 在“项目”菜单上，单击“属性”。<br />2.  Click the **Compile** tab.<br />3.  Make sure the **Disable all warnings** check box is unchecked.<br />4.  Make sure the **Treat all warnings as errors** check box is unchecked.<br />5.  Select **Error** from the **Notification** column adjacent to the warning that should be treated as an error.|  
  
## <a name="example"></a>示例  
 以下代码编译 `In.vb` 并指示编译器在第一次发现每个警告时显示错误。  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a>示例  
 以下代码编译 `T2.vb` 并仅将未使用的本地变量 (42024) 的警告视为错误。  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)
