---
ms.openlocfilehash: 86cdb845c436f424bbcc70e0736568031143b204
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522683"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft.VisualBasic.Constants.vbNewLine 已过时

自 .NET Core 3.0 预览版 8 起，<xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> 常量标记为[已过时](xref:System.ObsoleteAttribute)。

#### <a name="version-introduced"></a>引入的版本

3.0 预览版 8

#### <a name="change-description"></a>更改描述

自 .NET Core 3.0 预览版 8 起，已向 <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> 常量应用 [Obsolete](xref:System.ObsoleteAttribute) 属性。 使用常量会引发编辑器警告。 在之前的 .NET Core 和 .NET Framework 版本中，它未被标记为“已过时”。

此项更改旨在支持将 Visual Basic 用作多平台开发的一种语言。 `vbNewLine` 常量与 Windows 上的换行符序列 `\r\n` 等效。 在基于 Unix 的系统上，换行符为 `\n`。

#### <a name="recommended-action"></a>建议的操作

`vbNewLine` 的[已过时](xref:System.ObsoleteAttribute)属性消息包含以下建议：

> 对于回车符和换行符，请使用 [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf)。 对于当前平台的新行，请使用 <xref:System.Environment.NewLine?displayProperty=nameWithType>。

#### <a name="category"></a>类别

Visual Basic

#### <a name="affected-apis"></a>受影响的 API

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
