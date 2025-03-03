---
title: 使用 My.Resources 和 My.Settings 快速开发应用程序
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], developing applications
- rapid application development (RAD), My.Resources
- rapid application development (RAD), My.Settings
- My.Resources object [Visual Basic], developing applications
ms.assetid: 68284ab1-b685-4814-a2a4-01ae40445ff8
ms.openlocfilehash: ce9a5bf76ba3132f58aa40227a145d8b5bf1591d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349267"
---
# <a name="rapid-application-development-with-myresources-and-mysettings-visual-basic"></a>使用 My.Resources 和 My.Settings 快速开发应用程序 (Visual Basic)

The `My.Resources` object provides access to the application's resources and allows you to dynamically retrieve resources for your application.  
  
## <a name="retrieving-resources"></a>检索资源  

 A number of resources such as audio files, icons, images, and strings can be retrieved through the `My.Resources` object. For example, you can access the application's culture-specific resource files. The following example sets the icon of the form to the icon named `Form1Icon` stored in the application's resource file.  
  
 [!code-vb[VbVbcnMy#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMy/VB/Class1.vb#7)]  
  
 The `My.Resources` object exposes only global resources. It does not provide access to resource files associated with forms. You must access the form resources from the form.  
  
 Similarly, the `My.Settings` object provides access to the application's settings and allows you to dynamically store and retrieve property settings and other information for your application. For more information, see [My.Resources Object](../../../visual-basic/language-reference/objects/my-resources-object.md) and [My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
## <a name="see-also"></a>请参阅

- [My.Resources 对象](../../../visual-basic/language-reference/objects/my-resources-object.md)
- [My.Settings 对象](../../../visual-basic/language-reference/objects/my-settings-object.md)
- [访问应用程序设置](../../../visual-basic/developing-apps/programming/app-settings/index.md)
