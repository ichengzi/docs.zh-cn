---
title: IMetaDataEmit::DefineParam 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineParam
helpviewer_keywords:
- IMetaDataEmit::DefineParam method [.NET Framework metadata]
- DefineParam method [.NET Framework metadata]
ms.assetid: d86a3d14-4796-4909-9591-dfafe3de5ce4
topic_type:
- apiref
ms.openlocfilehash: 5c81bc82e19bce658336e4860a61f2721e17423d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431688"
---
# <a name="imetadataemitdefineparam-method"></a>IMetaDataEmit::DefineParam 方法
Creates a parameter definition with the specified signature for the method referenced by the specified token, and gets a token for that parameter definition.  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT DefineParam (  
    [in]  mdMethodDef md,   
    [in]  ULONG       ulParamSeq,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwParamFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,  
    [in]  ULONG       cchValue,   
    [out] mdParamDef  *ppd   
);  
```  
  
## <a name="parameters"></a>参数  
 `md`  
 [in] The token for the method whose parameter is being defined.  
  
 `ulParamSeq`  
 [in] The parameter sequence number.  
  
 `szName`  
 [in] The name of the parameter in Unicode.  
  
 `dwParamFlags`  
 [in] Flags for the parameter. This is a bitmask of `CorParamAttr` values.  
  
 `dwCPlusTypeFlag`  
 [in] `ELEMENT_TYPE_` *\** for the constant value.  
  
 `pValue`  
 [in] The constant value for the parameter.  
  
 `cchValue`  
 [in] The size, in Unicode characters, of `pValue`.  
  
 `ppd`  
 [out] The `mdParamDef` token assigned.  
  
## <a name="remarks"></a>备注  
 The sequence values in `ulParamSeq` begin with 1 for parameters. A return value has a sequence number of 0.  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MSCorEE.dll  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
