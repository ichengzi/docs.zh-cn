---
title: COR_PRF_STATIC_TYPE 枚举
ms.date: 03/30/2017
api_name:
- COR_PRF_STATIC_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_STATIC_TYPE
helpviewer_keywords:
- COR_PRF_STATIC_TYPE enumeration [.NET Framework profiling]
ms.assetid: 441d7809-5b65-41a5-ba64-2910a8008315
topic_type:
- apiref
ms.openlocfilehash: 40efe81f72a2043503bf521e3e47dad1a7f4530c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448449"
---
# <a name="cor_prf_static_type-enumeration"></a>COR_PRF_STATIC_TYPE 枚举
指示字段是否为静态的，并在字段为静态字段时指示应用于该字段的静态质量。 These values can be combined using the bitwise OR operation to indicate that the field has multiple, different static qualities.  
  
## <a name="syntax"></a>语法  
  
```cpp  
typedef enum {  
    COR_PRF_FIELD_NOT_A_STATIC = 0x0,  
    COR_PRF_FIELD_APP_DOMAIN_STATIC = 0x1,  
    COR_PRF_FIELD_THREAD_STATIC = 0x2,  
    COR_PRF_FIELD_CONTEXT_STATIC = 0x4,  
    COR_PRF_FIELD_RVA_STATIC = 0x8  
} COR_PRF_STATIC_TYPE;  
```  
  
## <a name="members"></a>Members  
  
|成员|描述|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|The field is not static.|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|The field is application domain-static.|  
|`COR_PRF_FIELD_THREAD_STATIC`|The field is thread-static.|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|The field is context-static.|  
|`COR_PRF_FIELD_RVA_STATIC`|The field is relative virtual address (RVA)-static.|  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **头文件：** CorProf.idl、CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [分析枚举](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
