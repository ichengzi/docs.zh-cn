---
title: AssemblyAttributesGoHereSM Class (System.Runtime.CompilerServices)
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHereSM
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHereSM
helpviewer_keywords:
- AssemblyAttributesGoHereSM type
- Alink API, AssemblyAttributesGoHereSM type
ms.assetid: 4cf9bf39-1527-49e0-a0e9-55e7a018bf66
topic_type:
- apiref
ms.openlocfilehash: 379ba20ebf675bec71e6e5f5bcfc0dc2fbd1f92c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446609"
---
# <a name="assemblyattributesgoheresm-class"></a>AssemblyAttributesGoHereSM Class

由 ALink 用作占位符以存储有关自定义特性的信息。

## <a name="syntax"></a>语法

```csharp
internal sealed class AssemblyAttributesGoHereSM
```

## <a name="remarks"></a>备注

对此类型的引用可能被嵌入网络模块内，模块的源包含程序集自定义属性。 当从一个或多个包含对这些类型的引用的网络模块生成程序集清单时，ALink 将使用附加到这些引用的信息来发出实际的自定义属性。 因此，此类型永远不会被实例化，而且对它的引用仅用作生成过程的一部分，在最终的程序集中不具有任何用途。

对此类型的引用指示了安全性相关的多用途自定义属性。

These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.

## <a name="requirements"></a>要求

mscorlib.dll

## <a name="see-also"></a>请参阅

- [AssemblyAttributesGoHere](assemblyattributesgohere.md)
- [AssemblyAttributesGoHereM](assemblyattributesgoherem.md)
- [AssemblyAttributesGoHereS](assemblyattributesgoheres.md)
