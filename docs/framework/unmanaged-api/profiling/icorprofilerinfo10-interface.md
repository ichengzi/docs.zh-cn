---
title: ICorProfilerInfo10 接口
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: f2bc716110c14972e5b2c32bceb3123b16e87c61
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449840"
---
# <a name="icorprofilerinfo10-interface"></a>ICorProfilerInfo10 接口

A subclass of [ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.

## <a name="methods"></a>方法  

| 方法|描述|  
| ------------|-----------------|  
|[EnumerateObjectReferences Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-enumerateobjectreferences-method.md)|Given an ObjectID, callback and clientData, enumerates each object reference (if any). |
|[IsFrozenObject Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-isfrozenobject-method.md)|Given an ObjectID, determines whether the object is in a read-only segment. |
|[GetLOHObjectSizeThreshold Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-getlohobjectsizethreshold-method.md)|Gets the value of the configured LOH threshold. |
|[RequestReJITWithInliners Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-requestrejitwithinliners-method.md)| ReJITs the methods requested, as well as any inliners of the methods requested.  |
|[SuspendRuntime Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-suspendruntime-method.md)| Suspends the runtime without performing a GC. |
|[ResumeRuntime Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-resumeruntime-method.md)| Resumes the runtime without performing a GC. |

## <a name="requirements"></a>要求  
**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).  
**头文件：** CorProf.idl、CorProf.h  
**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)] 

## <a name="see-also"></a>请参阅

- [Profiling 接口](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
