---
title: 如何：标记语句
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: be116ac8046c43e89e44c2d9127c6131e4dfaa52
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347385"
---
# <a name="how-to-label-statements-visual-basic"></a>如何：标记语句 (Visual Basic)

Statement blocks are made up of lines of code delimited by colons. Lines of code preceded by an identifying string or integer are said to be *labeled*. Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.

Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals. A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.

The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier. If it does not, the compiler assumes it is a label.

Labels have their own declaration space and do not interfere with other identifiers. A label's scope is the body of the method. Label declaration takes precedence in any ambiguous situation.

> [!NOTE]
> Labels can be used only on executable statements inside methods.

## <a name="to-label-a-line-of-code"></a>To label a line of code

Place an identifier, followed by a colon, at the beginning of the line of source code.

For example, the following lines of code are labeled with `Jump` and `120`, respectively:

[!code-vb[VbVbalrStatements#708](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#708)]

## <a name="see-also"></a>请参阅

- [语句](../../../visual-basic/programming-guide/language-features/statements.md)
- [已声明的元素名称](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [程序结构和代码约定](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
