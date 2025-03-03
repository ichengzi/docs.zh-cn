---
title: String 数据类型
ms.date: 07/20/2015
f1_keywords:
- vb.String
helpviewer_keywords:
- strings [Visual Basic], character
- strings [Visual Basic], fixed-length
- string keyword [Visual Basic]
- fixed-length strings [Visual Basic], string data type
- literals [Visual Basic], string
- text [Visual Basic], String data type
- $ identifier type character
- String data type
- fixed-length strings
- string literals [Visual Basic]
- data types [Visual Basic], assigning
- String literals [Visual Basic]
- identifier type characters [Visual Basic], $
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
ms.openlocfilehash: c2c6f9632646c432abb7b6da8887253e526cc994
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343912"
---
# <a name="string-data-type-visual-basic"></a>String 数据类型 (Visual Basic)

Holds sequences of unsigned 16-bit (2-byte) code points that range in value from 0 through 65535. Each *code point*, or character code, represents a single Unicode character. A string can contain from 0 to approximately two billion (2 ^ 31) Unicode characters.  
  
## <a name="remarks"></a>备注  

 Use the `String` data type to hold multiple characters without the array management overhead of `Char()`, an array of `Char` elements.  
  
 The default value of `String` is `Nothing` (a null reference). Note that this is not the same as the empty string (value `""`).  
  
## <a name="unicode-characters"></a>Unicode 字符  

 The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard. These first 128 code points are the same as those the ASCII character set defines. The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions. Unicode uses the remaining code points (256-65535) for a wide variety of symbols. This includes worldwide textual characters, diacritics, and mathematical and technical symbols.  
  
 You can use methods such as <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on an individual character in a `String` variable to determine its Unicode classification.  
  
## <a name="format-requirements"></a>格式要求  

 You must enclose a `String` literal within quotation marks (`" "`). If you must include a quotation mark as one of the characters in the string, you use two contiguous quotation marks (`""`). 下面的示例阐释了这一点。  
  
```vb  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 Note that the contiguous quotation marks that represent a quotation mark in the string are independent of the quotation marks that begin and end the `String` literal.  
  
## <a name="string-manipulations"></a>String Manipulations  

 Once you assign a string to a `String` variable, that string is *immutable*, which means you cannot change its length or contents. When you alter a string in any way, Visual Basic creates a new string and abandons the previous one. The `String` variable then points to the new string.  
  
 You can manipulate the contents of a `String` variable by using a variety of string functions. The following example illustrates the <xref:Microsoft.VisualBasic.Strings.Left%2A> function  
  
```vb  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 A string created by another component might be padded with leading or trailing spaces. If you receive such a string, you can use the <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, and <xref:Microsoft.VisualBasic.Strings.RTrim%2A> functions to remove these spaces.  
  
 For more information about string manipulations, see [Strings](../../../visual-basic/programming-guide/language-features/strings/index.md).  
  
## <a name="programming-tips"></a>编程提示  
  
- **Negative Numbers.** Remember that the characters held by `String` are unsigned and cannot represent negative values. In any case, you should not use `String` to hold numeric values.  
  
- **Interop Considerations.** If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that string characters have a different data width (8 bits) in other environments. If you are passing a string argument of 8-bit characters to such a component, declare it as `Byte()`, an array of `Byte` elements, instead of `String` in your new Visual Basic code.  
  
- **Type Characters.** Appending the identifier type character `$` to any identifier forces it to the `String` data type. `String` has no literal type character. However, the compiler treats literals enclosed in quotation marks (`" "`) as `String`.  
  
- **Framework Type.** The corresponding type in the .NET Framework is the <xref:System.String?displayProperty=nameWithType> class.  
  
## <a name="see-also"></a>请参阅

- <xref:System.String?displayProperty=nameWithType>
- [数据类型](../../../visual-basic/language-reference/data-types/index.md)
- [Char 数据类型](../../../visual-basic/language-reference/data-types/char-data-type.md)
- [类型转换函数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [转换摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [如何：调用采用无符号类型的 Windows 函数](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [有效使用数据类型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
