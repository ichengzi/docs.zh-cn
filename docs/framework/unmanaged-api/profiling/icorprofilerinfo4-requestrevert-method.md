---
title: ICorProfilerInfo4::RequestRevert 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestRevert
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestRevert
helpviewer_keywords:
- RequestRevert method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestRevert method [.NET Framework profiling]
ms.assetid: 70261da5-5933-4e25-9de0-ddf51cba56cc
topic_type:
- apiref
ms.openlocfilehash: c7ced05692e3030bace10dab9a6793a29fac6c26
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444836"
---
# <a name="icorprofilerinfo4requestrevert-method"></a>ICorProfilerInfo4::RequestRevert 方法
将指定函数的所有实例还原为其初始版本。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
## <a name="parameters"></a>参数  
 `cFunctions`  
 [in] 要还原的函数数目。  
  
 `moduleIds`  
 [in] 指定（`module`、`methodDef`）对的 `moduleId` 部分，它标识要还原的函数。  
  
 `methodIds`  
 [in] 指定（`module`、`methodDef`）对的 `methodId` 部分，它标识要还原的函数。  
  
 `status`  
 [out] 在本主题后面的“状态 HRESULT”章节中列出的 HRESULT 数组。 每个 HRESULT 表示尝试还原并行数组 `moduleIds` 和 `methodIds` 中指定的每个函数是成功还是失败。  
  
## <a name="return-value"></a>返回值  
 此方法返回以下特定 HRESULT 以及表示方法失败的 HRESULT 错误。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|尝试还原所有请求；但是，必须检查返回的状态数组，确定成功还原了哪些函数。|  
|CORPROF_E_CALLBACK4_REQUIRED|The profiler must implement the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface for this call to be supported.|  
|CORPROF_E_REJIT_NOT_ENABLED|尚未启用 JIT 重新编译。 You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.|  
|E_INVALIDARG|`cFunctions` 为 0，或者 `moduleIds` 或 `methodIds` 为 `NULL`。|  
|E_OUTOFMEMORY|CLR 无法完成请求，因为它已耗尽内存。|  
  
## <a name="status-hresults"></a>状态 HRESULTS  
  
|状态数组 HRESULT|描述|  
|--------------------------|-----------------|  
|S_OK|已成功还原相应函数。|  
|E_INVALIDARG|`moduleID` 或 `methodDef` 参数为 `NULL`。|  
|CORPROF_E_DATAINCOMPLETE|该模块尚未完全加载，或正在被卸载。|  
|CORPROF_E_MODULE_IS_DYNAMIC|已动态生成指定模块（例如通过 `Reflection.Emit` 生成）。 因此，此方法不支持它。|  
|CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND|CLR 无法还原指定函数，因为找不到对应的活动的重新编译请求。 从未请求重新编译或此函数已还原。|  
|其他|操作系统返回了 CLR 控件范围之外的失败。 例如，如果用于更改内存页访问权限保护的系统调用失败，将显示操作系统错误。|  
  
## <a name="remarks"></a>备注  
 在下次调用任何已还原的函数实例时，将运行此函数的初始版本。 如果已在运行某个函数，则将完成正在运行的版本的执行操作。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **头文件：** CorProf.idl、CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorProfilerInfo4 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Profiling 接口](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [分析](../../../../docs/framework/unmanaged-api/profiling/index.md)
