---
title: ASSEMBLYMETADATA 结构
ms.date: 03/30/2017
api_name:
- ASSEMBLYMETADATA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ASSEMBLYMETADATA
helpviewer_keywords:
- ASSEMBLYMETADATA structure [.NET Framework metadata]
ms.assetid: 1af98e57-9145-4d35-bb78-77d1da7c91a5
topic_type:
- apiref
ms.openlocfilehash: 24ec1f7d553a59425f7eb02af8e91010d940eb07
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444269"
---
# <a name="assemblymetadata-structure"></a>ASSEMBLYMETADATA 结构
Contains information about the referenced assembly, including its version and its level of support for locales, processors, and operating systems.  
  
## <a name="syntax"></a>语法  
  
```cpp  
typedef struct {  
    USHORT  usMajorVersion;  
    USHORT  usMinorVersion;  
    USHORT  usBuildNumber;  
    USHORT  usRevisionNumber;  
    LPWSTR  szLocale;  
    ULONG   cbLocale;  
    DWORD*  rdwProcessor[];  
    ULONG   ulProcessor  
    OSINFO* rOS[];  
    ULONG   ulOS;  
} ASSEMBLYMETADATA;  
```  
  
## <a name="members"></a>Members  
  
|成员|描述|  
|------------|-----------------|  
|`usMajorVersion`|The major version number of the referenced assembly. This value cannot be zero. If all the bits of `usMajorVersion` are set, the major version is not specified.|  
|`usMinorVersion`|The minor version number of the referenced assembly. This value cannot be zero. If all the bits of `usMinorVersion` are set, the minor version is not specified.|  
|`usBuildNumber`|The build number of the referenced assembly. This value cannot be zero. If all the bits of `usBuildNumber` are set, the build number is not specified.|  
|`usRevisionNumber`|The revision number of the referenced assembly. This value cannot be zero. If all the bits of `usRevisionNumber` are set, the revision number is not specified.|  
|`szLocale`|A list of locale names conforming to the RFC1766 specification, separated by semicolons, specifying the locales supported by the referenced assembly. A null value indicates locale independence. **Note:**  In the .NET Framework version 1.0 you cannot specify more than one locale.|  
|`cbLocale`|The size in wide characters of `szLocale`.|  
|`rdwProcessor`|An array of identifiers, as defined in Winnt.h, for the processor types that are supported by the referenced assembly. A NULL value indicates processor independence.|  
|`ulProcessor`|The length of the `rdwProcessor` array.|  
|`rOS`|An array of [OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) instances specifying the operating systems that are supported by the referenced assembly. A NULL value indicates operating-system independence.|  
|`ulOS`|The length of the `rOS` array.|  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [元数据结构](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [IMetaDataAssemblyEmit 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [OSINFO 结构](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
