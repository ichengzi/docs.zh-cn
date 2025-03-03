---
title: DataGrid 样式和模板
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], DataGrid
- ControlTemplate [WPF], DataGrid
- DataGrid [WPF], styles and templates
- templates [WPF], DataGrid
- styles [WPF], DataGrid
- parts [WPF], DataGrid
ms.assetid: 9cb31d63-f148-4d25-b079-816e73f988c7
ms.openlocfilehash: 066e8c9ce1112399be8128d0821498f0d56a3dc3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283808"
---
# <a name="datagrid-styles-and-templates"></a>DataGrid 样式和模板
本主题介绍 <xref:System.Windows.Controls.DataGrid> 控件的样式和模板。 您可以修改默认 <xref:System.Windows.Controls.ControlTemplate> 以使控件具有独特的外观。 有关详细信息，请参阅为[控件创建模板](../../../desktop-wpf/themes/how-to-create-apply-template.md)。  
  
## <a name="datagrid-parts"></a>DataGrid 部分  
 下表列出了 <xref:System.Windows.Controls.DataGrid> 控件的已命名部分。  
  
|部件|Type|描述|  
|-|-|-|  
|PART_ColumnHeadersPresenter|<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>|包含列标题的行。|  
  
 为 <xref:System.Windows.Controls.DataGrid>创建 <xref:System.Windows.Controls.ControlTemplate> 时，模板可能包含 <xref:System.Windows.Controls.ScrollViewer>中的 <xref:System.Windows.Controls.ItemsPresenter>。 （<xref:System.Windows.Controls.ItemsPresenter> 显示 <xref:System.Windows.Controls.DataGrid>中的每一项; <xref:System.Windows.Controls.ScrollViewer> 允许在控件中滚动）。  如果 <xref:System.Windows.Controls.ItemsPresenter> 不是 <xref:System.Windows.Controls.ScrollViewer>的直接子级，则必须为 <xref:System.Windows.Controls.ItemsPresenter> 指定名称 `ItemsPresenter`。  
  
 <xref:System.Windows.Controls.DataGrid> 的默认模板包含一个 <xref:System.Windows.Controls.ScrollViewer> 控件。 有关 <xref:System.Windows.Controls.ScrollViewer>定义的部分的详细信息，请参阅[ScrollViewer 样式和模板](scrollviewer-styles-and-templates.md)。  
  
## <a name="datagrid-states"></a>DataGrid 状态  
 下表列出了 <xref:System.Windows.Controls.DataGrid> 控件的可视状态。  
  
|VisualState 名称|VisualStateGroup 名称|描述|  
|-|-|-|  
|一般|CommonStates|默认状态。|  
|Disabled|CommonStates|已禁用控件。|  
|InvalidFocused|ValidationStates|控件无效，但具有焦点。|  
|InvalidUnfocused|ValidationStates|控件无效，并且没有焦点。|  
|有效|ValidationStates|控件有效。|  
  
## <a name="datagridcell-parts"></a>DataGridCell 部件  
 <xref:System.Windows.Controls.DataGridCell> 元素没有任何命名部分。  
  
## <a name="datagridcell-states"></a>DataGridCell 状态  
 下表列出了 <xref:System.Windows.Controls.DataGridCell> 元素的可视状态。  
  
|VisualState 名称|VisualStateGroup 名称|描述|  
|-|-|-|  
|一般|CommonStates|默认状态。|  
|MouseOver|CommonStates|鼠标指针位于单元格上。|  
|已设定焦点|FocusStates|单元格有焦点。|  
|失去焦点|FocusStates|单元格没有焦点|  
|当前|CurrentStates|单元格为当前单元格。|  
|规则|CurrentStates|单元格不是当前单元格。|  
|显示|InteractionStates|单元格处于显示模式。|  
|编辑|InteractionStates|单元格处于编辑模式。|  
|已选定|SelectionStates|选择该单元格。|  
|未选定|SelectionStates|未选择该单元格。|  
|InvalidFocused|ValidationStates|单元格无效，具有焦点。|  
|InvalidUnfocused|ValidationStates|单元格无效且没有焦点。|  
|有效|ValidationStates|单元格有效。|  
  
## <a name="datagridrow-parts"></a>DataGridRow 部件  
 <xref:System.Windows.Controls.DataGridRow> 元素没有任何命名部分。  
  
## <a name="datagridrow-states"></a>DataGridRow 状态  
 下表列出了 <xref:System.Windows.Controls.DataGridRow> 元素的可视状态。  
  
|VisualState 名称|VisualStateGroup 名称|描述|  
|-|-|-|  
|一般|CommonStates|默认状态。|  
|MouseOver|CommonStates|鼠标指针置于行的上方。|  
|MouseOver_Editing|CommonStates|鼠标指针置于行的上方，行处于编辑模式。|  
|MouseOver_Selected|CommonStates|鼠标指针置于行上方，并选中行。|  
|MouseOver_Unfocused_Editing|CommonStates|鼠标指针置于行的上方，行处于编辑模式，并且没有焦点。|  
|MouseOver_Unfocused_Selected|CommonStates|鼠标指针置于行上方，该行处于选中状态，并且没有焦点。|  
|Normal_AlternatingRow|CommonStates|该行是一个交替行。|  
|Normal_Editing|CommonStates|该行处于编辑模式。|  
|Normal_Selected|CommonStates|该行处于选中状态。|  
|Unfocused_Editing|CommonStates|该行处于编辑模式，没有焦点。|  
|Unfocused_Selected|CommonStates|该行处于选中状态，但没有焦点。|  
|InvalidFocused|ValidationStates|控件无效，但具有焦点。|  
|InvalidUnfocused|ValidationStates|控件无效，并且没有焦点。|  
|有效|ValidationStates|控件有效。|  
  
## <a name="datagridrowheader-parts"></a>DataGridRowHeader 部件  
 下表列出了 <xref:System.Windows.Controls.Primitives.DataGridRowHeader> 元素的已命名部分。  
  
|部件|Type|描述|  
|-|-|-|  
|PART_TopHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|用于从顶部调整行标题大小的元素。|  
|PART_BottomHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|用于从底部调整行标题大小的元素。|  
  
## <a name="datagridrowheader-states"></a>DataGridRowHeader 状态  
 下表列出了 <xref:System.Windows.Controls.Primitives.DataGridRowHeader> 元素的可视状态。  
  
|VisualState 名称|VisualStateGroup 名称|描述|  
|-|-|-|  
|一般|CommonStates|默认状态。|  
|MouseOver|CommonStates|鼠标指针置于行的上方。|  
|MouseOver_CurrentRow|CommonStates|鼠标指针置于行的上方，行是当前行。|  
|MouseOver_CurrentRow_Selected|CommonStates|鼠标指针置于行的上方，行是当前行并处于选定状态。|  
|MouseOver_EditingRow|CommonStates|鼠标指针置于行的上方，行处于编辑模式。|  
|MouseOver_Selected|CommonStates|鼠标指针置于行上方，并选中行。|  
|MouseOver_Unfocused_CurrentRow_Selected|CommonStates|鼠标指针置于行的上方，行是当前行并处于选定状态，并且没有焦点。|  
|MouseOver_Unfocused_EditingRow|CommonStates|鼠标指针置于行的上方，行处于编辑模式，并且没有焦点。|  
|MouseOver_Unfocused_Selected|CommonStates|鼠标指针置于行上方，该行处于选中状态，并且没有焦点。|  
|Normal_CurrentRow|CommonStates|该行是当前行。|  
|Normal_CurrentRow_Selected|CommonStates|该行是当前行并处于选定状态。|  
|Normal_EditingRow|CommonStates|该行处于编辑模式。|  
|Normal_Selected|CommonStates|该行处于选中状态。|  
|Unfocused_CurrentRow_Selected|CommonStates|该行是当前行，已选中，并且没有焦点。|  
|Unfocused_EditingRow|CommonStates|该行处于编辑模式，没有焦点。|  
|Unfocused_Selected|CommonStates|该行处于选中状态，但没有焦点。|  
|InvalidFocused|ValidationStates|控件无效，但具有焦点。|  
|InvalidUnfocused|ValidationStates|控件无效，并且没有焦点。|  
|有效|ValidationStates|控件有效。|  
  
## <a name="datagridcolumnheaderspresenter-parts"></a>DataGridColumnHeadersPresenter 部件  
 下表列出了 <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter> 元素的已命名部分。  
  
|部件|Type|描述|  
|-|-|-|  
|PART_FillerColumnHeader|<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>|列标题的占位符。|  
  
## <a name="datagridcolumnheaderspresenter-states"></a>DataGridColumnHeadersPresenter 状态  
 下表列出了 <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter> 元素的可视状态。  
  
|VisualState 名称|VisualStateGroup 名称|描述|  
|-|-|-|  
|InvalidFocused|ValidationStates|单元格无效，具有焦点。|  
|InvalidUnfocused|ValidationStates|单元格无效且没有焦点。|  
|有效|ValidationStates|单元格有效。|  
  
## <a name="datagridcolumnheader-parts"></a>DataGridColumnHeader 部件  
 下表列出了 <xref:System.Windows.Controls.Primitives.DataGridColumnHeader> 元素的已命名部分。  
  
|部件|Type|描述|  
|-|-|-|  
|PART_LeftHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|用于从左侧调整列标题大小的元素。|  
|PART_RightHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|用于从右侧调整列标题大小的元素。|  
  
## <a name="datagridcolumnheader-states"></a>DataGridColumnHeader 状态  
 下表列出了 <xref:System.Windows.Controls.Primitives.DataGridColumnHeader> 元素的可视状态。  
  
|VisualState 名称|VisualStateGroup 名称|描述|  
|-|-|-|  
|一般|CommonStates|默认状态。|  
|MouseOver|CommonStates|鼠标指针悬停在控件上。|  
|已按下|CommonStates|已按下控件。|  
|SortAscending|SortStates|列按升序排序。|  
|SortDescending|SortStates|列按降序排序。|  
|未排序|SortStates|列未排序。|  
|InvalidFocused|ValidationStates|控件无效，但具有焦点。|  
|InvalidUnfocused|ValidationStates|控件无效，并且没有焦点。|  
|有效|ValidationStates|控件有效。|  
  
## <a name="datagrid-controltemplate-example"></a>DataGrid System.windows.controls.controltemplate> 示例  
 下面的示例演示如何为 <xref:System.Windows.Controls.DataGrid> 控件及其关联的类型定义 <xref:System.Windows.Controls.ControlTemplate>。  
  
 [!code-xaml[ControlTemplateExamples#DataGrid](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datagrid.xaml#datagrid)]  
  
 上一示例使用了一个或多个以下资源。  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 有关完整示例，请参阅[使用 ControlTemplates 设置样式示例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [控件样式和模板](control-styles-and-templates.md)
- [控件自定义](control-customization.md)
- [样式设置和模板化](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [为控件创建模板](../../../desktop-wpf/themes/how-to-create-apply-template.md)
