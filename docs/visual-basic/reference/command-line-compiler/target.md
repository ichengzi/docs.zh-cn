---
title: -target
ms.date: 03/13/2018
helpviewer_keywords:
- target compiler options [Visual Basic]
- -target compiler options [Visual Basic]
- /target compiler options [Visual Basic]
ms.assetid: e0954147-548b-461f-9c4b-a8f88845616c
ms.openlocfilehash: bd79d95a18fb1935d97fff2d1b2c7767752b9765
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351721"
---
# <a name="-target-visual-basic"></a>-target (Visual Basic)

Specifies the format of compiler output.

## <a name="syntax"></a>语法

```console
-target:{exe | library | module | winexe | appcontainerexe | winmdobj}
```

## <a name="remarks"></a>备注

The following table summarizes the effect of the `-target` option.

|**选项**|**行为**|
|----------------|------------------|
|`-target:exe`|Causes the compiler to create an executable console application.<br /><br /> This is the default option when no `-target` option is specified. The executable file is created with an .exe extension.<br /><br /> Unless otherwise specified with the `/out` option, the output file name takes the name of the input file that contains the `Sub Main` procedure.<br /><br /> Only one `Sub Main` procedure is required in the source-code files that are compiled into an .exe file. Use the `-main` compiler option to specify which class contains the `Sub Main` procedure.|
|`-target:library`|Causes the compiler to create a dynamic-link library (DLL).<br /><br /> The dynamic-link library file is created with a .dll extension.<br /><br /> Unless otherwise specified with the `-out` option, the output file name takes the name of the first input file.<br /><br /> When building a DLL, a `Sub Main` procedure is not required.|
|`-target:module`|Causes the compiler to generate a module that can be added to an assembly.<br /><br /> The output file is created with an extension of .netmodule.<br /><br /> The .NET common language runtime cannot load a file that does not have an assembly. However, you can incorporate such a file into the assembly manifest of an assembly by using `-reference`.<br /><br /> When code in one module references internal types in another module, both modules must be incorporated into an assembly manifest by using `-reference`.<br /><br /> The [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) option imports metadata from a module.|
|`-target:winexe`|Causes the compiler to create an executable Windows-based application.<br /><br /> The executable file is created with an .exe extension. A Windows-based application is one that provides a user interface from either the .NET Framework class library or with the Windows APIs.<br /><br /> Unless otherwise specified with the `-out` option, the output file name takes the name of the input file that contains the `Sub Main` procedure.<br /><br /> Only one `Sub Main` procedure is required in the source-code files that are compiled into an .exe file. In cases where your code has more than one class that has a `Sub Main` procedure, use the `-main` compiler option to specify which class contains the `Sub Main` procedure|
|`-target:appcontainerexe`|Causes the compiler to create an executable Windows-based application that must be run in an app container. This setting is designed to be used for Windows 8.x Store applications.<br /><br /> The **appcontainerexe** setting sets a bit in the Characteristics field of the [Portable Executable](/windows/desktop/Debug/pe-format) file. This bit indicates that the app must be run in an app container. When this bit is set, an error occurs if the `CreateProcess` method tries to launch the application outside of an app container. Aside from this bit setting, **-target:appcontainerexe** is equivalent to **-target:winexe**.<br /><br /> The executable file is created with an .exe extension.<br /><br /> Unless you specify otherwise by using the `-out` option, the output file name takes the name of the input file that contains the `Sub Main` procedure.<br /><br /> Only one `Sub Main` procedure is required in the source-code files that are compiled into an .exe file. If your code contains more than one class that has a `Sub Main` procedure, use the `-main` compiler option to specify which class contains the `Sub Main` procedure|
|`-target:winmdobj`|Causes the compiler to create an intermediate file that you can convert to a Windows Runtime binary (.winmd) file. The .winmd file can be consumed by JavaScript and C++ programs, in addition to managed language programs.<br /><br /> The intermediate file is created with a .winmdobj extension.<br /><br /> Unless you specify otherwise by using the `-out` option, the output file name takes the name of the first input file. A `Sub Main` procedure isn’t required.<br /><br /> The .winmdobj file is designed to be used as input for the <xref:Microsoft.Build.Tasks.WinMDExp> export tool to produce a Windows metadata (WinMD) file. The WinMD file has a .winmd extension and contains both the code from the original library and the WinMD definitions that JavaScript, C++, and  the Windows Runtime use.|

Unless you specify `-target:module`, `-target` causes a .NET Framework assembly manifest to be added to an output file.

Each instance of Vbc.exe produces, at most, one output file. If you specify a compiler option such as `-out` or `-target` more than one time, the last one the compiler processes is put into effect. Information about all files in a compilation is added to the manifest. All output files except those created with `-target:module` contain assembly metadata in the manifest. Use [Ildasm.exe (IL Disassembler)](../../../framework/tools/ildasm-exe-il-disassembler.md) to view the metadata in an output file.

`-target` 的缩写形式是 `-t`。

### <a name="to-set--target-in-the-visual-studio-ide"></a>To set -target in the Visual Studio IDE

1. 在 “解决方案资源管理器”中选择一个项目。 在“项目”菜单上，单击“属性”。

2. 单击“应用程序” 选项卡。

3. Modify the value in the **Application Type** box.

## <a name="example"></a>示例

The following code compiles `in.vb`, creating `in.dll`:

```console
vbc -target:library in.vb
```

## <a name="see-also"></a>请参阅

- [Visual Basic 命令行编译器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-main](../../../visual-basic/reference/command-line-compiler/main.md)
- [-out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)
- [-reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)
- [.NET 中的程序集](../../../standard/assembly/index.md)
- [示例编译命令行](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
