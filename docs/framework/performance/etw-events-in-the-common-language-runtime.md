---
title: 公共语言运行时中的 ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: 5bb9b6a2-7b57-4aea-8809-32b28bc73e88
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83246f42275425bca48530915c7bf5c19f3b9f04
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447666"
---
# <a name="etw-events-in-the-common-language-runtime"></a>公共语言运行时中的 ETW 事件
公共语言运行时 (CLR) 通过大量的调试和分析事件，提供有用的 Windows 事件跟踪 (ETW) 诊断信息。 CLR ETW 事件利用 Windows ETW 跟踪系统来扩充公共语言运行时所提供的现有分析和调试支持。  
  
 More information about ETW is available in the [Improve Debugging and Performance Tuning with ETW](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw) article. 有关 Xperf 的详细信息，请参阅 NTDebugging 博客中的 [Windows Performance Toolkit - Xperf](https://blogs.msdn.microsoft.com/ntdebugging/2008/04/03/windows-performance-toolkit-xperf/)（Windows 性能工具包 - Xperf）。  
  
 The .NET Framework 4 or later is required for all the events described in the event topics. Windows Vista 操作系统是支持的最低客户端，而 Windows Server 2008 是支持的最低服务器。  
  
## <a name="in-this-section"></a>本节内容  
 [控制 .NET Framework 日志记录](controlling-logging.md)  
 介绍用于捕获和查看 ETW 事件的工具和命令。  
  
 [CLR ETW 提供程序](clr-etw-providers.md)  
 提供有关运行时和断开提供程序，以及如何使用它们收集 ETW 数据的信息。  
  
 [CLR ETW 关键字和级别](clr-etw-keywords-and-levels.md)  
 介绍运行时和断开提供程序的关键字，可通过这些关键字按类别筛选事件。  
  
 [CLR ETW 事件](clr-etw-events.md)  
 提供有关 CLR ETW 事件及其关键字、级别和事件数据的详细信息。  
  
## <a name="see-also"></a>请参阅

- [.NET Framework 中的 ETW 事件](etw-events.md)
