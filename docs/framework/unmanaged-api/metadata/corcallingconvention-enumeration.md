---
title: CorCallingConvention 枚举
ms.date: 03/30/2017
api_name:
- CorCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCallingConvention
helpviewer_keywords:
- CorCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 69156fbf-7219-43bf-b4b8-b13f1a2fcb86
topic_type:
- apiref
ms.openlocfilehash: 9d4690cb6adedc77717e577d409cb52b18b1b5ca
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443832"
---
# <a name="corcallingconvention-enumeration"></a>CorCallingConvention 枚举
包含一些值，用于描述托管代码中执行的调用约定类型。  
  
## <a name="syntax"></a>语法  
  
```cpp  
typedef enum CorCallingConvention  
{  
    IMAGE_CEE_CS_CALLCONV_DEFAULT       = 0x0,  
  
    IMAGE_CEE_CS_CALLCONV_VARARG        = 0x5,  
    IMAGE_CEE_CS_CALLCONV_FIELD         = 0x6,  
    IMAGE_CEE_CS_CALLCONV_LOCAL_SIG     = 0x7,  
    IMAGE_CEE_CS_CALLCONV_PROPERTY      = 0x8,  
    IMAGE_CEE_CS_CALLCONV_UNMGD         = 0x9,  
    IMAGE_CEE_CS_CALLCONV_GENERICINST   = 0xa,  
    IMAGE_CEE_CS_CALLCONV_NATIVEVARARG  = 0xb,  
    IMAGE_CEE_CS_CALLCONV_MAX           = 0xc,  
  
    IMAGE_CEE_CS_CALLCONV_MASK          = 0x0f,  
    IMAGE_CEE_CS_CALLCONV_HASTHIS       = 0x20,  
    IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS  = 0x40,  
    IMAGE_CEE_CS_CALLCONV_GENERIC       = 0x10  
  
} CorCallingConvention;  
```  
  
## <a name="members"></a>Members  
  
|成员|描述|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|Indicates a default calling convention.|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|Indicates that the method takes a variable number of parameters.|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|Indicates that the call is to a field.|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|Indicates that the call is to a local method.|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|Indicates that the call is to a property.|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|Indicates that the call is unmanaged.|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|Indicates a generic method instantiation.|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|Indicates a 64-bit PInvoke call to a method that takes a variable number of parameters.|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|Describes an invalid 4-bit value.|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|Indicates that the calling convention is described by the bottom four bits.|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|Indicates that the top bit describes a `this` parameter.|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|Indicates that a `this` parameter is explicitly described in the signature.|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|Indicates a generic method signature with an explicit number of type arguments. This precedes an ordinary parameter count.|  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **Header:** CorHdr.h  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [Metadata 枚举](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
