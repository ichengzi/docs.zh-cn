---
title: 输入概述
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- commands [WPF]
- input [WPF], overview
- keyboard focus [WPF]
- keyboard input [WPF]
- touch events [WPF]
- event routing [WPF]
- touch input [WPF]
- manipulation [WPF]
- logical focus [WPF]
- stylus input [WPF]
- text input [WPF]
- input events [WPF], handling
- WPF [WPF], input overview
- manipulation events [WPF]
- mouse input [WPF]
- mouse capture [WPF]
- focus [WPF]
- mouse position [WPF]
ms.assetid: ee5258b7-6567-415a-9b1c-c0cbe46e79ef
ms.openlocfilehash: a90c74542c1a6604ed27d37f882385b67402dd92
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005030"
---
# <a name="input-overview"></a>输入概述
<a name="introduction"></a>@No__t 1 子系统提供了一个功能强大的 API，用于从各种设备（包括鼠标、键盘、触摸和触笔）获取输入。 本主题介绍了 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供的服务，并说明了输入系统的体系结构。

<a name="input_api"></a>
## <a name="input-api"></a>输入 API
 主输入 API 公开内容在基本元素类上找到： <xref:System.Windows.UIElement>、<xref:System.Windows.ContentElement>、<xref:System.Windows.FrameworkElement> 和 @no__t。  有关基元素的详细信息，请参阅[基元素概述](base-elements-overview.md)。  这些类提供有关输入事件（例如按键、鼠标按钮、鼠标滚轮、鼠标移动、焦点管理和鼠标捕获等）的功能。 通过将输入 API 放在基元素上，而不是将所有输入事件视为一项服务，输入体系结构使输入事件可以通过 UI 中的特定对象来提供，并支持一个事件路由方案，使多个元素具有 opportunity 来处理输入事件。 许多输入事件都具有与之相关联的一对事件。  例如，键按下事件与 @no__t 0 和 @no__t 1 事件关联。  这些事件的区别在于它们如何路由至目标元素。  预览事件将元素树从根元素到目标元素向下进行隧道操作。  冒泡事件从目标元素到根元素向上进行冒泡操作。  本概述后面部分和[路由事件概述](routed-events-overview.md)中更详细地讨论了 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的事件路由。

### <a name="keyboard-and-mouse-classes"></a>键盘和鼠标类
 除了基本元素类上的输入 API 外，@no__t 的类和 @no__t 类还提供了用于使用键盘和鼠标输入的其他 API。

 @No__t-0 类上输入 API 的示例为 <xref:System.Windows.Input.Keyboard.Modifiers%2A> 属性，该属性返回当前按下的 @no__t）和 @no__t 3 方法，该方法确定是否按下了指定的键。

 下面的示例使用 <xref:System.Windows.Input.Keyboard.GetKeyStates%2A> 方法来确定 @no__t 是否处于关闭状态。

 [!code-csharp[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyArgsSnippetSample/CSharp/Window1.xaml.cs#keyeventargskeyboardgetkeystates)]
 [!code-vb[keyargssnippetsample#KeyEventArgsKeyBoardGetKeyStates](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyArgsSnippetSample/visualbasic/window1.xaml.vb#keyeventargskeyboardgetkeystates)]

 @No__t-0 类上输入 API 的示例 @no__t 为-1，它获取鼠标中键的状态，@no__t 为-2，这会获取鼠标指针当前悬停的元素。

 下面的示例确定鼠标上的 @no__t 0 是否处于 @no__t 状态。

 [!code-csharp[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](~/samples/snippets/csharp/VS_Snippets_Wpf/MouseRelatedSnippets/CSharp/Window1.xaml.cs#mouserelatedsnippetsgetleftbuttonmouse)]
 [!code-vb[mouserelatedsnippets#MouseRelatedSnippetsGetLeftButtonMouse](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MouseRelatedSnippets/visualbasic/window1.xaml.vb#mouserelatedsnippetsgetleftbuttonmouse)]

 本概述中更详细地介绍了 <xref:System.Windows.Input.Mouse> 和 @no__t 1 类。

### <a name="stylus-input"></a>触笔输入
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 对 @no__t 的集成支持。  @No__t-0 是 Tablet PC 流行的笔输入。  @no__t 0 应用程序可以通过使用鼠标 API 将触笔视为鼠标，但 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 还会公开使用类似于键盘和鼠标的模型的触笔设备抽象。  与触笔相关的所有 Api 都包含 "触笔" 一词。

 由于触笔可充当鼠标，因此仅支持鼠标输入的应用程序仍可以自动获得一定程度的触笔支持。 以这种方式使用触笔时，应用程序有能力处理相应的触笔事件，然后处理相应的鼠标事件。 此外，通过触笔设备抽象也可以使用墨迹输入等较高级别的服务。  有关墨迹输入的详细信息，请参阅[墨迹入门](getting-started-with-ink.md)。

<a name="event_routing"></a>
## <a name="event-routing"></a>事件路由
 @No__t-0 可以在其内容模型中包含作为子元素的其他元素，从而形成元素树。  在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，父元素可以通过处理事件来参与定向到其子元素或其他后代的输入。 这特别适合于从较小的控件中生成控件，该过程称为“控件组合”或“合成”。 有关元素树以及元素树如何与事件路由关联的详细信息，请参阅 [WPF 中的树](trees-in-wpf.md)。

 事件路由是将事件转发到多个元素的过程，以便使路由中的特定对象或元素可以选择对已由其他元素指明来源的事件提供重要响应（通过处理）。  路由事件使用三种路由机制的其中一种：直接、浮升和隧道。  在直接路由中，源元素是收到通知的唯一元素，事件不会路由至任何其他元素。 但是，直接路由事件仍会提供一些附加功能，这些功能仅适用于路由事件，而不是标准 CLR 事件。 浮升操作在元素树中向上进行，首先通知指明了事件来源的第一个元素，然后是父元素等等。  隧道操作从元素树的根开始，然后向下进行，以原始的源元素结束。  有关路由事件的详细信息，请参阅[路由事件概述](routed-events-overview.md)。

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 输入事件通常成对出现，由一个隧道事件和一个冒泡事件组成。  隧道事件与冒泡事件的不同之处在于它有“预览”前缀。  例如，@no__t 为鼠标移动事件的隧道版本，<xref:System.Windows.Input.Mouse.MouseMove> 是此事件的冒泡版本。 此事件配对是在元素级别实现的一种约定，不是 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 事件系统的固有功能。 有关详细信息，请参阅[路由事件概述](routed-events-overview.md)中的 WPF 输入事件部分。

<a name="handling_input_events"></a>
## <a name="handling-input-events"></a>处理输入事件
 若要在元素上接收输入，必须将事件处理程序与该特定事件关联。  在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中，这很简单：将事件的名称作为要侦听此事件的元素的特性进行引用。  然后，根据委托，将特性的值设置为所定义的事件处理程序的名称。  事件处理程序必须用代码（如） C#编写，并且可以包含在代码隐藏文件中。

 当操作系统报告发生键操作时，如果键盘焦点正处在元素上，则将发生键盘事件。 鼠标和触笔事件分别分为两类：报告指针位置相对于元素的变化的事件，和报告设备按钮状态的变化的事件。

### <a name="keyboard-input-event-example"></a>键盘输入事件示例
 以下示例侦听按下向左键的操作。  @No__t 创建一个 @no__t 为1的。  用于侦听按下箭头键的事件处理程序已附加到 <xref:System.Windows.Controls.Button> 实例。

 该示例的第一部分创建 @no__t 0 和 <xref:System.Windows.Controls.Button>，并附加 @no__t 的事件处理程序。

 [!code-xaml[InputOvw#Input_OvwKeyboardExampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwkeyboardexamplexaml)]

 [!code-csharp[InputOvw#Input_OvwKeyboardExampleUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexampleuicodebehind)]

 第二部分用代码编写，定义了事件处理程序。  按下向左键并 <xref:System.Windows.Controls.Button> 具有键盘焦点时，处理程序将运行并更改 @no__t 的 @no__t 1 颜色。  如果按下了键，但它不是左箭头键，则 <xref:System.Windows.Controls.Button> 的 @no__t 颜色将改回其起始颜色。

 [!code-csharp[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwkeyboardexamplehandlercodebehind)]
 [!code-vb[InputOvw#Input_OvwKeyboardExampleHandlerCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwkeyboardexamplehandlercodebehind)]

### <a name="mouse-input-event-example"></a>鼠标输入事件示例
 在下面的示例中，当鼠标指针进入 <xref:System.Windows.Controls.Button> 时，将更改 @no__t 的 @no__t 0 颜色。  当鼠标离开 @no__t 时，将还原 @no__t 的颜色。

 该示例的第一部分创建 @no__t 0 和 <xref:System.Windows.Controls.Button> 控件，并将 @no__t 2 和 3 @no__t 事件的事件处理程序附加到 @no__t。

 [!code-xaml[InputOvw#Input_OvwMouseExampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwmouseexamplexaml)]

 [!code-csharp[InputOvw#Input_OvwMouseExampleUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleuicodebehind)]
 [!code-vb[InputOvw#Input_OvwMouseExampleUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleuicodebehind)]

 该示例的第二部分用代码编写，定义了事件处理程序。  当鼠标进入 <xref:System.Windows.Controls.Button> 时，<xref:System.Windows.Controls.Button> 的 @no__t 颜色将更改为 @no__t。  当鼠标离开 <xref:System.Windows.Controls.Button> 时，@no__t 的第 1 @no__t 颜色将改回为 <xref:System.Windows.Media.Brushes.AliceBlue%2A>。

 [!code-csharp[InputOvw#Input_OvwMouseExampleEneterHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleeneterhandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleEneterHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleeneterhandler)]

 [!code-csharp[InputOvw#Input_OvwMouseExampleLeaveHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwmouseexampleleavehandler)]
 [!code-vb[InputOvw#Input_OvwMouseExampleLeaveHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwmouseexampleleavehandler)]

<a name="text_input"></a>
## <a name="text-input"></a>文本输入
 通过 <xref:System.Windows.ContentElement.TextInput> 事件，你可以以与设备无关的方式侦听文本输入。 键盘是文本输入的主要方式，但通过语音、手写和其他输入设备也可以生成文本输入。

 对于键盘输入，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 首先发送适当的 @no__t @ no__t-2 @ no__t 事件。 如果未处理这些事件，并且键是文本（而不是方向箭头或函数键等控制键），则会引发 @no__t 的事件。  在 <xref:System.Windows.ContentElement.KeyDown> @ no__t-1 @ no__t 和 @no__t 3 事件之间，并不总是有一种简单的一对一映射，因为多个击键可以生成一个文本输入字符，而单个击键可以生成多个字符的字符串。  对于中文、日语和韩语等语言，使用输入法编辑器（Ime）在其相应的字母表中生成成千上万个可能的字符时尤其如此。

 当 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 发送 @no__t @ no__t-2 @ no__t 事件时，如果击键可能成为 @no__t 事件的一部分（例如，按下 ALT + S），<xref:System.Windows.Input.KeyEventArgs.Key%2A> 设置为 <xref:System.Windows.Input.Key.System?displayProperty=nameWithType>。 这允许 @no__t 0 事件处理程序中的代码检查 @no__t 为-1，如果找到，则为后面引发的 @no__t 2 事件的处理程序保留处理。 在这些情况下，可以使用 <xref:System.Windows.Input.TextCompositionEventArgs> 参数的各种属性来确定原始击键。 同样，如果输入法处于活动状态，<xref:System.Windows.Input.Key> 的值为 <xref:System.Windows.Input.Key.ImeProcessed?displayProperty=nameWithType>，<xref:System.Windows.Input.KeyEventArgs.ImeProcessedKey%2A> 则提供原始击键或击键。

 下面的示例为 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件定义处理程序，并为 @no__t 1 事件定义处理程序。

 第一段代码或标记创建用户界面。

 [!code-xaml[InputOvw#Input_OvwTextInputXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#input_ovwtextinputxaml)]

 [!code-csharp[InputOvw#Input_OvwTextInputUICodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputuicodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputUICodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputuicodebehind)]

 第二段代码包含事件处理程序。

 [!code-csharp[InputOvw#Input_OvwTextInputHandlersCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml.cs#input_ovwtextinputhandlerscodebehind)]
 [!code-vb[InputOvw#Input_OvwTextInputHandlersCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InputOvw/VisualBasic/Page1.xaml.vb#input_ovwtextinputhandlerscodebehind)]

 由于输入事件向上冒泡事件路由，因此 <xref:System.Windows.Controls.StackPanel> 接收输入，而不考虑哪个元素具有键盘焦点。 将首先通知 @no__t 0 控件，并且仅当 <xref:System.Windows.Controls.TextBox> 未处理输入时，才调用 `OnTextInputKeyDown` 处理程序。 如果使用 @no__t 0 事件而不是 <xref:System.Windows.UIElement.KeyDown> 事件，则首先调用 @no__t 2 处理程序。

 在此示例中，处理逻辑写入了两次，分别针对 CTRL+O和按钮的单击事件。 使用命令，而不是直接处理输入事件，可简化此过程。  本概述和[命令概述](commanding-overview.md)中将讨论这些命令。

<a name="touch_and_manipulation"></a>
## <a name="touch-and-manipulation"></a>触摸和操作
 Windows 7 操作系统中的新硬件和 API 使应用程序能够同时接收来自多个触控的输入。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 通过在触摸发生时引发事件，从而使应用程序能够以类似于响应其他输入（例如鼠标或键盘）的方式来检测和响应触摸设备。

 发生触摸时，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 将公开两种类型的事件：触摸事件和操作事件。 触摸事件提供有关触摸屏上每个手指及其移动的原始数据。 操作事件将输入解释为特定操作。 本部分将讨论这两种类型的事件。

### <a name="prerequisites"></a>先决条件
 需要以下组件才能开发响应触摸的应用程序。

- Visual Studio 2010。

- Windows 7。

- 支持 Windows 触控的设备，如触摸屏。

### <a name="terminology"></a>术语
 讨论触摸时使用了以下术语。

- **触摸**是 Windows 7 可识别的一种用户输入。 通常，将手指放在触敏式屏幕上会触发触摸。 请注意，如果设备仅将手指的位置和移动转换为鼠标输入，则笔记本电脑上常用的触摸板等设备不支持触摸。

- **多点触摸**是同时发生在多个点上的触摸。 Windows 7 和 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 支持多点触摸。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 文档中每当论及触摸时，相关概念均适用于多点触摸。

- 当触摸被解释为应用于对象的实际操作时，就发生了**操作**。 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，操作事件将输入解释为转换、扩展或旋转操作。

- `touch device` 表示产生触摸输入的设备，例如触摸屏上的一根手指。

### <a name="controls-that-respond-to-touch"></a>响应触摸的控件
 如果以下控件的内容延伸到视图之外，则可以通过在控件上拖动手指来滚动该控件。

- <xref:System.Windows.Controls.ComboBox>

- <xref:System.Windows.Controls.ContextMenu>

- <xref:System.Windows.Controls.DataGrid>

- <xref:System.Windows.Controls.ListBox>

- <xref:System.Windows.Controls.ListView>

- <xref:System.Windows.Controls.MenuItem>

- <xref:System.Windows.Controls.TextBox>

- <xref:System.Windows.Controls.ToolBar>

- <xref:System.Windows.Controls.TreeView>

 @No__t-0 定义了 @no__t 1 附加属性，该属性使你能够指定是否水平、垂直、同时启用触控平移。 @No__t-0 属性指定当用户将手指从触摸屏上提起时，滚动速度变慢的速度。 @No__t-0 附加属性指定滚动偏移与转换操作偏移的比率。

### <a name="touch-events"></a>触摸事件
 基类 <xref:System.Windows.UIElement>、<xref:System.Windows.UIElement3D> 和 <xref:System.Windows.ContentElement> 定义可订阅的事件，使应用程序能够响应触控。 当应用程序将触摸解释为操作对象以外的其他操作时，触摸事件非常有用。 例如，使用户能够以一个或多个手指绘制的应用程序将订阅触摸事件。

 所有三个类都定义了以下事件，其行为类似，而无论定义类是什么。

- <xref:System.Windows.UIElement.TouchDown>

- <xref:System.Windows.UIElement.TouchMove>

- <xref:System.Windows.UIElement.TouchUp>

- <xref:System.Windows.UIElement.TouchEnter>

- <xref:System.Windows.UIElement.TouchLeave>

- <xref:System.Windows.UIElement.PreviewTouchDown>

- <xref:System.Windows.UIElement.PreviewTouchMove>

- <xref:System.Windows.UIElement.PreviewTouchUp>

- <xref:System.Windows.UIElement.GotTouchCapture>

- <xref:System.Windows.UIElement.LostTouchCapture>

 像键盘和鼠标事件一样，触摸事件也是路由事件。 以 `Preview` 开头的事件是隧道事件，以 `Touch` 开头的事件是冒泡事件。 有关路由事件的详细信息，请参阅[路由事件概述](routed-events-overview.md)。 处理这些事件时，可以通过调用 @no__t 0 或 <xref:System.Windows.Input.TouchEventArgs.GetIntermediateTouchPoints%2A> 方法来获取输入的相对于任何元素的位置。

 为了理解触控事件之间的交互，请考虑以下这种情况：用户将一个手指放在元素上，在该元素中移动手指，然后将手指从该元素上移开。 下图显示了冒泡事件的执行（为简单起见，省略了隧道事件）。

 ![触摸事件的序列。](./media/ndp-touchevents.png "NDP_TouchEvents")触摸事件

 下列内容描述了上图中的事件顺序。

1. 当用户将手指放在元素上时，将发生 @no__t 的事件一次。

2. @No__t 事件发生一次。

3. 当用户将手指移动到元素中时，会多次发生 <xref:System.Windows.UIElement.TouchMove> 事件。

4. 当用户将手指从元素中抬起时，将发生 @no__t 的事件一次。

5. @No__t 事件发生一次。

 当使用两根以上的手指时，每根手指都会发生事件。

### <a name="manipulation-events"></a>操作事件
 对于应用程序允许用户操纵对象的情况，@no__t 0 类定义操作事件。 与只是报告触摸位置的触摸事件不同，操作事件会报告可采用何种方式解释输入。 有三种类型的操作：转换、扩展和旋转。 下列内容介绍了如何调用这三种类型的操作。

- 将一根手指放在对象上，并在触摸屏上拖动手指以调用转换操作。 此操作通常会移动对象。

- 将两根手指放在物体上，并将手指相互靠拢或分开以调用扩展操作。 此操作通常会调整对象的大小。

- 将两根手指放在对象上，并将一个手指围绕另一个手指旋转以调用旋转操作。 此操作通常会旋转对象。

 多种类型的操作可以同时发生。

 使对象响应操作时，可以让对象看起来具有惯性。 这样可以使对象模拟真实的世界。 例如，在桌子上推一本书时，如果你足够用力，书将在你松手后继续移动。 利用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，可以通过在用户的手指松开对象后引发操作事件来模拟这种行为。

 有关如何创建使用户能够移动、调整大小和旋转对象的应用程序的信息，请参阅 [Walkthrough：正在创建您的第一个 Touch 应用程序 @ no__t。

 @No__t-0 定义以下操作事件。

- <xref:System.Windows.UIElement.ManipulationStarting>

- <xref:System.Windows.UIElement.ManipulationStarted>

- <xref:System.Windows.UIElement.ManipulationDelta>

- <xref:System.Windows.UIElement.ManipulationInertiaStarting>

- <xref:System.Windows.UIElement.ManipulationCompleted>

- <xref:System.Windows.UIElement.ManipulationBoundaryFeedback>

 默认情况下，@no__t 0 不会接收这些操作事件。 若要在 @no__t 上接收操作事件，请将 @no__t 设置为 `true`。

#### <a name="the-execution-path-of-manipulation-events"></a>操作事件的执行路径
 考虑用户“抛出”一个对象的情况。 用户将手指放在对象上，将手指在触摸屏上移动一段短距离，然后在移动的同时抬起手指。 此操作的结果是，该对象将在用户的手指下方移动，并在用户抬起手指后继续移动。

 下图显示了操作事件的执行路径和每个事件的重要信息。

 ![操作事件的序列。](./media/ndp-manipulationevents.png "NDP_ManipulationEvents")操作事件

 下列内容描述了上图中的事件顺序。

1. 当用户将手指放在对象上时，将发生 <xref:System.Windows.UIElement.ManipulationStarting> 事件。 除此之外，此事件还允许您设置 <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> 属性。 在随后的事件中，操作的位置将与 @no__t 相关。 在 <xref:System.Windows.UIElement.ManipulationStarting> 以外的事件中，此属性是只读的，因此只能在 @no__t 1 事件中设置此属性。

2. 接下来发生 <xref:System.Windows.UIElement.ManipulationStarted> 事件。 此事件报告操作的原始位置。

3. 当用户的手指在触摸屏上移动时，@no__t 的事件发生多次。 @No__t 类的 <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> 属性报告操作是解释为移动、扩展还是转换。 这是你执行操作对象的大部分工作的地方。

4. 当用户的手指与对象失去联系时，将发生 <xref:System.Windows.UIElement.ManipulationInertiaStarting> 事件。 此事件使你可以指定操作在惯性期间的减速。 这样，选择时对象就可以模拟不同的物理空间或特性。 例如，假设应用程序有两个表示真实世界中的物品的对象，并且一个物品比另一个物品重。 你可以使较重的对象比较轻的对象减速更快。

5. 发生惯性时，@no__t 0 事件发生多次。 请注意，当用户的手指在触摸屏上移动并且 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 模拟惯性时，将发生此事件。 换句话说，在 @no__t 1 事件之前和之后发生 @no__t。 @No__t-0 属性报告惯性期间是否发生了 @no__t 1 事件，因此您可以检查该属性并执行不同的操作，具体取决于其值。

6. 当操作和任何惯性结束时，将发生 @no__t 0 事件。 也就是说，在所有 <xref:System.Windows.UIElement.ManipulationDelta> 事件发生后，将发生 @no__t 1 事件，指示操作已完成。

 @No__t 还定义 @no__t 1 事件。 当 @no__t 事件中调用 <xref:System.Windows.Input.ManipulationDeltaEventArgs.ReportBoundaryFeedback%2A> 方法时发生此事件。 @No__t-0 事件使应用程序或组件能够在对象达到边界时提供可视反馈。 例如，<xref:System.Windows.Window> 类处理 @no__t 1 事件，以使窗口在遇到其边缘时轻微移动。

 您可以取消操作，方法是对任何操作事件中的事件参数调用 <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A> 方法，<xref:System.Windows.UIElement.ManipulationBoundaryFeedback> 事件除外。 调用 <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A> 时，将不再引发操作事件，并发生触控鼠标事件。 下表描述了取消操作的时间与所发生的鼠标事件之间的关系。

|在其中调用取消的事件|针对已经发生的输入发生的鼠标事件|
|----------------------------------------|-----------------------------------------------------------------|
|<xref:System.Windows.UIElement.ManipulationStarting> 和 <xref:System.Windows.UIElement.ManipulationStarted>|鼠标按下事件。|
|<xref:System.Windows.UIElement.ManipulationDelta>|鼠标按下和鼠标移动事件。|
|<xref:System.Windows.UIElement.ManipulationInertiaStarting> 和 <xref:System.Windows.UIElement.ManipulationCompleted>|鼠标按下、鼠标移动和鼠标弹起事件。|

 请注意，如果在操作处于惯性中时调用 <xref:System.Windows.Input.ManipulationStartingEventArgs.Cancel%2A>，则该方法将返回 `false`，并且输入不会引发鼠标事件。

### <a name="the-relationship-between-touch-and-manipulation-events"></a>触摸事件和操作事件之间的关系
 @No__t-0 总是可以接收触控事件。 如果 <xref:System.Windows.UIElement.IsManipulationEnabled%2A> 属性设置为 `true`，@no__t 则可以同时接收触控事件和操作事件。  如果未处理 @no__t 0 事件（即，@no__t 属性 `false`），则操作逻辑会将触摸屏捕获到元素，并生成操作事件。 如果在 <xref:System.Windows.UIElement.TouchDown> 事件中将 @no__t 0 属性设置为 `true`，则操作逻辑不会生成操作事件。 下图显示了触摸事件和操作事件之间的关系。

 ![触控事件和操作事件之间的关系](./media/ndp-touchmanipulateevents.png "NDP_TouchManipulateEvents")触控和操作事件

 下列内容描述了上图中所示的触摸事件和操作事件之间的关系。

- 当第一个触摸设备在 <xref:System.Windows.UIElement> 上生成 <xref:System.Windows.UIElement.TouchDown> 事件时，操作逻辑将调用 <xref:System.Windows.UIElement.CaptureTouch%2A> 方法，这将生成 @no__t 3 事件。

- 当 <xref:System.Windows.UIElement.GotTouchCapture> 时，操作逻辑将调用 <xref:System.Windows.Input.Manipulation.AddManipulator%2A?displayProperty=nameWithType> 方法，这将生成 @no__t 2 事件。

- 当 @no__t 0 事件发生时，操作逻辑将生成在 @no__t 2 事件之前发生的 @no__t 1 事件。

- 当元素上的最后一个触摸设备引发 <xref:System.Windows.UIElement.TouchUp> 事件时，操作逻辑将生成 @no__t 1 事件。

<a name="focus"></a>
## <a name="focus"></a>焦点
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，有两个与焦点有关的主要概念：键盘焦点和逻辑焦点。

### <a name="keyboard-focus"></a>键盘焦点
 键盘焦点指当前正在接收键盘输入的元素。  在整个桌面上，只能有一个具有键盘焦点的元素。  在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，具有键盘焦点的元素将 @no__t 设置为 `true`。  静态 <xref:System.Windows.Input.Keyboard> 方法 @no__t 返回当前具有键盘焦点的元素。

 可以通过切换到元素或在某些元素上单击鼠标（如 <xref:System.Windows.Controls.TextBox>）来获取键盘焦点。  还可以通过对 @no__t 1 类使用 <xref:System.Windows.Input.Keyboard.Focus%2A> 方法，以编程方式获取键盘焦点。  <xref:System.Windows.Input.Keyboard.Focus%2A> 尝试给指定元素键盘焦点。  @No__t 返回的元素是当前具有键盘焦点的元素。

 为了使元素获得键盘焦点，<xref:System.Windows.UIElement.Focusable%2A> 属性和 @no__t 属性必须设置为**true**。  某些类（如 <xref:System.Windows.Controls.Panel>） @no__t 默认设置为 `false`。因此，如果希望该元素能够获得焦点，则可能必须将此属性设置为 `true`。

 下面的示例使用 <xref:System.Windows.Input.Keyboard.Focus%2A> 将键盘焦点设置到 @no__t 1。  在应用程序中设置初始焦点的建议位置是在 @no__t 0 事件处理程序中。

 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]

 有关键盘焦点的详细信息，请参阅[焦点概述](focus-overview.md)。

### <a name="logical-focus"></a>逻辑焦点
 逻辑焦点指的是焦点范围中的 @no__t 0。  一个应用程序中可以有多个具有逻辑焦点的元素，但在一个特定的焦点范围中只能有一个具有逻辑焦点的元素。

 焦点作用域是一个容器元素，用于跟踪其范围内的 @no__t 0。  焦点离开焦点范围时，焦点元素会失去键盘焦点，但保留逻辑焦点。  焦点返回到焦点范围时，焦点元素会再次获得键盘焦点。  这使得键盘焦点可在多个焦点范围之间切换，但确保了焦点返回到焦点范围时，焦点范围中的焦点元素仍为焦点元素。

 可以通过将 @no__t 的附加属性设置为 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，将元素转换为焦点范围，方法是将第2个附加 @no__t 属性设置为 `true`，或在代码中通过使用 @no__t 方法设置附加属性。

 下面的示例通过设置 @no__t 附加属性，将 @no__t 0 转换为焦点范围。

 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]

 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]

 默认情况下，默认值为 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的类是 <xref:System.Windows.Window>、<xref:System.Windows.Controls.Menu>、<xref:System.Windows.Controls.ToolBar> 和 @no__t。

 具有键盘焦点的元素还将对其所属的焦点范围具有逻辑焦点;因此，将焦点设置到 @no__t 类或基元素类上具有 <xref:System.Windows.Input.Keyboard.Focus%2A> 方法的元素上时，将尝试为元素设置键盘焦点和逻辑焦点。

 若要确定焦点范围中的焦点元素，请使用 <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>。 若要更改焦点范围中的焦点元素，请使用 <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>。

 有关逻辑焦点的详细信息，请参阅[焦点概述](focus-overview.md)。

<a name="mouse_position"></a>
## <a name="mouse-position"></a>鼠标位置
 @No__t-0 输入 API 提供有关坐标空间的有用信息。  例如，坐标 `(0,0)` 为左上角坐标，但该坐标是树中那一个元素的左上角坐标？ 是属于输入目标的元素？ 是在其上附加事件处理程序的元素？ 还是其他内容？ 为避免混淆，在使用通过鼠标获取的坐标时，@no__t 输入 API 需要指定引用框架。 @No__t-0 方法返回鼠标指针相对于指定元素的坐标。

<a name="mouse_capture"></a>
## <a name="mouse-capture"></a>鼠标捕获
 鼠标设备专门保留称为鼠标捕获的模式特征。 鼠标捕获用于在拖放操作开始时保持转换的输入状态，从而不一定发生涉及鼠标指针的标称屏幕位置的其他操作。 拖动过程中，未终止拖放时用户无法单击，这使得大多数鼠标悬停提示在拖动来源拥有鼠标捕获时是不合适的。 输入系统公开可确定鼠标捕获状态的 Api，以及可强制将鼠标捕获到特定元素或清除鼠标捕获状态的 Api。 有关拖放操作的详细信息，请参阅[拖放概述](drag-and-drop-overview.md)。

<a name="commands"></a>
## <a name="commands"></a>命令
 使用命令，输入处理可以更多地在语义级别（而不是在设备输入级别）进行。  命令是简单的指令，如 `Cut`、`Copy`、`Paste` 或 `Open`。  命令可用于集中命令逻辑。  可以通过 <xref:System.Windows.Controls.Menu>、@no__t 或键盘快捷方式访问同一命令。 命令还提供一种机制，用于在命令不可用时禁用控件。

 @no__t 为 <xref:System.Windows.Input.ICommand> 的 @no__t 1 实现。  当执行 <xref:System.Windows.Input.RoutedCommand> 时，将在命令目标上引发 <xref:System.Windows.Input.CommandManager.PreviewExecuted> 和 @no__t 2 事件，此事件将通过元素树进行隧道和冒泡，如其他输入。  如果未设置命令目标，则具有键盘焦点的元素将成为命令目标。  执行命令的逻辑附加到 <xref:System.Windows.Input.CommandBinding>。  如果 @no__t 0 事件对于该特定命令达到 <xref:System.Windows.Input.CommandBinding>，则会调用 <xref:System.Windows.Input.CommandBinding> 的 @no__t。  此处理程序执行该命令的操作。

 有关命令的详细信息，请参阅[命令概述](commanding-overview.md)。

 @no__t 提供了一种通用命令库，其中包含 <xref:System.Windows.Input.ApplicationCommands>、<xref:System.Windows.Input.MediaCommands>、<xref:System.Windows.Input.ComponentCommands>、@no__t 和 @no__t，或者你可以定义自己的命令。

 下面的示例演示如何设置 <xref:System.Windows.Controls.MenuItem>，以便在单击此项时，它将调用 <xref:System.Windows.Controls.TextBox> 上的 <xref:System.Windows.Input.ApplicationCommands.Paste%2A> 命令，假定 @no__t 为3。

 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]

 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]

 有关 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的命令的详细信息，请参阅[命令概述](commanding-overview.md)。

<a name="the_input_system_and_base_elements"></a>
## <a name="the-input-system-and-base-elements"></a>输入系统和基元素
 输入事件（例如 <xref:System.Windows.Input.Mouse>、<xref:System.Windows.Input.Keyboard> 和 <xref:System.Windows.Input.Stylus> 类定义的附加事件）由输入系统引发，并根据运行时的可视化树命中测试，注入到对象模型中的特定位置。

 每个 <xref:System.Windows.Input.Mouse>、<xref:System.Windows.Input.Keyboard> 和 <xref:System.Windows.Input.Stylus> 定义为附加事件的事件也会由基元素类 <xref:System.Windows.UIElement> 和 <xref:System.Windows.ContentElement> 作为新的路由事件重新公开。 基元素路由事件由处理原始附加事件并重用事件数据的类生成。

 当输入事件通过其基元素输入事件实现与特定源元素相关联时，可以通过基于逻辑和可视化树对象的组合的事件路由的其余部分进行路由，并由应用程序代码进行处理。  通常，使用 <xref:System.Windows.UIElement> 和 <xref:System.Windows.ContentElement> 上的路由事件处理这些与设备有关的输入事件更方便，因为可以在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 和代码中使用更直观的事件处理程序语法。 你可以选择处理发起进程的附加事件，但将会面临几个问题：附加事件可能会被基元素类处理标记为已处理，并且你需要使用访问器方法（而不是真正的事件语法）才能为附加事件附加处理程序。

<a name="whats_next"></a>
## <a name="whats-next"></a>下一步
 现在有多种方法来处理 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的输入。  你还应该对 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用的各种类型的输入事件和路由事件机制有进一步的了解。

 也可以获取更详细说明 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 框架元素和事件路由的详细资源。 有关详细信息，请参阅以下概述：[命令概述](commanding-overview.md)、[焦点概述](focus-overview.md)、[基元素概述](base-elements-overview.md)、[WPF 中的树](trees-in-wpf.md)和[路由事件概述](routed-events-overview.md)。

## <a name="see-also"></a>请参阅

- [焦点概述](focus-overview.md)
- [命令概述](commanding-overview.md)
- [路由事件概述](routed-events-overview.md)
- [基元素概述](base-elements-overview.md)
- [属性](properties-wpf.md)
