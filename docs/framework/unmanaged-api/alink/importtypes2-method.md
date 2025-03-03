---
title: ImportTypes2 方法
ms.date: 03/30/2017
api_name:
- IALink2.ImportTypes2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes2
helpviewer_keywords:
- ImportTypes2 method
ms.assetid: 32f3ba58-9695-41e9-ba58-fd19e45ed396
topic_type:
- apiref
ms.openlocfilehash: 8dae903ab76ab83ac0818c4bc4a76e81094bdf65
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445664"
---
# <a name="importtypes2-method"></a>ImportTypes2 方法
Initiates the import of types. Call this method to begin importing types from each scope imported via [ImportFile Method](importfile-method.md).  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT ImportTypes2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport2** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a>参数  
 `AssemblyID`  
 ID of assembly into which to import.  
  
 `FileToken`  
 ID of file to from which to import.  
  
 `dwScope`  
 Zero-based scope from which to import.  
  
 `phEnum`  
 Receives enumerator handle for the types in the given scope.  
  
 `ppImportScope`  
 Optionally receives [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface.  
  
 `pdwCountOfTypes`  
 Optionally receives count of types in the specified scope.  
  
## <a name="return-value"></a>返回值  
 Returns S_OK if the method succeeds.  
  
## <a name="requirements"></a>要求  
 Requires alink.h  
  
## <a name="see-also"></a>请参阅

- [IALink2 接口](ialink2-interface.md)
- [IALink 接口](ialink-interface.md)
- [ALink API](index.md)
