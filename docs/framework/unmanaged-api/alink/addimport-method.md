---
title: AddImport 方法
ms.date: 03/30/2017
api_name:
- AddImport
- IALink.AddImport
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddImport
helpviewer_keywords:
- AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type:
- apiref
ms.openlocfilehash: 52e52ac62e2dcfeb182da3014a863409f640274e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446656"
---
# <a name="addimport-method"></a>AddImport 方法
Adds imports to the assembly.  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a>参数  
 `AssemblyID`  
 Unique ID of assembly to be augmented.  
  
 `ImportToken`  
 Unique ID, retrieved from [ImportFile Method](importfile-method.md), of file to be imported.  
  
 `dwFlags`  
 COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`. `dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).  
  
 `pFileToken`  
 Pointer to token that receives the ID for the resulting file.  
  
## <a name="return-value"></a>返回值  
 Returns S_OK if the method succeeds.  
  
## <a name="requirements"></a>要求  
 Requires alink.h  
  
## <a name="see-also"></a>请参阅

- [IALink 接口](ialink-interface.md)
- [IALink2 接口](ialink2-interface.md)
- [ALink API](index.md)
