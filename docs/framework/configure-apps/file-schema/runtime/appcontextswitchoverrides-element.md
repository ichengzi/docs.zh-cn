---
title: <AppContextSwitchOverrides> 元素
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
ms.openlocfilehash: 34187b5fdcfcd4d08b4067213372fd12c7533cf7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430520"
---
# <a name="appcontextswitchoverrides-element"></a>\<AppContextSwitchOverrides> Element
定义 <xref:System.AppContext> 类使用的一个或多个开关，用于提供新功能的选择退出机制。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<runtime>** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<AppContextSwitchOverrides>**  
  
## <a name="syntax"></a>语法  
  
```xml  
<AppContextSwitchOverrides value="name1=value1[[;name2=value2];...]" />  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|`value`|必需的特性。<br /><br /> Defines one or more switch names and their associated Boolean values.|  
  
### <a name="value-attribute"></a>value Attribute  
  
|“值”|描述|  
|-----------|-----------------|  
|"name=value"|A predefined switch name along with its value (`true` or `false`). Multiple switch name/value pairs are separated by semicolons (";"). For a list of predefined switch names supported by the .NET Framework, see the Remarks section.|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
|`runtime`|包含有关运行时初始化选项的信息。|  
  
## <a name="remarks"></a>备注  
 Starting with the .NET Framework 4.6, the `<AppContextSwitchOverrides>` element in a configuration file allows callers of an API to determine whether their app can take advantage of new functionality or preserve compatibility with previous versions of a library. For example, if the behavior of an API has changed between two versions of a library, the `<AppContextSwitchOverrides>` element allows callers of that API to opt out of the new behavior on versions of the library that support the new functionality. For apps that call APIs in the .NET Framework, the `<AppContextSwitchOverrides>` element can also allow callers whose apps target an earlier version of the .NET Framework to opt into new functionality if their app is running on a version of the .NET Framework that includes that functionality.  
  
 The `value` attribute of the `<AppContextSwitchOverrides>` element consists of a single string that consists of one or more semicolon-delimited name/value pairs.  Each name identifies a compatibility switch, and its corresponding value is a Boolean (`true` or `false`) that indicates whether the switch is set. By default, the switch is `false`, and libraries  provide the new functionality. They only provide the previous functionality if the switch is set (that is, its value is `true`). This allows libraries to provide new behavior for an existing API while allowing callers who depend on the previous behavior to opt out of the new functionality.  
  
 The .NET Framework supports the following switches:  
  
|Switch name|描述|Introduced|  
|-----------------|-----------------|----------------|  
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|Controls whether Windows Presentation Foundation uses legacy a algorithm for control layout. 有关详细信息，请参阅[缓解：WPF 布局](../../../migration-guide/mitigation-wpf-layout.md)。|.NET Framework 4.6|  
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|Controls whether the default algorithm used for signing parts of a package by PackageDigitalSignatureManager is SHA1 or SHA256.<br>由于与 SHA1 冲突，Microsoft 建议使用 SHA256。|.NET Framework 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|When set to `false`, allows debugging of XAML-based workflow projects with Visual Studio when FIPS is enabled. Without it, a <xref:System.NullReferenceException> is thrown in calls to methods in the System.Activities assembly.|.NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|Controls whether the checksum for a workflow instance in the debugger uses MD5 or SHA1. | .NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseSHA1HashForDebuggerSymbols`|Controls whether workflow checksum hashing uses the SHA1 algorithm introduced as the default in .NET Framework 4.7 (`true`), or whether it uses the default SHA256 algorithm introduced as the default in .NET Framework 4.8 (`false`).<br>由于与 SHA1 冲突，Microsoft 建议使用 SHA256。|.NET Framework 4.8|
|`Switch.System.Diagnostics.`<br/>`IgnorePortablePDBsInStackTraces`|Controls whether stack traces obtain when using portable PDBs can include source file and line information. `false` to include source file and line information; otherwise, `true`.|.NET Framework 4.7.2|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|Controls whether the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an exception when an <xref:System.Drawing.Icon> object has PNG frames. 有关详细信息，请参阅[缓解：图标对象中的 PNG 帧](../../../migration-guide/mitigation-png-frames-in-icon-objects.md)。|.NET Framework 4.6|
|`Switch.System.Drawing.Text.`<br/>`DoNotRemoveGdiFontsResourcesFromFontCollection`|Determines whether <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> objects are properly disposed when added to the collection by the <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType> method. `true` to maintain the legacy behavior; `false` to dispose of all private font objects. |.NET Framework 4.7.2|
|`Switch.System.Drawing.Printing.`<br>`OptimizePrintPreview`|Controls whether the performance of the <xref:System.Windows.Forms.PrintPreviewDialog> is optimized for network printers. For more information, see [PrintPreviewDialog control overview](../../../winforms/controls/printpreviewdialog-control-overview-windows-forms.md).|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceJapaneseEraYearRanges`|Controls whether year range checks for Japanese calendar eras are enforced. `true` to enforce year range checks, and `false` to disable them (the default behavior). For more information, see [Working with calendars](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceLegacyJapaneseDateParsing`|Controls whether only "1" is recognized as the first year of a Japanese calendar era in parsing operations. `true` to recognize only "1"; `false` to recognize either "1" or Gannen (the default behavior). For more information, see [Working with calendars](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6| 
|`Switch.System.Globalization.FormatJapaneseFirstYearAsANumber`|Controls whether the first year of a Japanese calendar era is represented as "1" or Gannen in formatting operations. `true` to format the era's first year as "1"; `false` to format it as Gannen (the default behavior). For more information, see [Working with calendars](../../../../standard/datetime/working-with-calendars.md).|.NET Framework 4.6|
|`Switch.System.Globalization.NoAsyncCurrentCulture`|Controls whether asynchronous operations do not flow from the calling thread's context. For more information, see [CurrentCulture and CurrentUICulture flow across tasks](../../../migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks).|.NET Framework 4.6|  
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|Controls whether the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the claim type only with the last DNS entry. 有关详细信息，请参阅[缓解：X509CertificateClaimSet.FindClaims 方法](../../../migration-guide/mitigation-x509certificateclaimset-findclaims-method.md)。|.NET Framework 4.6.1|  
|`Switch.System.IdentityModel.`<br/>`EnableCachedEmptyDefaultAuthorizationContext`|Controls whether to allow AuthorizationContext.Empty to return a mutable object.|.NET Framework 4.6|  
|`Switch.System.IO.BlockLongPaths`|Controls whether paths longer than `MAX_PATH` (260 characters) throw a <xref:System.IO.PathTooLongException>. For more information, see [Long Path Support](../../../migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support).|.NET Framework 4.6.2|  
|`Switch.System.IO.Compression.`<br/>`DoNotUseNativeZipLibraryForDecompression`|Controls whether native OS routines are used for decompression by the <xref:System.IO.Compression.DeflateStream> class. `false` to use native APIs; `true` to use the <xref:System.IO.Compression.DeflateStream> implementation.|.NET Framework 4.7.2|
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|Uses the backslash ("\\") rather than the forward slash ("/") as the path separator in the <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> property. For more information, see  [Mitigation: ZipArchiveEntry.FullName Path Separator](../../../migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md).|.NET Framework 4.6.1|  
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|Controls whether operating system exceptions that are thrown on background threads created with <xref:System.IO.Ports.SerialPort> streams terminate the process.|.NET Framework 4.7.1| 
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|Controls whether legacy path normalization is used and URI paths are supported by the <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> and <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> methods. For more information, see [Mitigation: Path Normalization](../../../migration-guide/mitigation-path-normalization.md) and [Mitigation: Path Colon Checks](../../../migration-guide/mitigation-path-colon-checks.md).|.NET Framework 4.6.2|
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|Controls whether a test for equality compares the <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType> property of one object with the <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType> property of the second object. For more information, see [Incorrect implementation of MemberDescriptor.Equals](../../../migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals).|.NET Framework 4.6.2|  
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|Disables certificate enhanced key usage (EKU) object identifier (OID) validation. 增强型密钥使用 (EKU) 扩展是指示使用密钥的应用程序的对象标识符 (OID) 的集合。|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|Disables TLS1.0 Browser Exploit Against SSL/TLS (BEAST) mitigation by disabling the use of SCH_SEND_AUX_RECORD.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|Controls whether the <xref:System.Net.ServicePointManager?displayProperty=nameWithType> and <xref:System.Net.Security.SslStream?displayProperty=nameWithType> classes can use the SSL 3.0 protocol. 有关详细信息，请参阅[缓解：TLS 协议](../../../migration-guide/mitigation-tls-protocols.md)。|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|Disables SystemDefault TLS versions reverting back to a default of Tls12, Tls11, Tls.|.NET Framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|Disables SslStream TLS server-side Alerts.|.NET Framework 4.7|
|`Switch.System.Runtime.InteropServices.`<br/>`DoNotMarshalOutByrefSafeArrayOnInvoke`|Controls whether ByRef SafeArray parameters on COM interop events marshal back to native code (`false`) or whether marshaling back to native code is disabled (`true`).|.NET Framework 4.8|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |Controls whether the [DataContractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer) serializes some control characters based on the ECMAScript V6 and V8 standards. 有关详细信息，请参阅[缓解：使用 DataContractJsonSerializer 对控制字符进行序列化](../../../migration-guide/mitigation-serialization-control-characters.md)| .NET Framework 4.7 |
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseTimeZoneInfo`|Controls whether the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> supports multiple adjustments or only a single adjustment for a time zone. If `true`, it uses the <xref:System.TimeZoneInfo> type to serialize and deserialize date and time data; otherwise, it uses the <xref:System.TimeZone> type, which does not support multiple adjustment rules.|.NET Framework 4.6.2|
|`Switch.System.Runtime.Serialization.UseNewMaxArraySize`|Controls whether <xref:System.Runtime.Serialization.ObjectManager?displayProperty=nameWithType> uses a larger array size during object serialization and deserialization. Set this switch to `true` to improve the performance of serialization and deserialization of large object graphs by types such as <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. |.NET Framework 4.7.2|
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|Controls whether the <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=nameWithType> constructor sets the  new object's <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType> property with an existing object reference. 有关详细信息，请参阅[缓解：ClaimsIdentity 构造函数](../../../migration-guide/retargeting/4.6.1-4.6.2.md)。|.NET Framework 4.6.2|  
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|Controls whether the attempt to reuse an <xref:System.Security.Cryptography.AesCryptoServiceProvider> decryptor throws a <xref:System.Security.Cryptography.CryptographicException>. For more information, see [AesCryptoServiceProvider decryptor provides a reusable transform](../../../migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform).|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|Controls whether the value of the [CspParameters.ParentWindowHandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle) property is an [IntPtr](xref:System.IntPtr) that represents the memory location of a window handle, or whether it is a window handle (an HWND). 有关详细信息，请参阅[缓解：应向 CspParameters.ParentWindowHandle 分配 HWND](../../../migration-guide/retargeting/4.6.2-4.7.md#cspparametersparentwindowhandle-now-expects-hwnd-value)。 |.NET Framework 4.7|   
|`Switch.System.Security.Cryptography.`<br/>`UseLegacyFipsThrow`|Controls whether the use of managed cryptography classes in FIPS mode throws a <xref:System.Security.Cryptography.CryptographicException> (`true`) or relies on the implementation of system libraries (`false`).|.NET Framework 4.8|
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|Determines whether the default for some SignedCMS operations is SHA1 or SHA256.<br>由于与 SHA1 冲突，Microsoft 建议使用 SHA256。|.NET Framework 4.7.1|
|`Switch.System.Security.Cryptography.X509Certificates.`<br/>`ECDsaCertificateExtensions.UseLegacyPublicKeyReader`|Controls whether the <xref:System.Security.Cryptography.X509Certificates.ECDsaCertificateExtensions.GetECDsaPublicKey%2A?displayProperty=nameWithType> method correctly handles all named curves supported by the operating system (`false`) or reverts to legacy behavior.|.NET Framework 4.8|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|Determines whether the default for some SignedXML operations is SHA1 or SHA256.<br>由于与 SHA1 冲突，Microsoft 建议使用 SHA256。|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|Determines whether the `TransportWithMessageCredential` security mode allows messages with an unsigned "to" header. This is an opt-in switch. For more information, see [Runtime Changes in the .NET Framework 4.6.1](../../../migration-guide/runtime/4.5.2-4.6.1.md#windows-communication-foundation-wcf).|.NET Framework 4.6.1| 
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|Controls whether the <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> constructor throws an <xref:System.ArgumentException> if one of the elements is `null`.|.NET Framework 4.7.1| 
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|Determines whether the attempt to use X509 certificates with a CSG key storage provider throws an exception. For more information, see [WCF transport security supports certificates stored using CNG](../../../migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableExplicitConnectionCloseHeader`|When using the HTTP transport with a self-hosted service, setting this value to `true` causes WCF to ignore an application adding the `Connection: close` header to the response headers for a request. Setting this value to `false` enables adding the `Connection: close` header to the response headers, which results in closing the request socket after a response has been sent.|.NET Framework 4.6|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|Handles deadlocks that result from restricting instances of a reentrant service to a single thread of execution at a time.|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|Along with `Switch.System.Net.DontEnableSchUseStrongCrypto`, determines whether WCF message security uses TLS 1.1 and TLS 1.2.|.NET Framework 4.7 |    
|`Switch.System.ServiceModel.`<br/>`DontEnableSystemDefaultTlsVersions`|A value of `false` sets the default configuration to allow the operating system to choose the protocol. A value of `true` sets the default to the highest protocol available. (Also available on servicing branch of previous framework versions)|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|Determines whether the default message signing algorithm for MSMQ messages in WCF is SHA1 or SHA256.<br>由于与 SHA1 冲突，Microsoft 建议使用 SHA256。|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|Controls whether WCF uses a SHA1 or a SHA256 hash to generate random names for named pipes.<br>由于与 SHA1 冲突，Microsoft 建议使用 SHA256。|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.Internals`<br/>`IncludeNullExceptionMessageInETWTrace`|Controls whether to throw a [NullReferenceException](xref:System.NullReferenceException) when the exception message is null.|.NET Framework 4.7|  
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|Controls whether exceptions thrown on service startup are propagated to the caller of the <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> method.|.NET Framework 4.7.1|
|`Switch.System.Threading.UseNetCoreTimer`|Controls whether <xref:System.Threading.Timer> instances take advantage of performance improvements for high-scale environments. If `true`, the performance improvements are enabled; if `false` (the default value), they are disabled.|.NET Framework 4.8|
|`Switch.System.Uri.`<br/>`DontEnableStrictRFC3986ReservedCharacterSets`|Determines whether certain percent-encoded characters that were sometimes decoded are now consistently left encoded. If `true`, they are decoded; otherwise, `false`.|.NET Framework 4.7.2|
|`Switch.System.Uri.`<br/>`DontKeepUnicodeBidiFormattingCharacters`|Determines the handling of Unicode bidirectional characters in URIs. `true` to strip them from URIs; `false` to preserve and percent-encode them.|.NET Framework 4.7.2|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |Determines whether Windows Presentation Foundation applies an old algorithm (`true`) or a new algorithm (`false`) in allocating space to \*-columns. 有关详细信息，请参阅[缓解：网格控件向 *-列分配空间](../../../migration-guide/retargeting/4.6.2-4.7.md#wpf-grid-allocation-of-space-to-star-columns)。 |.NET Framework 4.7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|Controls whether a selector or a tab control always updates the value of its selected value property before raising the selection changed event.|.NET Framework 4.7.1|
|`Switch.System.Windows.Controls.Text.`<br/>`UseAdornerForTextboxSelectionRendering`|Determines whether non-Adorner based selection rendering is available for the <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.PasswordBox> controls to prevent occluded text (`false`), or whether text is rendered only in the Adorner layer (`true`).|.NET Framework 4.7.2|
|`Switch.System.Windows.Data.Binding.`<br/>`IListIndexerHidesCustomIndexer`|Controls whether custom IList indexers are used incorrectly (`true`) or correctly (`false`) by the <xref:System.Windows.Data.Binding?displayProperty=nameWithType> class.|.NET Framework 4.8|
|`Switch.System.Windows.DoNotScaleForDpiChanges`|Determines whether DPI changes occur on a per-system (a value of `false`) or per-monitor basis (a value of `true`).|.NET Framework 4.6.2|
|`Switch.System.Windows.`<br/>`DoNotUsePresentationDpiCapabilityTier2OrGreater`|Controls whether improvements in sizing of controls in a <xref:System.Windows.Interop.HwndHost?displayProperty=nameWithType> when WPF is run in per-monitor aware mode are disabled (`true`) or enabled (`false`).|.NET Framework 4.8|
|`Switch.System.Windows.Forms.`<br/>`DomainUpDown.UseLegacyScrolling`|Determines whether the developer needs to specially handle the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> action when control text is present. `true` to handle the <xref:System.Windows.Forms.DomainUpDown.UpButton> action; `false` for the <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> and <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> actions to be properly in sync.|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|Opts out of the code that allows a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation to safely filter messages without throwing an exception when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called. 有关详细信息，请参阅[缓解：自定义 IMessageFilter.PreFilterMessage 实现](../../../migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)。|.NET Framework 4.6.1|  
|`Switch.System.Windows.Forms.`<br/>`UseLegacyContextMenuStripSourceControlValue`|Determines whether the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> property returns the source control when the user opens the menu from a nested <xref:System.Windows.Forms.ToolStripMenuItem> control. `true` to return `null`, the legacy behavior; `false` to return the source control.|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.UseLegacyToolTipDisplay`|Controls whether tooltip invocation support is disabled (`true`) or enabled (`false`). Enabling tooltip invocation support also requires legacy accessibility features defined by `Switch.UseLegacyAccessibilityFeatures`, `Switch.UseLegacyAccessibilityFeatures.2`, and `Switch.UseLegacyAccessibilityFeatures.3` all be disabled (set to `false`).|.NET Framework 4.8|
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|Determines whether an optional `WM_POINTER`-based touch/stylus stack is enabled in WPF applications. For more information, see [Mitigation: Pointer-based Touch and Stylus Support](../../../migration-guide/mitigation-pointer-based-touch-and-stylus-support.md)|.NET Framework 4.7|
|`Switch.System.Windows.Markup.`<br/>`DoNotUseSha256ForMarkupCompilerChecksumAlgorithm`|Determines whether the default hash algorithm used for checksums is SHA256 (`false`) or SHA1 (`true`).<br>由于与 SHA1 冲突，Microsoft 建议使用 SHA256。|.NET Framework 4.7.2|
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|Controls whether a legacy [NullReferenceException](xref:System.NullReferenceException) is thrown instead of the exception that more specifically indicates the cause of the exception (such as a [DirectoryNotFoundException](xref:System.IO.DirectoryNotFoundException) or a [FileNotFoundException](xref:System.IO.FileNotFoundException). It is intended for use by code that depends on handling the [NullReferenceException](xref:System.NullReferenceException). | .NET Framework 4.7 |
|`Switch.System.Workflow.ComponentModel.`<br/>`UseLegacyHashForXomlFileChecksum`|Controls whether checksum hashing of XOML files in workflow project builds use the MD5 algorithm (`true`), or whether they use the SHA256 algorithm introduced as the default in .NET Framework 4.8.<br>由于与 MD5 冲突，Microsoft 建议使用 SHA256。|.NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForSqlTrackingCacheKey`|Controls whether checksum hashing by the SqlTrackingService uses the MD5 algorithm (`true`) for cached strings, or whether it uses the SHA256 algorithm introduced as the default in .NET Framework 4.8.<br>由于与 MD5 冲突，Microsoft 建议使用 SHA256。|.NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForWorkflowDefinitionDispenserCacheKey`|Controls whether checksum hashing by the Workflow Runtime uses the MD5 algorithm (`true`) for cached workflow definitions, or whether it uses the SHA256 algorithm introduced as the default in .NET Framework 4.8.<br>由于与 MD5 冲突，Microsoft 建议使用 SHA256。|.NET Framework 4.8|
|`Switch.UseLegacyAccessibilityFeatures`|Controls whether accessibility features available starting with .NET Framework 4.7.1 are enabled or disabled. | .NET Framework 4.7.1 |
|`Switch.UseLegacyAccessibilityFeatures.2`|Controls whether accessibility features available in .NET Framework 4.7.2 are enabled (`false`) or disabled (`true`). If `true`, `Switch.UseLegacyAccessibilityFeatures` must also be `true` to enable .NET Framework 4.7.1 accessibility features.|.NET Framework 4.7.2|
|`Switch.UseLegacyAccessibilityFeatures.3`|Controls whether accessibility features introduced in .NET Framework 4.8 are enabled (`false`) or disabled (`true`). If `true`, `Switch.UseLegacyAccessibilityFeatures` and `Switch.UseLegacyAccessibilityFeatures.2` must also be `true`.|.NET Framework 4.8|
|`Switch.UseLegacyToolTipDisplay`|Controls whether tooltips are displayed when a user hovers the mouse cursor over a WPF control (`true`), or whether they are displayed both on keyboard focus and via keyboard shortcut key (`false`, the default behavior). For applications running on .NET Framework 4.8 but targeting previous versions of the .NET Framework, enabling both keyboard focus and shortcut key support requires that `Switch.UseLegacyAccessibilityFeatures`, `Switch.UseLegacyAccessibilityFeatures.2`, and `Switch.UseLegacyAccessibilityFeatures.3` all be set to `false`.|.NET Framework 4.8|
|`System.Xml.`<br /><br /> `IgnoreEmptyKeySequences`|Controls whether empty key sequences in compound keys are ignored by XSD schema validation. For more information, see [Mitigation: XML Schema Validation](../../../migration-guide/mitigation-xml-schema-validation.md).|.NET Framework 4.6|  
  
> [!NOTE]
> Instead of adding an `AppContextSwitchOverrides` element to an application configuration file, you can also set the switches programmatically by calling the `static` (in C#) or `Shared` (in Visual Basic) <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.  
  
 Library developers can also define custom switches to allow callers to opt out of changed functionality introduced  in later versions of their libraries. 有关更多信息，请参见 <xref:System.AppContext> 类。  
  
## <a name="switches-in-aspnet-applications"></a>Switches in ASP.NET applications

You can configure an ASP.NET application to use compatibility settings by adding an [\<Add>](../appsettings/add-element-for-appsettings.md) element to the [\<appSettings>](../appsettings/index.md) section of the web.config file. 

The following example uses the `<add>` element to add two settings to the `<appSettings>` section of a web.config file:

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="example"></a>示例

 The following example uses the `AppContextSwitchOverrides` element to define a single application  compatibility switch, `Switch.System.Globalization.NoAsyncCurrentCulture`, that prevents culture from flowing across threads in asynchronous method calls.  
  
```xml  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
   </runtime>  
</configuration>  
```  
  
 The following example uses the `AppContextSwitchOverrides` element to define two application  compatibility switches, `Switch.System.Globalization.NoAsyncCurrentCulture` and `Switch.System.IO.BlockLongPaths`. Note that a semicolon separates the two name/value pairs.  
  
```xml  
<configuration>  
    <runtime>  
       <AppContextSwitchOverrides   
          value="Switch.System.Globalization.NoAsyncCurrentCulture=true;Switch.System.IO.BlockLongPaths=true" />  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.AppContext?displayProperty=nameWithType>
- [\<runtime> Element](runtime-element.md)
- [\<configuration> 元素](../configuration-element.md)
