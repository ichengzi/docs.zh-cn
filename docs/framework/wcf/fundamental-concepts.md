---
title: Windows Communication Foundation 基础概念
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], concepts
- concepts [WCF]
- fundamentals [WCF]
- Windows Communication Foundation [WCF], concepts
ms.assetid: 3e7e0afd-7913-499d-bafb-eac7caacbc7a
ms.openlocfilehash: 9dcaa5f73dd8a4ec1943cb7fc840feee889563b8
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319851"
---
# <a name="fundamental-windows-communication-foundation-concepts"></a>Windows Communication Foundation 基础概念

本文档提供 Windows Communication Foundation （WCF）体系结构的概要视图。 本文档旨在解释关键概念以及这些概念之间的关系。 有关创建 WCF 服务和客户端的最简单版本的教程，请参阅[入门教程](getting-started-tutorial.md)。 若要了解 WCF 编程，请参阅[基本 Wcf 编程](basic-wcf-programming.md)。

## <a name="wcf-fundamentals"></a>WCF 基础知识

WCF 是一个运行时和一组 Api，用于创建在服务和客户端之间发送消息的系统。 它使用相同的基础结构和 API 来创建应用程序，这些应用程序可与同一计算机系统上或驻留在另一家公司内并通过 Internet 访问的系统上的其他应用程序进行通信。

### <a name="messaging-and-endpoints"></a>消息和终结点

WCF 基于基于消息的通信的概念，可作为消息建模的任何内容（例如 HTTP 请求或消息队列（也称为 MSMQ）消息）都可以在编程模型中以统一的方式表示。 这样，就可以在不同传输机制间提供一个统一的 API。

此模型区分_客户端_（启动通信的应用程序）和_服务_（这些应用程序等待客户端与其通信并响应通信）。 单个应用程序既可以充当客户端，也可以充当服务。 有关示例，请参阅[双工服务](./feature-details/duplex-services.md)和[对等网络](./feature-details/peer-to-peer-networking.md)。

消息在终结点之间发送。 _终结点_是发送或接收消息的位置，它们定义消息交换所需的所有信息。 服务公开一个或多个应用程序终结点（以及零个或更多个基础结构终结点），而客户端生成一个与服务的其中一个终结点兼容的终结点。

_终结点_以基于标准的方式描述消息应发送到的位置、消息的发送方式以及消息的外观。 服务可以公开此信息作为元数据，客户端可以处理这些元数据以生成相应的 WCF 客户端和通信_堆栈_。

### <a name="communication-protocols"></a>通信协议

通信堆栈中的一个必需元素是_传输协议_。 可以使用常用传输协议（如 HTTP 和 TCP）通过 Intranet 和 Internet 发送消息。 也可以使用其他支持与消息队列应用程序和对等网络网格上的节点进行通信的传输协议。 使用 WCF 的内置扩展点可以添加更多传输机制。

通信堆栈中的另一个必要元素是指定如何对任意给定消息进行格式化的编码。 WCF 提供以下编码：

- 文本编码，一种可互操作的编码。

- 消息传输优化机制 (MTOM) 编码，该编码是一种可互操作的方法，用于高效地将非结构化二进制数据发送到服务或从服务接收这些数据。

- 用于实现高效传输的二进制编码。

使用 WCF 的内置扩展点可以添加更多编码机制（例如，压缩编码）。

### <a name="message-patterns"></a>消息模式

WCF 支持多种消息传递模式，包括请求-答复、单向和双工通信。 不同传输协议支持不同的消息模式，因而会影响它们所支持的交互类型。 WCF Api 和运行时还有助于安全可靠地发送消息。

## <a name="wcf-terms"></a>WCF 术语

WCF 文档中使用的其他概念和术语包括：

**消息**  
 消息是一个独立的数据单元，它可能由几个部分组成，包括消息正文和消息头。

**服务**  
 服务是一个构造，它公开一个或多个终结点，其中每个终结点都公开一个或多个服务操作。

**终结点**  
 终结点是用来发送或接收消息（或同时执行这两种操作）的构造。 它包含一个位置（地址），用于定义消息的发送位置、描述消息发送方式的通信机制（绑定）规范，以及可以发送或接收的一组消息（或这两种消息的定义）描述可以发送的消息的位置（服务约定）。

WCF 服务作为终结点集合向外界公开。

**应用程序终结点**  
 一个终结点，由应用程序公开并对应于该应用程序实现的服务协定。

**基础结构终结点**  
 一个终结点，由基础结构公开，以便实现与服务协定无关的服务需要或提供的功能。 例如，服务可能拥有一个提供元数据信息的基础结构终结点。

**地址**  
 地址用于指定接收消息的位置。 地址以统一资源标识符 (URI) 的形式指定。 URI 架构部分指定用于到达地址的传输机制，如 HTTP 和 TCP。 URI 的层次结构部分包含一个唯一的位置，其格式取决于传输机制。

使用终结点地址可以为服务中的每个终结点创建唯一的终结点地址，或者在某些条件下在终结点之间共享一个地址。 下面的示例演示了一个将 HTTPS 协议和一个非默认端口结合使用的地址：

```http
HTTPS://cohowinery:8005/ServiceModelSamples/CalculatorService
```

**绑定**  
 绑定定义终结点与外界进行通信的方式。 它由一组称为绑定元素的要素构造而成，这些元素“堆叠”在一起以形成通信基础结构。 绑定最起码应定义传输协议（如 HTTP 或 TCP）和所使用的编码（如文本或二进制）。 绑定可以包含指定详细信息（例如，用于保护消息的安全机制或终结点所使用的消息模式）的绑定元素。 有关详细信息，请参阅[配置服务](configuring-services.md)。

**Binding 元素**  
 绑定元素表示绑定的特定部分，如传输协议、编码、基础结构级协议（如 WS-ReliableMessaging）的实现以及通信堆栈的其他任何要素。

**行为**  
 行为是控制服务、终结点、特定操作或客户端的各个运行时方面的要素。 行为按照范围进行分组：常见行为在全局范围内影响所有终结点，服务行为仅影响与服务相关的方面，终结点行为仅影响与终结点相关的属性，操作级行为影响特定操作。 例如，有一种服务行为是遏制，它指定当过多的消息可能超出服务的处理能力时，服务应该如何反应。 另一方面，终结点行为仅控制与终结点相关的方面，如查找安全凭据的方式和位置。

**系统提供的绑定**  
 WCF 包含许多系统提供的绑定。 这些绑定是针对特定方案进行优化的绑定元素的集合。 例如，<xref:System.ServiceModel.WSHttpBinding> 旨在实现与实现各种 WS \* 规范的服务的互操作性。 通过仅提供那些可以正确应用于特定方案的选项，这些预定义的绑定可以节省时间。 如果预定义的绑定不能满足你的需求，则可以创建你自己的自定义绑定。

**配置与编码**  
 可以通过代码编写、配置或将两者结合在一起对应用程序进行控制。 配置的优点在于，它使非开发人员（如网络管理员）可以在代码编写完成后直接对客户端和服务参数进行设置，而不必重新进行编译。 使用配置不仅可以设置值（如终结点地址），还可以通过添加终结点、绑定和行为来实施进一步的控制。 通过代码编写，开发人员可以保持对服务或客户端的所有组件的严格控制，而且可以对通过配置完成的所有设置进行检查，并根据需要通过代码进行重写。

**服务操作**  
 服务操作是在服务的代码中定义的过程，用于实现某种操作的功能。 此操作作为 WCF 客户端上的方法向客户端公开。 该方法可以返回一个值，并可采用数量可选的自变量，或是不采用任何自变量且不返回任何响应。 例如，一个实现简单的“Hello”的操作可以用作客户端存在通知，并可以开始一系列操作。

**服务协定**  
 服务协定将多个相关的操作联系在一起，组成单个功能单元。 协定可以定义服务级设置，如服务的命名空间、对应的回调协定以及其他此类设置。 在大多数情况下，协定的定义方法是用所选的编程语言创建一个接口，然后将 <xref:System.ServiceModel.ServiceContractAttribute> 属性应用于该接口。 通过实现该接口，可生成实际的服务代码。

**操作协定**  
 操作协定定义参数和操作的返回类型。 在创建定义服务协定的接口时，可以通过将 <xref:System.ServiceModel.OperationContractAttribute> 属性应用于协定中包含的每个方法定义来表示一个操作协定。 可以将操作建模为采用单个消息作为参数并返回单个消息，或者建模为采用一组类型作为参数并返回一个类型。 在后一种情况下，系统将确定需要为该操作交换的消息的格式。

**消息协定**  
 消息协定描述消息的格式。 例如，它会声明消息元素应包含在消息头中还是包含在消息正文中，应该对消息的何种元素应用何种级别的安全性，等等。

**错误协定**  
 可以将错误协定与服务操作进行关联，以指示可能返回到调用方的错误。 一个操作可以具有零个或更多个与其相关联的错误。 这些错误是在编程模型中作为异常建模的 SOAP 错误。

**数据协定**  
 服务使用的数据类型必须在元数据中进行描述， 以使其他各方可以与该服务进行交互操作。 数据类型可以在消息的任何部分使用（例如，作为参数或返回类型）。 如果服务仅使用简单类型，则无需显式使用数据协定。

**承载**  
 服务必须承载于某个进程中。 _宿主_是控制服务生存期的应用程序。 服务可以是自承载的，也可以由现有的宿主进程进行管理。

**自承载服务**  
 自承载服务是在开发人员创建的进程应用程序中运行的服务。 开发人员控制服务的生存期、设置服务的属性、打开服务（这会将服务设置为侦听模式）以及关闭服务。

**承载进程**  
 托管进程是专为承载服务而设计的应用程序。 这些宿主进程包括 Internet 信息服务 (IIS)、Windows 激活服务 (WAS) 和 Windows 服务。 在这些宿主方案中，由宿主控制服务的生存期。 例如，使用 IIS 可以设置包含服务程序集和配置文件的虚拟目录。 在收到消息时，IIS 将启动服务并控制服务的生存期。

**实例化**  
 每个服务都具有一个实例化模型。 有三种实例化模型：“单个”，在这种模型中，由单个 CLR 对象为所有客户端提供服务；“每个调用”，在这种模型中，将创建一个新的 CLR 对象来处理每个客户端调用；“每个会话”，在这种模型中，将创建一组 CLR 对象，并且为每个独立的会话使用一个对象。 实例化模型的选择取决于应用程序需求和服务的预期使用模式。

**客户端应用程序**  
 客户端应用程序是与一个或多个终结点交换消息的程序。 客户端应用程序可通过创建 WCF 客户端的实例和调用该 WCF 客户端的方法来启动。 需要注意的是，单个应用程序既可以充当客户端，也可以充当服务。

**频道**  
 通道是绑定元素的具体实现。 绑定表示配置，而通道是与该配置相关联的实现。 因此，每个绑定元素都有一个相关联的通道。 通道堆叠在一起以形成绑定的具体实现：通道堆栈。

**WCF 客户端**  
 客户端应用程序构造，将服务操作公开为方法（采用所选的 .NET Framework 编程语言，如 Visual Basic 或视觉对象C#）。 任何应用程序都可以承载 WCF 客户端，包括承载服务的应用程序。 因此，可以创建一个包含其他服务的 WCF 客户端的服务。

WCF 客户端可以使用 " [svcutil.exe" 元数据实用工具（）](servicemodel-metadata-utility-tool-svcutil-exe.md)进行自动生成，并将其指向发布元数据的运行中服务。

**元数据**  
 服务的元数据描述服务的各种特征，外部实体需要了解这些特征以便与该服务进行通信。 元数据[实用工具（svcutil.exe）](servicemodel-metadata-utility-tool-svcutil-exe.md)可以使用元数据生成 WCF 客户端，以及客户端应用程序可用于与服务进行交互的伴随配置。

服务所公开的元数据包括 XML 架构文档（用于定义服务的数据协定）和 WSDL 文档（用于描述服务的方法）。

启用元数据后，WCF 可通过检查服务及其终结点来自动生成服务的元数据。 若要发布服务的元数据，必须显式启用元数据行为。

**Security**  
 在 WCF 中，包括保密性（为防止窃听而进行的消息加密）、完整性（用于检测消息篡改的方法）、身份验证（用于验证服务器和客户端的方法）以及授权（对的访问控制资源）。 这些函数通过利用现有的安全机制（例如 HTTP 上的 TLS （也称为 HTTPS））或实现一个或多个不同的 WS \* 安全规范来提供。

**传输安全模式**  
 传输安全模式指定由传输层机制（如 HTTPS）提供保密性、完整性和身份验证。 在使用像 HTTPS 这样的传输协议时，此模式的优点在于性能出色，而且由于它在 Internet 上非常流行，因此很容易理解。 其缺点在于，这种安全分别应用于通信路径中的每个跃点，这使得通信容易遭受“中间人”攻击。

**消息安全模式**  
 指定通过实现一个或多个安全规范（如名为[Web Services 安全性： SOAP Message security](https://go.microsoft.com/fwlink/?LinkId=94684)的规范）来提供安全性。 每个消息都包含必要的安全机制，用于在消息传输过程中保证安全，并使接收方能够检测到篡改和对消息进行解密。 从这种意义上说，安全信息包装在每个消息中，从而提供了跨多个跃点的端到端安全。 由于安全信息成为消息的一部分，因此还可以在消息中包含多种凭据（这些凭据称为_声明_）。 这种方法还具有这样一个优点，即消息可以通过任意传输协议（包括在其起点和目标之间的多个传输协议）安全地传送。 这种方法的缺点在于所使用的加密机制较为复杂，使性能受到影响。

**带有消息凭据的传输安全模式**  
 此模式指定使用传输层来提供消息的保密性、身份验证和完整性，并且每个消息都可以包含消息接收方所要求的多个凭据（声明）。

**WS \***  
 一组不断增加的、在 WCF 中实现的 Web 服务 (WS) 规范（如 WS-Security、WS-ReliableMessaging 等）的简写。

## <a name="see-also"></a>请参阅

- [什么是 Windows Communication Foundation](whats-wcf.md)
- [Windows Communication Foundation 体系结构](architecture.md)
