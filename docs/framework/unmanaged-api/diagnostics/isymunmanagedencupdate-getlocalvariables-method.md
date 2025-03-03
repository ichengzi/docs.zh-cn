---
title: ISymUnmanagedENCUpdate::GetLocalVariables 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables method [.NET Framework debugging]
- GetLocalVariables method [.NET Framework debugging]
ms.assetid: 5c8840be-ffea-447f-9c8d-178f1eaf8d06
topic_type:
- apiref
ms.openlocfilehash: b5fc8b6807a4c8eb700ab3fa181a216e48a732ff
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449029"
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a>ISymUnmanagedENCUpdate::GetLocalVariables 方法
Gets the local variables.  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
## <a name="parameters"></a>参数  
 `mdMethodToken`  
 [in] The metadata token of the method.  
  
 `cLocals`  
 [in] A `ULONG` that indicates the size of the `rgLocals` parameter.  
  
 `rgLocals`  
 [out] The returned array of [ISymUnmanagedVariable](isymunmanagedvariable-interface.md) instances.  
  
 `pceltFetched`  
 [out] A pointer to a `ULONG` that receives the size of the `rgLocals` buffer required to contain the locals.  
  
## <a name="return-value"></a>返回值  
 S_OK if the method succeeds; otherwise, E_FAIL or some other error code.  
  
## <a name="requirements"></a>要求  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>请参阅

- [ISymUnmanagedENCUpdate 接口](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
