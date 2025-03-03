---
title: 过时成员 - .NET Framework
ms.custom: updateeachrelease
ms.date: 10/17/2017
helpviewer_keywords:
- .NET Framework, obsolete members
- members, obsolete in .NET Framework
- obsolete members [.NET Framework]
ms.assetid: 0ee25062-4071-4d3c-a552-87a75d3ecd34
ms.openlocfilehash: 2231552f9c3353890963a4ad5388194036fa27bf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134104"
---
# <a name="obsolete-members-in-the-net-framework"></a>.NET Framework 中的过时成员

本文中的表列出了 .NET Framework 4.5 和更高版本中由程序集组织的已过时的类型成员。 使用以下链接可查看每个程序集中过时的成员和建议的备选项的列表。 本文未列出过时类型的成员。 有关过时类型的列表，请参阅 [过时类型](obsolete-types.md)。

- [系统程序集中的过时成员](#SystemMembers)

  - [mscorlib.dll](#mscorlib)

  - [PresentationCore.dll](#PresentationCore)

  - [PresentationFramework.dll](#PresFW)

  - [System.Activities.dll](#Act)

  - [System.Activities.Presentation.dll](#ActPres)

  - [System.Core.dll](#core)

  - [System.Data.dll](#data)

  - [System.Data.Entity.dll](#entity)

  - [System.Data.OracleClient.dll](#oracleclient)

  - [System.Design.dll](#design)

  - [System.dll](#system)

  - [System.Drawing.dll](#drawing)

  - [System.Messaging.dll](#messaging)

  - [System.ServiceModel.dll](#servicemodel)

  - [System.ServiceModel.Discovery.dll](#smDisc)

  - [System.Web.DataVisualization.dll](#datavisualization)

  - [System.Web.dll](#web)

  - [System.Web.DynamicData.dll](#dynamicdata)

  - [System.Web.Extensions.dll](#extensions)

  - [System.Web.Services.dll](#services)

  - [System.Windows.Forms.dll](#forms)

  - [System.Xaml.dll](#xaml)

  - [System.Xml.dll](#xml)

- [Microsoft 程序集中的过时成员](#MicrosoftMembers)

  - [IEHost.dll 和 IEExec.exe](#IEHost)

  - [ISymWrapper.dll](#isymwrapper)

  - [Microsoft.Build.Conversion.v4.0.dll](#conversion)

  - [Microsoft.Build.Engine.dll](#engine)

  - [Microsoft.Build.Framework.dll](#BuildFW)

  - [Microsoft.Build.Utilities.v4.0.dll](#BuildUtil4)

  - [Microsoft.Data.Entity.Build.Tasks.dll](#data_entity_tasks)

  - [Microsoft.VisualBasic.dll](#visualbasic)

<a name="SystemMembers"></a>

## <a name="obsolete-members-in-system-assemblies"></a>系统程序集中的过时成员

下表列出了系统程序集中的过时成员。 这些程序集用于面向 .NET Framework 的通用\-应用程序开发。

<a name="mscorlib"></a>

### <a name="assembly-mscorlibdll"></a>程序集：mscorlib.dll

|类型|成员|消息|
|----------|------------|-------------|
|<xref:Microsoft.Win32.Registry?displayProperty=nameWithType>|<xref:Microsoft.Win32.Registry.DynData>|<xref:Microsoft.Win32.Registry.DynData> 注册表项仅适用于 Win9x，CLR 将不再支持。 在基于 NT 的操作系统上，请改用 <xref:Microsoft.Win32.Registry.PerformanceData?displayProperty=nameWithType> 注册表项或 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.PerformanceData%2A?displayProperty=nameWithType> 注册表代理。|
|<xref:System.Activator?displayProperty=nameWithType>|<xref:System.Activator.CreateInstance%28System.AppDomain%2CSystem.String%2CSystem.String%2CSystem.Boolean%2CSystem.Reflection.BindingFlags%2CSystem.Reflection.Binder%2CSystem.Object%5B%5D%2CSystem.Globalization.CultureInfo%2CSystem.Object%5B%5D%2CSystem.Security.Policy.Evidence%29>|对沙盒使用证据的方法已过时，并将从 .NET Framework 的未来版本中移除。 请使用不采用 <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 参数的 <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> 的重载。|
|<xref:System.Activator?displayProperty=nameWithType>|<xref:System.Activator.CreateInstance%28System.String%2CSystem.String%2CSystem.Boolean%2CSystem.Reflection.BindingFlags%2CSystem.Reflection.Binder%2CSystem.Object%5B%5D%2CSystem.Globalization.CultureInfo%2CSystem.Object%5B%5D%2CSystem.Security.Policy.Evidence%29>|对沙盒使用证据的方法已过时，并将从 .NET Framework 的未来版本中移除。 请使用不采用 <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 参数的 <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> 的重载。|
|<xref:System.Activator?displayProperty=nameWithType>|<xref:System.Activator.CreateInstanceFrom%28System.AppDomain%2CSystem.String%2CSystem.String%2CSystem.Boolean%2CSystem.Reflection.BindingFlags%2CSystem.Reflection.Binder%2CSystem.Object%5B%5D%2CSystem.Globalization.CultureInfo%2CSystem.Object%5B%5D%2CSystem.Security.Policy.Evidence%29>|对沙盒使用证据的方法已过时，并将从 .NET Framework 的未来版本中移除。 请使用不采用 <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 参数的 <xref:System.Activator.CreateInstanceFrom%2A?displayProperty=nameWithType> 的重载。|
|<xref:System.Activator?displayProperty=nameWithType>|<xref:System.Activator.CreateInstanceFrom%28System.String%2CSystem.String%2CSystem.Boolean%2CSystem.Reflection.BindingFlags%2CSystem.Reflection.Binder%2CSystem.Object%5B%5D%2CSystem.Globalization.CultureInfo%2CSystem.Object%5B%5D%2CSystem.Security.Policy.Evidence%29>|对沙盒使用证据的方法已过时，并将从 .NET Framework 的未来版本中移除。 请使用不采用 <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 参数的 <xref:System.Activator.CreateInstanceFrom%2A?displayProperty=nameWithType> 的重载。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.AppendPrivatePath%2A>|<xref:System.AppDomain.AppendPrivatePath%2A> 已弃用。 请改为调查 <xref:System.AppDomainSetup.PrivateBinPath%2A?displayProperty=nameWithType> 的用法。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.ClearPrivatePath%2A>|<xref:System.AppDomain.ClearPrivatePath%2A> 已弃用。 请改为调查 <xref:System.AppDomainSetup.PrivateBinPath%2A?displayProperty=nameWithType> 的用法。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.ClearShadowCopyPath%2A>|<xref:System.AppDomain.ClearShadowCopyPath%2A> 已弃用。 请改为调查 <xref:System.AppDomainSetup.ShadowCopyDirectories%2A?displayProperty=nameWithType> 的用法。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.CreateInstance%28System.String%2CSystem.String%2CSystem.Boolean%2CSystem.Reflection.BindingFlags%2CSystem.Reflection.Binder%2CSystem.Object%5B%5D%2CSystem.Globalization.CultureInfo%2CSystem.Object%5B%5D%2CSystem.Security.Policy.Evidence%29>|对沙盒使用证据的方法已过时，并将从 .NET Framework 的未来版本中移除。 请使用不采用 <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 参数的 <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> 的重载。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.CreateInstanceAndUnwrap%28System.String%2CSystem.String%2CSystem.Boolean%2CSystem.Reflection.BindingFlags%2CSystem.Reflection.Binder%2CSystem.Object%5B%5D%2CSystem.Globalization.CultureInfo%2CSystem.Object%5B%5D%2CSystem.Security.Policy.Evidence%29>|对沙盒使用证据的方法已过时，并将从 .NET Framework 的未来版本中移除。 请使用不采用 <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 参数的 <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> 的重载。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.CreateInstanceFrom%28System.String%2CSystem.String%2CSystem.Boolean%2CSystem.Reflection.BindingFlags%2CSystem.Reflection.Binder%2CSystem.Object%5B%5D%2CSystem.Globalization.CultureInfo%2CSystem.Object%5B%5D%2CSystem.Security.Policy.Evidence%29>|对沙盒使用证据的方法已过时，并将从 .NET Framework 的未来版本中移除。 请使用不采用 <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 参数的 <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType> 的重载。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.CreateInstanceFromAndUnwrap%28System.String%2CSystem.String%2CSystem.Boolean%2CSystem.Reflection.BindingFlags%2CSystem.Reflection.Binder%2CSystem.Object%5B%5D%2CSystem.Globalization.CultureInfo%2CSystem.Object%5B%5D%2CSystem.Security.Policy.Evidence%29>|对沙盒使用证据的方法已过时，并将从 .NET Framework 的未来版本中移除。 请使用不采用 <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 参数的 <xref:System.AppDomain.CreateInstanceFromAndUnwrap%2A?displayProperty=nameWithType> 的重载。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.DefineDynamicAssembly%28System.Reflection.AssemblyName%2CSystem.Reflection.Emit.AssemblyBuilderAccess%2CSystem.Security.Policy.Evidence%29>|程序集级别声明性安全已过时，默认情况下不再由 CLR 强制实施。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.DefineDynamicAssembly%28System.Reflection.AssemblyName%2CSystem.Reflection.Emit.AssemblyBuilderAccess%2CSystem.Security.Policy.Evidence%2CSystem.Security.PermissionSet%2CSystem.Security.PermissionSet%2CSystem.Security.PermissionSet%29>|程序集级别声明性安全已过时，默认情况下不再由 CLR 强制实施。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.DefineDynamicAssembly%28System.Reflection.AssemblyName%2CSystem.Reflection.Emit.AssemblyBuilderAccess%2CSystem.Security.PermissionSet%2CSystem.Security.PermissionSet%2CSystem.Security.PermissionSet%29>|程序集级别声明性安全已过时，默认情况下不再由 CLR 强制实施。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.DefineDynamicAssembly%28System.Reflection.AssemblyName%2CSystem.Reflection.Emit.AssemblyBuilderAccess%2CSystem.String%2CSystem.Security.Policy.Evidence%29>|对沙盒使用证据的方法已过时，并将从 .NET Framework 的未来版本中移除。 请使用不采用 <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 参数的 <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType> 的重载。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.DefineDynamicAssembly%28System.Reflection.AssemblyName%2CSystem.Reflection.Emit.AssemblyBuilderAccess%2CSystem.String%2CSystem.Security.Policy.Evidence%2CSystem.Security.PermissionSet%2CSystem.Security.PermissionSet%2CSystem.Security.PermissionSet%29>|程序集级别声明性安全已过时，默认情况下不再由 CLR 强制实施。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.DefineDynamicAssembly%28System.Reflection.AssemblyName%2CSystem.Reflection.Emit.AssemblyBuilderAccess%2CSystem.String%2CSystem.Security.Policy.Evidence%2CSystem.Security.PermissionSet%2CSystem.Security.PermissionSet%2CSystem.Security.PermissionSet%2CSystem.Boolean%29>|程序集级别声明性安全已过时，默认情况下不再由 CLR 强制实施。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.DefineDynamicAssembly%28System.Reflection.AssemblyName%2CSystem.Reflection.Emit.AssemblyBuilderAccess%2CSystem.String%2CSystem.Security.Policy.Evidence%2CSystem.Security.PermissionSet%2CSystem.Security.PermissionSet%2CSystem.Security.PermissionSet%2CSystem.Boolean%2CSystem.Collections.Generic.IEnumerable%7BSystem.Reflection.Emit.CustomAttributeBuilder%7D%29>|程序集级别声明性安全已过时，默认情况下不再由 CLR 强制实施。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.DefineDynamicAssembly%28System.Reflection.AssemblyName%2CSystem.Reflection.Emit.AssemblyBuilderAccess%2CSystem.String%2CSystem.Security.PermissionSet%2CSystem.Security.PermissionSet%2CSystem.Security.PermissionSet%29>|程序集级别声明性安全已过时，默认情况下不再由 CLR 强制实施。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.Security.Policy.Evidence%29>|对沙盒使用证据的方法已过时，并将从 .NET Framework 的未来版本中移除。 请使用不采用 <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 参数的 <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType> 的重载。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.String%5B%5D%29>|对沙盒使用证据的方法已过时，并将从 .NET Framework 的未来版本中移除。 请使用不采用 <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 参数的 <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType> 的重载。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29>|对沙盒使用证据的方法已过时，并将从 .NET Framework 的未来版本中移除。 请使用不采用 <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 参数的 <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType> 的重载。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.ExecuteAssemblyByName%28System.Reflection.AssemblyName%2CSystem.Security.Policy.Evidence%2CSystem.String%5B%5D%29>|对沙盒使用证据的方法已过时，并将从 .NET Framework 的未来版本中移除。 请使用不采用 <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 参数的 <xref:System.AppDomain.ExecuteAssemblyByName%2A?displayProperty=nameWithType> 的重载。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.ExecuteAssemblyByName%28System.String%2CSystem.Security.Policy.Evidence%29>|对沙盒使用证据的方法已过时，并将从 .NET Framework 的未来版本中移除。 请使用不采用 <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 参数的 <xref:System.AppDomain.ExecuteAssemblyByName%2A?displayProperty=nameWithType> 的重载。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.ExecuteAssemblyByName%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.String%5B%5D%29>|对沙盒使用证据的方法已过时，并将从 .NET Framework 的未来版本中移除。 请使用不采用 <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 参数的 <xref:System.AppDomain.ExecuteAssemblyByName%2A?displayProperty=nameWithType> 的重载。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.GetCurrentThreadId%2A>|<xref:System.AppDomain.GetCurrentThreadId%2A> 已弃用，因为当托管线程在纤程（又称轻量级线程）上运行时，它无法提供稳定的 ID。 若要获得托管线程的稳定标识符，请使用 <xref:System.Threading.Thread.ManagedThreadId%2A?displayProperty=nameWithType> 属性。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.Load%28System.Reflection.AssemblyName%2CSystem.Security.Policy.Evidence%29>|对沙盒使用证据的方法已过时，并将从 .NET Framework 的未来版本中移除。 请使用不采用 <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 参数的 <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> 的重载。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.Load%28System.Byte%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Security.Policy.Evidence%29>|对沙盒使用证据的方法已过时，并将从 .NET Framework 的未来版本中移除。 请使用不采用 <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 参数的 <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> 的重载。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.Load%28System.String%2CSystem.Security.Policy.Evidence%29>|对沙盒使用证据的方法已过时，并将从 .NET Framework 的未来版本中移除。 请使用不采用 <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 参数的 <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> 的重载。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.SetAppDomainPolicy%2A>|<xref:System.AppDomain> 策略级别已过时，并将从 .NET Framework 的未来版本中移除。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.SetCachePath%2A>|<xref:System.AppDomain.SetCachePath%2A> 已弃用。 请改为调查 <xref:System.AppDomainSetup.CachePath%2A?displayProperty=nameWithType> 的用法。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.SetDynamicBase%2A>|<xref:System.AppDomain.SetDynamicBase%2A> 已弃用。 请改为调查 <xref:System.AppDomainSetup.DynamicBase%2A?displayProperty=nameWithType> 的用法。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.SetShadowCopyFiles%2A>|<xref:System.AppDomain.SetShadowCopyFiles%2A> 已弃用。 请改为调查 <xref:System.AppDomainSetup.ShadowCopyFiles%2A?displayProperty=nameWithType> 的用法。|
|<xref:System.AppDomain?displayProperty=nameWithType>|<xref:System.AppDomain.SetShadowCopyPath%2A>|<xref:System.AppDomain.SetShadowCopyPath%2A> 已弃用。 请改为调查 <xref:System.AppDomainSetup.ShadowCopyDirectories%2A?displayProperty=nameWithType> 的用法。|
|<xref:System.Enum?displayProperty=nameWithType>|<xref:System.Enum.ToString(System.IFormatProvider)>|不使用 `provider` 参数。 请使用 <xref:System.Enum.ToString?displayProperty=nameWithType>。|
|<xref:System.Enum?displayProperty=nameWithType>|<xref:System.Enum.ToString(System.String,System.IFormatProvider)>|不使用 `provider` 参数。 请使用 <xref:System.Enum.ToString(System.String)?displayProperty=nameWithType>。|
|<xref:System.LoaderOptimization?displayProperty=nameWithType>|<xref:System.LoaderOptimization.DisallowBindings>|此方法已被否决。 请改用 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>。|
|<xref:System.LoaderOptimization?displayProperty=nameWithType>|<xref:System.LoaderOptimization.DomainMask>|此方法已被否决。 请改用 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>。|
|<xref:System.Collections.Hashtable?displayProperty=nameWithType>|<xref:System.Collections.Hashtable.%23ctor%28System.Collections.IDictionary%2CSystem.Collections.IHashCodeProvider%2CSystem.Collections.IComparer%29>|请改用 <xref:System.Collections.Hashtable.%23ctor%28System.Collections.IDictionary%2CSystem.Collections.IEqualityComparer%29?displayProperty=nameWithType>。|
|<xref:System.Collections.Hashtable?displayProperty=nameWithType>|<xref:System.Collections.Hashtable.%23ctor%28System.Collections.IHashCodeProvider%2CSystem.Collections.IComparer%29>|请改用 <xref:System.Collections.Hashtable.%23ctor%28System.Collections.IEqualityComparer%29?displayProperty=nameWithType>。|
|<xref:System.Collections.Hashtable?displayProperty=nameWithType>|<xref:System.Collections.Hashtable.%23ctor%28System.Int32%2CSystem.Collections.IHashCodeProvider%2CSystem.Collections.IComparer%29>|请改用 <xref:System.Collections.Hashtable.%23ctor%28System.Int32%2CSystem.Collections.IEqualityComparer%29?displayProperty=nameWithType>。|
|<xref:System.Collections.Hashtable?displayProperty=nameWithType>|<xref:System.Collections.Hashtable.%23ctor%28System.Int32%2CSystem.Single%2CSystem.Collections.IHashCodeProvider%2CSystem.Collections.IComparer%29>|请改用 <xref:System.Collections.Hashtable.%23ctor%28System.Int32%2CSystem.Single%2CSystem.Collections.IEqualityComparer%29?displayProperty=nameWithType>。|
|<xref:System.Collections.Hashtable?displayProperty=nameWithType>|<xref:System.Collections.Hashtable.comparer%2A?displayProperty=nameWithType>|使用 <xref:System.Collections.Hashtable.EqualityComparer%2A?displayProperty=nameWithType> 属性。|
|<xref:System.Collections.Hashtable?displayProperty=nameWithType>|<xref:System.Collections.Hashtable.hcp%2A?displayProperty=nameWithType>|使用 `KeyComparer` 属性。|
|<xref:System.Collections.Hashtable?displayProperty=nameWithType>|<xref:System.Collections.Hashtable.%23ctor%28System.Collections.IDictionary%2CSystem.Single%2CSystem.Collections.IHashCodeProvider%2CSystem.Collections.IComparer%29>|请改用 <xref:System.Collections.Hashtable.%23ctor%28System.Collections.IDictionary%2CSystem.Single%2CSystem.Collections.IEqualityComparer%29?displayProperty=nameWithType>。|
|<xref:System.Configuration.Assemblies.AssemblyHash?displayProperty=nameWithType>|<xref:System.Configuration.Assemblies.AssemblyHash.Algorithm%2A>|<xref:System.Configuration.Assemblies.AssemblyHash?displayProperty=nameWithType> 类已弃用。|
|<xref:System.Configuration.Assemblies.AssemblyHash?displayProperty=nameWithType>|<xref:System.Configuration.Assemblies.AssemblyHash.%23ctor%28System.Configuration.Assemblies.AssemblyHashAlgorithm%2CSystem.Byte%5B%5D%29>|<xref:System.Configuration.Assemblies.AssemblyHash?displayProperty=nameWithType> 类已弃用。|
|<xref:System.Configuration.Assemblies.AssemblyHash?displayProperty=nameWithType>|<xref:System.Configuration.Assemblies.AssemblyHash.%23ctor%28System.Byte%5B%5D%29>|<xref:System.Configuration.Assemblies.AssemblyHash?displayProperty=nameWithType> 类已弃用。|
|<xref:System.Configuration.Assemblies.AssemblyHash?displayProperty=nameWithType>|<xref:System.Configuration.Assemblies.AssemblyHash.Clone%2A>|<xref:System.Configuration.Assemblies.AssemblyHash?displayProperty=nameWithType> 类已弃用。|
|<xref:System.Configuration.Assemblies.AssemblyHash?displayProperty=nameWithType>|<xref:System.Configuration.Assemblies.AssemblyHash.Empty>|<xref:System.Configuration.Assemblies.AssemblyHash?displayProperty=nameWithType> 类已弃用。|
|<xref:System.Configuration.Assemblies.AssemblyHash?displayProperty=nameWithType>|<xref:System.Configuration.Assemblies.AssemblyHash.GetValue%2A>|<xref:System.Configuration.Assemblies.AssemblyHash?displayProperty=nameWithType> 类已弃用。|
|<xref:System.Configuration.Assemblies.AssemblyHash?displayProperty=nameWithType>|<xref:System.Configuration.Assemblies.AssemblyHash.SetValue%2A>|<xref:System.Configuration.Assemblies.AssemblyHash?displayProperty=nameWithType> 类已弃用。|
|<xref:System.Diagnostics.Debugger?displayProperty=nameWithType>|<xref:System.Diagnostics.Debugger.%23ctor%2A>|请勿创建 <xref:System.Diagnostics.Debugger> 类的实例。 请改为在此类型上直接调用静态方法。|
|<xref:System.Diagnostics.StackTrace?displayProperty=nameWithType>|<xref:System.Diagnostics.StackTrace.%23ctor%28System.Threading.Thread%2CSystem.Boolean%29>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 此构造函数已弃用。 使用不需要 <xref:System.Threading.Thread> 参数的构造函数。|
|<xref:System.Diagnostics.SymbolStore.ISymbolBinder?displayProperty=nameWithType>|<xref:System.Diagnostics.SymbolStore.ISymbolBinder.GetReader%2A>|建议的替代项是 <xref:System.Diagnostics.SymbolStore.ISymbolBinder1.GetReader%2A?displayProperty=nameWithType>，其将导入程序接口指针视为 <xref:System.IntPtr> 而不是 <xref:System.Int32>，因此可以同时在 32 位和 64 位体系结构上工作。|
|<xref:System.Globalization.CultureTypes?displayProperty=nameWithType>|<xref:System.Globalization.CultureTypes.FrameworkCultures>|此值已弃用。 使用 <xref:System.Globalization.CultureTypes?displayProperty=nameWithType> 中的其他值。|
|<xref:System.Globalization.CultureTypes?displayProperty=nameWithType>|<xref:System.Globalization.CultureTypes.WindowsOnlyCultures>|此值已弃用。 使用 <xref:System.Globalization.CultureTypes?displayProperty=nameWithType> 中的其他值。|
|<xref:System.IO.FileStream?displayProperty=nameWithType>|<xref:System.IO.FileStream.%23ctor%28System.IntPtr%2CSystem.IO.FileAccess%29>|此构造函数已弃用。 请改用 <xref:System.IO.FileStream.%23ctor%28Microsoft.Win32.SafeHandles.SafeFileHandle%2CSystem.IO.FileAccess%29?displayProperty=nameWithType>。|
|<xref:System.IO.FileStream?displayProperty=nameWithType>|<xref:System.IO.FileStream.%23ctor%28System.IntPtr%2CSystem.IO.FileAccess%2CSystem.Boolean%29>|此构造函数已弃用。 请改用 <xref:System.IO.FileStream.%23ctor%28Microsoft.Win32.SafeHandles.SafeFileHandle%2CSystem.IO.FileAccess%29?displayProperty=nameWithType>，如果需要，也可以选择通过 `ownsHandle`= `false` 设置新 <xref:Microsoft.Win32.SafeHandles.SafeFileHandle?displayProperty=nameWithType>。|
|<xref:System.IO.FileStream?displayProperty=nameWithType>|<xref:System.IO.FileStream.%23ctor%28System.IntPtr%2CSystem.IO.FileAccess%2CSystem.Boolean%2CSystem.Int32%29>|此构造函数已弃用。 请改用 <xref:System.IO.FileStream.%23ctor%28Microsoft.Win32.SafeHandles.SafeFileHandle%2CSystem.IO.FileAccess%2CSystem.Int32%29?displayProperty=nameWithType>，如果需要，也可以选择通过 `ownsHandle`= `false` 设置新 <xref:Microsoft.Win32.SafeHandles.SafeFileHandle?displayProperty=nameWithType>。|
|<xref:System.IO.FileStream?displayProperty=nameWithType>|<xref:System.IO.FileStream.%23ctor%28System.IntPtr%2CSystem.IO.FileAccess%2CSystem.Boolean%2CSystem.Int32%2CSystem.Boolean%29>|此构造函数已弃用。 请改用 <xref:System.IO.FileStream.%23ctor%28Microsoft.Win32.SafeHandles.SafeFileHandle%2CSystem.IO.FileAccess%2CSystem.Int32%2CSystem.Boolean%29?displayProperty=nameWithType>，如果需要，也可以选择通过 `ownsHandle`= `false` 设置新 <xref:Microsoft.Win32.SafeHandles.SafeFileHandle?displayProperty=nameWithType>。|
|<xref:System.IO.FileStream?displayProperty=nameWithType>|<xref:System.IO.FileStream.Handle%2A>|此属性已弃用。 改用 <xref:System.IO.FileStream.SafeFileHandle%2A?displayProperty=nameWithType> 属性。|
|<xref:System.IO.Path?displayProperty=nameWithType>|<xref:System.IO.Path.InvalidPathChars>|请改用 <xref:System.IO.Path.GetInvalidPathChars%2A?displayProperty=nameWithType> 或 <xref:System.IO.Path.GetInvalidFileNameChars%2A?displayProperty=nameWithType>。|
|<xref:System.IO.Stream?displayProperty=nameWithType>|<xref:System.IO.Stream.CreateWaitHandle%2A>|最终将移除 <xref:System.IO.Stream.CreateWaitHandle%2A>。 请改用 `new ManualResetEvent(false)`。|
|<xref:System.IO.Stream?displayProperty=nameWithType>|<xref:System.IO.Stream.ObjectInvariant%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 请勿调用或重写此方法。|
|<xref:System.IO.IsolatedStorage.IsolatedStorage?displayProperty=nameWithType>|<xref:System.IO.IsolatedStorage.IsolatedStorage.CurrentSize%2A>|<xref:System.IO.IsolatedStorage.IsolatedStorage.CurrentSize%2A> 已弃用，因为它不符合 CLS。 若要获得当前大小，请使用 <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A?displayProperty=nameWithType>。|
|<xref:System.IO.IsolatedStorage.IsolatedStorage?displayProperty=nameWithType>|<xref:System.IO.IsolatedStorage.IsolatedStorage.MaximumSize%2A>|<xref:System.IO.IsolatedStorage.IsolatedStorage.MaximumSize%2A> 已弃用，因为它不符合 CLS。 若要获得最大大小，请使用 <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A?displayProperty=nameWithType>。|
|<xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>|<xref:System.IO.IsolatedStorage.IsolatedStorageFile.CurrentSize%2A>|<xref:System.IO.IsolatedStorage.IsolatedStorageFile.CurrentSize%2A> 已弃用，因为它不符合 CLS。 若要获得当前大小，请使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.UsedSize%2A>。|
|<xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>|<xref:System.IO.IsolatedStorage.IsolatedStorageFile.MaximumSize%2A>|<xref:System.IO.IsolatedStorage.IsolatedStorageFile.MaximumSize%2A> 已弃用，因为它不符合 CLS。 若要获得最大大小，请使用 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Quota%2A?displayProperty=nameWithType>。|
|<xref:System.IO.IsolatedStorage.IsolatedStorageFileStream?displayProperty=nameWithType>|<xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.Handle%2A>|此属性已弃用。 改用 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.SafeFileHandle%2A?displayProperty=nameWithType> 属性。|
|<xref:System.Reflection.Assembly?displayProperty=nameWithType>|<xref:System.Reflection.Assembly.Load%28System.Reflection.AssemblyName%2CSystem.Security.Policy.Evidence%29>|此方法已过时，并将从 .NET Framework 的未来版本中移除。 请使用不采用 <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 参数的 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 的重载。|
|<xref:System.Reflection.Assembly?displayProperty=nameWithType>|<xref:System.Reflection.Assembly.Load%28System.Byte%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Security.Policy.Evidence%29>|此方法已过时，并将从 .NET Framework 的未来版本中移除。 请使用不采用 <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 参数的 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 的重载。|
|<xref:System.Reflection.Assembly?displayProperty=nameWithType>|<xref:System.Reflection.Assembly.Load%28System.String%2CSystem.Security.Policy.Evidence%29>|此方法已过时，并将从 .NET Framework 的未来版本中移除。 请使用不采用 <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 参数的 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 的重载。|
|<xref:System.Reflection.Assembly?displayProperty=nameWithType>|<xref:System.Reflection.Assembly.LoadFile%28System.String%2CSystem.Security.Policy.Evidence%29>|此方法已过时，并将从 .NET Framework 的未来版本中移除。 请使用不采用 <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 参数的 <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> 的重载。|
|<xref:System.Reflection.Assembly?displayProperty=nameWithType>|<xref:System.Reflection.Assembly.LoadFrom%28System.String%2CSystem.Security.Policy.Evidence%29>|此方法已过时，并将从 .NET Framework 的未来版本中移除。 请使用不采用 <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 参数的 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> 的重载。|
|<xref:System.Reflection.Assembly?displayProperty=nameWithType>|<xref:System.Reflection.Assembly.LoadFrom%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29>|此方法已过时，并将从 .NET Framework 的未来版本中移除。 请使用不采用 <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 参数的 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> 的重载。|
|<xref:System.Reflection.Assembly?displayProperty=nameWithType>|<xref:System.Reflection.Assembly.LoadWithPartialName%28System.String%29>|此方法已被否决。 请改用 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>。|
|<xref:System.Reflection.Assembly?displayProperty=nameWithType>|<xref:System.Reflection.Assembly.LoadWithPartialName%28System.String%2CSystem.Security.Policy.Evidence%29>|此方法已被否决。 请改用 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>。|
|<xref:System.Reflection.AssemblyFlagsAttribute?displayProperty=nameWithType>|<xref:System.Reflection.AssemblyFlagsAttribute.%23ctor%28System.Int32%29>|此构造函数已弃用。 请改用 <xref:System.Reflection.AssemblyFlagsAttribute.%23ctor%28System.Reflection.AssemblyNameFlags%29?displayProperty=nameWithType>。|
|<xref:System.Reflection.AssemblyFlagsAttribute?displayProperty=nameWithType>|<xref:System.Reflection.AssemblyFlagsAttribute.%23ctor%28System.UInt32%29>|此构造函数已弃用。 请改用 <xref:System.Reflection.AssemblyFlagsAttribute.%23ctor%28System.Reflection.AssemblyNameFlags%29?displayProperty=nameWithType>。|
|<xref:System.Reflection.AssemblyFlagsAttribute?displayProperty=nameWithType>|<xref:System.Reflection.AssemblyFlagsAttribute.Flags%2A>|此属性已弃用。 请改用 <xref:System.Reflection.AssemblyFlagsAttribute.AssemblyFlags%2A?displayProperty=nameWithType>。|
|<xref:System.Reflection.Emit.ConstructorBuilder?displayProperty=nameWithType>|<xref:System.Reflection.Emit.ConstructorBuilder.ReturnType%2A>|此属性已弃用。|
|<xref:System.Reflection.Emit.FieldBuilder?displayProperty=nameWithType>|<xref:System.Reflection.Emit.FieldBuilder.SetMarshal%2A>|有一个可用的备用 API：发出 <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> 自定义特性。|
|<xref:System.Reflection.Emit.FlowControl?displayProperty=nameWithType>|<xref:System.Reflection.Emit.FlowControl.Phi>|此 API 已弃用。|
|<xref:System.Reflection.Emit.MethodBuilder?displayProperty=nameWithType>|<xref:System.Reflection.Emit.MethodBuilder.SetMarshal%2A>|有一个可用的备用 API：发出 <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> 自定义特性。|
|<xref:System.Reflection.Emit.OpCodeType?displayProperty=nameWithType>|<xref:System.Reflection.Emit.OpCodeType.Annotation>|此 API 已弃用。|
|<xref:System.Reflection.Emit.OperandType?displayProperty=nameWithType>|<xref:System.Reflection.Emit.OperandType.InlinePhi>|此 API 已弃用。|
|<xref:System.Reflection.Emit.ParameterBuilder?displayProperty=nameWithType>|<xref:System.Reflection.Emit.ParameterBuilder.SetMarshal%2A>|有一个可用的备用 API：发出 <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> 自定义特性。|
|<xref:System.Resources.ResourceManager?displayProperty=nameWithType>|<xref:System.Resources.ResourceManager.ResourceSets>|请改为调用 <xref:System.Resources.ResourceManager.InternalGetResourceSet%28System.Globalization.CultureInfo%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.GetManagedThunkForUnmanagedMethodPtr%2A>|<xref:System.Runtime.InteropServices.Marshal.GetManagedThunkForUnmanagedMethodPtr%2A> 方法已弃用，并将从未来版本中移除。|
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.GetThreadFromFiberCookie%2A>|<xref:System.Runtime.InteropServices.Marshal.GetThreadFromFiberCookie%2A> 方法已弃用。 若要执行此操作，请使用托管 API。|
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.GetTypeInfoName%28System.Runtime.InteropServices.UCOMITypeInfo%29>|请改用 <xref:System.Runtime.InteropServices.Marshal.GetTypeInfoName%28System.Runtime.InteropServices.ComTypes.ITypeInfo%29?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.GetTypeLibGuid%28System.Runtime.InteropServices.UCOMITypeLib%29>|请改用 <xref:System.Runtime.InteropServices.Marshal.GetTypeLibGuid%28System.Runtime.InteropServices.ComTypes.ITypeLib%29?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.GetTypeLibLcid%28System.Runtime.InteropServices.UCOMITypeLib%29>|请改用 <xref:System.Runtime.InteropServices.Marshal.GetTypeLibLcid%28System.Runtime.InteropServices.ComTypes.ITypeLib%29?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.GetTypeLibName%28System.Runtime.InteropServices.UCOMITypeLib%29>|请改用 <xref:System.Runtime.InteropServices.Marshal.GetTypeLibName%28System.Runtime.InteropServices.ComTypes.ITypeLib%29?displayProperty=nameWithType>。|
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.GetUnmanagedThunkForManagedMethodPtr%2A>|<xref:System.Runtime.InteropServices.Marshal.GetUnmanagedThunkForManagedMethodPtr%2A> 方法已弃用，并将从未来版本中移除。|
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReleaseThreadCache%2A>|此 API 未执行任何操作，并将从 CLR 的未来版本中删除。|
|<xref:System.Runtime.InteropServices.RuntimeEnvironment?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.RuntimeEnvironment.%23ctor%2A>|使用此成员会生成编译器错误。<br /><br /> 请勿创建 <xref:System.Runtime.InteropServices.RuntimeEnvironment?displayProperty=nameWithType> 类的实例。 请改为在此类型上直接调用静态方法。|
|<xref:System.Runtime.Remoting.Channels.ChannelServices?displayProperty=nameWithType>|<xref:System.Runtime.Remoting.Channels.ChannelServices.RegisterChannel%2A>|请改用 <xref:System.Runtime.Remoting.Channels.ChannelServices.RegisterChannel%28System.Runtime.Remoting.Channels.IChannel%2CSystem.Boolean%29?displayProperty=nameWithType>。|
|<xref:System.Runtime.Remoting.Lifetime.LifetimeServices?displayProperty=nameWithType>|<xref:System.Runtime.Remoting.Lifetime.LifetimeServices.%23ctor%2A>|使用此成员会生成编译器错误。<br /><br /> 请勿创建 <xref:System.Runtime.Remoting.Lifetime.LifetimeServices> 类的实例。 请改为在此类型上直接调用静态方法。|
|<xref:System.Runtime.Remoting.RemotingConfiguration?displayProperty=nameWithType>|<xref:System.Runtime.Remoting.RemotingConfiguration.Configure%28System.String%29>|请改用 <xref:System.Runtime.Remoting.RemotingConfiguration.Configure%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType>。|
|<xref:System.Runtime.Remoting.RemotingServices?displayProperty=nameWithType>|<xref:System.Runtime.Remoting.RemotingServices.LogRemotingStage%2A>|建议不要使用此方法。 <xref:System.Runtime.Remoting.RemotingServices.LogRemotingStage%2A> 仅供内部诊断使用。|
|<xref:System.Security.CodeAccessPermission?displayProperty=nameWithType>|<xref:System.Security.CodeAccessPermission.Deny%2A>|<xref:System.Security.CodeAccessPermission.Deny%2A> 已过时，并将从 .NET Framework 的未来版本中移除。|
|<xref:System.Security.CodeAccessPermission?displayProperty=nameWithType>|<xref:System.Security.CodeAccessPermission.RevertDeny%2A>|<xref:System.Security.CodeAccessPermission.Deny%2A> 已过时，并将从 .NET Framework 的未来版本中移除。|
|<xref:System.Security.HostSecurityManager?displayProperty=nameWithType>|<xref:System.Security.HostSecurityManager.DomainPolicy%2A>|AppDomain 策略级别已过时，并将从 .NET Framework 的未来版本中移除。|
|<xref:System.Security.HostSecurityManagerOptions?displayProperty=nameWithType>|<xref:System.Security.HostSecurityManagerOptions.HostPolicyLevel>|AppDomain 策略级别已过时，并将从 .NET Framework 的未来版本中移除。|
|<xref:System.Security.PermissionSet?displayProperty=nameWithType>|<xref:System.Security.PermissionSet.ConvertPermissionSet%2A>|此方法已过时，不应再使用。|
|<xref:System.Security.PermissionSet?displayProperty=nameWithType>|<xref:System.Security.PermissionSet.Deny%2A>|<xref:System.Security.PermissionSet.Deny%2A> 已过时，并将从 .NET Framework 的未来版本中移除。|
|<xref:System.Security.SecurityCriticalAttribute?displayProperty=nameWithType>|<xref:System.Security.SecurityCriticalAttribute.Scope%2A>|<xref:System.Security.SecurityCriticalScope?displayProperty=nameWithType> 仅用于实现 .NET 2.0 透明度兼容性。|
|<xref:System.Security.SecurityManager?displayProperty=nameWithType>|<xref:System.Security.SecurityManager.CheckExecutionRights%2A>|由于执行权限检查再也无法关闭，因此 <xref:System.Security.SecurityManager.CheckExecutionRights%2A> 属性将不再起作用。|
|<xref:System.Security.SecurityManager?displayProperty=nameWithType>|<xref:System.Security.SecurityManager.IsGranted%2A>|<xref:System.Security.SecurityManager.IsGranted%2A> 已过时，并将从 .NET Framework 的未来版本中移除。 请改用 <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType> 属性或 <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType> 属性。|
|<xref:System.Security.SecurityManager?displayProperty=nameWithType>|<xref:System.Security.SecurityManager.LoadPolicyLevelFromFile%2A>|此方法已过时，并将从 .NET Framework 的未来版本中移除。|
|<xref:System.Security.SecurityManager?displayProperty=nameWithType>|<xref:System.Security.SecurityManager.LoadPolicyLevelFromString%2A>|此方法已过时，并将从 .NET Framework 的未来版本中移除。|
|<xref:System.Security.SecurityManager?displayProperty=nameWithType>|<xref:System.Security.SecurityManager.PolicyHierarchy%2A>|此方法已过时，并将从 .NET Framework 的未来版本中移除。|
|<xref:System.Security.SecurityManager?displayProperty=nameWithType>|<xref:System.Security.SecurityManager.ResolvePolicy%28System.Security.Policy.Evidence%29>|此方法已过时，并将从 .NET Framework 的未来版本中移除。|
|<xref:System.Security.SecurityManager?displayProperty=nameWithType>|<xref:System.Security.SecurityManager.ResolvePolicy%28System.Security.Policy.Evidence%2CSystem.Security.PermissionSet%2CSystem.Security.PermissionSet%2CSystem.Security.PermissionSet%2CSystem.Security.PermissionSet%40%29>|此方法已过时，并将从 .NET Framework 的未来版本中移除。|
|<xref:System.Security.SecurityManager?displayProperty=nameWithType>|<xref:System.Security.SecurityManager.ResolvePolicy%28System.Security.Policy.Evidence%5B%5D%29>|此方法已过时，并将从 .NET Framework 的未来版本中移除。|
|<xref:System.Security.SecurityManager?displayProperty=nameWithType>|<xref:System.Security.SecurityManager.ResolvePolicyGroups%2A>|此方法已过时，并将从 .NET Framework 的未来版本中移除。|
|<xref:System.Security.SecurityManager?displayProperty=nameWithType>|<xref:System.Security.SecurityManager.ResolveSystemPolicy%2A>|此方法已过时，并将从 .NET Framework 的未来版本中移除。|
|<xref:System.Security.SecurityManager?displayProperty=nameWithType>|<xref:System.Security.SecurityManager.SavePolicy%2A>|此方法已过时，并将从 .NET Framework 的未来版本中移除。|
|<xref:System.Security.SecurityManager?displayProperty=nameWithType>|<xref:System.Security.SecurityManager.SavePolicyLevel%2A>|此方法已过时，并将从 .NET Framework 的未来版本中移除。|
|<xref:System.Security.SecurityManager?displayProperty=nameWithType>|<xref:System.Security.SecurityManager.SecurityEnabled%2A>|由于安全性再也无法关闭，因此 <xref:System.Security.SecurityManager.SecurityEnabled%2A> 属性将不再起作用。|
|<xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=nameWithType>|<xref:System.Security.Cryptography.PasswordDeriveBytes.GetBytes%2A>|<xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> 替换 <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=nameWithType> 从密码派生密钥材料，并且在新应用程序中为首选。|
|<xref:System.Security.Cryptography.X509Certificates.X509Certificate?displayProperty=nameWithType>|<xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetIssuerName%2A>|此方法已被否决。 改用 <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Issuer%2A?displayProperty=nameWithType> 属性。|
|<xref:System.Security.Cryptography.X509Certificates.X509Certificate?displayProperty=nameWithType>|<xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetName%2A>|此方法已被否决。 改用 <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Subject%2A?displayProperty=nameWithType> 属性。|
|<xref:System.Security.Permissions.FileIOPermissionAttribute?displayProperty=nameWithType>|<xref:System.Security.Permissions.FileIOPermissionAttribute.All%2A>|改用 <xref:System.Security.Permissions.FileIOPermissionAttribute.ViewAndModify%2A?displayProperty=nameWithType> 属性。|
|<xref:System.Security.Permissions.ReflectionPermissionAttribute?displayProperty=nameWithType>|<xref:System.Security.Permissions.ReflectionPermissionAttribute.ReflectionEmit%2A>|CLR 不再使用此权限。|
|<xref:System.Security.Permissions.ReflectionPermissionAttribute?displayProperty=nameWithType>|<xref:System.Security.Permissions.ReflectionPermissionAttribute.TypeInformation%2A>|此 API 已弃用。|
|<xref:System.Security.Permissions.ReflectionPermissionFlag?displayProperty=nameWithType>|<xref:System.Security.Permissions.ReflectionPermissionFlag.AllFlags>|此权限已弃用。 <xref:System.Security.Permissions.ReflectionPermissionFlag.AllFlags> 枚举成员不包括 <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess>。 使用 <xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType> 获取完全访问权限。|
|<xref:System.Security.Permissions.ReflectionPermissionFlag?displayProperty=nameWithType>|<xref:System.Security.Permissions.ReflectionPermissionFlag.ReflectionEmit>|CLR 不再使用此权限。|
|<xref:System.Security.Permissions.ReflectionPermissionFlag?displayProperty=nameWithType>|<xref:System.Security.Permissions.ReflectionPermissionFlag.TypeInformation>|此 API 已弃用。|
|<xref:System.Security.Permissions.RegistryPermissionAttribute?displayProperty=nameWithType>|<xref:System.Security.Permissions.RegistryPermissionAttribute.All%2A>|改用 <xref:System.Security.Permissions.RegistryPermissionAttribute.ViewAndModify%2A?displayProperty=nameWithType> 属性。|
|<xref:System.Security.Permissions.SecurityAction?displayProperty=nameWithType>|<xref:System.Security.Permissions.SecurityAction.Deny>|<xref:System.Security.Permissions.SecurityAction.Deny> 已过时，并将从 .NET Framework 的未来版本中移除。|
|<xref:System.Security.Permissions.SecurityAction?displayProperty=nameWithType>|<xref:System.Security.Permissions.SecurityAction.RequestMinimum>|程序集级别声明性安全已过时，默认情况下不再由 CLR 强制实施。|
|<xref:System.Security.Permissions.SecurityAction?displayProperty=nameWithType>|<xref:System.Security.Permissions.SecurityAction.RequestOptional>|程序集级别声明性安全已过时，默认情况下不再由 CLR 强制实施。|
|<xref:System.Security.Permissions.SecurityAction?displayProperty=nameWithType>|<xref:System.Security.Permissions.SecurityAction.RequestRefuse>|程序集级别声明性安全已过时，默认情况下不再由 CLR 强制实施。|
|<xref:System.Security.Policy.Evidence?displayProperty=nameWithType>|<xref:System.Security.Policy.Evidence.AddAssembly%2A>|此方法已过时。 请改用 <xref:System.Security.Policy.Evidence.AddAssemblyEvidence%2A?displayProperty=nameWithType>。|
|<xref:System.Security.Policy.Evidence?displayProperty=nameWithType>|<xref:System.Security.Policy.Evidence.AddHost%2A>|此方法已过时。 请改用 <xref:System.Security.Policy.Evidence.AddHostEvidence%2A?displayProperty=nameWithType>。|
|<xref:System.Security.Policy.Evidence?displayProperty=nameWithType>|<xref:System.Security.Policy.Evidence.CopyTo%2A>|证据不应被视为 <xref:System.Collections.ICollection?displayProperty=nameWithType>。 请使用 <xref:System.Security.Policy.Evidence.GetHostEnumerator%2A?displayProperty=nameWithType> 和 <xref:System.Security.Policy.Evidence.GetAssemblyEnumerator%2A?displayProperty=nameWithType> 方法，而不是使用 <xref:System.Security.Policy.Evidence.CopyTo%2A>。|
|<xref:System.Security.Policy.Evidence?displayProperty=nameWithType>|<xref:System.Security.Policy.Evidence.Count%2A>|证据不应被视为 <xref:System.Collections.ICollection?displayProperty=nameWithType>。 请使用 <xref:System.Security.Policy.Evidence.GetHostEnumerator%2A?displayProperty=nameWithType> 和 <xref:System.Security.Policy.Evidence.GetAssemblyEnumerator%2A?displayProperty=nameWithType> 循环访问证据，以收集计数。|
|<xref:System.Security.Policy.Evidence?displayProperty=nameWithType>|<xref:System.Security.Policy.Evidence.%23ctor%28System.Object%5B%5D%2CSystem.Object%5B%5D%29>|此构造函数已过时。 请改用 <xref:System.Security.Policy.Evidence.%23ctor%28System.Security.Policy.EvidenceBase%5B%5D%2CSystem.Security.Policy.EvidenceBase%5B%5D%29?displayProperty=nameWithType> 构造函数。|
|<xref:System.Security.Policy.Evidence?displayProperty=nameWithType>|<xref:System.Security.Policy.Evidence.GetEnumerator%2A>|<xref:System.Security.Policy.Evidence.GetEnumerator%2A> 已过时。 请改用 <xref:System.Security.Policy.Evidence.GetHostEnumerator%2A?displayProperty=nameWithType> 和 <xref:System.Security.Policy.Evidence.GetAssemblyEnumerator%2A?displayProperty=nameWithType>。|
|<xref:System.Security.Policy.PolicyLevel?displayProperty=nameWithType>|<xref:System.Security.Policy.PolicyLevel.AddFullTrustAssembly%28System.Security.Policy.StrongName%29>|由于所有 GAC 程序集始终都获得完全信任，则完全信任列表不再有意义。 应安装在 GAC 安全策略中所使用的任何程序集，以确保它们是受信任的。|
|<xref:System.Security.Policy.PolicyLevel?displayProperty=nameWithType>|<xref:System.Security.Policy.PolicyLevel.AddFullTrustAssembly%28System.Security.Policy.StrongNameMembershipCondition%29>|由于所有 GAC 程序集始终都获得完全信任，则完全信任列表不再有意义。 应安装在 GAC 安全策略中所使用的任何程序集，以确保它们是受信任的。|
|<xref:System.Security.Policy.PolicyLevel?displayProperty=nameWithType>|<xref:System.Security.Policy.PolicyLevel.CreateAppDomainLevel%2A>|AppDomain 策略级别已过时，并将从 .NET Framework 的未来版本中移除。|
|<xref:System.Security.Policy.PolicyLevel?displayProperty=nameWithType>|<xref:System.Security.Policy.PolicyLevel.FullTrustAssemblies%2A>|由于所有 GAC 程序集始终都获得完全信任，则完全信任列表不再有意义。 应安装在 GAC 安全策略中所使用的任何程序集，以确保它们是受信任的。|
|<xref:System.Security.Policy.PolicyLevel?displayProperty=nameWithType>|<xref:System.Security.Policy.PolicyLevel.RemoveFullTrustAssembly%28System.Security.Policy.StrongName%29>|由于所有 GAC 程序集始终都获得完全信任，则完全信任列表不再有意义。 应安装在 GAC 安全策略中所使用的任何程序集，以确保它们是受信任的。|
|<xref:System.Security.Policy.PolicyLevel?displayProperty=nameWithType>|<xref:System.Security.Policy.PolicyLevel.RemoveFullTrustAssembly%28System.Security.Policy.StrongNameMembershipCondition%29>|由于所有 GAC 程序集始终都获得完全信任，则完全信任列表不再有意义。 应安装在 GAC 安全策略中所使用的任何程序集，以确保它们是受信任的。|
|<xref:System.Threading.Overlapped?displayProperty=nameWithType>|<xref:System.Threading.Overlapped.EventHandle%2A>|此属性不兼容 64 位系统或软件。 请改用 <xref:System.Threading.Overlapped.EventHandleIntPtr%2A?displayProperty=nameWithType>。|
|<xref:System.Threading.Overlapped?displayProperty=nameWithType>|<xref:System.Threading.Overlapped.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.IAsyncResult%29>|此构造函数不兼容 64 位系统或软件。 请使用采用事件句柄的 <xref:System.IntPtr?displayProperty=nameWithType> 的 <xref:System.Threading.Overlapped.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.IntPtr%2CSystem.IAsyncResult%29?displayProperty=nameWithType> 构造函数|
|<xref:System.Threading.Overlapped?displayProperty=nameWithType>|<xref:System.Threading.Overlapped.Pack%28System.Threading.IOCompletionCallback%29>|此方法不安全。 请改用 <xref:System.Threading.Overlapped.Pack%28System.Threading.IOCompletionCallback%2CSystem.Object%29?displayProperty=nameWithType>。|
|<xref:System.Threading.Overlapped?displayProperty=nameWithType>|<xref:System.Threading.Overlapped.UnsafePack%28System.Threading.IOCompletionCallback%29>|此方法不安全。 请改用 <xref:System.Threading.Overlapped.UnsafePack%28System.Threading.IOCompletionCallback%2CSystem.Object%29?displayProperty=nameWithType>。|
|<xref:System.Threading.Thread?displayProperty=nameWithType>|<xref:System.Threading.Thread.ApartmentState%2A>|<xref:System.Threading.Thread.ApartmentState%2A> 属性已弃用。 请改用 <xref:System.Threading.Thread.GetApartmentState%2A?displayProperty=nameWithType>、<xref:System.Threading.Thread.SetApartmentState%2A?displayProperty=nameWithType> 或 <xref:System.Threading.Thread.TrySetApartmentState%2A?displayProperty=nameWithType>。|
|<xref:System.Threading.Thread?displayProperty=nameWithType>|<xref:System.Threading.Thread.GetCompressedStack%2A>|<xref:System.Threading.Thread.GetCompressedStack%2A> 不再受支持。 使用 <xref:System.Threading.CompressedStack?displayProperty=nameWithType> 类。|
|<xref:System.Threading.Thread?displayProperty=nameWithType>|<xref:System.Threading.Thread.Resume%2A>|<xref:System.Threading.Thread.Resume%2A> 已弃用。 请使用 <xref:System.Threading?displayProperty=nameWithType> 中的其他类，如 <xref:System.Threading.Monitor>、<xref:System.Threading.Mutex>、<xref:System.Threading.EventWaitHandle> 和 <xref:System.Threading.Semaphore>，以同步线程或保护资源。|
|<xref:System.Threading.Thread?displayProperty=nameWithType>|<xref:System.Threading.Thread.SetCompressedStack%2A>|<xref:System.Threading.Thread.SetCompressedStack%2A> 不再受支持。 使用 <xref:System.Threading.CompressedStack?displayProperty=nameWithType> 类。|
|<xref:System.Threading.Thread?displayProperty=nameWithType>|<xref:System.Threading.Thread.Suspend%2A>|<xref:System.Threading.Thread.Suspend%2A> 已弃用。 请使用 <xref:System.Threading?displayProperty=nameWithType> 中的其他类，如 <xref:System.Threading.Monitor>、<xref:System.Threading.Mutex>、<xref:System.Threading.EventWaitHandle> 和 <xref:System.Threading.Semaphore>，以同步线程或保护资源。|
|<xref:System.Threading.ThreadPool?displayProperty=nameWithType>|<xref:System.Threading.ThreadPool.BindHandle%28System.IntPtr%29>|<xref:System.Threading.ThreadPool.BindHandle%28System.IntPtr%29> 已弃用。 请改用 <xref:System.Threading.ThreadPool.BindHandle%28System.Runtime.InteropServices.SafeHandle%29?displayProperty=nameWithType>。|
|<xref:System.Threading.WaitHandle?displayProperty=nameWithType>|<xref:System.Threading.WaitHandle.Handle%2A>|改用 <xref:System.Threading.WaitHandle.SafeWaitHandle%2A?displayProperty=nameWithType> 属性。|

<a name="PresentationCore"></a>

### <a name="assembly-presentationcoredll"></a>程序集：PresentationCore.dll

|类型|成员|消息|
|----------|------------|-------------|
|<xref:System.Windows.UIElement?displayProperty=nameWithType>|<xref:System.Windows.UIElement.BitmapEffect%2A>|位图效果已弃用，并将不再工作。 请考虑在适用处改用 <xref:System.Windows.Media.Effects.Effect?displayProperty=nameWithType>。|
|<xref:System.Windows.UIElement?displayProperty=nameWithType>|<xref:System.Windows.UIElement.BitmapEffectInput%2A>|位图效果已弃用，并将不再工作。 请考虑在适用处改用 <xref:System.Windows.Media.Effects.Effect?displayProperty=nameWithType>。|
|<xref:System.Windows.UIElement?displayProperty=nameWithType>|<xref:System.Windows.UIElement.PersistId%2A>|<xref:System.Windows.UIElement.PersistId%2A> 是一个过时的属性，并可能会从未来版本中移除。 未定义此属性的值。|
|<xref:System.Windows.Media.ContainerVisual?displayProperty=nameWithType>|<xref:System.Windows.Media.ContainerVisual.BitmapEffect%2A>|位图效果已弃用，并将不再工作。 请考虑在适用处改用 <xref:System.Windows.Media.Effects.Effect?displayProperty=nameWithType>。|
|<xref:System.Windows.Media.ContainerVisual?displayProperty=nameWithType>|<xref:System.Windows.Media.ContainerVisual.BitmapEffectInput%2A>|位图效果已弃用，并将不再工作。 请考虑在适用处改用 <xref:System.Windows.Media.Effects.Effect?displayProperty=nameWithType>。|
|<xref:System.Windows.Media.DrawingContext?displayProperty=nameWithType>|<xref:System.Windows.Media.DrawingContext.PushEffect%2A>|位图效果已弃用，并将不再工作。 请考虑在适用处改用 <xref:System.Windows.Media.Effects.Effect?displayProperty=nameWithType>。|
|<xref:System.Windows.Media.FormattedText?displayProperty=nameWithType>|<xref:System.Windows.Media.FormattedText.%23ctor(System.String,System.Globalization.CultureInfo,System.Windows.FlowDirection,System.Windows.Media.Typeface,System.Double,System.Windows.Media.Brush)?displayProperty=nameWithType>|使用 PixelsPerDip 重写。|
|<xref:System.Windows.Media.FormattedText?displayProperty=nameWithType>|<xref:System.Windows.Media.FormattedText.%23ctor(System.String,System.Globalization.CultureInfo,System.Windows.FlowDirection,System.Windows.Media.Typeface,System.Double,System.Windows.Media.Brush,System.Windows.Media.NumberSubstitution)>|使用 PixelsPerDip 重写。|
|<xref:System.Windows.Media.FormattedText?displayProperty=nameWithType>|<xref:System.Windows.Media.FormattedText.%23ctor(System.String,System.Globalization.CultureInfo,System.Windows.FlowDirection,System.Windows.Media.Typeface,System.Double,System.Windows.Media.Brush,System.Windows.Media.NumberSubstitution,System.Windows.Media.TextFormattingMode)>|使用 PixelsPerDip 重写。|
|<xref:System.Windows.Media.GlyphRun?displayProperty=nameWithType>|<xref:System.Windows.Media.GlyphRun.%23ctor>|使用 PixelsPerDip 重写。|
|<xref:System.Windows.Media.GlyphRun?displayProperty=nameWithType>|<xref:System.Windows.Media.GlyphRun.%23ctor(System.Windows.Media.GlyphTypeface,System.Int32,System.Boolean,System.Double,System.Collections.Generic.IList{System.UInt16},System.Windows.Point,System.Collections.Generic.IList{System.Double},System.Collections.Generic.IList{System.Windows.Point},System.Collections.Generic.IList{System.Char},System.String,System.Collections.Generic.IList{System.UInt16},System.Collections.Generic.IList{System.Boolean},System.Windows.Markup.XmlLanguage)>|使用 PixelsPerDip 重写。|
|<xref:System.Windows.Media.RenderCapability?displayProperty=nameWithType>|<xref:System.Windows.Media.RenderCapability.IsShaderEffectSoftwareRenderingSupported%2A>|此属性已弃用。 请改用静态 <xref:System.Windows.Media.RenderCapability.IsPixelShaderVersionSupportedInSoftware%2A?displayProperty=nameWithType> 方法。|
|<xref:System.Windows.Media.Visual?displayProperty=nameWithType>|<xref:System.Windows.Media.Visual.VisualBitmapEffect%2A>|位图效果已弃用，并将不再工作。 请考虑在适用处改用 <xref:System.Windows.Media.Effects.Effect?displayProperty=nameWithType>。|
|<xref:System.Windows.Media.Visual?displayProperty=nameWithType>|<xref:System.Windows.Media.Visual.VisualBitmapEffectInput%2A>|位图效果已弃用，并将不再工作。 请考虑在适用处改用 <xref:System.Windows.Media.Effects.Effect?displayProperty=nameWithType>。|
|<xref:System.Windows.Media.Effects.BevelBitmapEffect?displayProperty=nameWithType>|<xref:System.Windows.Media.Effects.BitmapEffect.CreateUnmanagedEffect%2A>|位图效果已弃用，并将不再工作。 请考虑在适用处改用 <xref:System.Windows.Media.Effects.Effect?displayProperty=nameWithType>。|
|<xref:System.Windows.Media.Effects.BevelBitmapEffect?displayProperty=nameWithType>|<xref:System.Windows.Media.Effects.BitmapEffect.UpdateUnmanagedPropertyState%2A>|位图效果已弃用，并将不再工作。 请考虑在适用处改用 <xref:System.Windows.Media.Effects.Effect?displayProperty=nameWithType>。|
|<xref:System.Windows.Media.Effects.BitmapEffect?displayProperty=nameWithType>|<xref:System.Windows.Media.Effects.BitmapEffect.CreateBitmapEffectOuter%2A>|位图效果已弃用，并将不再工作。 请考虑在适用处改用 <xref:System.Windows.Media.Effects.Effect?displayProperty=nameWithType>。|
|<xref:System.Windows.Media.Effects.BitmapEffect?displayProperty=nameWithType>|<xref:System.Windows.Media.Effects.BitmapEffect.CreateUnmanagedEffect%2A>|位图效果已弃用，并将不再工作。 请考虑在适用处改用 <xref:System.Windows.Media.Effects.Effect?displayProperty=nameWithType>。|
|<xref:System.Windows.Media.Effects.BitmapEffect?displayProperty=nameWithType>|<xref:System.Windows.Media.Effects.BitmapEffect.GetOutput%2A>|位图效果已弃用，并将不再工作。 请考虑在适用处改用 <xref:System.Windows.Media.Effects.Effect?displayProperty=nameWithType>。|
|<xref:System.Windows.Media.Effects.BitmapEffect?displayProperty=nameWithType>|<xref:System.Windows.Media.Effects.BitmapEffect.InitializeBitmapEffect%2A>|位图效果已弃用，并将不再工作。 请考虑在适用处改用 <xref:System.Windows.Media.Effects.Effect?displayProperty=nameWithType>。|
|<xref:System.Windows.Media.Effects.BitmapEffect?displayProperty=nameWithType>|<xref:System.Windows.Media.Effects.BitmapEffect.SetValue%2A>|位图效果已弃用，并将不再工作。 请考虑在适用处改用 <xref:System.Windows.Media.Effects.Effect?displayProperty=nameWithType>。|
|<xref:System.Windows.Media.Effects.BitmapEffect?displayProperty=nameWithType>|<xref:System.Windows.Media.Effects.BitmapEffect.UpdateUnmanagedPropertyState%2A>|位图效果已弃用，并将不再工作。 请考虑在适用处改用 <xref:System.Windows.Media.Effects.Effect?displayProperty=nameWithType>。|
|<xref:System.Windows.Media.Effects.BitmapEffectGroup?displayProperty=nameWithType>|<xref:System.Windows.Media.Effects.BitmapEffect.CreateUnmanagedEffect%2A>|位图效果已弃用，并将不再工作。 请考虑在适用处改用 <xref:System.Windows.Media.Effects.Effect?displayProperty=nameWithType>。|
|<xref:System.Windows.Media.Effects.BitmapEffectGroup?displayProperty=nameWithType>|<xref:System.Windows.Media.Effects.BitmapEffect.UpdateUnmanagedPropertyState%2A>|位图效果已弃用，并将不再工作。 请考虑在适用处改用 <xref:System.Windows.Media.Effects.Effect?displayProperty=nameWithType>。|
|<xref:System.Windows.Media.Effects.BlurBitmapEffect?displayProperty=nameWithType>|<xref:System.Windows.Media.Effects.BitmapEffect.CreateUnmanagedEffect%2A>|位图效果已弃用，并将不再工作。 请考虑在适用处改用 <xref:System.Windows.Media.Effects.Effect?displayProperty=nameWithType>。|
|<xref:System.Windows.Media.Effects.BlurBitmapEffect?displayProperty=nameWithType>|<xref:System.Windows.Media.Effects.BitmapEffect.UpdateUnmanagedPropertyState%2A>|位图效果已弃用，并将不再工作。 请考虑在适用处改用 <xref:System.Windows.Media.Effects.Effect?displayProperty=nameWithType>。|
|<xref:System.Windows.Media.Effects.DropShadowBitmapEffect?displayProperty=nameWithType>|<xref:System.Windows.Media.Effects.BitmapEffect.CreateUnmanagedEffect%2A>|位图效果已弃用，并将不再工作。 请考虑在适用处改用 <xref:System.Windows.Media.Effects.Effect?displayProperty=nameWithType>。|
|<xref:System.Windows.Media.Effects.DropShadowBitmapEffect?displayProperty=nameWithType>|<xref:System.Windows.Media.Effects.BitmapEffect.UpdateUnmanagedPropertyState%2A>|位图效果已弃用，并将不再工作。 请考虑在适用处改用 <xref:System.Windows.Media.Effects.Effect?displayProperty=nameWithType>。|
|<xref:System.Windows.Media.Effects.EmbossBitmapEffect?displayProperty=nameWithType>|<xref:System.Windows.Media.Effects.BitmapEffect.CreateUnmanagedEffect%2A>|位图效果已弃用，并将不再工作。 请考虑在适用处改用 <xref:System.Windows.Media.Effects.Effect?displayProperty=nameWithType>。|
|<xref:System.Windows.Media.Effects.EmbossBitmapEffect?displayProperty=nameWithType>|<xref:System.Windows.Media.Effects.BitmapEffect.UpdateUnmanagedPropertyState%2A>|位图效果已弃用，并将不再工作。 请考虑在适用处改用 <xref:System.Windows.Media.Effects.Effect?displayProperty=nameWithType>。|
|<xref:System.Windows.Media.Effects.OuterGlowBitmapEffect?displayProperty=nameWithType>|<xref:System.Windows.Media.Effects.BitmapEffect.CreateUnmanagedEffect%2A>|位图效果已弃用，并将不再工作。 请考虑在适用处改用 <xref:System.Windows.Media.Effects.Effect?displayProperty=nameWithType>。|
|<xref:System.Windows.Media.Effects.OuterGlowBitmapEffect?displayProperty=nameWithType>|<xref:System.Windows.Media.Effects.BitmapEffect.UpdateUnmanagedPropertyState%2A>|位图效果已弃用，并将不再工作。 请考虑在适用处改用 <xref:System.Windows.Media.Effects.Effect?displayProperty=nameWithType>。|
|<xref:System.Windows.Media.Media3D.Viewport3DVisual?displayProperty=nameWithType>|<xref:System.Windows.Media.Media3D.Viewport3DVisual.BitmapEffect%2A>|位图效果已弃用，并将不再工作。 请考虑在适用处改用 <xref:System.Windows.Media.Effects.Effect?displayProperty=nameWithType>。|
|<xref:System.Windows.Media.Media3D.Viewport3DVisual?displayProperty=nameWithType>|<xref:System.Windows.Media.Media3D.Viewport3DVisual.BitmapEffectInput%2A>|位图效果已弃用，并将不再工作。 请考虑在适用处改用 <xref:System.Windows.Media.Effects.Effect?displayProperty=nameWithType>。|

<a name="PresFW"></a>
### <a name="assembly-presentationframeworkdll"></a>程序集：PresentationFramework.dll

|类型|成员|消息|
|----------|------------|-------------|
|<xref:System.Windows.Data.BindingListCollectionView?displayProperty=nameWithType>|<xref:System.Windows.Data.CollectionView.OnBeginChangeLogging%2A>|替换为 <xref:System.Windows.Data.CollectionView.OnAllowsCrossThreadChangesChanged%2A?displayProperty=nameWithType>。|
|<xref:System.Windows.Data.CollectionView?displayProperty=nameWithType>|<xref:System.Windows.Data.CollectionView.ClearChangeLog%2A>|替换为 <xref:System.Windows.Data.CollectionView.ClearPendingChanges%2A?displayProperty=nameWithType>。|
|<xref:System.Windows.Data.CollectionView?displayProperty=nameWithType>|<xref:System.Windows.Data.CollectionView.OnBeginChangeLogging%2A>|替换为 <xref:System.Windows.Data.CollectionView.OnAllowsCrossThreadChangesChanged%2A?displayProperty=nameWithType>。|
|<xref:System.Windows.Data.ListCollectionView?displayProperty=nameWithType>|<xref:System.Windows.Data.ListCollectionView.OnBeginChangeLogging%2A>|替换为 <xref:System.Windows.Data.ListCollectionView.OnAllowsCrossThreadChangesChanged%2A?displayProperty=nameWithType>。|

<a name="Act"></a>

### <a name="assembly-systemactivitiesdll"></a>程序集：System.Activities.dll

|类型|成员|消息|
|----------|------------|-------------|
|<xref:System.Activities.Debugger.XamlDebuggerXmlReader?displayProperty=nameWithType>|<xref:System.Activities.Debugger.XamlDebuggerXmlReader.%23ctor%28System.Xaml.XamlReader%2CSystem.Xaml.IXamlLineInfo%2CSystem.IO.TextReader%29>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 不要使用此构造函数。 请改用 <xref:System.Activities.Debugger.XamlDebuggerXmlReader.%23ctor%28System.IO.TextReader%29?displayProperty=nameWithType> 或 <xref:System.Activities.Debugger.XamlDebuggerXmlReader.%23ctor%28System.IO.TextReader%2CSystem.Xaml.XamlSchemaContext%29?displayProperty=nameWithType>。|
|<xref:System.Activities.Debugger.XamlDebuggerXmlReader?displayProperty=nameWithType>|<xref:System.Activities.Debugger.XamlDebuggerXmlReader.%23ctor%28System.Xaml.XamlReader%2CSystem.IO.TextReader%29?displayProperty=nameWithType>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 不要使用此构造函数。 请改用 <xref:System.Activities.Debugger.XamlDebuggerXmlReader.%23ctor%28System.IO.TextReader%29?displayProperty=nameWithType> 或 <xref:System.Activities.Debugger.XamlDebuggerXmlReader.%23ctor%28System.IO.TextReader%2CSystem.Xaml.XamlSchemaContext%29?displayProperty=nameWithType>。|

<a name="ActPres"></a>

### <a name="assembly-systemactivitiespresentationdll"></a>程序集：System.Activities.Presentation.dll

|类型|成员|消息|
|----------|------------|-------------|
|<xref:System.Activities.Presentation.DragDropHelper?displayProperty=nameWithType>|<xref:System.Activities.Presentation.DragDropHelper.DoDragMove%28System.Activities.Presentation.WorkflowViewElement%2CSystem.Windows.Point%29>|此方法不支持拖动多个项。|
|<xref:System.Activities.Presentation.DragDropHelper?displayProperty=nameWithType>|<xref:System.Activities.Presentation.DragDropHelper.GetCompositeView%28System.Windows.DragEventArgs%29>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 此方法不支持拖动多个项。 请改用 <xref:System.Activities.Presentation.DragDropHelper.GetCompositeView%28System.Activities.Presentation.WorkflowViewElement%29>。|
|<xref:System.Activities.Presentation.DragDropHelper?displayProperty=nameWithType>|<xref:System.Activities.Presentation.DragDropHelper.GetDragDropCompletedEffects%2A>|此方法不支持拖动多个项。|
|<xref:System.Activities.Presentation.DragDropHelper?displayProperty=nameWithType>|<xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 此方法不支持拖动多个项。 请改用 <xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItems%2A>。|
|<xref:System.Activities.Presentation.DragDropHelper?displayProperty=nameWithType>|<xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 此方法不支持拖动多个项。 请改用 <xref:System.Activities.Presentation.DragDropHelper.GetDroppedObjects%2A>。|
|<xref:System.Activities.Presentation.DragDropHelper?displayProperty=nameWithType>|<xref:System.Activities.Presentation.DragDropHelper.SetDragDropCompletedEffects%2A>|此方法不支持拖动多个项。|
|<xref:System.Activities.Presentation.Services.ModelChangedEventArgs?displayProperty=nameWithType>|<xref:System.Activities.Presentation.Services.ModelChangedEventArgs.ItemsAdded%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 不要使用此属性。 请改用 <xref:System.Activities.Presentation.Services.ModelChangedEventArgs.ModelChangeInfo%2A>。|
|<xref:System.Activities.Presentation.Services.ModelChangedEventArgs?displayProperty=nameWithType>|<xref:System.Activities.Presentation.Services.ModelChangedEventArgs.ItemsRemoved%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 不要使用此属性。 请改用 <xref:System.Activities.Presentation.Services.ModelChangedEventArgs.ModelChangeInfo%2A>。|
|<xref:System.Activities.Presentation.Services.ModelChangedEventArgs?displayProperty=nameWithType>|<xref:System.Activities.Presentation.Services.ModelChangedEventArgs.PropertiesChanged%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 不要使用此属性。 请改用 <xref:System.Activities.Presentation.Services.ModelChangedEventArgs.ModelChangeInfo%2A>。|

<a name="core"></a>

### <a name="assembly-systemcoredll"></a>程序集：System.Core.dll

|类型|成员|消息|
|----------|------------|-------------|
|<xref:System.Diagnostics.Eventing.Reader.StandardEventKeywords?displayProperty=nameWithType>|<xref:System.Diagnostics.Eventing.Reader.StandardEventKeywords.CorrelationHint>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 不正确的值；请改用 <xref:System.Diagnostics.Eventing.Reader.StandardEventKeywords.CorrelationHint2>。|
|<xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType>|<xref:System.Linq.ParallelEnumerable.Concat%60%601%28System.Linq.ParallelQuery%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%600%7D%29>|二进制运算符的第二个数据源必须为类型 <xref:System.Linq.ParallelQuery%601?displayProperty=nameWithType> 而不是 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>。 若要解决此问题，请使用 <xref:System.Linq.ParallelEnumerable.AsParallel%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> 扩展方法将正确的数据源转换为 <xref:System.Linq.ParallelQuery%601?displayProperty=nameWithType>。|
|<xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType>|<xref:System.Linq.ParallelEnumerable.Except%60%601%28System.Linq.ParallelQuery%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%600%7D%29>|二进制运算符的第二个数据源必须为类型 <xref:System.Linq.ParallelQuery%601?displayProperty=nameWithType> 而不是 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>。 若要解决此问题，请使用 <xref:System.Linq.ParallelEnumerable.AsParallel%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> 扩展方法将正确的数据源转换为 <xref:System.Linq.ParallelQuery%601?displayProperty=nameWithType>。|
|<xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType>|<xref:System.Linq.ParallelEnumerable.Except%60%601%28System.Linq.ParallelQuery%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%600%7D%29>|二进制运算符的第二个数据源必须为类型 <xref:System.Linq.ParallelQuery%601?displayProperty=nameWithType> 而不是 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>。 若要解决此问题，请使用 <xref:System.Linq.ParallelEnumerable.AsParallel%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> 扩展方法将正确的数据源转换为 <xref:System.Linq.ParallelQuery%601?displayProperty=nameWithType>。|
|<xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType>|<xref:System.Linq.ParallelEnumerable.GroupJoin%60%604%28System.Linq.ParallelQuery%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2C%60%603%7D%29>|二进制运算符的第二个数据源必须为类型 <xref:System.Linq.ParallelQuery%601?displayProperty=nameWithType> 而不是 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>。 若要解决此问题，请使用 <xref:System.Linq.ParallelEnumerable.AsParallel%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> 扩展方法将正确的数据源转换为 <xref:System.Linq.ParallelQuery%601?displayProperty=nameWithType>。|
|<xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType>|<xref:System.Linq.ParallelEnumerable.GroupJoin%60%604%28System.Linq.ParallelQuery%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%602%7D%29>|二进制运算符的第二个数据源必须为类型 <xref:System.Linq.ParallelQuery%601?displayProperty=nameWithType> 而不是 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>。 若要解决此问题，请使用 <xref:System.Linq.ParallelEnumerable.AsParallel%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> 扩展方法将正确的数据源转换为 <xref:System.Linq.ParallelQuery%601?displayProperty=nameWithType>。|
|<xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType>|<xref:System.Linq.ParallelEnumerable.Intersect%60%601%28System.Linq.ParallelQuery%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%600%7D%29>|二进制运算符的第二个数据源必须为类型 <xref:System.Linq.ParallelQuery%601?displayProperty=nameWithType> 而不是 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>。 若要解决此问题，请使用 <xref:System.Linq.ParallelEnumerable.AsParallel%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> 扩展方法将正确的数据源转换为 <xref:System.Linq.ParallelQuery%601?displayProperty=nameWithType>。|
|<xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType>|<xref:System.Linq.ParallelEnumerable.Intersect%60%601%28System.Linq.ParallelQuery%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%600%7D%29>|二进制运算符的第二个数据源必须为类型 <xref:System.Linq.ParallelQuery%601?displayProperty=nameWithType> 而不是 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>。 若要解决此问题，请使用 <xref:System.Linq.ParallelEnumerable.AsParallel%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> 扩展方法将正确的数据源转换为 <xref:System.Linq.ParallelQuery%601?displayProperty=nameWithType>。|
|<xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType>|<xref:System.Linq.ParallelEnumerable.Join%60%604%28System.Linq.ParallelQuery%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%29>|二进制运算符的第二个数据源必须为类型 <xref:System.Linq.ParallelQuery%601?displayProperty=nameWithType> 而不是 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>。 若要解决此问题，请使用 <xref:System.Linq.ParallelEnumerable.AsParallel%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> 扩展方法将正确的数据源转换为 <xref:System.Linq.ParallelQuery%601?displayProperty=nameWithType>。|
|<xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType>|<xref:System.Linq.ParallelEnumerable.Join%60%604%28System.Linq.ParallelQuery%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%602%7D%29>|二进制运算符的第二个数据源必须为类型 <xref:System.Linq.ParallelQuery%601?displayProperty=nameWithType> 而不是 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>。 若要解决此问题，请使用 <xref:System.Linq.ParallelEnumerable.AsParallel%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> 扩展方法将正确的数据源转换为 <xref:System.Linq.ParallelQuery%601?displayProperty=nameWithType>。|
|<xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType>|<xref:System.Linq.ParallelEnumerable.SequenceEqual%60%601%28System.Linq.ParallelQuery%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%600%7D%29>|二进制运算符的第二个数据源必须为类型 <xref:System.Linq.ParallelQuery%601?displayProperty=nameWithType> 而不是 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>。 若要解决此问题，请使用 <xref:System.Linq.ParallelEnumerable.AsParallel%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> 扩展方法将正确的数据源转换为 <xref:System.Linq.ParallelQuery%601?displayProperty=nameWithType>。|
|<xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType>|<xref:System.Linq.ParallelEnumerable.SequenceEqual%60%601%28System.Linq.ParallelQuery%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%600%7D%29>|二进制运算符的第二个数据源必须为类型 <xref:System.Linq.ParallelQuery%601?displayProperty=nameWithType> 而不是 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>。 若要解决此问题，请使用 <xref:System.Linq.ParallelEnumerable.AsParallel%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> 扩展方法将正确的数据源转换为 <xref:System.Linq.ParallelQuery%601?displayProperty=nameWithType>。|
|<xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType>|<xref:System.Linq.ParallelEnumerable.Union%60%601%28System.Linq.ParallelQuery%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%600%7D%29>|二进制运算符的第二个数据源必须为类型 <xref:System.Linq.ParallelQuery%601?displayProperty=nameWithType> 而不是 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>。 若要解决此问题，请使用 <xref:System.Linq.ParallelEnumerable.AsParallel%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> 扩展方法将正确的数据源转换为 <xref:System.Linq.ParallelQuery%601?displayProperty=nameWithType>。|
|<xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType>|<xref:System.Linq.ParallelEnumerable.Union%60%601%28System.Linq.ParallelQuery%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%600%7D%29>|二进制运算符的第二个数据源必须为类型 <xref:System.Linq.ParallelQuery%601?displayProperty=nameWithType> 而不是 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>。 若要解决此问题，请使用 <xref:System.Linq.ParallelEnumerable.AsParallel%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> 扩展方法将正确的数据源转换为 <xref:System.Linq.ParallelQuery%601?displayProperty=nameWithType>。|
|<xref:System.Linq.ParallelEnumerable?displayProperty=nameWithType>|<xref:System.Linq.ParallelEnumerable.Zip%2A>|二进制运算符的第二个数据源必须为类型 <xref:System.Linq.ParallelQuery%601?displayProperty=nameWithType> 而不是 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>。 若要解决此问题，请使用 <xref:System.Linq.ParallelEnumerable.AsParallel%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> 扩展方法将正确的数据源转换为 <xref:System.Linq.ParallelQuery%601?displayProperty=nameWithType>。|
|<xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>|<xref:System.Linq.Expressions.Expression.%23ctor%28System.Linq.Expressions.ExpressionType%2CSystem.Type%29>|使用不采用 <xref:System.Linq.Expressions.ExpressionType?displayProperty=nameWithType> 参数的其他构造函数。 然后，重写 <xref:System.Linq.Expressions.Expression.NodeType%2A?displayProperty=nameWithType> 和 <xref:System.Linq.Expressions.Expression.Type%2A?displayProperty=nameWithType> 属性以提供可能指定给此构造函数的值。|
|<xref:System.Linq.Expressions.MemberBinding?displayProperty=nameWithType>|<xref:System.Linq.Expressions.MemberBinding.%23ctor%2A>|不要使用此构造函数。 它将从未来版本中移除。|
|<xref:System.Runtime.CompilerServices.CallSiteOps?displayProperty=nameWithType>|<xref:System.Runtime.CompilerServices.CallSiteOps.AddRule%2A>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|
|<xref:System.Runtime.CompilerServices.CallSiteOps?displayProperty=nameWithType>|<xref:System.Runtime.CompilerServices.CallSiteOps.Bind%2A>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|
|<xref:System.Runtime.CompilerServices.CallSiteOps?displayProperty=nameWithType>|<xref:System.Runtime.CompilerServices.CallSiteOps.ClearMatch%2A>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|
|<xref:System.Runtime.CompilerServices.CallSiteOps?displayProperty=nameWithType>|<xref:System.Runtime.CompilerServices.CallSiteOps.CreateMatchmaker%2A>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|
|<xref:System.Runtime.CompilerServices.CallSiteOps?displayProperty=nameWithType>|<xref:System.Runtime.CompilerServices.CallSiteOps.GetCachedRules%60%601%28System.Runtime.CompilerServices.RuleCache%7B%60%600%7D%29>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|
|<xref:System.Runtime.CompilerServices.CallSiteOps?displayProperty=nameWithType>|<xref:System.Runtime.CompilerServices.CallSiteOps.GetMatch%2A>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|
|<xref:System.Runtime.CompilerServices.CallSiteOps?displayProperty=nameWithType>|<xref:System.Runtime.CompilerServices.CallSiteOps.GetRuleCache%2A>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|
|<xref:System.Runtime.CompilerServices.CallSiteOps?displayProperty=nameWithType>|<xref:System.Runtime.CompilerServices.CallSiteOps.GetRules%2A>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|
|<xref:System.Runtime.CompilerServices.CallSiteOps?displayProperty=nameWithType>|<xref:System.Runtime.CompilerServices.CallSiteOps.MoveRule%60%601%28System.Runtime.CompilerServices.RuleCache%7B%60%600%7D%2C%60%600%2CSystem.Int32%29>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|
|<xref:System.Runtime.CompilerServices.CallSiteOps?displayProperty=nameWithType>|<xref:System.Runtime.CompilerServices.CallSiteOps.SetNotMatched%2A>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|
|<xref:System.Runtime.CompilerServices.CallSiteOps?displayProperty=nameWithType>|<xref:System.Runtime.CompilerServices.CallSiteOps.UpdateRules%2A>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|
|<xref:System.Runtime.CompilerServices.RuntimeOps?displayProperty=nameWithType>|<xref:System.Runtime.CompilerServices.RuntimeOps.CreateRuntimeVariables>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|
|<xref:System.Runtime.CompilerServices.RuntimeOps?displayProperty=nameWithType>|<xref:System.Runtime.CompilerServices.RuntimeOps.CreateRuntimeVariables%28System.Object%5B%5D%2CSystem.Int64%5B%5D%29>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|
|<xref:System.Runtime.CompilerServices.RuntimeOps?displayProperty=nameWithType>|<xref:System.Runtime.CompilerServices.RuntimeOps.ExpandoCheckVersion%2A>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|
|<xref:System.Runtime.CompilerServices.RuntimeOps?displayProperty=nameWithType>|<xref:System.Runtime.CompilerServices.RuntimeOps.ExpandoPromoteClass%2A>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|
|<xref:System.Runtime.CompilerServices.RuntimeOps?displayProperty=nameWithType>|<xref:System.Runtime.CompilerServices.RuntimeOps.ExpandoTryDeleteValue%2A>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|
|<xref:System.Runtime.CompilerServices.RuntimeOps?displayProperty=nameWithType>|<xref:System.Runtime.CompilerServices.RuntimeOps.ExpandoTryGetValue%2A>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|
|<xref:System.Runtime.CompilerServices.RuntimeOps?displayProperty=nameWithType>|<xref:System.Runtime.CompilerServices.RuntimeOps.ExpandoTrySetValue%2A>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|
|<xref:System.Runtime.CompilerServices.RuntimeOps?displayProperty=nameWithType>|<xref:System.Runtime.CompilerServices.RuntimeOps.MergeRuntimeVariables%2A>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|
|<xref:System.Runtime.CompilerServices.RuntimeOps?displayProperty=nameWithType>|<xref:System.Runtime.CompilerServices.RuntimeOps.Quote%2A>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|

<a name="data"></a>

### <a name="assembly-systemdatadll"></a>程序集：System.Data.dll

|类型|成员|消息|
|----------|------------|-------------|
|<xref:System.Data.DataSysDescriptionAttribute?displayProperty=nameWithType>|<xref:System.Data.DataSysDescriptionAttribute.%23ctor%2A>|<xref:System.Data.DataSysDescriptionAttribute> 已弃用。|
|<xref:System.Data.Common.DataAdapter?displayProperty=nameWithType>|<xref:System.Data.Common.DataAdapter.CloneInternals%2A>|<xref:System.Data.Common.DataAdapter.CloneInternals%2A> 已弃用。 请使用 <xref:System.Data.Common.DataAdapter.%23ctor%28System.Data.Common.DataAdapter%29> 构造函数。|
|<xref:System.Data.Common.DBDataPermission?displayProperty=nameWithType>|<xref:System.Data.Common.DBDataPermission.%23ctor>|使用此成员会生成编译器错误。<br /><br /> 此构造函数已弃用。 向 <xref:System.Data.Common.DBDataPermission.%23ctor%28System.Security.Permissions.PermissionState%29> 构造函数传递一个 <xref:System.Security.Permissions.PermissionState.None?displayProperty=nameWithType> 值。|
|<xref:System.Data.Common.DBDataPermission?displayProperty=nameWithType>|<xref:System.Data.Common.DBDataPermission.%23ctor%28System.Security.Permissions.PermissionState%2CSystem.Boolean%29>|使用此成员会生成编译器错误。<br /><br /> 此构造函数已弃用。 向 <xref:System.Data.Common.DBDataPermission.%23ctor%28System.Security.Permissions.PermissionState%29> 构造函数传递一个 <xref:System.Security.Permissions.PermissionState.None?displayProperty=nameWithType> 值。|
|<xref:System.Data.Odbc.OdbcParameterCollection?displayProperty=nameWithType>|<xref:System.Data.Odbc.OdbcParameterCollection.Add%28System.String%2CSystem.Object%29>|<xref:System.Data.Odbc.OdbcParameterCollection.Add%28System.String%2CSystem.Object%29> 已弃用。 请使用 <xref:System.Data.Odbc.OdbcParameterCollection.AddWithValue%28System.String%2CSystem.Object%29?displayProperty=nameWithType>。|
|<xref:System.Data.Odbc.OdbcPermission?displayProperty=nameWithType>|<xref:System.Data.Odbc.OdbcPermission.%23ctor>|使用此成员会生成编译器错误。<br /><br /> <xref:System.Data.Odbc.OdbcPermission.%23ctor> 已弃用。 向 <xref:System.Data.Odbc.OdbcPermission.%23ctor%28System.Security.Permissions.PermissionState%29> 构造函数传递一个 <xref:System.Security.Permissions.PermissionState.None?displayProperty=nameWithType> 值。|
|<xref:System.Data.Odbc.OdbcPermission?displayProperty=nameWithType>|<xref:System.Data.Odbc.OdbcPermission.%23ctor%28System.Security.Permissions.PermissionState%2CSystem.Boolean%29>|使用此成员会生成编译器错误。<br /><br /> <xref:System.Data.Odbc.OdbcPermission.%23ctor%28System.Security.Permissions.PermissionState%2CSystem.Boolean%29> 已弃用。 向 <xref:System.Data.Odbc.OdbcPermission.%23ctor%28System.Security.Permissions.PermissionState%29> 构造函数传递一个 <xref:System.Security.Permissions.PermissionState.None?displayProperty=nameWithType> 值。|
|<xref:System.Data.OleDb.OleDbParameterCollection?displayProperty=nameWithType>|<xref:System.Data.OleDb.OleDbParameterCollection.Add%28System.String%2CSystem.Object%29>|<xref:System.Data.OleDb.OleDbParameterCollection.Add%28System.String%2CSystem.Object%29> 已弃用。 使用 <xref:System.Data.OleDb.OleDbParameterCollection.AddWithValue%2A?displayProperty=nameWithType> 方法。|
|<xref:System.Data.OleDb.OleDbPermission?displayProperty=nameWithType>|<xref:System.Data.OleDb.OleDbPermission.%23ctor>|使用此成员会生成编译器错误。<br /><br /> <xref:System.Data.OleDb.OleDbPermission.%23ctor> 已弃用。 向 <xref:System.Data.OleDb.OleDbPermission.%23ctor%28System.Security.Permissions.PermissionState%29> 传递一个 <xref:System.Security.Permissions.PermissionState.None?displayProperty=nameWithType> 值。|
|<xref:System.Data.OleDb.OleDbPermission?displayProperty=nameWithType>|<xref:System.Data.OleDb.OleDbPermission.%23ctor%28System.Security.Permissions.PermissionState%2CSystem.Boolean%29>|使用此成员会生成编译器错误。<br /><br /> <xref:System.Data.OleDb.OleDbPermission.%23ctor%28System.Security.Permissions.PermissionState%2CSystem.Boolean%29> 已弃用。 向 <xref:System.Data.OleDb.OleDbPermission.%23ctor%28System.Security.Permissions.PermissionState%29> 传递一个 <xref:System.Security.Permissions.PermissionState.None?displayProperty=nameWithType> 值。|
|<xref:System.Data.OleDb.OleDbPermission?displayProperty=nameWithType>|<xref:System.Data.OleDb.OleDbPermission.Provider%2A>|<xref:System.Data.OleDb.OleDbPermission.Provider?displayProperty=nameWithType> 属性已弃用。 使用 <xref:System.Data.Common.DBDataPermission.Add%28System.String%2CSystem.String%2CSystem.Data.KeyRestrictionBehavior%29?displayProperty=nameWithType> 方法。|
|<xref:System.Data.OleDb.OleDbPermissionAttribute?displayProperty=nameWithType>|<xref:System.Data.OleDb.OleDbPermissionAttribute.Provider%2A>|<xref:System.Data.OleDb.OleDbPermissionAttribute.Provider?displayProperty=nameWithType> 属性已弃用。 使用 <xref:System.Data.Common.DBDataPermission.Add%28System.String%2CSystem.String%2CSystem.Data.KeyRestrictionBehavior%29?displayProperty=nameWithType> 方法。|
|<xref:System.Data.SqlClient.SqlClientPermission?displayProperty=nameWithType>|<xref:System.Data.SqlClient.SqlClientPermission.%23ctor>|使用此构造函数会生成编译器错误。<br /><br /> <xref:System.Data.SqlClient.SqlClientPermission.%23ctor> 已弃用。 向 <xref:System.Data.SqlClient.SqlClientPermission.%23ctor%28System.Security.Permissions.PermissionState%29> 构造函数传递一个 <xref:System.Security.Permissions.PermissionState.None?displayProperty=nameWithType> 值。|
|<xref:System.Data.SqlClient.SqlClientPermission?displayProperty=nameWithType>|<xref:System.Data.SqlClient.SqlClientPermission.%23ctor%28System.Security.Permissions.PermissionState%2CSystem.Boolean%29>|使用此构造函数会生成编译器错误。<br /><br /> <xref:System.Data.SqlClient.SqlClientPermission.%23ctor%28System.Security.Permissions.PermissionState%2CSystem.Boolean%29> 已弃用。 向 <xref:System.Data.SqlClient.SqlClientPermission.%23ctor%28System.Security.Permissions.PermissionState%29> 构造函数传递一个 <xref:System.Security.Permissions.PermissionState.None?displayProperty=nameWithType> 值。|
|<xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectionReset%2A>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder.ConnectionReset%2A> 已弃用。 <xref:System.Data.SqlClient.SqlConnection?displayProperty=nameWithType> 将忽略“连接重置”关键字，并始终重置该连接。|
|<xref:System.Data.SqlClient.SqlParameterCollection?displayProperty=nameWithType>|<xref:System.Data.SqlClient.SqlParameterCollection.Add%28System.String%2CSystem.Object%29>|<xref:System.Data.SqlClient.SqlParameterCollection.Add%28System.String%2CSystem.Object%29> 已弃用。 请使用 <xref:System.Data.SqlClient.SqlParameterCollection.AddWithValue%2A?displayProperty=nameWithType>。|

<a name="entity"></a>

### <a name="assembly-systemdataentitydll"></a>程序集：System.Data.Entity.dll

|类型|成员|消息|
|----------|------------|-------------|
|<xref:System.Data.Metadata.Edm.AssociationSetEnd?displayProperty=nameWithType>|<xref:System.Data.Metadata.Edm.AssociationSetEnd.Role%2A>|此属性将停用，请改用 <xref:System.Data.Metadata.Edm.AssociationSetEnd.Name%2A?displayProperty=nameWithType> 属性。|
|<xref:System.Data.Metadata.Edm.MetadataWorkspace?displayProperty=nameWithType>|<xref:System.Data.Metadata.Edm.MetadataWorkspace.GetRequiredOriginalValueMembers%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 请改用 <xref:System.Data.Metadata.Edm.MetadataWorkspace.GetRelevantMembersForUpdate%2A?displayProperty=nameWithType>。|
|<xref:System.Data.Objects.ObjectContext?displayProperty=nameWithType>|<xref:System.Data.Objects.ObjectContext.ApplyPropertyChanges%2A>|请改用 <xref:System.Data.Objects.ObjectContext.ApplyCurrentValues%2A?displayProperty=nameWithType>。|
|<xref:System.Data.Objects.ObjectContext?displayProperty=nameWithType>|<xref:System.Data.Objects.ObjectContext.SaveChanges%28System.Boolean%29>|请改用 <xref:System.Data.Objects.ObjectContext.SaveChanges%28System.Data.Objects.SaveOptions%29>。|

<a name="oracleclient"></a>

### <a name="assembly-systemdataoracleclientdll"></a>程序集：System.Data.OracleClient.dll

|类型|成员|消息|
|----------|------------|-------------|
|<xref:System.Data.OracleClient.OracleParameter?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleParameter.Precision%2A>|<xref:System.Data.OracleClient.OracleParameter.Precision%2A> 已弃用。 使用 <xref:System.Math?displayProperty=nameWithType> 类显式设置某小数的精度。|
|<xref:System.Data.OracleClient.OracleParameter?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleParameter.Scale%2A>|<xref:System.Data.OracleClient.OracleParameter.Scale%2A> 已弃用。 使用 <xref:System.Math?displayProperty=nameWithType> 类显式设置某小数的小数位数。|
|<xref:System.Data.OracleClient.OracleParameterCollection?displayProperty=nameWithType>|<xref:System.Data.OracleClient.OracleParameterCollection.Add%28System.String%2CSystem.Object%29>|<xref:System.Data.OracleClient.OracleParameterCollection.Add%28System.String%2CSystem.Object%29> 已弃用。 请使用 <xref:System.Data.OracleClient.OracleParameterCollection.AddWithValue%2A?displayProperty=nameWithType>。|

<a name="design"></a>

### <a name="assembly-systemdesigndll"></a>程序集：System.Design.dll

|类型|成员|消息|
|----------|------------|-------------|
|<xref:System.ComponentModel.Design.ComponentDesigner?displayProperty=nameWithType>|<xref:System.ComponentModel.Design.ComponentDesigner.InitializeNonDefault%2A>|此方法已被否决。 请改用 <xref:System.ComponentModel.Design.ComponentDesigner.InitializeExistingComponent%2A?displayProperty=nameWithType>。|
|<xref:System.ComponentModel.Design.ComponentDesigner?displayProperty=nameWithType>|<xref:System.ComponentModel.Design.ComponentDesigner.OnSetComponentDefaults%2A>|此方法已被否决。 请改用 <xref:System.ComponentModel.Design.ComponentDesigner.InitializeNewComponent%2A?displayProperty=nameWithType>。|
|<xref:System.ComponentModel.Design.DesignSurface?displayProperty=nameWithType>|<xref:System.ComponentModel.Design.DesignSurface.CreateComponent%2A>|<xref:System.ComponentModel.Design.DesignSurface.CreateComponent%2A> 方法已替换为 <xref:System.ComponentModel.Design.DesignSurface.CreateInstance%28System.Type%29>。|
|<xref:System.ComponentModel.Design.Serialization.CodeDomSerializer?displayProperty=nameWithType>|<xref:System.ComponentModel.Design.Serialization.CodeDomSerializer.SerializeToReferenceExpression%2A>|此方法已被否决。 请改用 <xref:System.ComponentModel.Design.Serialization.CodeDomSerializerBase.SerializeToExpression%2A> 或 <xref:System.ComponentModel.Design.Serialization.CodeDomSerializerBase.GetExpression%2A>。|
|<xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.ControlDesigner.DesignTimeElementView%2A>|使用此属性会生成编译器错误。<br /><br /> 错误：将不再引用此属性，并已含入现有已编译的应用程序中。 不再使用设计\-时元素视图体系结构。|
|<xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.ControlDesigner.DesignTimeHtmlRequiresLoadComplete%2A>|建议的替代项为使用 [`ControlDesigner.SetViewFlags(ViewFlags.DesignTimeHtmlRequiresLoadComplete, true)`](xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A)。|
|<xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.ControlDesigner.GetPersistInnerHtml%2A>|建议的替代项为 <xref:System.Web.UI.Design.ControlDesigner.GetPersistenceContent%2A?displayProperty=nameWithType>。|
|<xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.ControlDesigner.IsDirty%2A>|建议的替代项为使用 [`ControlDesigner.Tag.SetDirty`](xref:System.Web.UI.Design.IControlDesignerTag.SetDirty%2A) 和 [`ControlDesigner.Tag.IsDirty`](xref:System.Web.UI.Design.IControlDesignerTag.IsDirty%2A)。|
|<xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.ControlDesigner.IsPropertyBound%2A>|建议的替代项为 [`ControlDesigner.DataBindings.Contains`](xref:System.Web.UI.DataBindingCollection.Contains%2A)。 <xref:System.Web.UI.DataBindingCollection?displayProperty=nameWithType> 类允许在更大程度上控制与该控件关联的数据绑定。|
|<xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.ControlDesigner.OnBindingsCollectionChanged%2A>|建议的替代项是处理 `ControlDesigner.DataBindings.Changed` 事件。 [`ControlDesigner.DataBindings`](xref:System.Web.UI.Design.HtmlControlDesigner.DataBindings%2A) 属性返回的 <xref:System.Web.UI.DataBindingCollection> 集合允许在更大程度上控制与该控件关联的数据绑定。|
|<xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.ControlDesigner.OnControlResize%2A>|建议的替代项是 <xref:System.Web.UI.Design.ControlDesigner.OnComponentChanged%2A>，在控件属性更改时调用。|
|<xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.ControlDesigner.RaiseResizeEvent%2A>|建议不要使用此方法，因为调整大小的操作由 <xref:System.Web.UI.Design.ControlDesigner.OnComponentChanged%2A?displayProperty=nameWithType> 方法处理。|
|<xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.ControlDesigner.ReadOnly%2A>|建议的替代项改为从 <xref:System.Web.UI.Design.ContainerControlDesigner?displayProperty=nameWithType> 继承，并使用 <xref:System.Web.UI.Design.EditableDesignerRegion?displayProperty=nameWithType>。 利用区域，可更好地控制设计器中的内容。|
|<xref:System.Web.UI.Design.HtmlControlDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.HtmlControlDesigner.Behavior%2A>|建议的替代项为 <xref:System.Web.UI.Design.ControlDesigner.Tag%2A?displayProperty=nameWithType>。|
|<xref:System.Web.UI.Design.HtmlControlDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.HtmlControlDesigner.DesignTimeElement%2A>|使用此属性会生成编译器错误。<br /><br /> 错误：将不再引用此属性，并已含入现有已编译的应用程序中。 设计\-时元素可能无法始终提供对标记中元素的访问。 <xref:System.Web.UI.Design.WebFormsRootDesigner?displayProperty=nameWithType> 上处理客户端脚本和控件的替换方法。|
|<xref:System.Web.UI.Design.HtmlControlDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.HtmlControlDesigner.OnBehaviorAttached%2A>|建议的替代项为 <xref:System.Web.UI.Design.ControlDesigner.Tag%2A?displayProperty=nameWithType>。|
|<xref:System.Web.UI.Design.HtmlControlDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.HtmlControlDesigner.OnBehaviorDetaching%2A>|建议的替代项为 <xref:System.Web.UI.Design.ControlDesigner.Tag%2A?displayProperty=nameWithType>。|
|<xref:System.Web.UI.Design.HtmlControlDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.HtmlControlDesigner.OnBindingsCollectionChanged%2A>|建议的替代项是处理 [HtmlControlDesigner.DataBindings.Changed](xref:System.Web.UI.DataBindingCollection.Changed) 事件。 <xref:System.Web.UI.Design.HtmlControlDesigner.DataBindings%2A?displayProperty=nameWithType> 属性返回的 <xref:System.Web.UI.DataBindingCollection> 集合允许在更大程度上控制与该控件关联的数据绑定。|
|<xref:System.Web.UI.Design.HtmlControlDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.HtmlControlDesigner.ShouldCodeSerialize%2A>|建议不要使用此属性，因为不支持代码序列化。|
|<xref:System.Web.UI.Design.TemplatedControlDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.TemplatedControlDesigner.ActiveTemplateEditingFrame%2A>|建议不要使用此属性，因为模板编辑是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 中处理的。 若要支持模板编辑，请在 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> 属性中公开模板数据，并调用 [`ControlDesigner.SetViewFlags(ViewFlags.TemplateEditing, true)`](xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A)。|
|<xref:System.Web.UI.Design.TemplatedControlDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.TemplatedControlDesigner.CreateTemplateEditingFrame%2A>|建议不要使用此方法，因为模板编辑是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 中处理的。 若要支持模板编辑，请在 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> 属性中公开模板数据，并调用 [`ControlDesigner.SetViewFlags(ViewFlags.TemplateEditing, true)`](xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A)。|
|<xref:System.Web.UI.Design.TemplatedControlDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.TemplatedControlDesigner.EnterTemplateMode%2A>|建议不要使用此方法，因为模板编辑是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 中处理的。 若要支持模板编辑，请在 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> 属性中公开模板数据，并调用 [`ControlDesigner.SetViewFlags(ViewFlags.TemplateEditing, true)`](xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A)。|
|<xref:System.Web.UI.Design.TemplatedControlDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.TemplatedControlDesigner.ExitTemplateMode%2A>|建议不要使用此方法，因为模板编辑是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 中处理的。 若要支持模板编辑，请在 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> 属性中公开模板数据，并调用 [`ControlDesigner.SetViewFlags(ViewFlags.TemplateEditing, true)`](xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A)。|
|<xref:System.Web.UI.Design.TemplatedControlDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.TemplatedControlDesigner.GetCachedTemplateEditingVerbs%2A>|建议不要使用此方法，因为模板编辑是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 中处理的。 若要支持模板编辑，请在 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> 属性中公开模板数据，并调用 [`ControlDesigner.SetViewFlags(ViewFlags.TemplateEditing, true)`](xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A)。|
|<xref:System.Web.UI.Design.TemplatedControlDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.TemplatedControlDesigner.GetTemplateContainerDataItemProperty%2A>|建议不要使用此方法，因为模板编辑是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 中处理的。 若要支持模板编辑，请在 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> 属性中公开模板数据，并调用 [`ControlDesigner.SetViewFlags(ViewFlags.TemplateEditing, true)`](xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A)。|
|<xref:System.Web.UI.Design.TemplatedControlDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.TemplatedControlDesigner.GetTemplateContainerDataSource%2A>|建议不要使用此方法，因为模板编辑是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 中处理的。 若要支持模板编辑，请在 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> 属性中公开模板数据，并调用 [`ControlDesigner.SetViewFlags(ViewFlags.TemplateEditing, true)`](xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A)。|
|<xref:System.Web.UI.Design.TemplatedControlDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.TemplatedControlDesigner.GetTemplateContent%2A>|建议不要使用此方法，因为模板编辑是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 中处理的。 若要支持模板编辑，请在 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> 属性中公开模板数据，并调用 [`ControlDesigner.SetViewFlags(ViewFlags.TemplateEditing, true)`](xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A)。|
|<xref:System.Web.UI.Design.TemplatedControlDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.TemplatedControlDesigner.GetTemplateEditingVerbs%2A>|建议不要使用此方法，因为模板编辑是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 中处理的。 若要支持模板编辑，请在 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> 属性中公开模板数据，并调用 [`ControlDesigner.SetViewFlags(ViewFlags.TemplateEditing, true)`](xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A)。|
|<xref:System.Web.UI.Design.TemplatedControlDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.TemplatedControlDesigner.GetTemplatePropertyParentType%2A>|建议不要使用此方法，因为模板编辑是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 中处理的。 若要支持模板编辑，请在 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> 属性中公开模板数据，并调用 [`ControlDesigner.SetViewFlags(ViewFlags.TemplateEditing, true)`](xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A)。|
|<xref:System.Web.UI.Design.TemplatedControlDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.TemplatedControlDesigner.InTemplateMode%2A>|建议的替代项为 <xref:System.Web.UI.Design.ControlDesigner.InTemplateMode%2A?displayProperty=nameWithType>。|
|<xref:System.Web.UI.Design.TemplatedControlDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.TemplatedControlDesigner.OnBehaviorAttached%2A>|建议的替代项为 <xref:System.Web.UI.Design.ControlDesigner.Tag%2A?displayProperty=nameWithType>。|
|<xref:System.Web.UI.Design.TemplatedControlDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.TemplatedControlDesigner.SetTemplateContent%2A>|建议不要使用此方法，因为模板编辑是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 中处理的。 若要支持模板编辑，请在 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> 属性中公开模板数据，并调用 [`ControlDesigner.SetViewFlags(ViewFlags.TemplateEditing, true)`](xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A)。|
|<xref:System.Web.UI.Design.WebControls.BaseDataListDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.WebControls.BaseDataListDesigner.GetTemplateContainerDataSource%2A>|建议不要使用此方法，因为模板编辑是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 中处理的。 若要支持模板编辑，请在 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> 属性中公开模板数据，并调用 [`ControlDesigner.SetViewFlags(ViewFlags.TemplateEditing, true)`](xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A)。|
|<xref:System.Web.UI.Design.WebControls.BaseDataListDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.WebControls.BaseDataListDesigner.OnAutoFormat%2A>|建议不要使用此方法，因为 AutoFormat  对话框由设计器宿主启动。 <xref:System.Web.UI.Design.ControlDesigner.AutoFormats%2A?displayProperty=nameWithType> 属性公开了可用的 AutoFormat 的列表。|
|<xref:System.Web.UI.Design.WebControls.DataGridDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.WebControls.DataGridDesigner.CreateTemplateEditingFrame%2A>|建议不要使用此方法，因为模板编辑是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 中处理的。 若要支持模板编辑，请在 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A> 属性中公开模板数据，并调用 [`ControlDesigner.SetViewFlags(ViewFlags.TemplateEditing, true)`](xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A)。|
|<xref:System.Web.UI.Design.WebControls.DataGridDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.WebControls.DataGridDesigner.GetCachedTemplateEditingVerbs%2A>|建议不要使用此方法，因为模板编辑是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 中处理的。 若要支持模板编辑，请在 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A> 属性中公开模板数据，并调用 [`ControlDesigner.SetViewFlags(ViewFlags.TemplateEditing, true)`](xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A)。|
|<xref:System.Web.UI.Design.WebControls.DataGridDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.WebControls.DataGridDesigner.GetTemplateContainerDataItemProperty%2A>|建议不要使用此方法，因为模板编辑是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 中处理的。 若要支持模板编辑，请在 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> 属性中公开模板数据，并调用 [`ControlDesigner.SetViewFlags(ViewFlags.TemplateEditing, true)`](xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A)。|
|<xref:System.Web.UI.Design.WebControls.DataGridDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.WebControls.DataGridDesigner.GetTemplateContent%2A>|建议不要使用此方法，因为模板编辑是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 中处理的。 若要支持模板编辑，请在 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> 属性中公开模板数据，并调用 [`ControlDesigner.SetViewFlags(ViewFlags.TemplateEditing, true)`](xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A)。|
|<xref:System.Web.UI.Design.WebControls.DataGridDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.WebControls.DataGridDesigner.GetTemplatePropertyParentType%2A>|建议不要使用此方法，因为模板编辑是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 中处理的。 若要支持模板编辑，请在 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> 属性中公开模板数据，并调用 [`ControlDesigner.SetViewFlags(ViewFlags.TemplateEditing, true)`](xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A)。|
|<xref:System.Web.UI.Design.WebControls.DataGridDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.WebControls.DataGridDesigner.SetTemplateContent%2A>|建议不要使用此方法，因为模板编辑是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 中处理的。 若要支持模板编辑，请在 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> 属性中公开模板数据，并调用 [`ControlDesigner.SetViewFlags(ViewFlags.TemplateEditing, true)`](xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A)。|
|<xref:System.Web.UI.Design.WebControls.DataListDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.WebControls.DataListDesigner.CreateTemplateEditingFrame%2A>|建议不要使用此方法，因为模板编辑是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 中处理的。 若要支持模板编辑，请在 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> 属性中公开模板数据，并调用 [`ControlDesigner.SetViewFlags(ViewFlags.TemplateEditing, true)`](xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A)。|
|<xref:System.Web.UI.Design.WebControls.DataListDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.WebControls.DataListDesigner.GetCachedTemplateEditingVerbs%2A>|建议不要使用此方法，因为模板编辑是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 中处理的。 若要支持模板编辑，请在 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> 属性中公开模板数据，并调用 [`ControlDesigner.SetViewFlags(ViewFlags.TemplateEditing, true)`](xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A)。|
|<xref:System.Web.UI.Design.WebControls.DataListDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.WebControls.DataListDesigner.GetTemplateContainerDataItemProperty%2A>|建议不要使用此方法，因为模板编辑是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 中处理的。 若要支持模板编辑，请在 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> 属性中公开模板数据，并调用 [`ControlDesigner.SetViewFlags(ViewFlags.TemplateEditing, true)`](xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A)。|
|<xref:System.Web.UI.Design.WebControls.DataListDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.WebControls.DataListDesigner.GetTemplateContent%2A>|建议不要使用此方法，因为模板编辑是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 中处理的。 若要支持模板编辑，请在 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> 属性中公开模板数据，并调用 [`ControlDesigner.SetViewFlags(ViewFlags.TemplateEditing, true)`](xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A)。|
|<xref:System.Web.UI.Design.WebControls.DataListDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.WebControls.DataListDesigner.SetTemplateContent%2A>|建议不要使用此方法，因为模板编辑是在 <xref:System.Web.UI.Design.ControlDesigner?displayProperty=nameWithType> 中处理的。 若要支持模板编辑，请在 <xref:System.Web.UI.Design.ControlDesigner.TemplateGroups%2A?displayProperty=nameWithType> 属性中公开模板数据，并调用 [`ControlDesigner.SetViewFlags(ViewFlags.TemplateEditing, true)`](xref:System.Web.UI.Design.ControlDesigner.SetViewFlags%2A)。|
|<xref:System.Web.UI.Design.WebControls.PanelDesigner?displayProperty=nameWithType>|<xref:System.Web.UI.Design.WebControls.PanelDesigner.OnBehaviorAttached%2A>|建议的替代项为 <xref:System.Web.UI.Design.ControlDesigner.Tag%2A?displayProperty=nameWithType>。|
|<xref:System.Windows.Forms.Design.ControlDesigner?displayProperty=nameWithType>|<xref:System.Windows.Forms.Design.ControlDesigner.OnSetComponentDefaults%2A>|此方法已被否决。 请改用 <xref:System.Windows.Forms.Design.ControlDesigner.InitializeNewComponent%2A?displayProperty=nameWithType>。|

<a name="system"></a>

### <a name="assembly-systemdll"></a>程序集：System.dll

|类型|成员|消息|
|----------|------------|-------------|
|<xref:Microsoft.CSharp.CSharpCodeProvider?displayProperty=nameWithType>|<xref:Microsoft.CSharp.CSharpCodeProvider.CreateCompiler%2A>|调用方不应使用 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> 接口，并应改为直接在 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> 类上使用此方法。|
|<xref:Microsoft.CSharp.CSharpCodeProvider?displayProperty=nameWithType>|<xref:Microsoft.CSharp.CSharpCodeProvider.CreateGenerator%2A>|调用方不应使用 <xref:System.CodeDom.Compiler.ICodeGenerator?displayProperty=nameWithType> 接口，并应改为直接在 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> 类上使用此方法。|
|<xref:Microsoft.VisualBasic.VBCodeProvider?displayProperty=nameWithType>|<xref:Microsoft.VisualBasic.VBCodeProvider.CreateCompiler%2A>|调用方不应使用 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> 接口，并应改为直接在 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> 类上使用此方法。|
|<xref:Microsoft.VisualBasic.VBCodeProvider?displayProperty=nameWithType>|<xref:Microsoft.VisualBasic.VBCodeProvider.CreateGenerator%2A>|调用方不应使用 <xref:System.CodeDom.Compiler.ICodeGenerator?displayProperty=nameWithType> 接口，并应改为直接在 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> 类上使用此方法。|
|<xref:Microsoft.Win32.SystemEvents?displayProperty=nameWithType>|<xref:Microsoft.Win32.SystemEvents.LowMemory>|此事件已弃用。|
|<xref:System.Uri?displayProperty=nameWithType>|<xref:System.Uri.Canonicalize%2A>|此方法已弃用。 系统不会使用它。|
|<xref:System.Uri?displayProperty=nameWithType>|<xref:System.Uri.CheckSecurity%2A>|此方法已弃用。 系统不会使用它。|
|<xref:System.Uri?displayProperty=nameWithType>|<xref:System.Uri.Escape%2A>|此方法已弃用。 系统不会使用它。|
|<xref:System.Uri?displayProperty=nameWithType>|<xref:System.Uri.EscapeString%2A>|此方法已弃用。 请使用 <xref:System.Uri.GetComponents%2A> 方法或静态 <xref:System.Uri.EscapeUriString%2A> 方法对 URI 组件或字符串进行转义。|
|<xref:System.Uri?displayProperty=nameWithType>|<xref:System.Uri.IsBadFileSystemCharacter%2A>|此方法已弃用。 系统不会使用它。|
|<xref:System.Uri?displayProperty=nameWithType>|<xref:System.Uri.IsExcludedCharacter%2A>|此方法已弃用。 系统不会使用它。|
|<xref:System.Uri?displayProperty=nameWithType>|<xref:System.Uri.IsReservedCharacter%2A>|此方法已弃用。 系统不会使用它。|
|<xref:System.Uri?displayProperty=nameWithType>|<xref:System.Uri.MakeRelative%2A>|此方法已弃用。 请使用 <xref:System.Uri.MakeRelativeUri%2A?displayProperty=nameWithType>。|
|<xref:System.Uri?displayProperty=nameWithType>|<xref:System.Uri.Parse%2A>|此方法已弃用。 系统不会使用它。|
|<xref:System.Uri?displayProperty=nameWithType>|<xref:System.Uri.Unescape%2A>|此方法已弃用。 请使用 <xref:System.Uri.GetComponents%2A?displayProperty=nameWithType> 方法或静态 <xref:System.Uri.EscapeUriString%2A?displayProperty=nameWithType> 方法对 URI 组件或字符串进行转义。|
|<xref:System.Uri?displayProperty=nameWithType>|<xref:System.Uri.%23ctor%28System.String%2CSystem.Boolean%29>|此构造函数已弃用。 请使用 <xref:System.Uri.%23ctor%28System.String%29>。 `dontEscape` 参数已弃用，并且始终为 `false`。|
|<xref:System.Uri?displayProperty=nameWithType>|<xref:System.Uri.%23ctor%28System.Uri%2CSystem.String%2CSystem.Boolean%29>|此构造函数已弃用。 请使用 <xref:System.Uri.%23ctor%28System.Uri%2CSystem.String%29>。 `dontEscape` 参数已弃用，并且始终为 `false`。|
|<xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>|<xref:System.CodeDom.Compiler.CodeDomProvider.CreateCompiler%2A>|调用方不应使用 <xref:System.CodeDom.Compiler.ICodeCompiler?displayProperty=nameWithType> 接口，并应改为直接在 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> 类上使用此方法。 从 <xref:System.CodeDom.Compiler.CodeDomProvider> 的继承必须还要实现此接口，并应该排除此警告，或淘汰此方法。|
|<xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>|<xref:System.CodeDom.Compiler.CodeDomProvider.CreateGenerator%2A>|调用方不应使用 <xref:System.CodeDom.Compiler.ICodeGenerator?displayProperty=nameWithType> 接口，并应改为直接在 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> 类上使用此方法。 从 <xref:System.CodeDom.Compiler.CodeDomProvider> 的继承必须还要实现此接口，并应该排除此警告，或淘汰此方法。|
|<xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>|<xref:System.CodeDom.Compiler.CodeDomProvider.CreateParser%2A>|调用方不应使用 <xref:System.CodeDom.Compiler.ICodeParser?displayProperty=nameWithType> 接口，并应改为直接在 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> 类上使用此方法。 从 <xref:System.CodeDom.Compiler.CodeDomProvider> 的继承必须还要实现此接口，并应该排除此警告，或淘汰此方法。|
|<xref:System.CodeDom.Compiler.CompilerParameters?displayProperty=nameWithType>|<xref:System.CodeDom.Compiler.CompilerParameters.Evidence%2A>|CAS 策略已过时，并将从 .NET Framework 的未来版本中移除。 有关详细信息，请参阅 [.NET Framework 4 中的安全性更改](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee191568%28v=vs.100%29)。|
|<xref:System.CodeDom.Compiler.CompilerResults?displayProperty=nameWithType>|<xref:System.CodeDom.Compiler.CompilerResults.Evidence%2A>|CAS 策略已过时，并将从 .NET Framework 的未来版本中移除。 有关详细信息，请参阅 [.NET Framework 4 中的安全性更改](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee191568%28v=vs.100%29)。|
|<xref:System.Collections.Specialized.NameObjectCollectionBase?displayProperty=nameWithType>|<xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor%28System.Collections.IHashCodeProvider%2CSystem.Collections.IComparer%29>|请改用 <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor%28System.Collections.IEqualityComparer%29>。|
|<xref:System.Collections.Specialized.NameObjectCollectionBase?displayProperty=nameWithType>|<xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor%28System.Int32%2CSystem.Collections.IHashCodeProvider%2CSystem.Collections.IComparer%29>|请改用 <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor%28System.Int32%2CSystem.Collections.IEqualityComparer%29>。|
|<xref:System.Collections.Specialized.NameValueCollection?displayProperty=nameWithType>|<xref:System.Collections.Specialized.NameValueCollection.%23ctor%28System.Collections.IHashCodeProvider%2CSystem.Collections.IComparer%29>|请改用 <xref:System.Collections.Specialized.NameValueCollection.%23ctor%28System.Collections.IEqualityComparer%29>。|
|<xref:System.Collections.Specialized.NameValueCollection?displayProperty=nameWithType>|<xref:System.Collections.Specialized.NameValueCollection.%23ctor%28System.Int32%2CSystem.Collections.IHashCodeProvider%2CSystem.Collections.IComparer%29>|请改用 <xref:System.Collections.Specialized.NameValueCollection.%23ctor%28System.Int32%2CSystem.Collections.IEqualityComparer%29>。|
|<xref:System.ComponentModel.AsyncCompletedEventArgs?displayProperty=nameWithType>|<xref:System.ComponentModel.AsyncCompletedEventArgs.%23ctor>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 使用此成员会生成编译器错误。<br /><br /> 此 API 支持 .NET Framework 基础结构，但不应在代码中直接使用。|
|<xref:System.ComponentModel.MemberDescriptor?displayProperty=nameWithType>|<xref:System.ComponentModel.MemberDescriptor.GetInvokee%2A>|此方法已被否决。 请改用 <xref:System.ComponentModel.MemberDescriptor.GetInvocationTarget%2A?displayProperty=nameWithType>。|
|<xref:System.ComponentModel.TypeDescriptor?displayProperty=nameWithType>|<xref:System.ComponentModel.TypeDescriptor.ComNativeDescriptorHandler%2A>|此属性已弃用。 改用类型说明提供程序提供 COM 类型的类型信息。|
|<xref:System.ComponentModel.Design.DesignerTransactionCloseEventArgs?displayProperty=nameWithType>|<xref:System.ComponentModel.Design.DesignerTransactionCloseEventArgs.%23ctor%28System.Boolean%29>|此构造函数已过时。 请改用 <xref:System.ComponentModel.Design.DesignerTransactionCloseEventArgs.%23ctor%28System.Boolean%2CSystem.Boolean%29>。|
|<xref:System.ComponentModel.Design.SelectionTypes?displayProperty=nameWithType>|<xref:System.ComponentModel.Design.SelectionTypes.Click>|此值已弃用。 请改用 <xref:System.ComponentModel.Design.SelectionTypes.Primary?displayProperty=nameWithType>。|
|<xref:System.ComponentModel.Design.SelectionTypes?displayProperty=nameWithType>|<xref:System.ComponentModel.Design.SelectionTypes.MouseDown>|此值已弃用。 它不再受支持。|
|<xref:System.ComponentModel.Design.SelectionTypes?displayProperty=nameWithType>|<xref:System.ComponentModel.Design.SelectionTypes.MouseUp>|此值已弃用。 它不再受支持。|
|<xref:System.ComponentModel.Design.SelectionTypes?displayProperty=nameWithType>|<xref:System.ComponentModel.Design.SelectionTypes.Normal>|此值已弃用。 请改用 <xref:System.ComponentModel.Design.SelectionTypes.Auto?displayProperty=nameWithType>。|
|<xref:System.ComponentModel.Design.SelectionTypes?displayProperty=nameWithType>|<xref:System.ComponentModel.Design.SelectionTypes.Valid>|此值已弃用。 使用 <xref:System.Enum?displayProperty=nameWithType> 类方法或类型转换器来确定有效值。|
|<xref:System.ComponentModel.Design.ViewTechnology?displayProperty=nameWithType>|<xref:System.ComponentModel.Design.ViewTechnology.Passthrough>|此值已弃用。 请改用 <xref:System.ComponentModel.Design.ViewTechnology.Default?displayProperty=nameWithType>。|
|<xref:System.ComponentModel.Design.ViewTechnology?displayProperty=nameWithType>|<xref:System.ComponentModel.Design.ViewTechnology.WindowsForms>|此值已弃用。 请改用 <xref:System.ComponentModel.Design.ViewTechnology.Default?displayProperty=nameWithType>。|
|<xref:System.Configuration.ConfigurationException?displayProperty=nameWithType>|<xref:System.Configuration.ConfigurationException.%23ctor>|此类已过时。 若要创建新异常，请创建 <xref:System.Configuration.ConfigurationErrorsException?displayProperty=nameWithType>。|
|<xref:System.Configuration.ConfigurationException?displayProperty=nameWithType>|<xref:System.Configuration.ConfigurationException.%23ctor%28System.String%29>|此类已过时。 若要创建新异常，请创建 <xref:System.Configuration.ConfigurationErrorsException?displayProperty=nameWithType>。|
|<xref:System.Configuration.ConfigurationException?displayProperty=nameWithType>|<xref:System.Configuration.ConfigurationException.%23ctor%28System.String%2CSystem.Exception%29>|此类已过时。 若要创建新异常，请创建 <xref:System.Configuration.ConfigurationErrorsException?displayProperty=nameWithType>。|
|<xref:System.Configuration.ConfigurationException?displayProperty=nameWithType>|<xref:System.Configuration.ConfigurationException.%23ctor%28System.String%2CSystem.Exception%2CSystem.String%2CSystem.Int32%29>|此类已过时。 若要创建新异常，请创建 <xref:System.Configuration.ConfigurationErrorsException?displayProperty=nameWithType>。|
|<xref:System.Configuration.ConfigurationException?displayProperty=nameWithType>|<xref:System.Configuration.ConfigurationException.%23ctor%28System.String%2CSystem.Exception%2CSystem.Xml.XmlNode%29>|此类已过时。 若要创建新异常，请创建 <xref:System.Configuration.ConfigurationErrorsException?displayProperty=nameWithType>。|
|<xref:System.Configuration.ConfigurationException?displayProperty=nameWithType>|<xref:System.Configuration.ConfigurationException.%23ctor%28System.String%2CSystem.String%2CSystem.Int32%29>|此类已过时。 若要创建新异常，请创建 <xref:System.Configuration.ConfigurationErrorsException?displayProperty=nameWithType>。|
|<xref:System.Configuration.ConfigurationException?displayProperty=nameWithType>|<xref:System.Configuration.ConfigurationException.%23ctor%28System.String%2CSystem.Xml.XmlNode%29>|此类已过时。 若要创建新异常，请创建 <xref:System.Configuration.ConfigurationErrorsException?displayProperty=nameWithType>。|
|<xref:System.Configuration.ConfigurationException?displayProperty=nameWithType>|<xref:System.Configuration.ConfigurationException.GetXmlNodeFilename%2A>|此类已过时。 请改用 <xref:System.Configuration.ConfigurationErrorsException.GetFilename%2A?displayProperty=nameWithType>。|
|<xref:System.Configuration.ConfigurationException?displayProperty=nameWithType>|<xref:System.Configuration.ConfigurationException.GetXmlNodeLineNumber%2A>|此类已过时。 请改用 <xref:System.Configuration.ConfigurationErrorsException.GetLineNumber%28System.Xml.XmlNode%29?displayProperty=nameWithType>。|
|<xref:System.Configuration.ConfigurationSettings?displayProperty=nameWithType>|<xref:System.Configuration.ConfigurationSettings.AppSettings%2A>|此方法已过时。 已替换为 <xref:System.Configuration.ConfigurationManager.AppSettings%2A?displayProperty=nameWithType>。|
|<xref:System.Configuration.ConfigurationSettings?displayProperty=nameWithType>|<xref:System.Configuration.ConfigurationSettings.GetConfig%2A>|此方法已过时。 已替换为 <xref:System.Configuration.ConfigurationManager.GetSection%2A?displayProperty=nameWithType>。|
|<xref:System.Diagnostics.EventLog?displayProperty=nameWithType>|<xref:System.Diagnostics.EventLog.CreateEventSource%28System.String%2CSystem.String%2CSystem.String%29>|此方法已被否决。 请改用 <xref:System.Diagnostics.EventLog.CreateEventSource%28System.Diagnostics.EventSourceCreationData%29>。|
|<xref:System.Diagnostics.EventLogEntry?displayProperty=nameWithType>|<xref:System.Diagnostics.EventLogEntry.EventID%2A>|此属性已弃用。 请改用 <xref:System.Diagnostics.EventLogEntry.InstanceId%2A?displayProperty=nameWithType>。|
|<xref:System.Diagnostics.EventLogPermissionAccess?displayProperty=nameWithType>|<xref:System.Diagnostics.EventLogPermissionAccess.Audit>|此成员已弃用。 请改用 <xref:System.Diagnostics.EventLogPermissionAccess.Administer?displayProperty=nameWithType>。|
|<xref:System.Diagnostics.EventLogPermissionAccess?displayProperty=nameWithType>|<xref:System.Diagnostics.EventLogPermissionAccess.Browse>|此成员已弃用。 请改用 <xref:System.Diagnostics.EventLogPermissionAccess.Administer?displayProperty=nameWithType>。|
|<xref:System.Diagnostics.EventLogPermissionAccess?displayProperty=nameWithType>|<xref:System.Diagnostics.EventLogPermissionAccess.Instrument>|此成员已弃用。 请改用 <xref:System.Diagnostics.EventLogPermissionAccess.Write?displayProperty=nameWithType>。|
|<xref:System.Diagnostics.InstanceDataCollection?displayProperty=nameWithType>|<xref:System.Diagnostics.InstanceDataCollection.%23ctor%2A>|此构造函数已弃用。 请改用 <xref:System.Diagnostics.InstanceDataCollectionCollection.Item%2A?displayProperty=nameWithType> 来获取此集合的实例。|
|<xref:System.Diagnostics.InstanceDataCollectionCollection?displayProperty=nameWithType>|<xref:System.Diagnostics.InstanceDataCollectionCollection.%23ctor%2A>|此构造函数已弃用。 请改用 <xref:System.Diagnostics.PerformanceCounterCategory.ReadCategory%2A?displayProperty=nameWithType> 来获取此集合的实例。|
|<xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType>|<xref:System.Diagnostics.PerformanceCounter.DefaultFileMappingSize>|此字段已弃用，系统不会使用它。 使用 machine.config 或应用程序配置文件设置 <xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType> 文件映射的大小。|
|<xref:System.Diagnostics.PerformanceCounterCategory?displayProperty=nameWithType>|<xref:System.Diagnostics.PerformanceCounterCategory.Create%28System.String%2CSystem.String%2CSystem.Diagnostics.CounterCreationDataCollection%29>|此方法已被否决。 请改用 <xref:System.Diagnostics.PerformanceCounterCategory.Create%28System.String%2CSystem.String%2CSystem.Diagnostics.PerformanceCounterCategoryType%2CSystem.Diagnostics.CounterCreationDataCollection%29>。|
|<xref:System.Diagnostics.PerformanceCounterCategory?displayProperty=nameWithType>|<xref:System.Diagnostics.PerformanceCounterCategory.Create%28System.String%2CSystem.String%2CSystem.String%2CSystem.String%29>|此方法已被否决。 请改用 <xref:System.Diagnostics.PerformanceCounterCategory.Create%28System.String%2CSystem.String%2CSystem.Diagnostics.PerformanceCounterCategoryType%2CSystem.String%2CSystem.String%29>。|
|<xref:System.Diagnostics.PerformanceCounterManager?displayProperty=nameWithType>|<xref:System.Diagnostics.PerformanceCounterManager.System%23Diagnostics%23ICollectData%23CloseData%2A>|此类已弃用。 改为通过 <xref:System.Diagnostics.PerformanceCounter> 类使用性能计数器。|
|<xref:System.Diagnostics.PerformanceCounterManager?displayProperty=nameWithType>|<xref:System.Diagnostics.PerformanceCounterManager.System%23Diagnostics%23ICollectData%23CollectData%2A>|此类已弃用。 改为通过 <xref:System.Diagnostics.PerformanceCounter> 类使用性能计数器。|
|<xref:System.Diagnostics.PerformanceCounterManager?displayProperty=nameWithType>|<xref:System.Diagnostics.PerformanceCounterManager.%23ctor%2A>|此类已弃用。 改为通过 <xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType> 类使用性能计数器。|
|<xref:System.Diagnostics.PerformanceCounterPermissionAccess?displayProperty=nameWithType>|<xref:System.Diagnostics.PerformanceCounterPermissionAccess.Browse>|此成员已弃用。 请改用 <xref:System.Diagnostics.PerformanceCounterPermissionAccess.Read?displayProperty=nameWithType>。|
|<xref:System.Diagnostics.PerformanceCounterPermissionAccess?displayProperty=nameWithType>|<xref:System.Diagnostics.PerformanceCounterPermissionAccess.Instrument>|此成员已弃用。 请改用 <xref:System.Diagnostics.PerformanceCounterPermissionAccess.Write?displayProperty=nameWithType>。|
|<xref:System.Diagnostics.Process?displayProperty=nameWithType>|<xref:System.Diagnostics.Process.NonpagedSystemMemorySize%2A>|此属性已弃用。 请改用 <xref:System.Diagnostics.Process.NonpagedSystemMemorySize64%2A?displayProperty=nameWithType>。|
|<xref:System.Diagnostics.Process?displayProperty=nameWithType>|<xref:System.Diagnostics.Process.PagedMemorySize%2A>|此属性已弃用。 请改用 <xref:System.Diagnostics.Process.PagedMemorySize64%2A>。|
|<xref:System.Diagnostics.Process?displayProperty=nameWithType>|<xref:System.Diagnostics.Process.PagedSystemMemorySize%2A>|此属性已弃用。 请改用 <xref:System.Diagnostics.Process.PagedSystemMemorySize64%2A?displayProperty=nameWithType>。|
|<xref:System.Diagnostics.Process?displayProperty=nameWithType>|<xref:System.Diagnostics.Process.PeakPagedMemorySize%2A>|此属性已弃用。 请改用 <xref:System.Diagnostics.Process.PeakPagedMemorySize64%2A?displayProperty=nameWithType>。|
|<xref:System.Diagnostics.Process?displayProperty=nameWithType>|<xref:System.Diagnostics.Process.PeakVirtualMemorySize%2A>|此属性已弃用。 请改用 <xref:System.Diagnostics.Process.PeakVirtualMemorySize64%2A?displayProperty=nameWithType>。|
|<xref:System.Diagnostics.Process?displayProperty=nameWithType>|<xref:System.Diagnostics.Process.PeakWorkingSet%2A>|此属性已弃用。 请改用 <xref:System.Diagnostics.Process.PeakWorkingSet64%2A?displayProperty=nameWithType>。|
|<xref:System.Diagnostics.Process?displayProperty=nameWithType>|<xref:System.Diagnostics.Process.PrivateMemorySize%2A>|此属性已弃用。 请改用 <xref:System.Diagnostics.Process.PrivateMemorySize64%2A?displayProperty=nameWithType>。|
|<xref:System.Diagnostics.Process?displayProperty=nameWithType>|<xref:System.Diagnostics.Process.VirtualMemorySize%2A>|此属性已弃用。 请改用 <xref:System.Diagnostics.Process.VirtualMemorySize64%2A?displayProperty=nameWithType>。|
|<xref:System.Diagnostics.Process?displayProperty=nameWithType>|<xref:System.Diagnostics.Process.WorkingSet%2A>|此属性已弃用。 请改用 <xref:System.Diagnostics.Process.WorkingSet64%2A?displayProperty=nameWithType>。|
|<xref:System.Net.Dns?displayProperty=nameWithType>|<xref:System.Net.Dns.BeginGetHostByName%2A>|<xref:System.Net.Dns.BeginGetHostByName%2A> 对于此类型已过时，请改用 <xref:System.Net.Dns.BeginGetHostEntry%28System.String%2CSystem.AsyncCallback%2CSystem.Object%29?displayProperty=nameWithType>。|
|<xref:System.Net.Dns?displayProperty=nameWithType>|<xref:System.Net.Dns.BeginResolve%28System.String%2CSystem.AsyncCallback%2CSystem.Object%29>|<xref:System.Net.Dns.BeginResolve%28System.String%2CSystem.AsyncCallback%2CSystem.Object%29> 对于此类型已过时，请改用 <xref:System.Net.Dns.BeginGetHostEntry%28System.String%2CSystem.AsyncCallback%2CSystem.Object%29?displayProperty=nameWithType>。|
|<xref:System.Net.Dns?displayProperty=nameWithType>|<xref:System.Net.Dns.EndGetHostByName%2A>|<xref:System.Net.Dns.EndGetHostByName%2A> 对于此类型已过时，请改用 <xref:System.Net.Dns.EndGetHostEntry%2A?displayProperty=nameWithType>。|
|<xref:System.Net.Dns?displayProperty=nameWithType>|<xref:System.Net.Dns.EndResolve%2A>|<xref:System.Net.Dns.EndResolve%2A> 对于此类型已过时，请改用 <xref:System.Net.Dns.EndGetHostEntry%2A?displayProperty=nameWithType>。|
|<xref:System.Net.Dns?displayProperty=nameWithType>|<xref:System.Net.Dns.GetHostByAddress%28System.Net.IPAddress%29>|<xref:System.Net.Dns.GetHostByAddress%28System.Net.IPAddress%29> 对于此类型已过时，请改用 <xref:System.Net.Dns.GetHostEntry%28System.Net.IPAddress%29?displayProperty=nameWithType>。|
|<xref:System.Net.Dns?displayProperty=nameWithType>|<xref:System.Net.Dns.GetHostByAddress%28System.String%29>|<xref:System.Net.Dns.GetHostByAddress%28System.String%29> 对于此类型已过时，请改用 <xref:System.Net.Dns.GetHostEntry%28System.String%29?displayProperty=nameWithType>。|
|<xref:System.Net.Dns?displayProperty=nameWithType>|<xref:System.Net.Dns.GetHostByName%2A>|<xref:System.Net.Dns.GetHostByName%2A> 对于此类型已过时，请改用 <xref:System.Net.Dns.GetHostEntry%28System.String%29?displayProperty=nameWithType>。|
|<xref:System.Net.Dns?displayProperty=nameWithType>|<xref:System.Net.Dns.Resolve%2A>|<xref:System.Net.Dns.Resolve%2A> 对于此类型已过时，请改用 <xref:System.Net.Dns.GetHostEntry%28System.String%29?displayProperty=nameWithType>。|
|<xref:System.Net.FileWebRequest?displayProperty=nameWithType>|<xref:System.Net.FileWebRequest.%23ctor%2A>|序列化对于此类型已过时。|
|<xref:System.Net.FileWebResponse?displayProperty=nameWithType>|<xref:System.Net.FileWebResponse.%23ctor%2A>|序列化对于此类型已过时。|
|<xref:System.Net.HttpWebRequest?displayProperty=nameWithType>|<xref:System.Net.HttpWebRequest.%23ctor>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 使用此成员会生成编译器错误。<br /><br /> 此 API 支持 .NET Framework 基础结构，但不应在代码中直接使用。|
|<xref:System.Net.HttpWebRequest?displayProperty=nameWithType>|<xref:System.Net.HttpWebRequest.%23ctor%28System.Runtime.Serialization.SerializationInfo%2CSystem.Runtime.Serialization.StreamingContext%29>|序列化对于此类型已过时。|
|<xref:System.Net.HttpWebResponse?displayProperty=nameWithType>|<xref:System.Net.HttpWebResponse.%23ctor>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 使用此成员会生成编译器错误。<br /><br /> 此 API 支持 .NET Framework 基础结构，但不应在代码中直接使用。|
|<xref:System.Net.HttpWebResponse?displayProperty=nameWithType>|<xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)>|序列化对于此类型已过时。|
|<xref:System.Net.IPAddress?displayProperty=nameWithType>|<xref:System.Net.IPAddress.Address%2A>|此属性已弃用。 它依赖于地址族。 请改用 <xref:System.Net.IPAddress.Equals%2A?displayProperty=nameWithType> 方法来执行比较。|
|<xref:System.Net.ServicePointManager?displayProperty=nameWithType>|<xref:System.Net.ServicePointManager.CertificatePolicy%2A>|<xref:System.Net.ServicePointManager.CertificatePolicy%2A> 对于此类型已过时。 请改用 <xref:System.Net.ServicePointManager.ServerCertificateValidationCallback%2A?displayProperty=nameWithType>。|
|<xref:System.Net.WebClient?displayProperty=nameWithType>|<xref:System.Net.WebClient.AllowReadStreamBuffering%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 使用此成员会生成编译器错误。<br /><br /> 此 API 支持 .NET Framework 基础结构，但不应在代码中直接使用。|
|<xref:System.Net.WebClient?displayProperty=nameWithType>|<xref:System.Net.WebClient.AllowWriteStreamBuffering%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 使用此成员会生成编译器错误。<br /><br /> 此 API 支持 .NET Framework 基础结构，但不应在代码中直接使用。|
|<xref:System.Net.WebClient?displayProperty=nameWithType>|<xref:System.Net.WebClient.OnWriteStreamClosed%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 使用此成员会生成编译器错误。<br /><br /> 此 API 支持 .NET Framework 基础结构，但不应在代码中直接使用。|
|<xref:System.Net.WebClient?displayProperty=nameWithType>|<xref:System.Net.WebClient.WriteStreamClosed>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 使用此成员会生成编译器错误。<br /><br /> 此 API 支持 .NET Framework 基础结构，但不应在代码中直接使用。|
|<xref:System.Net.WebProxy?displayProperty=nameWithType>|<xref:System.Net.WebProxy.GetDefaultProxy%2A>|此方法已被否决。 请使用默认为你选择的代理。|
|<xref:System.Net.WebRequest?displayProperty=nameWithType>|<xref:System.Net.WebRequest.CreatorInstance%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 使用此成员会生成编译器错误。<br /><br /> 此 API 支持 .NET Framework 基础结构，但不应在代码中直接使用。|
|<xref:System.Net.WebRequest?displayProperty=nameWithType>|<xref:System.Net.WebRequest.RegisterPortableWebRequestCreator%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 使用此成员会生成编译器错误。<br /><br /> 此 API 支持 .NET Framework 基础结构，但不应在代码中直接使用。|
|<xref:System.Net.WriteStreamClosedEventArgs?displayProperty=nameWithType>|<xref:System.Net.WriteStreamClosedEventArgs.Error%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 使用此成员会生成编译器错误。<br /><br /> 此 API 支持 .NET Framework 基础结构，但不应在代码中直接使用。|
|<xref:System.Net.WriteStreamClosedEventArgs?displayProperty=nameWithType>|<xref:System.Net.WriteStreamClosedEventArgs.%23ctor%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 使用此成员会生成编译器错误。<br /><br /> 此 API 支持 .NET Framework 基础结构，但不应在代码中直接使用。|
|<xref:System.Net.Mail.MailMessage?displayProperty=nameWithType>|<xref:System.Net.Mail.MailMessage.ReplyTo%2A>|<xref:System.Net.Mail.MailMessage.ReplyTo%2A> 对于此类型已过时。 请改用可接受多个地址的 <xref:System.Net.Mail.MailMessage.ReplyToList%2A?displayProperty=nameWithType>。|
|<xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType>|<xref:System.Net.NetworkInformation.NetworkChange.%23ctor>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 使用此成员会生成编译器错误。<br /><br /> 此 API 支持 .NET Framework 基础结构，但不应在代码中直接使用。|
|<xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType>|<xref:System.Net.NetworkInformation.NetworkChange.RegisterNetworkChange%28System.Net.NetworkInformation.NetworkChange%29>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 使用此成员会生成编译器错误。<br /><br /> 此 API 支持 .NET Framework 基础结构，但不应在代码中直接使用。|
|<xref:System.Net.Sockets.Socket?displayProperty=nameWithType>|<xref:System.Net.Sockets.Socket.SupportsIPv4%2A>|<xref:System.Net.Sockets.Socket.SupportsIPv4%2A> 对于此类型已过时。 请改用 <xref:System.Net.Sockets.Socket.OSSupportsIPv4%2A?displayProperty=nameWithType>。|
|<xref:System.Net.Sockets.Socket?displayProperty=nameWithType>|<xref:System.Net.Sockets.Socket.SupportsIPv6%2A>|<xref:System.Net.Sockets.Socket.SupportsIPv6%2A> 对于此类型已过时。 请改用 <xref:System.Net.Sockets.Socket.OSSupportsIPv6%2A?displayProperty=nameWithType>。|
|<xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType>|<xref:System.Net.Sockets.SocketAsyncEventArgs.SocketClientAccessPolicyProtocol>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 使用此成员会生成编译器错误。<br /><br /> 此 API 支持 .NET Framework 基础结构，但不应在代码中直接使用。|
|<xref:System.Net.Sockets.TcpListener?displayProperty=nameWithType>|<xref:System.Net.Sockets.TcpListener.%23ctor%28System.Int32%29>|此方法已被否决。 请改用 <xref:System.Net.Sockets.TcpListener.%23ctor%28System.Net.IPAddress%2CSystem.Int32%29>。|
|<xref:System.Net.WebSockets.WebSocket?displayProperty=nameWithType>|<xref:System.Net.WebSockets.WebSocket.IsApplicationTargeting45%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 此成员仅供内部使用，并将从 .NET Framework 的未来版本中移除。 请勿调用它。|
|<xref:System.Security.Claims.DynamicRoleClaimProvider?displayProperty=nameWithType>|<xref:System.Security.Claims.DynamicRoleClaimProvider.AddDynamicRoleClaims%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 使用此成员会生成编译器错误。<br /><br /> 使用 <xref:System.Security.Claims.ClaimsAuthenticationManager?displayProperty=nameWithType> 向 <xref:System.Security.Claims.ClaimsIdentity> 添加声明。|

<a name="drawing"></a>

### <a name="assembly-systemdrawingdll"></a>程序集：System.Drawing.dll

|类型|成员|消息|
|----------|------------|-------------|
|<xref:System.Drawing.FontFamily?displayProperty=nameWithType>|<xref:System.Drawing.FontFamily.GetFamilies%2A>|请勿使用 <xref:System.Drawing.FontFamily.GetFamilies%2A> 方法；请改用 <xref:System.Drawing.FontFamily.Families%2A?displayProperty=nameWithType> 属性。|
|<xref:System.Drawing.Imaging.EncoderParameter?displayProperty=nameWithType>|<xref:System.Drawing.Imaging.EncoderParameter.%23ctor%28System.Drawing.Imaging.Encoder%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 此构造函数已弃用。 请使用 <xref:System.Drawing.Imaging.EncoderParameter.%23ctor%28System.Drawing.Imaging.Encoder%2CSystem.Int32%2CSystem.Drawing.Imaging.EncoderParameterValueType%2CSystem.IntPtr%29>。|

<a name="messaging"></a>

### <a name="assembly-systemmessagingdll"></a>程序集：System.Messaging.dll

|类型|成员|消息|
|----------|------------|-------------|
|<xref:System.Messaging.MessageQueue?displayProperty=nameWithType>|<xref:System.Messaging.MessageQueue.GetEnumerator%2A>|此方法以错误方式返回实现 <xref:System.Messaging.MessageEnumerator.RemoveCurrent%2A?displayProperty=nameWithType> 方法系列的 <xref:System.Messaging.MessageEnumerator?displayProperty=nameWithType>。 请改用 <xref:System.Messaging.MessageQueue.GetMessageEnumerator2%2A?displayProperty=nameWithType>。|
|<xref:System.Messaging.MessageQueue?displayProperty=nameWithType>|<xref:System.Messaging.MessageQueue.GetMessageEnumerator%2A>|此方法以错误方式返回实现 <xref:System.Messaging.MessageEnumerator.RemoveCurrent%2A?displayProperty=nameWithType> 方法系列的 <xref:System.Messaging.MessageEnumerator?displayProperty=nameWithType>。 请改用 <xref:System.Messaging.MessageQueue.GetMessageEnumerator2%2A?displayProperty=nameWithType>。|

<a name="servicemodel"></a>

### <a name="assembly-systemservicemodeldll"></a>程序集：System.ServiceModel.dll

|类型|成员|消息|
|----------|------------|-------------|
|<xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>|<xref:System.ServiceModel.BasicHttpBinding.EnableHttpCookieContainer%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 此属性已过时。 要启用 Http <xref:System.Net.CookieContainer>，请改用 <xref:System.ServiceModel.HttpBindingBase.AllowCookies%2A?displayProperty=nameWithType> 属性。|
|<xref:System.ServiceModel.Configuration.BindingsSection?displayProperty=nameWithType>|<xref:System.ServiceModel.Configuration.BindingsSection.NetPeerTcpBinding%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 对等通道功能已过时，并将在以后删除。|
|<xref:System.ServiceModel.Dispatcher.ClientOperationCompatBase?displayProperty=nameWithType>|<xref:System.ServiceModel.Dispatcher.ClientOperationCompatBase.ParameterInspectors%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 使用此类型会生成编译器错误。<br /><br /> 此 API 支持 .NET Framework 基础结构，但不应在代码中直接使用。|
|<xref:System.ServiceModel.Dispatcher.ClientRuntimeCompatBase?displayProperty=nameWithType>|<xref:System.ServiceModel.Dispatcher.ClientRuntimeCompatBase.MessageInspectors%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 使用此类型会生成编译器错误。<br /><br /> 此 API 支持 .NET Framework 基础结构，但不应在代码中直接使用。|
|<xref:System.ServiceModel.Dispatcher.ClientRuntimeCompatBase?displayProperty=nameWithType>|<xref:System.ServiceModel.Dispatcher.ClientRuntimeCompatBase.Operations%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 使用此类型会生成编译器错误。<br /><br /> 此 API 支持 .NET Framework 基础结构，但不应在代码中直接使用。|
|<xref:System.ServiceModel.Security.WindowsClientCredential?displayProperty=nameWithType>|<xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A>|此属性已弃用，并且仅为向后兼容性而维护。 本地计算机策略将用于确定是否应使用 NTLM。|

<a name="smDisc"></a>

### <a name="assembly-systemservicemodeldiscoverydll"></a>程序集：System.ServiceModel.Discovery.dll

|类型|成员|消息|
|----------|------------|-------------|
|<xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint?displayProperty=nameWithType>|<xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint.TransportSettings%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint.TransportSettings%2A> 属性已过时。 请考虑使用 <xref:System.ServiceModel.Channels.UdpTransportBindingElement?displayProperty=nameWithType> 来设置传输属性。|
|<xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint?displayProperty=nameWithType>|<xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.TransportSettings%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint.TransportSettings%2A> 属性已过时。 请考虑使用 <xref:System.ServiceModel.Channels.UdpTransportBindingElement?displayProperty=nameWithType> 来设置传输属性。|

<a name="datavisualization"></a>

### <a name="assembly-systemwebdatavisualizationdll"></a>程序集：System.Web.DataVisualization.dll

|类型|成员|消息|
|----------|------------|-------------|
|<xref:System.Web.UI.DataVisualization.Charting.Chart?displayProperty=nameWithType>|<xref:System.Web.UI.DataVisualization.Charting.Chart.ViewStateData%2A>|<xref:System.Web.UI.DataVisualization.Charting.Chart.ViewStateData%2A> 已弃用。 请改为调查 <xref:System.Web.UI.Control.ViewState%2A?displayProperty=nameWithType>。|

<a name="web"></a>

### <a name="assembly-systemwebdll"></a>程序集：System.Web.dll

|类型|成员|消息|
|----------|------------|-------------|
|<xref:System.Web.HttpContext?displayProperty=nameWithType>|<xref:System.Web.HttpContext.GetAppConfig%2A>|建议的替代项为 System.Web.dll 中的 <xref:System.Web.Configuration.WebConfigurationManager.GetWebApplicationSection%2A?displayProperty=nameWithType>。|
|<xref:System.Web.HttpContext?displayProperty=nameWithType>|<xref:System.Web.HttpContext.GetConfig%2A>|建议的替代项为 System.Web.dll 中的 <xref:System.Web.HttpContext.GetSection%2A?displayProperty=nameWithType>。|
|<xref:System.Web.HttpUtility?displayProperty=nameWithType>|<xref:System.Web.HttpUtility.UrlEncodeUnicode%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 此方法生成的输出不\-符合\-标准，并存在互操作性问题。 首选替代项为 <xref:System.Web.HttpUtility.UrlEncode%28System.String%29>。|
|<xref:System.Web.HttpUtility?displayProperty=nameWithType>|<xref:System.Web.HttpUtility.UrlEncodeUnicodeToBytes%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 此方法生成的输出不\-符合\-标准，并存在互操作性问题。 首选替代项为 <xref:System.Web.HttpUtility.UrlEncodeToBytes%28System.String%29>。|
|<xref:System.Web.Configuration.AuthenticationMode?displayProperty=nameWithType>|<xref:System.Web.Configuration.AuthenticationMode.Passport>|此字段已过时。 Passport 身份验证产品不再受支持，并且已由 [Microsoft 帐户](https://go.microsoft.com/fwlink/?LinkId=733413)取代。|
|<xref:System.Web.Configuration.AuthenticationSection?displayProperty=nameWithType>|<xref:System.Web.Configuration.AuthenticationSection.Passport%2A>|此属性已过时。 Passport 身份验证产品不再受支持，并且已由 [Microsoft 帐户](https://go.microsoft.com/fwlink/?LinkId=733413)取代。|
|<xref:System.Web.Configuration.HttpCapabilitiesBase?displayProperty=nameWithType>|<xref:System.Web.Configuration.HttpCapabilitiesBase.JavaScript%2A>|建议的替代项为 <xref:System.Web.Configuration.HttpCapabilitiesBase.EcmaScriptVersion%2A?displayProperty=nameWithType> 属性。 <xref:System.Version.Major%2A?displayProperty=nameWithType> 版本值大于或等于 1 暗示支持 JavaScript。|
|<xref:System.Web.Configuration.SystemWebSectionGroup?displayProperty=nameWithType>|<xref:System.Web.Configuration.SystemWebSectionGroup.MobileControls%2A>|System.Web.Mobile.dll 已过时。|
|<xref:System.Web.Routing.UrlRoutingModule?displayProperty=nameWithType>|<xref:System.Web.Routing.UrlRoutingModule.PostMapRequestHandler%2A>|此方法已过时。 重写 <xref:System.Web.Routing.UrlRoutingModule.Init%2A> 方法以使用 <xref:System.Web.Routing.UrlRoutingModule.PostMapRequestHandler%2A> 事件。|
|<xref:System.Web.Security.FormsAuthentication?displayProperty=nameWithType>|<xref:System.Web.Security.FormsAuthentication.Authenticate%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 建议的替代项为使用 <xref:System.Web.Security.Membership?displayProperty=nameWithType> API，例如 <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType>。|
|<xref:System.Web.Security.FormsAuthentication?displayProperty=nameWithType>|<xref:System.Web.Security.FormsAuthentication.HashPasswordForStoringInConfigFile%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 建议的替代项为使用 <xref:System.Web.Security.Membership?displayProperty=nameWithType> API，例如 <xref:System.Web.Security.Membership.CreateUser%2A?displayProperty=nameWithType>。|
|<xref:System.Web.Security.MachineKey?displayProperty=nameWithType>|<xref:System.Web.Security.MachineKey.Decode%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 此方法已过时，仅提供它以便与现有代码兼容。 建议新代码改用 <xref:System.Web.Security.MachineKey.Protect%2A> 和 <xref:System.Web.Security.MachineKey.Unprotect%2A> 方法。|
|<xref:System.Web.Security.MachineKey?displayProperty=nameWithType>|<xref:System.Web.Security.MachineKey.Encode%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 此方法已过时，仅提供它以便与现有代码兼容。 建议新代码改用 <xref:System.Web.Security.MachineKey.Protect%2A> 和 <xref:System.Web.Security.MachineKey.Unprotect%2A> 方法。|
|<xref:System.Web.UI.Page?displayProperty=nameWithType>|<xref:System.Web.UI.Page.FileDependencies%2A>|建议的替代项为 <xref:System.Web.HttpResponse.AddFileDependencies%2A?displayProperty=nameWithType>。|
|<xref:System.Web.UI.Page?displayProperty=nameWithType>|<xref:System.Web.UI.Page.GetPostBackClientEvent%2A>|建议的替代项为 <xref:System.Web.UI.ClientScriptManager.GetPostBackEventReference%2A?displayProperty=nameWithType>。|
|<xref:System.Web.UI.Page?displayProperty=nameWithType>|<xref:System.Web.UI.Page.GetPostBackClientHyperlink%2A>|建议的替代项为 <xref:System.Web.UI.ClientScriptManager.GetPostBackClientHyperlink%2A?displayProperty=nameWithType>。|
|<xref:System.Web.UI.Page?displayProperty=nameWithType>|<xref:System.Web.UI.Page.GetPostBackEventReference%28System.Web.UI.Control%29>|建议的替代项为 <xref:System.Web.UI.ClientScriptManager.GetPostBackEventReference%28System.Web.UI.Control%2CSystem.String%29?displayProperty=nameWithType>。|
|<xref:System.Web.UI.Page?displayProperty=nameWithType>|<xref:System.Web.UI.Page.GetPostBackEventReference%28System.Web.UI.Control%2CSystem.String%29>|建议的替代项为 <xref:System.Web.UI.ClientScriptManager.GetPostBackEventReference%2A?displayProperty=nameWithType>。|
|<xref:System.Web.UI.Page?displayProperty=nameWithType>|<xref:System.Web.UI.Page.IsClientScriptBlockRegistered%2A>|建议的替代项为 <xref:System.Web.UI.ClientScriptManager.IsClientScriptBlockRegistered%2A?displayProperty=nameWithType>。|
|<xref:System.Web.UI.Page?displayProperty=nameWithType>|<xref:System.Web.UI.Page.IsStartupScriptRegistered%2A>|建议的替代项为 <xref:System.Web.UI.ClientScriptManager.IsStartupScriptRegistered%2A?displayProperty=nameWithType>。|
|<xref:System.Web.UI.Page?displayProperty=nameWithType>|<xref:System.Web.UI.Page.RegisterArrayDeclaration%2A>|建议的替代项为 <xref:System.Web.UI.ClientScriptManager.RegisterArrayDeclaration%2A?displayProperty=nameWithType>。|
|<xref:System.Web.UI.Page?displayProperty=nameWithType>|<xref:System.Web.UI.Page.RegisterClientScriptBlock%2A>|建议的替代项为 <xref:System.Web.UI.ClientScriptManager.RegisterClientScriptBlock%2A?displayProperty=nameWithType>。|
|<xref:System.Web.UI.Page?displayProperty=nameWithType>|<xref:System.Web.UI.Page.RegisterHiddenField%2A>|建议的替代项为 <xref:System.Web.UI.ClientScriptManager.RegisterHiddenField%2A?displayProperty=nameWithType>。|
|<xref:System.Web.UI.Page?displayProperty=nameWithType>|<xref:System.Web.UI.Page.RegisterOnSubmitStatement%2A>|建议的替代项为 <xref:System.Web.UI.ClientScriptManager.RegisterOnSubmitStatement%2A?displayProperty=nameWithType>。|
|<xref:System.Web.UI.Page?displayProperty=nameWithType>|<xref:System.Web.UI.Page.RegisterStartupScript%2A>|建议的替代项为 <xref:System.Web.UI.ClientScriptManager.RegisterStartupScript%2A?displayProperty=nameWithType>。|
|<xref:System.Web.UI.Page?displayProperty=nameWithType>|<xref:System.Web.UI.Page.SmartNavigation%2A>|建议的替代项为 <xref:System.Web.UI.Page.SetFocus%2A?displayProperty=nameWithType> 和 <xref:System.Web.UI.Page.MaintainScrollPositionOnPostBack%2A?displayProperty=nameWithType>。|
|<xref:System.Web.UI.TemplateControl?displayProperty=nameWithType>|<xref:System.Web.UI.TemplateControl.AutoHandlers%2A>|由于该属性已不再有用，建议不要使用此属性。|
|<xref:System.Web.UI.WebControls.GridView?displayProperty=nameWithType>|<xref:System.Web.UI.WebControls.GridView.CreateAutoGeneratedColumn%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 此方法将保留向后兼容性。 此 API 不再使用。|
|<xref:System.Web.UI.WebControls.Xml?displayProperty=nameWithType>|<xref:System.Web.UI.WebControls.Xml.Document%2A>|建议的替代项为 <xref:System.Web.UI.WebControls.Xml.XPathNavigator%2A?displayProperty=nameWithType> 属性。 创建一个 <xref:System.Xml.XPath.XPathDocument?displayProperty=nameWithType> 并调用 <xref:System.Xml.XPath.XPathDocument.CreateNavigator%2A?displayProperty=nameWithType> 来来创建一个 <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>。|

<a name="dynamicdata"></a>

### <a name="assembly-systemwebdynamicdatadll"></a>程序集：System.Web.DynamicData.dll

|类型|成员|消息|
|----------|------------|-------------|
|<xref:System.Web.DynamicData.DynamicDataExtensions?displayProperty=nameWithType>|<xref:System.Web.DynamicData.DynamicDataExtensions.EnablePersistedSelection%2A>|在数据绑定控件（如 <xref:System.Web.UI.WebControls.GridView?displayProperty=nameWithType> 或 <xref:System.Web.UI.WebControls.ListView?displayProperty=nameWithType>）上使用 `EnablePersistedSelection` 属性。|

<a name="extensions"></a>

### <a name="assembly-systemwebextensionsdll"></a>程序集：System.Web.Extensions.dll

|类型|成员|消息|
|----------|------------|-------------|
|<xref:System.Web.UI.CompositeScriptReference?displayProperty=nameWithType>|<xref:System.Web.UI.CompositeScriptReference.IsFromSystemWebExtensions%2A>|请使用 <xref:System.Web.UI.CompositeScriptReference.IsAjaxFrameworkScript%2A?displayProperty=nameWithType>。|
|<xref:System.Web.UI.ScriptManager?displayProperty=nameWithType>|<xref:System.Web.UI.ScriptManager.ScriptPath%2A>|此属性已过时。 改为对每个 <xref:System.Web.UI.ScriptReference?displayProperty=nameWithType> 设置 [`System.Web.UI.ScriptReference.Path`](xref:System.Web.UI.ScriptReferenceBase.Path%2A) 属性。|
|<xref:System.Web.UI.ScriptReference?displayProperty=nameWithType>|<xref:System.Web.UI.ScriptReference.IgnoreScriptPath%2A>|此属性已过时。 不使用 <xref:System.Web.UI.ScriptManager.ScriptPath%2A?displayProperty=nameWithType>，改为对每个 <xref:System.Web.UI.ScriptReference?displayProperty=nameWithType> 设置 [`System.Web.UI.ScriptReference.Path`](xref:System.Web.UI.ScriptReferenceBase.Path%2A) 属性。|
|<xref:System.Web.UI.ScriptReference?displayProperty=nameWithType>|<xref:System.Web.UI.ScriptReference.IsFromSystemWebExtensions%2A>|请使用 <xref:System.Web.UI.ScriptReference.IsAjaxFrameworkScript%2A?displayProperty=nameWithType>。|
|<xref:System.Web.UI.ScriptReferenceBase?displayProperty=nameWithType>|<xref:System.Web.UI.ScriptReferenceBase.IsFromSystemWebExtensions%2A>|请使用 <xref:System.Web.UI.ScriptReferenceBase.IsAjaxFrameworkScript%2A?displayProperty=nameWithType>。|
|<xref:System.Web.UI.ScriptReferenceBase?displayProperty=nameWithType>|<xref:System.Web.UI.ScriptReferenceBase.NotifyScriptLoaded%2A>|脚本引用不再需要 <xref:System.Web.UI.ScriptReferenceBase.NotifyScriptLoaded%2A>。|
|<xref:System.Web.UI.ScriptResourceAttribute?displayProperty=nameWithType>|<xref:System.Web.UI.ScriptResourceAttribute.ScriptResourceName%2A>|此属性已过时。 请改用 <xref:System.Web.UI.ScriptResourceAttribute.StringResourceName%2A?displayProperty=nameWithType>。|
|<xref:System.Web.UI.ScriptResourceAttribute?displayProperty=nameWithType>|<xref:System.Web.UI.ScriptResourceAttribute.TypeName%2A>|此属性已过时。 请改用 <xref:System.Web.UI.ScriptResourceAttribute.StringResourceClientTypeName%2A?displayProperty=nameWithType>。|

<a name="services"></a>

### <a name="assembly-systemwebservicesdll"></a>程序集：System.Web.Services.dll

|类型|成员|消息|
|----------|------------|-------------|
|<xref:System.Web.Services.Discovery.DiscoveryClientProtocol?displayProperty=nameWithType>|<xref:System.Web.Services.Discovery.DiscoveryClientProtocol.LoadExternals%2A>|此方法将从未来版本中移除。 资源发现不再需要方法调用。|
|<xref:System.Web.Services.Protocols.SoapHeaderAttribute?displayProperty=nameWithType>|<xref:System.Web.Services.Protocols.SoapHeaderAttribute.Required%2A>|此属性将从未来版本中移除。 将不再强制要求在 SOAP 消息中显示特定标头。|

<a name="forms"></a>

### <a name="assembly-systemwindowsformsdll"></a>程序集：System.Windows.Forms.dll

|类型|成员|消息|
|----------|------------|-------------|
|<xref:System.Windows.Forms.AccessibleStates?displayProperty=nameWithType>|<xref:System.Windows.Forms.AccessibleStates.Valid>|此枚举值已弃用。 没有替换。|
|<xref:System.Windows.Forms.ComboBox?displayProperty=nameWithType>|<xref:System.Windows.Forms.ComboBox.AddItemsCore%2A>|此方法已被否决。 没有替换。|
|<xref:System.Windows.Forms.Control?displayProperty=nameWithType>|<xref:System.Windows.Forms.Control.RenderRightToLeft%2A>|此属性已弃用。 请改用 <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=nameWithType>。|
|<xref:System.Windows.Forms.Control?displayProperty=nameWithType>|<xref:System.Windows.Forms.Control.Scale%28System.Single%29>|此方法已被否决。 请改用 <xref:System.Windows.Forms.Control.Scale%28System.Drawing.SizeF%29?displayProperty=nameWithType> 方法。|
|<xref:System.Windows.Forms.Control?displayProperty=nameWithType>|<xref:System.Windows.Forms.Control.Scale%28System.Single%2CSystem.Single%29>|此方法已被否决。 请改用 <xref:System.Windows.Forms.Control.Scale%28System.Drawing.SizeF%29?displayProperty=nameWithType> 方法。|
|<xref:System.Windows.Forms.Form?displayProperty=nameWithType>|<xref:System.Windows.Forms.Form.ApplyAutoScaling%2A>|此方法已被否决。 请改用 <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> 方法。|
|<xref:System.Windows.Forms.Form?displayProperty=nameWithType>|<xref:System.Windows.Forms.Form.AutoScale%2A>|此属性已弃用。 改用 <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A?displayProperty=nameWithType> 属性。|
|<xref:System.Windows.Forms.Form?displayProperty=nameWithType>|<xref:System.Windows.Forms.Form.GetAutoScaleSize%2A>|此方法已被否决。 改用 <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A?displayProperty=nameWithType> 属性。|
|<xref:System.Windows.Forms.Label?displayProperty=nameWithType>|<xref:System.Windows.Forms.Label.RenderTransparent%2A>|此属性已弃用。 请改用 <xref:System.Windows.Forms.Control.BackColor%2A>。|
|<xref:System.Windows.Forms.ListBox?displayProperty=nameWithType>|<xref:System.Windows.Forms.ListBox.AddItemsCore%2A>|此方法已被否决。 没有替换。|
|<xref:System.Windows.Forms.PrintPreviewDialog?displayProperty=nameWithType>|<xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A>|此属性已弃用。 改用 <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A?displayProperty=nameWithType> 属性。|

<a name="xaml"></a>

### <a name="assembly-systemxamldll"></a>程序集：System.Xaml.dll

|类型|成员|消息|
|----------|------------|-------------|
|<xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute?displayProperty=nameWithType>|<xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute.ExpressionType%2A>|XAML 分析器不会使用它。 请参阅 <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute?displayProperty=nameWithType>。|
|<xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute?displayProperty=nameWithType>|<xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute.%23ctor%28System.Type%2CSystem.Type%29>|XAML 分析器不使用 `expressionType` 参数。 若要指定预期的返回类型，请使用 <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute.%23ctor%28System.Type%29?displayProperty=nameWithType>。 若要指定表达式类型的自定义处理，请使用 <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute?displayProperty=nameWithType>。|

<a name="xml"></a>

### <a name="assembly-systemxmldll"></a>程序集：System.Xml.dll

|类型|成员|消息|
|----------|------------|-------------|
|<xref:System.Xml.ValidationType?displayProperty=nameWithType>|<xref:System.Xml.ValidationType.Auto>|验证类型应指定为 <xref:System.Xml.ValidationType.DTD?displayProperty=nameWithType> 或 <xref:System.Xml.ValidationType.Schema?displayProperty=nameWithType>。|
|<xref:System.Xml.ValidationType?displayProperty=nameWithType>|<xref:System.Xml.ValidationType.XDR>|通过 <xref:System.Xml.XmlValidatingReader?displayProperty=nameWithType> 验证 XDR 已过时。|
|<xref:System.Xml.XmlConvert?displayProperty=nameWithType>|<xref:System.Xml.XmlConvert.ToDateTime%28System.String%29>|请使用 <xref:System.Xml.XmlConvert.ToDateTime%28System.String%2CSystem.Xml.XmlDateTimeSerializationMode%29?displayProperty=nameWithType>。|
|<xref:System.Xml.XmlConvert?displayProperty=nameWithType>|<xref:System.Xml.XmlConvert.ToString%28System.DateTime%29>|请使用 <xref:System.Xml.XmlConvert.ToString%28System.DateTime%2CSystem.Xml.XmlDateTimeSerializationMode%29?displayProperty=nameWithType>。|
|<xref:System.Xml.XmlReaderSettings?displayProperty=nameWithType>|<xref:System.Xml.XmlReaderSettings.ProhibitDtd%2A>|改用 <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A?displayProperty=nameWithType> 属性。|
|<xref:System.Xml.XmlReaderSettings?displayProperty=nameWithType>|<xref:System.Xml.XmlReaderSettings.%23ctor%28System.Xml.XmlResolver%29>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 使用此成员会生成编译器错误。<br /><br /> 此 API 支持 .NET Framework 基础结构，但不应在代码中直接使用。|
|<xref:System.Xml.XmlTextReader?displayProperty=nameWithType>|<xref:System.Xml.XmlTextReader.ProhibitDtd%2A>|改用 <xref:System.Xml.XmlTextReader.DtdProcessing%2A?displayProperty=nameWithType> 属性。|
|<xref:System.Xml.Schema.XmlSchema?displayProperty=nameWithType>|<xref:System.Xml.Schema.XmlSchema.Compile%28System.Xml.Schema.ValidationEventHandler%29>|请使用 <xref:System.Xml.Schema.XmlSchemaSet> 进行架构编译和验证。|
|<xref:System.Xml.Schema.XmlSchema?displayProperty=nameWithType>|<xref:System.Xml.Schema.XmlSchema.Compile%28System.Xml.Schema.ValidationEventHandler%2CSystem.Xml.XmlResolver%29>|请使用 <xref:System.Xml.Schema.XmlSchemaSet> 进行架构编译和验证。|
|<xref:System.Xml.Schema.XmlSchemaAttribute?displayProperty=nameWithType>|<xref:System.Xml.Schema.XmlSchemaAttribute.AttributeType%2A>|此属性已弃用。 请使用 <xref:System.Xml.Schema.XmlSchemaAttribute.AttributeSchemaType%2A?displayProperty=nameWithType> 属性，它返回强类型的属性类型。|
|<xref:System.Xml.Schema.XmlSchemaElement?displayProperty=nameWithType>|<xref:System.Xml.Schema.XmlSchemaElement.ElementType%2A>|此属性已弃用。 请使用 <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A?displayProperty=nameWithType> 属性，它返回强类型的元素类型。|
|<xref:System.Xml.Schema.XmlSchemaType?displayProperty=nameWithType>|<xref:System.Xml.Schema.XmlSchemaType.BaseSchemaType%2A>|此属性已弃用。 请使用 <xref:System.Xml.Schema.XmlSchemaType.BaseXmlSchemaType%2A?displayProperty=nameWithType> 属性，它返回强类型的基本架构类型。|
|<xref:System.Xml.Serialization.CodeIdentifier?displayProperty=nameWithType>|<xref:System.Xml.Serialization.CodeIdentifier.%23ctor%2A>|此类将不会获取构造，因为它仅包含静态方法。|
|<xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>|<xref:System.Xml.Serialization.XmlSerializer.FromMappings%28System.Xml.Serialization.XmlMapping%5B%5D%2CSystem.Security.Policy.Evidence%29>|此方法已过时，并将从 .NET Framework 的未来版本中移除。 请使用不采用 <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 参数的 <xref:System.Xml.Serialization.XmlSerializer.FromMappings%2A?displayProperty=nameWithType> 的重载。|
|<xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>|<xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%2CSystem.String%2CSystem.Security.Policy.Evidence%29>|此方法已过时，并将从 .NET Framework 的未来版本中移除。 请使用不采用 <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 参数的 <xref:System.Xml.Serialization.XmlSerializer.%23ctor%2A?displayProperty=nameWithType> 构造函数重载。|
|<xref:System.Xml.Serialization.XmlSerializerFactory?displayProperty=nameWithType>|<xref:System.Xml.Serialization.XmlSerializerFactory.CreateSerializer%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%2CSystem.String%2CSystem.Security.Policy.Evidence%29>|此方法已过时，并将从 .NET Framework 的未来版本中移除。 请使用不采用 <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 参数的 <xref:System.Xml.Serialization.XmlSerializerFactory.CreateSerializer%2A?displayProperty=nameWithType> 的重载。|

<a name="MicrosoftMembers"></a>

## <a name="obsolete-members-in-microsoft-assemblies"></a>Microsoft 程序集中的过时成员

下表列出了 Microsoft 程序集中的过时成员。 这些是特殊用途的程序集，包括面向单一语言（如 Microsoft.VisualBasic.dll）或生成系统（如 Microsoft.Build.Engine.dll）的程序集。

<a name="IEHost"></a>

### <a name="assembly-iehostdll-and-ieexecexe"></a>程序集：IEHost.dll 和 IEExec.exe

IEHost.dll 和 IEExec.exe 程序集已从 .NET Framework 中删除。 其所有类型和成员已过时，且在 .NET Framework 4.5 中不受支持。 这些程序集过去用于承载 Windows 窗体控件和在 Internet Explorer 中运行可执行文件。 该技术的替代项包括 ClickOnce、XAML 浏览器应用程序 (XBAP) 和 Microsoft Silverlight。

<a name="isymwrapper"></a>

### <a name="assembly-isymwrapperdll"></a>程序集：ISymWrapper.dll

|类型|成员|消息|
|----------|------------|-------------|
|<xref:System.Diagnostics.SymbolStore.SymBinder?displayProperty=nameWithType>|<xref:System.Diagnostics.SymbolStore.SymBinder.GetReader%28System.Int32%2CSystem.String%2CSystem.String%29>|建议的替代项为 <xref:System.Diagnostics.SymbolStore.SymBinder.GetReader%28System.IntPtr%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType>。 <xref:System.Diagnostics.SymbolStore.ISymbolBinder1.GetReader%2A?displayProperty=nameWithType> 将导入程序接口指针视为 <xref:System.IntPtr?displayProperty=nameWithType> 而不是 <xref:System.Int32?displayProperty=nameWithType>，因此可以同时在 32 位和 64 位体系结构上工作。|

<a name="conversion"></a>

### <a name="assembly-microsoftbuildconversionv40dll"></a>程序集：Microsoft.Build.Conversion.v4.0.dll

|类型|成员|消息|
|----------|------------|-------------|
|<xref:Microsoft.Build.Conversion.ProjectFileConverter?displayProperty=nameWithType>|<xref:Microsoft.Build.Conversion.ProjectFileConverter.Convert%28Microsoft.Build.BuildEngine.ProjectLoadSettings%29>|改用无参数 <xref:Microsoft.Build.Conversion.ProjectFileConverter.Convert> 重载。|
|<xref:Microsoft.Build.Conversion.ProjectFileConverter?displayProperty=nameWithType>|<xref:Microsoft.Build.Conversion.ProjectFileConverter.Convert%28System.String%29>|改用无参数 <xref:Microsoft.Build.Conversion.ProjectFileConverter.Convert> 重载。|
|<xref:Microsoft.Build.Conversion.ProjectFileConverter?displayProperty=nameWithType>|<xref:Microsoft.Build.Conversion.ProjectFileConverter.ConvertInMemory%28Microsoft.Build.BuildEngine.Engine%29>|改用无参数 <xref:Microsoft.Build.Conversion.ProjectFileConverter.ConvertInMemory?displayProperty=nameWithType> 方法。|
|<xref:Microsoft.Build.Conversion.ProjectFileConverter?displayProperty=nameWithType>|<xref:Microsoft.Build.Conversion.ProjectFileConverter.ConvertInMemory%28Microsoft.Build.BuildEngine.Engine%2CMicrosoft.Build.BuildEngine.ProjectLoadSettings%29>|改用无参数 <xref:Microsoft.Build.Conversion.ProjectFileConverter.ConvertInMemory?displayProperty=nameWithType> 方法。|

<a name="engine"></a>

### <a name="assembly-microsoftbuildenginedll"></a>程序集：Microsoft.Build.Engine.dll

|类型|成员|消息|
|----------|------------|-------------|
|<xref:Microsoft.Build.BuildEngine.Engine?displayProperty=nameWithType>|<xref:Microsoft.Build.BuildEngine.Engine.BinPath%2A>|避免设置 <xref:Microsoft.Build.BuildEngine.Engine.BinPath%2A>。 如果仅作为 <xref:Microsoft.Build.BuildEngine.Engine.BinPath%2A> 传入 .NET Framework 位置，则无需其他操作。 否则，改为在注册表或配置文件中，或通过向引擎的 <xref:Microsoft.Build.BuildEngine.ToolsetCollection?displayProperty=nameWithType> 添加元素来定义工具集，以便使用自定义 <xref:Microsoft.Build.BuildEngine.Engine.BinPath%2A>。|
|<xref:Microsoft.Build.BuildEngine.Engine?displayProperty=nameWithType>|<xref:Microsoft.Build.BuildEngine.Engine.%23ctor%28System.String%29>|如果仅作为 <xref:Microsoft.Build.BuildEngine.Engine.BinPath%2A> 传入 .NET Framework 位置，则只要更改为无参数 <xref:Microsoft.Build.BuildEngine.Engine.%23ctor?displayProperty=nameWithType> 构造函数即可。 否则，你可以在注册表或配置文件中定义自定义工具集，或将元素添加到引擎的 <xref:Microsoft.Build.BuildEngine.ToolsetCollection?displayProperty=nameWithType>。 然后改用 <xref:Microsoft.Build.BuildEngine.Engine.%23ctor?displayProperty=nameWithType> 或 <xref:Microsoft.Build.BuildEngine.Engine.%23ctor%28Microsoft.Build.BuildEngine.ToolsetDefinitionLocations%29?displayProperty=nameWithType> 构造函数。|

<a name="BuildFW"></a>

### <a name="assembly-microsoftbuildframeworkdll"></a>程序集：Microsoft.Build.Framework.dll

|类型|成员|消息|
|----------|------------|-------------|
|<xref:Microsoft.Build.Framework.XamlTypes.ContentType?displayProperty=nameWithType>|<xref:Microsoft.Build.Framework.XamlTypes.ContentType.ItemGroupName%2A>|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 使用此成员会生成编译器错误。<br /><br /> 改用 <xref:Microsoft.Build.Framework.XamlTypes.ContentType.ItemType%2A?displayProperty=nameWithType> 属性。|

<a name="BuildUtil4"></a>

### <a name="assembly-microsoftbuildutilitiesv40dll"></a>程序集：Microsoft.Build.Utilities.v4.0.dll

|类型|成员|消息|
|----------|------------|-------------|
|<xref:Microsoft.Build.Utilities.ToolTask?displayProperty=nameWithType>|<xref:Microsoft.Build.Utilities.ToolTask.EnvironmentOverride%2A>|使用 <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A?displayProperty=nameWithType> 属性。|

<a name="data_entity_tasks"></a>

### <a name="assembly-microsoftdataentitybuildtasksdll"></a>程序集：Microsoft.Data.Entity.Build.Tasks.dll

|类型|成员|消息|
|----------|------------|-------------|
|`Microsoft.Data.Entity.Build.Tasks.EntityDeploy`|`EntityDataModelEmbeddedResources`|在 .NET Framework 4.5 中首次被废弃。<br /><br /> 仅用于 3.5 版的向后兼容性。|

<a name="visualbasic"></a>

### <a name="assembly-microsoftvisualbasicdll"></a>程序集：Microsoft.VisualBasic.dll

|类型|成员|消息|
|----------|------------|-------------|
|<xref:Microsoft.VisualBasic.FileSystem?displayProperty=nameWithType>|<xref:Microsoft.VisualBasic.FileSystem.FilePut%28System.Object%2CSystem.Object%2CSystem.Object%29>|此成员已弃用。 请使用 <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A?displayProperty=nameWithType> 编写 <xref:System.Object> 类型，或强制将 `FileNumber` 和 `RecordNumber` 转换为 <xref:System.Int32> 用于编写非对象类型。|
|<xref:Microsoft.VisualBasic.CompilerServices.Conversions?displayProperty=nameWithType>|<xref:Microsoft.VisualBasic.CompilerServices.Conversions.FallbackUserDefinedConversion%2A>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|
|<xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>|<xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding.FallbackCall%2A>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|
|<xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>|<xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding.FallbackGet%2A>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|
|<xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>|<xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding.FallbackIndexSet%2A>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|
|<xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>|<xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding.FallbackIndexSetComplex%2A>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|
|<xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>|<xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding.FallbackInvokeDefault1%2A>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|
|<xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>|<xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding.FallbackInvokeDefault2%2A>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|
|<xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>|<xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding.FallbackSet%2A>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|
|<xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>|<xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding.FallbackSetComplex%2A>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|
|<xref:Microsoft.VisualBasic.CompilerServices.Operators?displayProperty=nameWithType>|<xref:Microsoft.VisualBasic.CompilerServices.Operators.FallbackInvokeUserDefinedOperator%2A>|使用此成员会生成编译器错误。<br /><br /> 不要使用此方法。|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy?displayProperty=nameWithType>|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy.DynData%2A>|`DynData` 注册表项仅适用于 Win9x，在此版本的.NET Framework 中不受支持。 改用 `PerformanceData` 注册表项。 此属性将从 Framework 的未来版本中移除。|

## <a name="see-also"></a>请参阅

- [类库中过时的内容](whats-obsolete.md)
- [过时类型](obsolete-types.md)
