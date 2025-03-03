---
title: UI 自动化对 Menu 控件类型的支持
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Menu
- UI Automation, Menu control type
- Menu control type
ms.assetid: 016323cb-f800-4938-b77b-2eb25d646090
ms.openlocfilehash: f09438d9941f2abb49cae8f7542efe84f44e81dc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446741"
---
# <a name="ui-automation-support-for-the-menu-control-type"></a>UI 自动化对 Menu 控件类型的支持
> [!NOTE]
> 本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。 有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。  
  
 本主题介绍 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 对 Menu 控件类型的支持。 本主题描述控件的 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 树结构并为特定的控件方案提供属性和控件模式。  
  
 使用菜单控件，可以对与命令和事件处理程序相关联的元素以分层方式进行组织。 In a typical Microsoft Windows application, a menu bar contains several menu buttons (such as **File**, **Edit**, and **Window**), and each menu button displays a menu. 菜单包含一系列菜单项（如“新建”、“打开”和“关闭”），可以通过展开这些菜单项来显示额外的菜单项，或者通过单击它们来执行特定的操作。  
  
 以下几节定义了 Menu 控件类型必需的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 树结构、属性、控件模式和事件。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 要求适用于所有列表控件，无论控件是 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]、 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]还是 [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]。  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>必需的 UI 自动化树结构  
 下表描述了与菜单控件有关的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 树的控件视图和内容视图，以及每个视图中可包含的内容。 有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 树的详细信息，请参阅 [UI Automation Properties Overview](ui-automation-tree-overview.md)。  
  
|控件视图|内容视图|  
|------------------|------------------|  
|菜单<br /><br /> -   MenuItem (1 or many)|不适用（除非菜单控件是上下文菜单，后者为非菜单项对象的父级）<br /><br /> -   MenuItem (1 or many)|  
  
 菜单控件始终出现在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 树的控件视图和内容视图中。 菜单控件类型应当出现在其信息引用的控件下方。 UI 自动化客户端必须侦听 `MenuOpenedEvent` 才能确保以一致的方式获取由菜单控件传达的信息。 上下文菜单控件是一个特例。 它们显示为桌面的子级。  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>必需的 UI 自动化属性  
 下表列出了值或定义与 Menu 控件类型密切相关的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 属性。 For more information on [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] properties, see [UI Automation Properties for Clients](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 属性|“值”|注意|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|不支持|菜单控件不要求设置 Name 属性。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|不使用典型的菜单控件来准备任何标签。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|菜单|此值对于所有 UI 框架均相同。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|False|菜单控件不包括在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 树的内容视图中。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|菜单控件始终包括在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 树的控件视图中。|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>必需的 UI 自动化控件模式  
 Menu 控件类型不需要任何控件模式。  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>必需的 UI 自动化事件  
 当菜单控件出现在屏幕上时，它们必须引发 `MenuOpenedEvent` 。 `MenuOpenedEvent` 将包括控件的文本。 当菜单从屏幕上消失时，它们必须引发 `MenuClosedEvent` 。  
  
 下表列出需要由所有菜单控件支持的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件。 有关事件的详细信息，请参阅 [F:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty](ui-automation-events-overview.md)。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件|支持/值|注意|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.MenuOpenedEvent>|必需|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.MenuClosedEvent>|必需|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> 属性更改事件。|必需|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> 属性更改事件。|必需|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 属性更改事件。|必需|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|必需|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|必需|None|  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Automation.ControlType.Menu>
- [UI 自动化控件模式概述](ui-automation-control-patterns-overview.md)
- [UI 自动化控件类型概述](ui-automation-control-types-overview.md)
- [UI 自动化概述](ui-automation-overview.md)
