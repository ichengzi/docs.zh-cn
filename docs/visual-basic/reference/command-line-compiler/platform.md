---
title: -platform
ms.date: 03/13/2018
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
ms.openlocfilehash: a6226b73d5d5d4d48a71afe39e8a546019d4c0bc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352343"
---
# <a name="-platform-visual-basic"></a>-platform (Visual Basic)
指定公共语言运行时 (CLR) 的哪个平台版本可以运行输出文件。  
  
## <a name="syntax"></a>语法  
  
```console  
-platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a>自变量  
  
|术语|定义|  
|---|---|  
|`x86`|将程序集编译成可由 32 位、x86 可兼容 CLR 运行。|  
|`x64`|将程序集编译成可由支持 AMD64 或 EM64T 指令集的计算机上的 64 位 CLR 运行。|  
|`Itanium`|将程序集编译成可由配有 Itanium 处理器的计算机上的 64 位 CLR 运行。|  
|`arm`|将程序集编译成可在配有高级 RISC 计算机 (ARM) 处理器的计算机上运行。|  
|`anycpu`|将程序集编译成可在任意平台上运行。 应用程序将作为 32 位应用程序在 Windows 的 32 位版本上运行，作为 64 位应用程序在 Windows 的 64 位版本上运行。 此标志为默认值。|  
|`anycpu32bitpreferred`|将程序集编译成可在任意平台上运行。 应用程序将作为 32 位 应用程序在 Windows 的 32 位版本和 64 位版本上运行。 This flag is valid only for executables (.EXE) and requires .NET Framework 4.5.|  
  
## <a name="remarks"></a>备注  
 使用 `-platform` 选项来指定输出文件所面向的处理器类型。  
  
 通常，无论平台如何，Visual Basic 内编写的 .NET Framework 程序集将运行相同内容。 但是，存在一些不同平台行为不同的情况。 这些常见的情况是：  
  
- 结构中包含大小随平台而改变的成员，如任何指针类型。  
  
- 指针算术包含固定大小。  
  
- 平台调用错误，或使用句柄的 `Integer` 而非 <xref:System.IntPtr> 的 COM 声明不正确。  
  
- 将 <xref:System.IntPtr> 强制转换为 `Integer`。  
  
- 将平台调用或 COM 互操作与不存在于任何平台的组件一起使用。  
  
 The **-platform** option will mitigate some issues if you know you have made assumptions about the architecture your code will run on. 尤其是在下列情况下：  
  
- 如果你针对 64 位平台且应用程序在 32 位计算机上运行，则相对于不使用此开关而出现的错误，此错误消息更早出现且更加针对问题。  
  
- 如果你在选项上设置 `x86` 标志且之后应用程序在 64 位计算机上运行，则应用程序将在 WOW 子系统中运行而不是在本机上运行。  
  
 在 64 位 Windows 操作系统上：  
  
- 用 `-platform:x86` 编译的程序集将在 WOW64 下运行的 32 位 CLR 上执行。  
  
- 用 `-platform:anycpu` 编译的可执行文件将在 64 位 CLR 上执行。  
  
- 用 `-platform:anycpu` 编译的 DLL 将在加载它的进程所在的同一 CLR 上执行。  
  
- 用 `-platform:anycpu32bitpreferred` 编译的可执行文件将在 32 位 CLR 上执行。  
  
 For more information about how to develop an application to run on a 64-bit version of Windows, see [64-bit Applications](../../../framework/64-bit-apps.md).  
  
### <a name="to-set--platform-in-the-visual-studio-ide"></a>To set -platform in the Visual Studio IDE  
  
1. In **Solution Explorer**, choose the project, open the **Project** menu, and then click **Properties**.  
  
2. On the **Compile** tab, select or clear the **Prefer 32-bit** check box, or, in the **Target CPU** list, choose a value.  
  
     For more information, see [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
## <a name="example"></a>示例  
 下例阐释使用 `-platform` 编译器选项的方式。  
  
```console
vbc -platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a>请参阅

- [-target (Visual Basic)](target.md)
- [Visual Basic 命令行编译器](index.md)
- [示例编译命令行](sample-compilation-command-lines.md)
