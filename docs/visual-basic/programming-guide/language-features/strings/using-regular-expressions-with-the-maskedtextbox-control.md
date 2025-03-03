---
title: 在 MaskedTextBox 控件中使用正则表达式
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
ms.openlocfilehash: 12d500fa0ff4945dcf2d5009bdba6d337834707e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346267"
---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>在 MaskedTextBox 控件中使用正则表达式 (Visual Basic)
This example demonstrates how to convert simple regular expressions to work with the <xref:System.Windows.Forms.MaskedTextBox> control.  
  
## <a name="description-of-the-masking-language"></a>Description of the Masking Language  
 The standard <xref:System.Windows.Forms.MaskedTextBox> masking language is based on the one used by the `Masked Edit` control in Visual Basic 6.0 and should be familiar to users migrating from that platform.  
  
 The <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> property of the <xref:System.Windows.Forms.MaskedTextBox> control specifies what input mask to use. The mask must be a string composed of one or more of the masking elements from the following table.  
  
|Masking element|描述|Regular expression element|  
|---------------------|-----------------|--------------------------------|  
|0|Any single digit between 0 and 9. Entry required.|\d|  
|9|Digit or space. Entry optional.|[ \d]?|  
|#|Digit or space. Entry optional. If this position is left blank in the mask, it will be rendered as a space. Plus (+) and minus (-) signs are allowed.|[ \d+-]?|  
|L|ASCII letter. Entry required.|[a-zA-Z]|  
|?|ASCII letter. Entry optional.|[a-zA-Z]?|  
|&|字符。 Entry required.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]|  
|C|字符。 Entry optional.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]?|  
|包含当前请求的 URL 的|Alphanumeric. Entry optional.|\W|  
|方法。|Culture-appropriate decimal placeholder.|不可用。|  
|,|Culture-appropriate thousands placeholder.|不可用。|  
|:|Culture-appropriate time separator.|不可用。|  
|/|Culture-appropriate date separator.|不可用。|  
|$|Culture-appropriate currency symbol.|不可用。|  
|\<|Converts all characters that follow to lowercase.|不可用。|  
|>|Converts all characters that follow to uppercase.|不可用。|  
|&#124;|Undoes a previous shift up or shift down.|不可用。|  
|&#92;|Escapes a mask character, turning it into a literal. "\\\\" is the escape sequence for a backslash.|&#92;|  
|All other characters.|Literals. All non-mask elements will appear as themselves within <xref:System.Windows.Forms.MaskedTextBox>.|All other characters.|  
  
 The decimal (.), thousandths (,), time (:), date (/), and currency ($) symbols default to displaying those symbols as defined by the application's culture. You can force them to display symbols for another culture by using the <xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A> property.  
  
## <a name="regular-expressions-and-masks"></a>Regular Expressions and Masks  
 Although you can use regular expressions and masks to validate user input, they are not completely equivalent. Regular expressions can express more complex patterns than masks, but masks can express the same information more succinctly and in a culturally relevant format.  
  
 The following table compares four regular expressions and the equivalent mask for each.  
  
|正则表达式|掩码|注意|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|The `/` character in the mask is a logical date separator, and it will appear to the user as the date separator appropriate to the application's current culture.|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|A date (day, month abbreviation, and year) in United States format in which the three-letter month abbreviation is displayed with an initial uppercase letter followed by two lowercase letters.|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|United States phone number, area code optional. If the user does not wish to enter the optional characters, she can either enter spaces or place the mouse pointer directly at the position in the mask represented by the first 0.|  
|`$\d{6}.00`|`$999,999.00`|A currency value in the range of 0 to 999999. The currency, thousandth, and decimal characters will be replaced at run-time with their culture-specific equivalents.|  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>
- <xref:System.Windows.Forms.MaskedTextBox>
- [在 Visual Basic 中验证字符串](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
- [MaskedTextBox 控件](../../../../framework/winforms/controls/maskedtextbox-control-windows-forms.md)
