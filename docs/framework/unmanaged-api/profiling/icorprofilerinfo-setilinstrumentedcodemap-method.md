---
title: ICorProfilerInfo::SetILInstrumentedCodeMap 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type:
- apiref
ms.openlocfilehash: 32e63a6d2b6f739025d4c5558c16fe2d74fde73c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449863"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a>ICorProfilerInfo::SetILInstrumentedCodeMap 方法

Sets a code map for the specified function using the specified Microsoft intermediate language (MSIL) map entries.

> [!NOTE]
> In the .NET Framework version 2.0, calling `SetILInstrumentedCodeMap` on a `FunctionID` that represents a generic function in a particular application domain will affect all instances of that function in the application domain.

## <a name="syntax"></a>语法

```cpp
HRESULT SetILInstrumentedCodeMap(
    [in]  FunctionID functionId,
    [in]  BOOL       fStartJit,
    [in]  ULONG      cILMapEntries,
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);
```

## <a name="parameters"></a>参数

`functionId`\
[in] The ID of the function for which to set the code map.

`fStartJit`\
[in] A Boolean value that indicates whether the call to the `SetILInstrumentedCodeMap` method is the first for a particular `FunctionID`. Set `fStartJit` to `true` in the first call to `SetILInstrumentedCodeMap` for a given `FunctionID`, and to `false` thereafter.

`cILMapEntries`\
[in] The number of elements in the `cILMapEntries` array.

`rgILMapEntries`\
[in] An array of COR_IL_MAP structures, each of which specifies an MSIL offset.

## <a name="remarks"></a>备注

A profiler often inserts statements within the source code of a method in order to instrument that method (for example, to notify when a given source line is reached). `SetILInstrumentedCodeMap` enables a profiler to map the original MSIL instructions to their new locations. A profiler can use the [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) method to get the original MSIL offset for a given native offset.

The debugger will assume that each old offset refers to an MSIL offset within the original, unmodified MSIL code, and that each new offset refers to the MSIL offset within the new, instrumented code. The map should be sorted in increasing order. For stepping to work properly, follow these guidelines:

- Do not reorder instrumented MSIL code.

- Do not remove the original MSIL code.

- Include entries for all the sequence points from the program database (PDB) file in the map. The map does not interpolate missing entries. So, given the following map:

  (0 old, 0 new)

  (5 old, 10 new)

  (9 old, 20 new)

  - An old offset of 0, 1, 2, 3, or 4 will be mapped to new offset 0.

  - An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.

  - An old offset of 9 or higher will be mapped to new offset 20.

  - A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.

  - A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.

  - A new offset of 20 or higher will be mapped to old offset 9.

In the .NET Framework 3.5 and previous versions, you allocate the `rgILMapEntries` array by calling the [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) method. Because the runtime takes ownership of this memory, the profiler should not attempt to free it.

## <a name="requirements"></a>要求

**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。

**头文件：** CorProf.idl、CorProf.h

**库：** CorGuids.lib

**.NET Framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]

## <a name="see-also"></a>请参阅

- [ICorProfilerInfo 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
