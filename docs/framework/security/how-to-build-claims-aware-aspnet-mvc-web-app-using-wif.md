---
title: 如何：使用 WIF 生成声明感知 ASP.NET MVC Web 应用程序
ms.date: 03/30/2017
ms.assetid: 0efb76bc-9f7b-4afe-be1c-2a57c917010b
author: BrucePerlerMS
ms.openlocfilehash: 4d245288b04d8ed3d997bc5572b40c7f8a9334e5
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045451"
---
# <a name="how-to-build-claims-aware-aspnet-mvc-web-application-using-wif"></a>如何：使用 WIF 生成声明感知 ASP.NET MVC Web 应用程序
## <a name="applies-to"></a>适用于  
  
- Microsoft® Windows® Identity Foundation (WIF)  
  
- ASP.NET® MVC  
  
## <a name="summary"></a>总结  
 本操作说明提供了创建简单的声明感知 ASP.NET MVC Web 应用程序的详细分步过程。 还提供关于如何测试简单的声明感知 ASP.NET MVC Web 应用程序以确保成功实现基于声明的身份验证的说明。 本操作说明不包括如何创建安全令牌服务 (STS) 的详细说明，且假定你已配置 STS。  
  
## <a name="contents"></a>内容  
  
- 目标  
  
- 步骤摘要  
  
- 步骤 1 – 创建简单的 ASP.NET MVC 应用程序  
  
- 步骤 2 – 为基于声明的身份验证配置 ASP.NET MVC 应用程序  
  
- 步骤 3 - 测试你的解决方案  
  
- 相关项  
  
## <a name="objectives"></a>目标  
  
- 为基于声明的身份验证配置 ASP.NET MVC Web 应用程序  
  
- 测试成功的声明感知 ASP.NET MVC Web 应用程序  
  
## <a name="summary-of-steps"></a>步骤摘要  
  
- 步骤 1 – 创建简单的 ASP.NET MVC 应用程序  
  
- 步骤 2 – 为基于声明的身份验证配置 ASP.NET MVC 应用程序  
  
- 步骤 3 - 测试你的解决方案  
  
## <a name="step-1--create-simple-aspnet-mvc-application"></a>步骤 1 – 创建简单的 ASP.NET MVC 应用程序  
 在此步骤中，将创建一个新的 ASP.NET MVC 应用程序。  
  
#### <a name="to-create-simple-aspnet-mvc-application"></a>创建简单的 ASP.NET MVC 应用程序  
  
1. 启动 Visual Studio，然后依次单击“文件”、“新建”和“项目”。  
  
2. 在“新建项目”窗口中，单击“ASP.NET MVC 3 Web 应用程序”。  
  
3. 在“名称”中，输入 `TestApp`，然后按“确定”。  
  
4. 在“新建 ASP.NET MVC 3 项目”对话框中，从可用模板中选择“Internet 应用程序”，确保将“视图引擎”设置为“Razor”，然后单击“确定”。  
  
5. 打开新建项目时，右键单击“解决方案资源管理器”中的“TestApp”项目，然后选择“属性面板”选项。  
  
6. 在项目的属性页上，单击左侧的“Web”选项卡，并确保选择了“使用本地 IIS Web 服务器”选项。  
  
## <a name="step-2--configure-aspnet-mvc-application-for-claims-based-authentication"></a>步骤 2 – 为基于声明的身份验证配置 ASP.NET MVC 应用程序  
 在此步骤中，将配置条目添加到 ASP.NET MVC Web 应用程序的 Web.config 配置文件中，以使其可感知声明。  
  
#### <a name="to-configure-aspnet-mvc-application-for-claims-based-authentication"></a>为基于声明的身份验证配置 ASP.NET MVC 应用程序  
  
1. 将以下配置节定义添加到 Web.config 配置文件。 它们定义 Windows Identity Foundation 所需的配置节。 将定义紧随添加在 \<configuration> 起始元素后：  
  
    ```xml  
    <configSections>  
        <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
        <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    </configSections>  
    ```  
  
2. 添加 \<location> 元素，用于启用对应用程序的联合元数据的访问权限：  
  
    ```xml  
    <location path="FederationMetadata">  
        <system.web>  
            <authorization>  
                <allow users="*" />  
            </authorization>  
        </system.web>  
    </location>  
    ```  
  
3. 在 \<system.web> 元素内添加以下配置条目以拒绝用户、禁用本机身份验证并启用 WIF 来管理身份验证。  
  
    ```xml  
    <authorization>  
        <deny users="?" />  
    </authorization>  
    <authentication mode="None" />  
    ```  
  
4. 添加以下 Windows Identity Foundation 相关配置条目，并确保 ASP.NET 应用程序的 URL 和端口号与 \<audienceUris> 条目、\<wsFederation> 元素的“realm”特性和 \<wsFederation> 元素的“reply”特性中的值相匹配。 还需确保“issuer”值与安全令牌服务 (STS) URL 相适应。  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <audienceUris>  
                <add value="http://localhost:28503/" />  
            </audienceUris>  
            <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
                <trustedIssuers>  
                    <add thumbprint="1234567890ABCDEFGHIJKLMNOPQRSTUVWXYZ1234" name="YourSTSName" />  
                </trustedIssuers>   
            </issuerNameRegistry>  
            <certificateValidation certificateValidationMode="None" />  
        </identityConfiguration>  
    </system.identityModel>  
    <system.identityModel.services>  
        <federationConfiguration>  
            <cookieHandler requireSsl="false" />  
            <wsFederation passiveRedirectEnabled="true" issuer="http://localhost:13922/wsFederationSTS/Issue" realm="http://localhost:28503/" reply="http://localhost:28503/" requireHttps="false" />  
        </federationConfiguration>  
    </system.identityModel.services>  
    ```  
  
5. 将引用添加到 <xref:System.IdentityModel> 程序集。  
  
6. 编译此解决方案，确保没有任何错误。  
  
## <a name="step-3--test-your-solution"></a>步骤 3 - 测试你的解决方案  
 在此步骤中，将测试为基于声明的身份验证配置的 ASP.NET MVC Web 应用程序。 若要执行基本测试，需添加用于在安全令牌服务 (STS) 颁发的令牌中显示声明的简单代码。  
  
#### <a name="to-test-your-aspnet-mvc-application-for-claims-based-authentication"></a>为基于声明的身份验证测试 ASP.NET MVC 应用程序  
  
1. 在“解决方案资源管理器”中，展开 Controllers 文件夹，并在编辑器中打开 HomeController.cs 文件。 将以下代码添加到 Index 方法中：  
  
    ```csharp  
    public ActionResult Index()  
    {  
        ViewBag.ClaimsIdentity = Thread.CurrentPrincipal.Identity;  
  
        return View();  
    }  
    ```  
  
2. 在“解决方案资源管理器”中，依次展开 Views 和 Home 文件夹，然后在编辑器中打开 Index.cshtml 文件。 删除其内容并添加以下标记：  
  
    ```html  
    @{  
        ViewBag.Title = "Home Page";  
    }  
  
    <h2>Welcome: @ViewBag.ClaimsIdentity.Name</h2>  
    <h3>Values from Identity</h3>  
    <table>  
        <tr>  
            <th>  
                IsAuthenticated   
            </th>  
            <td>  
                @ViewBag.ClaimsIdentity.IsAuthenticated   
            </td>  
        </tr>  
        <tr>  
            <th>  
                Name   
            </th>          
            <td>  
                @ViewBag.ClaimsIdentity.Name  
            </td>          
        </tr>  
    </table>  
    <h3>Claims from ClaimsIdentity</h3>  
    <table>  
        <tr>  
            <th>  
                Claim Type  
            </th>  
            <th>  
                Claim Value  
            </th>  
            <th>  
                Value Type  
            </th>  
            <th>  
                Subject Name  
            </th>          
            <th>  
                Issuer Name  
            </th>          
        </tr>  
            @foreach (System.Security.Claims.Claim claim in ViewBag.ClaimsIdentity.Claims ) {  
        <tr>  
            <td>  
                @claim.Type  
            </td>  
            <td>  
                @claim.Value  
            </td>  
            <td>  
                @claim.ValueType  
            </td>  
            <td>  
                @claim.Subject.Name  
            </td>  
            <td>  
                @claim.Issuer  
            </td>  
        </tr>  
    }  
    </table>  
    ```  
  
3. 按 F5 键运行解决方案。  
  
4. 应当会看到在安全令牌服务颁发给你的令牌中显示声明的页面。  
  
## <a name="related-items"></a>相关项  
  
- [如何：使用 WIF 生成声明感知 ASP.NET Web 窗体应用程序](how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)
