---
title: <applicationPool> 元素（网络设置）
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: c88f4e5407e550047eaf0f5c8d0d2924da611e93
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699221"
---
# <a name="applicationpool-element-web-settings"></a>\<applicationPool > 元素（Web 设置）
指定 ASP.NET 在 IIS 7.0 或更高版本的集成模式下运行时，用于管理进程范围行为的配置设置。  
  
> [!IMPORTANT]
> 仅当 ASP.NET 应用程序托管在 IIS 7.0 或更高版本上时，此元素和它支持的功能才起作用。  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp;&nbsp;[ **\<system.web >** ](system-web-element-web-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp; **\<applicationPool >**  
  
## <a name="syntax"></a>语法  
  
```xml  
<applicationPool   
    maxConcurrentRequestsPerCPU="5000"   
    maxConcurrentThreadsPerCPU="0"   
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a>属性和元素  

下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>Attributes  
  
|属性|说明|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|指定 ASP.NET 每 CPU 允许的并发请求数。|  
|`maxConcurrentThreadsPerCPU`|指定每个 CPU 的应用程序池可以运行的线程数。 这提供了一种方法来控制 ASP.NET 并发，因为你可以限制每个 CPU 可用于处理请求的托管线程数。 默认情况下，此设置为0，这意味着 ASP.NET 不会限制可为每个 CPU 创建的线程数，尽管 CLR 线程池还限制了可创建的线程数。|  
|`requestQueueLimit`|指定可在单个进程中为 ASP.NET 排队的最大请求数。 当两个或多个 ASP.NET 应用程序在单个应用程序池中运行时，对应用程序池中的任何应用程序发出的累积请求将受到此设置的限制。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|说明|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|包含有关 ASP.NET 如何与宿主应用程序进行交互的信息。|  
  
## <a name="remarks"></a>备注  

在集成模式下运行 IIS 7.0 或更高版本时，此元素组合可让你配置当应用程序托管在 IIS 应用程序池中时，ASP.NET 如何管理线程和队列请求。 如果运行 IIS 6 或在经典模式下或在 ISAPI 模式下运行 IIS 7.0，则将忽略这些设置。  
  
`applicationPool` 设置适用于在 .NET Framework 的特定版本上运行的所有应用程序池。 这些设置包含在 aspnet .config 文件中。 此文件的版本2.0 和 4.0 .NET Framework。 （版本3.0 和 3.5 .NET Framework 共享包含版本2.0 的 aspnet .config 文件。）  
  
> [!IMPORTANT]
> 如果在 [!INCLUDE[win7](../../../../../includes/win7-md.md)]上运行 IIS 7.0，则可以为每个应用程序池配置单独的 aspnet .config 文件。 这使你可以为每个应用程序池定制线程性能。  
  
对于 `maxConcurrentRequestsPerCPU` 设置，.NET Framework 4 中的默认设置 "5000" 有效地关闭了由 ASP.NET 控制的请求阻止，除非你实际每个 CPU 有5000或更多请求。 默认设置依赖于 CLR 线程池来自动管理每个 CPU 的并发。 对于大量使用异步请求处理的应用程序，或在网络 i/o 上阻塞多个长时间运行的请求的应用程序，将从 .NET Framework 4 中增加的默认限制中受益。 将 `maxConcurrentRequestsPerCPU` 设置为零将关闭使用托管线程来处理 ASP.NET 请求。 当应用程序在 IIS 应用程序池中运行时，请求将保留在 IIS i/o 线程上，因此并发会受到 IIS 线程设置的限制。  
  
`requestQueueLimit` 设置的工作方式与在 ASP.NET 应用程序的 web.config 文件中设置的[processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100))元素的 `requestQueueLimit` 属性相同。 但是，aspnet 文件中的 `requestQueueLimit` 设置会覆盖 Web.config 文件中的 `requestQueueLimit` 设置。 换句话说，如果同时设置了这两个属性（默认情况下为 true），则将优先使用 aspnet .config 文件中的 `requestQueueLimit` 设置。  
  
## <a name="example"></a>示例  

下面的示例演示如何在以下情况下配置 ASP.NET 中的进程范围行为：  
  
- 该应用程序托管在 IIS 7.0 应用程序池中。  
  
- IIS 7.0 正在集成模式下运行。  
  
- 应用程序使用的是 .NET Framework 3.5 SP1 或更高版本。  
  
示例中的值为默认值。  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool   
        maxConcurrentRequestsPerCPU="5000"  
        maxConcurrentThreadsPerCPU="0"   
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a>元素信息  
  
|||  
|-|-|  
|命名空间||  
|架构名称||  
|验证文件||  
|可以为空||  
  
## <a name="see-also"></a>另请参阅

- [\<system.web> 元素（Web 设置）](system-web-element-web-settings.md)
