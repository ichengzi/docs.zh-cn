---
title: GetScope 方法
ms.date: 03/30/2017
api_name:
- IALink.GetScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope
helpviewer_keywords:
- GetScope method
ms.assetid: e1555328-2c71-4ece-b357-9eb6d3a8efc4
topic_type:
- apiref
ms.openlocfilehash: 078168ae8860f18ff6f811dcc972e3eb3c857e1d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447207"
---
# <a name="getscope-method"></a>GetScope 方法
Gets an import scope.  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
## <a name="parameters"></a>参数  
 `AssemblyID`  
 Unique ID of assembly to import to.  
  
 `FileToken`  
 Unique ID of the file to import from.  
  
 `dwScope`  
 Zero-based scope to import.  
  
 `ppImportScope`  
 Receives [IMetaDataImport Interface](../metadata/imetadataimport-interface.md) interface for the scope.  
  
## <a name="return-value"></a>返回值  
 Returns S_OK if the method succeeds.  
  
## <a name="requirements"></a>要求  
 Requires alink.h  
  
## <a name="see-also"></a>请参阅

- [IALink 接口](ialink-interface.md)
- [IALink2 接口](ialink2-interface.md)
- [ALink API](index.md)
