---
title: UI 自动化对 MenuItem 控件类型的支持
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Menu Item
- Menu Item control type
- UI Automation, Menu Item control type
ms.assetid: 54bce311-3d23-40b9-ba90-1bdbdaf8fbba
ms.openlocfilehash: c65e30ffea64a9b577cfee7535fd92e489bc7632
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446705"
---
# <a name="ui-automation-support-for-the-menuitem-control-type"></a>UI 自动化对 MenuItem 控件类型的支持

> [!NOTE]
> 本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。 有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。

本主题提供有关对 MenuItem 控件类型的 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 支持的信息。 本主题描述控件的 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 树结构，并提供 MenuItem 控件类型所必需的属性和控件模式。

使用菜单控件，可以对与命令和事件处理程序相关联的元素以分层方式进行组织。 In a typical Microsoft Windows application, a menu bar contains several menu items (such as **File**, **Edit**, and **Window**), and each menu item displays a menu. 菜单包含一系列菜单项（如“新建”、“打开”和“关闭”），可以通过展开这些菜单项来显示额外的菜单项，或者通过单击它们来执行特定的操作。 菜单项可以承载于菜单、菜单栏或工具栏中。

以下几节定义了 MenuItem 控件类型必需的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 树结构、属性、控件模式和事件。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 要求适用于所有列表控件，无论控件是 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]、 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]还是 [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]。

<a name="Required_UI_Automation_Tree_Structure"></a>

## <a name="required-ui-automation-tree-structure"></a>必需的 UI 自动化树结构

下表描述了与菜单项控件有关的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 树的控件视图和内容视图，以及每个视图中可包含的内容。 有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 树的详细信息，请参阅 [UI Automation Properties Overview](ui-automation-tree-overview.md)。

|控件视图|内容视图|
|------------------|------------------|
|MenuItem “帮助”<br /><br /> <ul><li>菜单（帮助菜单项的子菜单）<br /><br /> <ul><li>MenuItem“帮助主题”</li><li>MenuItem “关于 Notepad”</li></ul></li></ul>|MenuItem “帮助”<br /><br /> -   MenuItem "Help Topics"<br />-   MenuItem "About Notepad"|

菜单项控件的控件视图具有如上所示的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 树结构。 Note that the **Help** menu item is included to better illustrate the structure in a typical menu to submenu hierarchy.

而对于内容视图而言，菜单不存在于 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 树，因为它不给最终用户提供有意义的信息。

<a name="Required_UI_Automation_Properties"></a>

## <a name="required-ui-automation-properties"></a>必需的 UI 自动化属性

下表列出 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 属性，这些属性的值或定义与菜单项控件尤其相关。 For more information on [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] properties, see [UI Automation Properties for Clients](ui-automation-properties-for-clients.md).

|Property|“值”|描述|
|--------------|-----------|-----------------|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|请参阅注释。|此属性的值在应用程序的所有控件中都必须保持唯一。|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|请参阅注释。|包含整个控件的最外层矩形。|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|请参阅注释。|如果存在边界矩形，则受支持。 如果边界矩形中存在无法单击的点，而你要执行专门的命中测试，则重写并提供可单击的点。|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|请参阅注释。|如果该控件可以接收键盘焦点，则它必须支持此属性。|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|请参阅注释。|菜单项控件不包括在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 树的内容视图中，且自己标有名称。|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|无标签。|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|MenuItem|此值对于所有 UI 框架均相同。|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|“菜单项”|与 MenuItem 控件类型相对应的已本地化字符串。|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|菜单项控件决不包括在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 树的内容视图中。|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|菜单项控件必须始终包括在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 树的控件视图中。|

<a name="Required_UI_Automation_Control_Patterns"></a>

## <a name="required-ui-automation-control-patterns"></a>必需的 UI 自动化控件模式

下表列出需要由菜单项控件支持的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 控件模式。 有关控件模式的详细信息，请参阅 [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md)。

|控件模式属性|支持|注意|
|------------------------------|-------------|-----------|
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|视情况而定|如果控件可以展开或折叠，则实现 <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>。|
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|视情况而定|如果该控件执行单个操作或命令，则实现 <xref:System.Windows.Automation.Provider.IInvokeProvider>。|
|<xref:System.Windows.Automation.Provider.IToggleProvider>|视情况而定|如果该控件表示可以打开或关闭的选项，则实现 <xref:System.Windows.Automation.Provider.IToggleProvider>。|
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|视情况而定|如果该控件用于从菜单项之间的选项列表中选择，则实现 <xref:System.Windows.Automation.Provider.ISelectionItemProvider>。|

<a name="UI_Automation_Events_for_Menu_Item"></a>

## <a name="ui-automation-events-for-menu-item"></a>菜单项的 UI 自动化事件

下表列出与菜单项控件关联的 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 事件。

|Event — 事件|支持|说明|
|-----------|-------------|-----------------|
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|视情况而定|如果控件支持 Invoke 控件模式则必须引发。|
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty> 属性更改事件。|视情况而定|如果控件支持 Toggle 控件模式则必须引发。|
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty> 属性更改事件。|视情况而定|如果控件支持 Expand Collapse 控件模式则必须引发。|
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|视情况而定|无。|

<a name="Required_UI_Automation_Events"></a>

## <a name="required-ui-automation-events"></a>必需的 UI 自动化事件

下表列出需要由所有菜单项控件支持的 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件。 有关事件的详细信息，请参阅 [F:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty](ui-automation-events-overview.md)。

|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件|支持/值|注意|
|---------------------------------------------------------------------------------|--------------------|-----------|
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|视情况而定|None|
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|视情况而定|None|
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|视情况而定|None|
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|视情况而定|None|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> 属性更改事件。|必需|None|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> 属性更改事件。|必需|None|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> 属性更改事件。|必需|None|
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty> 属性更改事件。|视情况而定|None|
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty> 属性更改事件。|视情况而定|None|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|必需|None|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|必需|None|

<a name="Legacy_Issues"></a>

## <a name="legacy-issues"></a>遗留问题

仅当 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] 菜单项被选中且能够以编程方式被确定为支持 Toggle 模式所必需时，才可支持 Toggle 模式。 因为 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] 菜单项不会公开它是否有具有被选中的能力，所以未选中菜单项时将支持 Invoke 模式。 异常将始终支持 Invoke 模式，这甚至适用于应仅支持 Toggle 模式的菜单项。 这是为了当曾支持 Invoke 模式的元素（未选中菜单项时）在选中后不再持该模式时，使客户端不至于困惑。

## <a name="see-also"></a>请参阅

- <xref:System.Windows.Automation.ControlType.MenuItem>
- [UI 自动化控件模式概述](ui-automation-control-patterns-overview.md)
- [UI 自动化控件类型概述](ui-automation-control-types-overview.md)
- [UI 自动化概述](ui-automation-overview.md)
