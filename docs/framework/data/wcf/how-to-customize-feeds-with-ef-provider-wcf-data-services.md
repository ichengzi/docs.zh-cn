---
title: 如何：通过实体框架提供程序（WCF 数据服务）自定义源
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: fd16272e-36f2-415e-850e-8a81f2b17525
ms.openlocfilehash: 8f994065ea42d6fc522fa297cafa8c46a8164e67
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780152"
---
# <a name="how-to-customize-feeds-with-the-entity-framework-provider-wcf-data-services"></a>如何：通过实体框架提供程序（WCF 数据服务）自定义源
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 使您可以在数据服务响应中自定义 Atom 序列化，以便可以将实体属性映射到在 AtomPub 协议中定义的未使用的元素。 本主题演示如何使用实体框架提供程序为 .edmx 文件中定义的数据模型中的实体类型定义映射特性。 有关详细信息，请参阅[源自定义](feed-customization-wcf-data-services.md)。  
  
 在本主题中，您将手动修改由工具生成且包含数据模型的 .edmx 文件。 由于实体设计器不支持数据模型扩展，因此必须手动修改此文件。 有关实体数据模型工具生成的 .edmx 文件的详细信息，请参阅[.Edmx 文件概述（实体框架）](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))。 本主题中的示例使用罗斯文示例数据服务和自动生成的客户端数据服务类。 此服务和客户端数据类是在完成[WCF 数据服务快速入门](quickstart-wcf-data-services.md)时创建的。  
  
### <a name="to-manually-modify-the-northwindedmx-file-to-add-feed-customization-attributes"></a>手动修改 Northwind.edmx 文件以添加源自定义特性  
  
1. 在**解决方案资源管理器**中，右键单击该`Northwind.edmx`文件，然后单击 "**打开方式**"。  
  
2. 在 "**打开 With Northwind** " 对话框中，选择 " **XML 编辑器**"，然后单击 **"确定"** 。  
  
3. 找到 `ConceptualModels` 元素，并用以下包含源自定义映射特性的元素替换现有的 `Customers` 实体类型：  
  
     [!code-xml[Astoria Custom Feeds#EdmFeedCustomers](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/northwind.csdl#edmfeedcustomers)]  
  
4. 保存更改并关闭 Northwind.edmx 文件。  
  
5. 可有可无右键单击 Northwind 文件，然后单击 "**运行自定义工具**"。  
  
     此时将重新生成可能需要的对象层文件。  
  
6. 重新编译该项目。  
  
## <a name="example"></a>示例  
 上面的示例为 URI `http://myservice/Northwind.svc/Customers('ALFKI')` 返回以下结果。  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/edmfeedresult.xml#edmfeedresult)]  
  
## <a name="see-also"></a>请参阅

- [实体框架提供程序](entity-framework-provider-wcf-data-services.md)
