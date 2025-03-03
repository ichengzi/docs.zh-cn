---
title: <requestCaching> 元素（网络设置）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
ms.openlocfilehash: f0979d2e0caeb0b22b90572aef0ad53235020f1d
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697828"
---
# <a name="requestcaching-element-network-settings"></a>\<requestCaching> 元素（网络设置）
控制网络请求的缓存机制。  
  
[ **\<configuration>** ](../configuration-element.md)  
\<&nbsp;[**的 &nbsp;>** ](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp; **\<requestCaching >**  
  
## <a name="syntax"></a>语法  
  
```xml  
<requestCaching  
  isPrivateCache ="true|false"  
  disableAllCaching="true|false"  
  defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
  unspecifiedMaximumAge= "d.hh.mm.ss">  
    <defaultHttpCachePolicy>...</defaultHttpCachePolicy>  
    <defaultFtpCachePolicy>...</defaultFtpCachePolicy>  
</requestCaching>
```  
  
## <a name="attributes-and-elements"></a>属性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>Attributes  
  
|属性|说明|  
|---------------|-----------------|  
|`isPrivateCache`|指定缓存是否在不同用户的信息之间提供隔离。 默认值为 `true`。 应为中间层应用程序 `false` 此值。|  
|`disableAllCaching`|指定为所有 Web 响应禁用缓存，且不能以编程方式重写。|  
|`defaultPolicyLevel`|<xref:System.Net.Cache.RequestCacheLevel> 枚举中的值之一。 默认值为 `BypassCache`。|  
|`unspecifiedMaximumAge`|指定将内容标记为过期的默认时间。|  
  
## <a name="policylevel-attribute"></a>policyLevel 特性  
  
|值|说明|  
|-----------|-----------------|  
|`Default`|如果资源是最新的，则返回缓存的资源，内容长度准确，并且存在过期、修改和内容长度属性。|  
|`BypassCache`|从服务器返回资源。|  
|`CacheOnly`|如果内容长度存在并且与条目大小匹配，则返回缓存的资源。|  
|`CacheIfAvailable`|如果提供了内容长度并与条目大小匹配，则返回缓存的资源;否则，将从服务器下载资源，并将其返回给调用方。|  
|`Revalidate`|如果缓存资源的时间戳与服务器上资源的时间戳相同，则返回缓存的资源;否则，将从服务器下载资源，并将其存储在缓存中，并将其返回给调用方。|  
|`Reload`|从服务器下载资源，将其存储在缓存中，并将资源返回给调用方。|  
|`NoCacheNoStore`|如果缓存的资源存在，则将其删除。 从服务器下载资源，并将其返回给调用方。|  
|`Revalidate`|如果时间戳与服务器上资源的时间戳相同，则使用资源的缓存副本满足请求;否则，会从服务器下载资源，并将其提供给调用方，并存储在缓存中。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|说明|  
|-------------|-----------------|  
|[defaultHttpCachePolicy](defaulthttpcachepolicy-element-network-settings.md)|可选元素。<br /><br /> 描述 HTTP 缓存是否处于活动状态，并描述默认缓存策略。|  
|[\<defaultFtpCachePolicy > 元素（网络设置）](defaultftpcachepolicy-element-network-settings.md)|可选元素。<br /><br /> 介绍 FTP 缓存是否处于活动状态，并描述默认缓存策略。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|说明|  
|-------------|-----------------|  
|[system.net](system-net-element-network-settings.md)|包含指定 .NET Framework 如何连接到网络的设置。|  
  
## <a name="example"></a>示例  
 下面的示例演示如何禁用所有缓存。  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Net.Cache?displayProperty=nameWithType>
- [网络设置架构](index.md)
