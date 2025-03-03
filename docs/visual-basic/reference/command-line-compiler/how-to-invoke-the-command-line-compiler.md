---
title: 如何：调用命令行编译器
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: 3b34ebba68c9c9b2a8335822d0ffaef2a9b06d7c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344262"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a>如何：调用命令行编译器 (Visual Basic)

You can invoke the command-line compiler by typing the name of its executable file into the command line, also known as the MS-DOS prompt. If you compile from the default Windows Command Prompt, you must type the fully qualified path to the executable file. To override this default behavior, you can either use the Developer Command Prompt for Visual Studio, or modify the PATH environment variable. Both allow you to compile from any directory by simply typing the compiler name.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a>To invoke the compiler using the Developer Command Prompt for Visual Studio

1. Open the Visual Studio Tools program folder within the Microsoft Visual Studio program group.

2. You can use the Developer Command Prompt for Visual Studio to access the compiler from any directory on your machine, if Visual Studio is installed.

3. Invoke the Developer Command Prompt for Visual Studio.

4. At the command line, type `vbc.exe` *sourceFileName* and then press ENTER.

    For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory. If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.

## <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a>To set the PATH environment variable to the compiler for the Windows Command Prompt

1. Use the Windows Search feature to find Vbc.exe on your local disk.

    The exact name of the directory where the compiler is located depends on the location of the Windows directory and the version of the ".NET Framework" installed. If you have more than one version of the ".NET Framework" installed, you must determine which version to use (typically the latest version).

2. From your **Start** Menu, right-click **My Computer**, and then click **Properties** from the shortcut menu.

3. Click the **Advanced** tab, and then click **Environment Variables**.

4. In the **System** variables pane, select **Path** from the list and click **Edit**.

5. In the **Edit System** Variable dialog box, move the insertion point to the end of the string in the **Variable Value** field and type a semicolon (;) followed by the full directory name found in Step 1.

6. Click **OK** to confirm your edits and close the dialog boxes.

     After you change the PATH environment variable, you can run the Visual Basic compiler at the Windows Command Prompt from any directory on the computer.

## <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a>To invoke the compiler using the Windows Command Prompt

1. From the **Start** menu, click on the **Accessories** folder, and then open the **Windows Command Prompt**.

2. At the command line, type `vbc.exe`*sourceFileName* and then press ENTER.

     For example, if you stored your source code in a directory called `SourceFiles`, you would open the Command Prompt and type `cd SourceFiles` to change to that directory. If the directory contained a source file named `Source.vb`, you could compile it by typing `vbc.exe Source.vb`.

## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [条件编译](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
