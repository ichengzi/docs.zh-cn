---
title: IMetaDataEmit::MergeEnd 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.MergeEnd
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::MergeEnd
helpviewer_keywords:
- MergeEnd method [.NET Framework metadata]
- IMetaDataEmit::MergeEnd method [.NET Framework metadata]
ms.assetid: 2d64315a-1af1-4c60-aedf-f8a781914aea
topic_type:
- apiref
ms.openlocfilehash: 34ecfc2f01f22971e135358806adeea632e02f8b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448036"
---
# <a name="imetadataemitmergeend-method"></a>IMetaDataEmit::MergeEnd 方法

Merges into the current scope all the metadata scopes specified by one or more prior calls to [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md).

## <a name="syntax"></a>语法

```cppcpp
HRESULT MergeEnd ();
```

## <a name="parameters"></a>参数

This method takes no parameters.

## <a name="remarks"></a>备注

This routine triggers the actual merge of metadata, of all import scopes specified by preceding calls to `IMetaDataEmit::Merge`, into the current output scope.

The following special conditions apply to the merge:

- A module version identifier (MVID) is never imported, because it is unique to the metadata in the import scope.

- No existing module-wide properties are overwritten.

  If module properties were already set for the current scope, no module properties are imported. However, if module properties have not been set in the current scope, they are imported only once, when they are first encountered. If those module properties are encountered again, they are duplicates. If the values of all module properties (except MVID) are compared and no duplicates are found, an error is raised.

- For type definitions (`TypeDef`), no duplicates are merged into the current scope. `TypeDef` objects are checked for duplicates against each *fully-qualified object name* + *GUID* + *version number*. If there is a match on either name or GUID, and any of the other two elements is different, an error is raised. Otherwise, if all three items match, `MergeEnd` does a cursory check to ensure the entries are indeed duplicates; if not, an error is raised. This cursory check looks for:

  - The same member declarations, occurring in the same order. Members that are flagged as `mdPrivateScope` (see the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration) are not included in this check; they are merged specially.

  - The same class layout.

  This means that a `TypeDef` object must always be fully and consistently defined in every metadata scope in which it is declared; if its member implementations (for a class) are spread across multiple compilation units, the full definition is assumed to be present in every scope and not incremental to each scope. For example, if parameter names are relevant to the contract, they must be emitted the same way into every scope; if they are not relevant, they should not be emitted into metadata.

  The exception is that a `TypeDef` object can have incremental members flagged as `mdPrivateScope`. On encountering these, `MergeEnd` incrementally adds them to the current scope without regard for duplicates. Because the compiler understands the private scope, the compiler must be responsible for enforcing rules.

- Relative virtual addresses (RVAs) are not imported or merged; the compiler is expected to re-emit this information.

- Custom attributes are merged only when the item to which they are attached is merged. For example, custom attributes associated with a class are merged when the class is first encountered. If custom attributes are associated with a `TypeDef` or `MemberDef` that is specific to the compilation unit (such as the time stamp of a member compile), they are not merged and it is up to the compiler to remove or update such metadata.

## <a name="requirements"></a>要求

**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。

**Header:** Cor.h

**Library:** Used as a resource in MSCorEE.dll

**.NET Framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]

## <a name="see-also"></a>请参阅

- [IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
