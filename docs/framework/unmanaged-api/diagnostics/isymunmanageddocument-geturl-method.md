---
title: ISymUnmanagedDocument::GetURL 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetURL
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetURL
helpviewer_keywords:
- GetURL method [.NET Framework debugging]
- ISymUnmanagedDocument::GetURL method [.NET Framework debugging]
ms.assetid: 60600178-c2b5-4cab-b3a5-f0f61acebaf1
topic_type:
- apiref
ms.openlocfilehash: 134a89d62a0fc455a9579de1e577103f1fe6abcf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449120"
---
# <a name="isymunmanageddocumentgeturl-method"></a>ISymUnmanagedDocument::GetURL 方法
Returns the uniform resource locator (URL) for this document.  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetURL(  
    [in]  ULONG32  cchUrl,  
    [out] ULONG32  *pcchUrl,  
    [out, size_is(cchUrl), length_is(*pcchUrl)] WCHAR szUrl[]);  
```  
  
## <a name="parameters"></a>参数  
 `cchUrl`  
 [in] The size, in characters, of the `szURL` buffer.  
  
 `pcchUrl`  
 [out] A pointer to a variable that receives the size of the URL, including the null termination.  
  
 `szUrl`  
 [out] The buffer containing the URL.  
  
## <a name="return-value"></a>返回值  
 S_OK if the method succeeds; otherwise, an error code.  
  
## <a name="see-also"></a>请参阅

- [ISymUnmanagedDocument 接口](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
