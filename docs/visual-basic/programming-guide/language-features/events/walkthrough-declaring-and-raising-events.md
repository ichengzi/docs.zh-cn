---
title: 声明和引发事件
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: 6f4c303604f9cf55b4ecd500636e0d2772b6234c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345092"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>演练：声明和引发事件 (Visual Basic)
This walkthrough demonstrates how to declare and raise events for a class named `Widget`. After you complete the steps, you might want to read the companion topic, [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), which shows how to use events from `Widget` objects to provide status information in an application.  
  
## <a name="the-widget-class"></a>The Widget Class  
 Assume for the moment that you have a `Widget` class. Your `Widget` class has a method that can take a long time to execute, and you want your application to be able to put up some kind of completion indicator.  
  
 Of course, you could make the `Widget` object show a percent-complete dialog box, but then you would be stuck with that dialog box in every project in which you used the `Widget` class. A good principle of object design is to let the application that uses an object handle the user interface—unless the whole purpose of the object is to manage a form or dialog box.  
  
 The purpose of `Widget` is to perform other tasks, so it is better to add a `PercentDone` event and let the procedure that calls `Widget`'s methods handle that event and display status updates. The `PercentDone` event can also provide a mechanism for canceling the task.  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>To build the code example for this topic  
  
1. Open a new Visual Basic Windows Application project and create a form named `Form1`.  
  
2. Add two buttons and a label to `Form1`.  
  
3. 按下表所示命名对象。  
  
    |对象|Property|设置|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|Start Task|  
    |`Button2`|`Text`|取消|  
    |`Label`|`(Name)`，`Text`|lblPercentDone, 0|  
  
4. On the **Project** menu, choose **Add Class** to add a class named `Widget.vb` to the project.  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>To declare an event for the Widget class  
  
- Use the `Event` keyword to declare an event in the `Widget` class. Note that an event can have `ByVal` and `ByRef` arguments, as `Widget`'s `PercentDone` event demonstrates:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 When the calling object receives a `PercentDone` event, the `Percent` argument contains the percentage of the task that is complete. The `Cancel` argument can be set to `True` to cancel the method that raised the event.  
  
> [!NOTE]
> You can declare event arguments just as you do arguments of procedures, with the following exceptions: Events cannot have `Optional` or `ParamArray` arguments, and events do not have return values.  
  
 The `PercentDone` event is raised by the `LongTask` method of the `Widget` class. `LongTask` takes two arguments: the length of time the method pretends to be doing work, and the minimum time interval before `LongTask` pauses to raise the `PercentDone` event.  
  
#### <a name="to-raise-the-percentdone-event"></a>To raise the PercentDone event  
  
1. To simplify access to the `Timer` property used by this class, add an `Imports` statement to the top of the declarations section of your class module, above the `Class Widget` statement.  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. 将下面的代码添加到 `Widget` 类中:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 When your application calls the `LongTask` method, the `Widget` class raises the `PercentDone` event every `MinimumInterval` seconds. When the event returns, `LongTask` checks to see if the `Cancel` argument was set to `True`.  
  
 A few disclaimers are necessary here. For simplicity, the `LongTask` procedure assumes you know in advance how long the task will take. This is almost never the case. Dividing tasks into chunks of even size can be difficult, and often what matters most to users is simply the amount of time that passes before they get an indication that something is happening.  
  
 You may have spotted another flaw in this sample. The `Timer` property returns the number of seconds that have passed since midnight; therefore, the application gets stuck if it is started just before midnight. A more careful approach to measuring time would take boundary conditions such as this into consideration, or avoid them altogether, using properties such as `Now`.  
  
 Now that the `Widget` class can raise events, you can move to the next walkthrough. [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) demonstrates how to use `WithEvents` to associate an event handler with the `PercentDone` event.  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [演练：处理事件](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [事件](../../../../visual-basic/programming-guide/language-features/events/index.md)
