---
title: COM 互操作介绍
ms.date: 07/20/2015
helpviewer_keywords:
- interop assemblies
- COM interop [Visual Basic], about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
ms.openlocfilehash: c7909b3b6a2c9f0b397b9621b7e5125c232be313
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353198"
---
# <a name="introduction-to-com-interop-visual-basic"></a>COM 互操作介绍 (Visual Basic)
The Component Object Model (COM) lets an object expose its functionality to other components and to host applications. While COM objects have been fundamental to Windows programming for many years, applications designed for the common language runtime (CLR) offer many advantages.  
  
 .NET Framework applications will eventually replace those developed with COM. Until then, you may have to use or create COM objects by using Visual Studio. Interoperability with COM, or *COM interop*, enables you to use existing COM objects while transitioning to the .NET Framework at your own pace.  
  
 By using the .NET Framework to create COM components, you can use registration-free COM interop. This lets you control which DLL version is enabled when more than one version is installed on a computer, and lets end users use XCOPY or FTP to copy your application to an appropriate directory on their computer where it can be run. For more information, see [Registration-Free COM Interop](../../../framework/interop/registration-free-com-interop.md).  
  
## <a name="managed-code-and-data"></a>Managed Code and Data  
 Code developed for the .NET Framework is referred to as *managed code*, and contains metadata that is used by the CLR. Data used by .NET Framework applications is called *managed data* because the runtime manages data-related tasks such as allocating and reclaiming memory and performing type checking. By default, Visual Basic .NET uses managed code and data, but you can access the unmanaged code and data of COM objects using interop assemblies (described later on this page).  
  
## <a name="assemblies"></a>程序集  
 An assembly is the primary building block of a .NET Framework application. It is a collection of functionality that is built, versioned, and deployed as a single implementation unit containing one or more files. Each assembly contains an assembly manifest.  
  
## <a name="type-libraries-and-assembly-manifests"></a>Type Libraries and Assembly Manifests  
 Type libraries describe characteristics of COM objects, such as member names and data types. Assembly manifests perform the same function for .NET Framework applications. They include information about the following:  
  
- Assembly identity, version, culture, and digital signature.  
  
- Files that make up the assembly implementation.  
  
- Types and resources that make up the assembly. This includes those that are exported from it.  
  
- Compile-time dependencies on other assemblies.  
  
- Permissions required for the assembly to run correctly.  
  
 For more information about assemblies and assembly manifests, see [Assemblies in .NET](../../../standard/assembly/index.md).  
  
### <a name="importing-and-exporting-type-libraries"></a>Importing and Exporting Type Libraries  
 Visual Studio contains a utility, Tlbimp, that lets you import information from a type library into a .NET Framework application. You can generate type libraries from assemblies by using the Tlbexp utility.  
  
 For information about Tlbimp and Tlbexp, see [Tlbimp.exe (Type Library Importer)](../../../framework/tools/tlbimp-exe-type-library-importer.md) and [Tlbexp.exe (Type Library Exporter)](../../../framework/tools/tlbexp-exe-type-library-exporter.md).  
  
## <a name="interop-assemblies"></a>Interop Assemblies  
 Interop assemblies are .NET Framework assemblies that bridge between managed and unmanaged code, mapping COM object members to equivalent .NET Framework managed members. Interop assemblies created by Visual Basic .NET handle many of the details of working with COM objects, such as interoperability marshaling.  
  
## <a name="interoperability-marshaling"></a>Interoperability Marshaling  
 All .NET Framework applications share a set of common types that enable interoperability of objects, regardless of the programming language that is used. The parameters and return values of COM objects sometimes use data types that differ from those used in managed code. *Interoperability marshaling* is the process of packaging parameters and return values into equivalent data types as they move to and from COM objects. For more information, see [Interop Marshaling](../../../framework/interop/interop-marshaling.md).  
  
## <a name="see-also"></a>请参阅

- [COM 互操作](../../../visual-basic/programming-guide/com-interop/index.md)
- [演练：使用 COM 对象实现继承](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [与非托管代码交互操作](../../../framework/interop/index.md)
- [互操作性疑难解答](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
- [.NET 中的程序集](../../../standard/assembly/index.md)
- [Tlbimp.exe（类型库导入程序）](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe（类型库导出程序）](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [互操作封送处理](../../../framework/interop/interop-marshaling.md)
- [免注册 COM 互操作](../../../framework/interop/registration-free-com-interop.md)
