---
title: 常量和枚举
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- constants [Visual Basic]
- constants [Visual Basic], list of
ms.assetid: 309c0ad5-83e4-4f96-99ea-83cd95107417
ms.openlocfilehash: de03ce61535d4695a00d0c4b8998ef4b81583425
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347867"
---
# <a name="constants-and-enumerations-visual-basic"></a>常量和枚举 (Visual Basic)

Visual Basic supplies a number of predefined constants and enumerations for developers. Constants store values that remain constant throughout the execution of an application. 枚举提供了使用相关常量集以及将常量值与名称相关联的一个便捷方法。  
  
## <a name="constants"></a>常量  
  
### <a name="conditional-compilation-constants"></a>Conditional Compilation Constants  

 The following table lists the predefined constants available for conditional compilation.  
  
|**常量**|**描述**|  
|---|---|  
|`CONFIG`|A string that corresponds to the current setting of the **Active Solution Configuration** box in the **Configuration Manager**.|  
|`DEBUG`|A `Boolean` value that can be set in the **Project Properties** dialog box. By default, the Debug configuration for a project defines `DEBUG`. When `DEBUG` is defined, <xref:System.Diagnostics.Debug> class methods generate output to the **Output** window. When it is not defined, <xref:System.Diagnostics.Debug> class methods are not compiled and no Debug output is generated.|  
|`TARGET`|A string representing the output type for the project or the setting of the command-line **/target** option. The possible values of `TARGET` are:<br /><br /> -   "winexe" for a Windows application.<br />-   "exe" for a console application.<br />-   "library" for a class library.<br />-   "module" for a module.<br />-   The **/target** option may be set in the Visual Studio integrated development environment. For more information, see [-target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md).|  
|`TRACE`|A `Boolean` value that can be set in the **Project Properties** dialog box. By default, all configurations for a project define `TRACE`. When `TRACE` is defined, <xref:System.Diagnostics.Trace> class methods generate output to the **Output** window. When it is not defined, <xref:System.Diagnostics.Trace> class methods are not compiled and no `Trace` output is generated.|  
|`VBC_VER`|A number representing the Visual Basic version, in *major*.*minor* format.|  
  
### <a name="print-and-display-constants"></a>Print and Display Constants  

 When you call print and display functions, you can use the following constants in your code in place of the actual values.  
  
|**常量**|**描述**|  
|---|---|  
|`vbCrLf`|Carriage return/linefeed character combination.|  
|`vbCr`|Carriage return character.|  
|`vbLf`|Linefeed character.|  
|`vbNewLine`|Newline character.|  
|`vbNullChar`|Null character.|  
|`vbNullString`|Not the same as a zero-length string (""); used for calling external procedures.|  
|`vbObjectError`|错误号。 User-defined error numbers should be greater than this value. 例如:<br /><br /> `Err.Raise(Number) = vbObjectError + 1000`|  
|`vbTab`|Tab character.|  
|`vbBack`|Backspace character.|  
|`vbFormFeed`|Not used in Microsoft Windows.|  
|`vbVerticalTab`|Not useful in Microsoft Windows.|  
  
## <a name="enumerations"></a>枚举  

 The following table lists and describes the enumerations provided by Visual Basic.  
  
|枚举|描述|  
|---|---|  
|<xref:Microsoft.VisualBasic.AppWinStyle>|Indicates the window style to use for the invoked program when calling the <xref:Microsoft.VisualBasic.Interaction.Shell%2A> function.|  
|<xref:Microsoft.VisualBasic.AudioPlayMode>|Indicates how to play sounds when calling audio methods.|  
|<xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole>|Indicates the type of role to check when calling the <xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A> method.|  
|<xref:Microsoft.VisualBasic.CallType>|Indicates the type of procedure being invoked when calling the <xref:Microsoft.VisualBasic.Interaction.CallByName%2A> function.|  
|<xref:Microsoft.VisualBasic.CompareMethod>|Indicates how to compare strings when calling comparison functions.|  
|<xref:Microsoft.VisualBasic.DateFormat>|Indicates how to display dates when calling the <xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A> function.|  
|<xref:Microsoft.VisualBasic.DateInterval>|指示当调用与日期相关的函数时如何确定日期间隔并设置其格式。|  
|<xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption>|Specifies what should be done when a directory that is to be deleted contains files or directories.|  
|<xref:Microsoft.VisualBasic.DueDate>|Indicates when payments are due when calling financial methods.|  
|<xref:Microsoft.VisualBasic.FileIO.FieldType>|Indicates whether text fields are delimited or fixed-width.|  
|<xref:Microsoft.VisualBasic.FileAttribute>|Indicates the file attributes to use when calling file-access functions.|  
|<xref:Microsoft.VisualBasic.FirstDayOfWeek>|Indicates the first day of the week to use when calling date-related functions.|  
|<xref:Microsoft.VisualBasic.FirstWeekOfYear>|Indicates the first week of the year to use when calling date-related functions.|  
|<xref:Microsoft.VisualBasic.MsgBoxResult>|指示在消息框上按下了哪个按钮，由 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 函数返回。|  
|<xref:Microsoft.VisualBasic.MsgBoxStyle>|指示调用 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 函数时显示的按钮。|  
|<xref:Microsoft.VisualBasic.OpenAccess>|Indicates how to open a file when calling file-access functions.|  
|<xref:Microsoft.VisualBasic.OpenMode>|Indicates how to open a file when calling file-access functions.|  
|<xref:Microsoft.VisualBasic.OpenShare>|Indicates how to open a file when calling file-access functions.|  
|<xref:Microsoft.VisualBasic.FileIO.RecycleOption>|Specifies whether a file should be deleted permanently or placed in the Recycle Bin.|  
|<xref:Microsoft.VisualBasic.FileIO.SearchOption>|Specifies whether to search all or only top-level directories.|  
|<xref:Microsoft.VisualBasic.TriState>|Indicates a `Boolean` value or whether the default should be used when calling number-formatting functions.|  
|<xref:Microsoft.VisualBasic.FileIO.UICancelOption>|Specifies what should be done if the user clicks **Cancel** during an operation.|  
|<xref:Microsoft.VisualBasic.FileIO.UIOption>|Specifies whether or not to show a progress dialog when copying, deleting, or moving files or directories.|  
|<xref:Microsoft.VisualBasic.VariantType>|Indicates the type of a variant object, returned by the <xref:Microsoft.VisualBasic.Information.VarType%2A> function.|  
|<xref:Microsoft.VisualBasic.VbStrConv>|指示调用 <xref:Microsoft.VisualBasic.Strings.StrConv%2A> 函数时要执行的转换类型。|  
  
## <a name="see-also"></a>请参阅

- [Visual Basic 语言参考](../../visual-basic/language-reference/index.md)
- [Visual Basic](../../visual-basic/index.md)
- [常量概述](../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [枚举概述](../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
