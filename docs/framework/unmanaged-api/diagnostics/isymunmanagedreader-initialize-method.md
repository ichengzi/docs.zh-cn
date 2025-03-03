---
title: ISymUnmanagedReader::Initialize 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::Initialize
helpviewer_keywords:
- ISymUnmanagedReader::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 8f0dd2fe-7df7-464e-91f4-5518c586bb5f
topic_type:
- apiref
ms.openlocfilehash: ca34d1d84d6f9960d021c35566f8412df321464d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429748"
---
# <a name="isymunmanagedreaderinitialize-method"></a>ISymUnmanagedReader::Initialize 方法
Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.  
  
> [!NOTE]
> This method can be called only once, and must be called before any other reader methods.  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a>参数  
 `importer`  
 [in] The metadata importer interface with which this reader will be associated.  
  
 `filename`  
 [in] The file name of the module. You can use the `pIStream` parameter instead.  
  
 `searchPath`  
 [in] The path to search. 此参数可选。  
  
 `pIStream`  
 [in] The file stream, used as an alternative to the filename parameter.  
  
## <a name="return-value"></a>返回值  
 S_OK if the method succeeds; otherwise, E_FAIL or some other error code.  
  
## <a name="remarks"></a>备注  
 You need to specify only one of the `filename` or the `pIStream` parameters, not both. `searchPath` 参数是可选的。  
  
## <a name="requirements"></a>要求  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>请参阅

- [ISymUnmanagedReader 接口](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
