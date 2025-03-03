---
title: 客户端 UI 自动化提供程序的实现
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, client-side provider implementation
- client-side UI Automation provider, implementation
- provider implementation, UI Automation
ms.assetid: 3584c0a1-9cd0-4968-8b63-b06390890ef6
ms.openlocfilehash: 03df282022c39673a7e160dd5d79bdadd0c7adda
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433989"
---
# <a name="client-side-ui-automation-provider-implementation"></a>客户端 UI 自动化提供程序的实现
> [!NOTE]
> 本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。 有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。  
  
 Several different [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] frameworks are in use within Microsoft operating systems, including [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)], [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], and [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 向客户公开有关 UI 元素的信息。 但是， [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 本身并不了解存在于这些框架中的不同类型的控件以及从中提取信息所需的技术。 而是将此任务留给称为提供程序的对象。 一个提供程序从特定控件中提取信息，并将该信息传递给 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，后者随后以一致的方式将其呈现给客户端。  
  
 提供程序可以存在于服务器端或客户端上。 服务器端提供程序由控件本身实现。 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] 元素实现提供程序，正如可以在考虑到 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 的情况下写入第三方控件一样。  
  
 但较旧的控件（例如 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] 和 [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] 中的控件）不直接支持 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]。 这些控件都将改为由存在于客户端进程中的提供程序提供，并且使用跨进程通信获取有关控件的信息；例如，通过监视在窗口与控件之间来回的消息。 此类客户端提供程序有时称为代理。  
  
 Windows Vista supplies providers for standard [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] and Windows Forms controls. In addition, a fallback provider gives partial [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] support to any control that is not served by another server-side provider or proxy but has a Microsoft Active Accessibility implementation. 所有这样的提供程序均已自动加载，并且可供客户端应用程序使用。  
  
 For more information on support for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] and Windows Forms controls, see [UI Automation Support for Standard Controls](ui-automation-support-for-standard-controls.md).  
  
 应用程序还可以注册其他客户端提供程序。  
  
<a name="Distributing_Client-Side_Providers"></a>   
## <a name="distributing-client-side-providers"></a>分布客户端提供程序  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 预期在托管代码程序集中查找客户端提供程序。 此程序集中命名空间的名称应与程序集名称相同。 例如，名为 ContosoProxies.dll 的程序集将包含 ContosoProxies 命名空间。 在命名空间内创建一个 <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders> 类。 在静态 <xref:UIAutomationClientsideProviders.UIAutomationClientSideProviders.ClientSideProviderDescriptionTable> 字段的实现中，创建一个描述提供程序的 <xref:System.Windows.Automation.ClientSideProviderDescription> 结构数组。  
  
<a name="Registering_and_Configuring_Client-Side_Providers"></a>   
## <a name="registering-and-configuring-client-side-providers"></a>注册并配置客户端提供程序  
 Client-side providers in a dynamic-link library (DLL) are loaded by calling <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviderAssembly%2A>. 客户端应用程序不需要任何进一步的操作即可使用提供程序。  
  
 在客户端自己的代码中实现的提供程序通过使用 <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>注册。 此方法将 <xref:System.Windows.Automation.ClientSideProviderDescription> 结构数组作为参数，每个结构均指定以下属性：  
  
- 创建提供程序对象的回调函数。  
  
- 提供程序将提供的控件的类名。  
  
- 提供程序将提供的应用程序（通常为可执行文件的完整名称）的映像名称。  
  
- 控制如何将类名与在目标应用程序中找到的窗口类进行匹配的标志。  
  
 最后两个参数为可选。 当客户端需要为不同的应用程序使用不同的提供程序时，它可能会指定目标应用程序的映像名称。 例如，客户端可能会为支持“多视图”模式的已知应用程序中的 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] 列表视图控件使用一个提供程序，为不支持“多视图”模式的另一个已知应用程序中的类似控件使用另一个提供程序。  
  
## <a name="see-also"></a>请参阅

- [创建客户端 UI 自动化提供程序](create-a-client-side-ui-automation-provider.md)
- [在客户端应用程序中实现 UI 自动化提供程序](implement-ui-automation-providers-in-a-client-application.md)
