---
title: CorElementType 枚举
ms.date: 03/30/2017
api_name:
- CorElementType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorElementType
helpviewer_keywords:
- CorElementType enumeration [.NET Framework metadata]
ms.assetid: c3809c8f-1737-4f0f-9442-0c01ee689871
topic_type:
- apiref
ms.openlocfilehash: 0ce84e1545523302cd47e60b9f047bc470e6bf0f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443625"
---
# <a name="corelementtype-enumeration"></a>CorElementType 枚举

Specifies a common language runtime <xref:System.Type>, a type modifier, or information about a type in a metadata type signature.

## <a name="syntax"></a>语法

```cpp
typedef enum CorElementType {
    ELEMENT_TYPE_END            = 0x0,
    ELEMENT_TYPE_VOID           = 0x1,
    ELEMENT_TYPE_BOOLEAN        = 0x2,
    ELEMENT_TYPE_CHAR           = 0x3,
    ELEMENT_TYPE_I1             = 0x4,
    ELEMENT_TYPE_U1             = 0x5,
    ELEMENT_TYPE_I2             = 0x6,
    ELEMENT_TYPE_U2             = 0x7,
    ELEMENT_TYPE_I4             = 0x8,
    ELEMENT_TYPE_U4             = 0x9,
    ELEMENT_TYPE_I8             = 0xa,
    ELEMENT_TYPE_U8             = 0xb,
    ELEMENT_TYPE_R4             = 0xc,
    ELEMENT_TYPE_R8             = 0xd,
    ELEMENT_TYPE_STRING         = 0xe,

    ELEMENT_TYPE_PTR            = 0xf,
    ELEMENT_TYPE_BYREF          = 0x10,

    ELEMENT_TYPE_VALUETYPE      = 0x11,
    ELEMENT_TYPE_CLASS          = 0x12,
    ELEMENT_TYPE_VAR            = 0x13,
    ELEMENT_TYPE_ARRAY          = 0x14,
    ELEMENT_TYPE_GENERICINST    = 0x15,
    ELEMENT_TYPE_TYPEDBYREF     = 0x16,

    ELEMENT_TYPE_I              = 0x18,
    ELEMENT_TYPE_U              = 0x19,
    ELEMENT_TYPE_FNPTR          = 0x1B,
    ELEMENT_TYPE_OBJECT         = 0x1C,
    ELEMENT_TYPE_SZARRAY        = 0x1D,
    ELEMENT_TYPE_MVAR           = 0x1e,

    ELEMENT_TYPE_CMOD_REQD      = 0x1F,
    ELEMENT_TYPE_CMOD_OPT       = 0x20,

    ELEMENT_TYPE_INTERNAL       = 0x21,
    ELEMENT_TYPE_MAX            = 0x22,

    ELEMENT_TYPE_MODIFIER       = 0x40,
    ELEMENT_TYPE_SENTINEL       = 0x01 | ELEMENT_TYPE_MODIFIER,
    ELEMENT_TYPE_PINNED         = 0x05 | ELEMENT_TYPE_MODIFIER

} CorElementType;
```

## <a name="members"></a>Members

|成员|描述|
|------------|-----------------|
|`ELEMENT_TYPE_END`|内部使用。|
|`ELEMENT_TYPE_VOID`|A void type.|
|`ELEMENT_TYPE_BOOLEAN`|A Boolean type|
|`ELEMENT_TYPE_CHAR`|一个字符类型。|
|`ELEMENT_TYPE_I1`|A signed 1-byte integer.|
|`ELEMENT_TYPE_U1`|1 字节无符号整数。|
|`ELEMENT_TYPE_I2`|A signed 2-byte integer.|
|`ELEMENT_TYPE_U2`|An unsigned 2-byte integer.|
|`ELEMENT_TYPE_I4`|A signed 4-byte integer.|
|`ELEMENT_TYPE_U4`|An unsigned 4-byte integer.|
|`ELEMENT_TYPE_I8`|A signed 8-byte integer.|
|`ELEMENT_TYPE_U8`|An unsigned 8-byte integer.|
|`ELEMENT_TYPE_R4`|A 4-byte floating point.|
|`ELEMENT_TYPE_R8`|An 8-byte floating point.|
|`ELEMENT_TYPE_STRING`|A System.String type.|
|`ELEMENT_TYPE_PTR`|A pointer type modifier.|
|`ELEMENT_TYPE_BYREF`|A reference type modifier.|
|`ELEMENT_TYPE_VALUETYPE`|A value type modifier.|
|`ELEMENT_TYPE_CLASS`|A class type modifier.|
|`ELEMENT_TYPE_VAR`|A class variable type modifier.|
|`ELEMENT_TYPE_ARRAY`|A multi-dimensional array type modifier.|
|`ELEMENT_TYPE_GENERICINST`|A type modifier for generic types.|
|`ELEMENT_TYPE_TYPEDBYREF`|类型化的引用。|
|`ELEMENT_TYPE_I`|Size of a native integer.|
|`ELEMENT_TYPE_U`|Size of an unsigned native integer.|
|`ELEMENT_TYPE_FNPTR`|A pointer to a function.|
|`ELEMENT_TYPE_OBJECT`|A System.Object type.|
|`ELEMENT_TYPE_SZARRAY`|A single-dimensional, zero lower-bound array type modifier.|
|`ELEMENT_TYPE_MVAR`|A method variable type modifier.|
|`ELEMENT_TYPE_CMOD_REQD`|A C language required modifier.|
|`ELEMENT_TYPE_CMOD_OPT`|A C language optional modifier.|
|`ELEMENT_TYPE_INTERNAL`|内部使用。|
|`ELEMENT_TYPE_MAX`|无效类型。|
|`ELEMENT_TYPE_MODIFIER`|内部使用。|
|`ELEMENT_TYPE_SENTINEL`|A type modifier that is a sentinel for a list of a variable number of parameters.|
|`ELEMENT_TYPE_PINNED`|内部使用。|

## <a name="remarks"></a>备注

The type modifiers form the basis for representing more complex types. A `CorElementType` type modifier value is applied to the value that immediately follows it in the type signature. The value that follows the `CorElementType` type modifier value can be a `CorElementType` simple type value, a metadata token, or other value, as specified in the following table.

> [!NOTE]
> All numbers (*number*, *argument Count*, *metadata token*, *rank*, *count*, and *bound*) are stored as compressed integers. See [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=116487) on the ECMA Web site for details.

|Type modifier|格式|
|-------------------|------------|
|`ELEMENT_TYPE_PTR`|ELEMENT_TYPE_PTR \<a `CorElementType` value>|
|`ELEMENT_TYPE_BYREF`|ELEMENT_TYPE_BYREF \<a `CorElementType` value>|
|`ELEMENT_TYPE_VALUETYPE`|ELEMENT_TYPE_VALUETYPE \<an `mdTypeDef` metadata token>|
|`ELEMENT_TYPE_CLASS`|ELEMENT_TYPE_CLASS \<an `mdTypeDef` metadata token>|
|`ELEMENT_TYPE_VAR`|ELEMENT_TYPE_VAR \<number>|
|`ELEMENT_TYPE_ARRAY`|ELEMENT_TYPE_ARRAY \<a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN> \<boundN>|
|`ELEMENT_TYPE_GENERICINST`|ELEMENT_TYPE_GENERICINST \<an `mdTypeDef` metadata token> \<argument Count> \<arg1> ... \<argN>|
|`ELEMENT_TYPE_FNPTR`|ELEMENT_TYPE_FNPTR \<complete signature for the function, including calling convention>|
|`ELEMENT_TYPE_SZARRAY`|ELEMENT_TYPE_SZARRAY \<a `CorElementType` value>|
|`ELEMENT_TYPE_MVAR`|ELEMENT_TYPE_MVAR \<number>|
|`ELEMENT_TYPE_CMOD_REQD`|ELEMENT_TYPE_\<a `mdTypeRef` or `mdTypeDef` metadata token>|
|`ELEMENT_TYPE_CMOD_OPT`|E_T_CMOD_OPT \<a `mdTypeRef` or `mdTypeDef` metadata token>|

## <a name="requirements"></a>要求

**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。

**Header:** CorHdr.h

**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>请参阅

- [Metadata 枚举](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
