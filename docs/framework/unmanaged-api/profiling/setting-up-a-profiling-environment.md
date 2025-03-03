---
title: 设置分析环境
ms.date: 03/30/2017
helpviewer_keywords:
- environment variables, profiling API
- profiling API [.NET Framework], setting up environment
- COR_PROFILER environment variable
- Windows Service applications, profiling
- profiling API [.NET Framework], Windows Service applications
- COR_ENABLE_PROFILING environment variable
- profiling API [.NET Framework], enabling
ms.assetid: fefca07f-7555-4e77-be86-3c542e928312
ms.openlocfilehash: 86720cb1739e3f193cd1d5081577d69bca1cf0f9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427050"
---
# <a name="setting-up-a-profiling-environment"></a>设置分析环境
> [!NOTE]
> There have been substantial changes to profiling in the .NET Framework 4.  
  
 托管进程（应用程序或服务）启动时，将加载公共语言运行时 (CLR)。 初始化 CLR 时，将评估以下两个环境变量以决定进程是否应连接到探查器：  
  
- COR_ENABLE_PROFILING：仅当此环境变量存在并设置为 1 时，CLR 连接到探查器。  
  
- COR_PROFILER：如果 COR_ENABLE_PROFILING 检查通过，CLR 将连接到具有此 CLSID 或 ProgID 的探查器（已事先存储在注册表中）。 COR_PROFILER 环境变量被定义为字符串，如以下两个示例中所示。  
  
    ```cpp  
    set COR_PROFILER={32E2F4DA-1BEA-47ea-88F9-C5DAF691C94A}  
    set COR_PROFILER="MyProfiler"  
    ```  
  
 若要分析 CLR 应用程序，必须在运行该应用程序之前设置 COR_ENABLE_PROFILING 和 COR_PROFILER 环境变量。 还必须确保已注册探查器 DLL。  
  
> [!NOTE]
> Starting with the .NET Framework 4, profilers do not have to be registered.  
  
> [!NOTE]
> To use .NET Framework versions 2.0, 3.0, and 3.5 profilers in the .NET Framework 4 and later versions, you must set the COMPLUS_ProfAPI_ProfilerCompatibilitySetting environment variable.  
  
## <a name="environment-variable-scope"></a>环境变量范围  
 设置 COR_ENABLE_PROFILING 和 COR_PROFILER 环境变量的方式将决定其影响范围。 可以通过下列方式之一设置这些变量：  
  
- If you set the variables in an [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) call, they will apply only to the application that you are running at the time. （它们将也应用于由继承环境的应用程序启动的其他应用程序。）  
  
- 如果在“命令提示符”窗口中设置变量，则它们将应用于从该窗口中启动的所有应用程序。  
  
- 如果在用户级别设置变量，它们将应用于用文件资源管理器启动的所有应用程序。 在设置变量后打开的“命令提示符”窗口将具有这些环境设置，从该窗口中启动的任何应用程序也将如此。 To set environment variables at the user level, right-click **My Computer**, click **Properties**, click the **Advanced** tab, click **Environment Variables**, and add the variables to the **User variables** list.  
  
- 如果在计算机级别设置变量，它们将应用于在该计算机上启动的所有应用程序。 在该计算机上打开的“命令提示符”窗口将具有这些环境设置，从该窗口中启动的任何应用程序也将如此。 这表示该计算机上的每个托管进程都将通过你的探查器启动。 To set environment variables at the computer level, right-click **My Computer**, click **Properties**, click the **Advanced** tab, click **Environment Variables**, add the variables to the **System variables** list, and then restart your computer. 重启后，变量将在系统范围内可用。  
  
 如果要分析 Windows 服务，必须在设置环境变量并注册探查器 DLL 之后重启计算机。 For more information about these considerations, see the section [Profiling a Windows Service](#windows_service).  
  
## <a name="additional-considerations"></a>其他注意事项  
  
- The profiler class implements the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) and [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) interfaces. 在 .NET Framework 2.0 版中，探查器必须实现 `ICorProfilerCallback2`。 否则，将不会加载 `ICorProfilerCallback2`。  
  
- 在给定环境中一次只能由一个事件探查器分析进程。 可以在不同环境中注册两个不同的探查器，但每个探查器必须分析单独的进程。 必须将探查器作为进程内 COM 服务器 DLL 实现，后者被映射到与正在被分析的进程相同的地址空间。 这表示探查器在进程内运行。 .NET Framework 不支持任何其他类型的 COM 服务器。 例如，如果探查器要监视远程计算机上的应用程序，则它必须在每台计算机上实现收集器代理。 这些代理将批处理结果，并将它们传递给中央数据收集计算机。  
  
- 由于探查器是在进程内实例化的 COM 对象，所以每个被分析的应用程序都将具有其自己的探查器副本。 因此，单个探查器实例不一定要处理来自多个应用程序的数据。 但是，必须向探查器的日志记录代码添加逻辑，以防日志文件从其他被分析的应用程序进行覆盖。  
  
## <a name="initializing-the-profiler"></a>初始化探查器  
 如果两次环境变量检查均通过，CLR 就会以与 COM `CoCreateInstance` 函数类似的方式创建探查器实例。 直接调用 `CoCreateInstance` 不会加载探查器。 因此避免了调用 `CoInitialize`（需设置线程模型）。 The CLR then calls the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) method in the profiler. 此方法的签名如下。  
  
```cpp  
HRESULT Initialize(IUnknown *pICorProfilerInfoUnk)  
```  
  
 The profiler must query `pICorProfilerInfoUnk` for an [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) or [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) interface pointer and save it so that it can request more information later during profiling.  
  
## <a name="setting-event-notifications"></a>设置事件通知  
 The profiler then calls the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to specify which categories of notifications it is interested in. 例如，如果探查器只关注函数进入和离开通知以及垃圾回收通知，它将指定以下内容。  
  
```cpp  
ICorProfilerInfo* pInfo;  
pICorProfilerInfoUnk->QueryInterface(IID_ICorProfilerInfo, (void**)&pInfo);  
pInfo->SetEventMask(COR_PRF_MONITOR_ENTERLEAVE | COR_PRF_MONITOR_GC)  
```  
  
 通过以这种方式设置通知掩码，探查器可以限制它接收的通知。 此方法帮助用户构建简单探查器或具有特殊用途的探查器。 它还能减少发送探查器只会忽略的通知将浪费的 CPU 时间。  
  
 某些探查器事件是不可变的。 这表示，一旦在 `ICorProfilerCallback::Initialize` 回调中设置了这些事件，就不能将它们关闭，也不能打开新事件。 试图更改不可变事件将导致 `ICorProfilerInfo::SetEventMask` 返回失败的 HRESULT。  
  
<a name="windows_service"></a>   
## <a name="profiling-a-windows-service"></a>分析 Windows 服务  
 分析 Windows 服务与分析公共语言运行时应用程序相似。 两种分析操作都通过环境变量启用。 由于 Windows 服务已于操作系统启动时启动，本主题中之前所述的环境变量必须在系统启动前就已经存在并设置为所需的值。 此外，必须已在系统上注册了分析 DLL。  
  
 设置 COR_ENABLE_PROFILING 和 COR_PROFILER 环境变量并注册探查器 DLL 后，应重启目标计算机，以便 Windows 服务能够检测这些更改。  
  
 请注意，这些更改将在整个系统范围内启用分析。 若要防止对随后运行的每个托管应用程序进行分析，应在重启目标计算机后删除系统环境变量。  
  
 此技术也会导致对每个 CLR 进程进行分析。 The profiler should add logic to its [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback to detect whether the current process is of interest. 如果不相关，探查器可使回调失败而不执行初始化。  
  
## <a name="see-also"></a>请参阅

- [分析概述](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)
