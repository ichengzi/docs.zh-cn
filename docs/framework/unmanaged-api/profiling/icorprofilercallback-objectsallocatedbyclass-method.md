---
title: ICorProfilerCallback::ObjectsAllocatedByClass 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectsAllocatedByClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectsAllocatedByClass
helpviewer_keywords:
- ObjectsAllocatedByClass method [.NET Framework profiling]
- ICorProfilerCallback::ObjectsAllocatedByClass method [.NET Framework profiling]
ms.assetid: 91d688f3-a80e-419d-9755-ff94bc04188a
topic_type:
- apiref
ms.openlocfilehash: 9ba021ec223d00e57081567b76f70f59768e6b9a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445868"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a>ICorProfilerCallback::ObjectsAllocatedByClass 方法
Notifies the profiler about the number of instances of each specified class that have been created since the most recent garbage collection.  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a>参数  
 `cClassCount`  
 [in] The size of the `classIds` and `cObjects` arrays.  
  
 `classIds`  
 [in] An array of class IDs, where each ID specifies a class with one or more instances.  
  
 `cObjects`  
 [in] An array of integers, where each integer specifies the number of instances for the corresponding class in the `classIds` array.  
  
## <a name="remarks"></a>备注  
 The `classIds` and `cObjects` arrays are parallel arrays. For example, `classIds[i]` and `cObjects[i]` reference the same class. If no instance of a class has been created since the previous garbage collection, the class is omitted. The `ObjectsAllocatedByClass` callback will not report objects allocated in the large object heap.  
  
 The numbers reported by `ObjectsAllocatedByClass` are only estimates. For exact counts, use [ICorProfilerCallback::ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).  
  
 The `classIds` array may contain one or more null entries if the corresponding `cObjects` array has types that are unloading.  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **头文件：** CorProf.idl、CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorProfilerCallback 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
