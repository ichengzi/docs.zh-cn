---
title: ISymUnmanagedVariable::GetAttributes 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAttributes
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAttributes
helpviewer_keywords:
- GetAttributes method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAttributes method [.NET Framework debugging]
ms.assetid: 80f168af-a6a6-4c8f-b9e6-8a82dc834ed5
topic_type:
- apiref
ms.openlocfilehash: cfc28dfcda7bf4b3d1fc6fe3530a212ee76fadd2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446087"
---
# <a name="isymunmanagedvariablegetattributes-method"></a>ISymUnmanagedVariable::GetAttributes 方法
Gets the attribute flags for this variable.  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a>参数  
 `pRetVal`  
 [out] A pointer to a `ULONG32` that receives the attributes. The returned value will be one of the values defined in the [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) enumeration.  
  
## <a name="return-value"></a>返回值  
 S_OK if the method succeeds; otherwise, E_FAIL or some other error code.  
  
## <a name="requirements"></a>要求  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>请参阅

- [ISymUnmanagedVariable 接口](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
