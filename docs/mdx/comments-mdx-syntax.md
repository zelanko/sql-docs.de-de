---
title: Kommentare (MDX Syntax) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 17693d0dc76dd6cb8b3a4d0c3ead9f95c0599580
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63181566"
---
# <a name="comments-mdx-syntax"></a>Kommentare (MDX-Syntax)


  Kommentare sind Textzeichenfolgen im Programmcode, die nicht ausgeführt werden. (Kommentare werden auch als Anmerkungen bezeichnet.) Sie können Kommentare dazu verwenden, Code zu dokumentieren oder Teile von MDX-Anweisungen (Multidimensional Expressions) und Skripts, für die eine Fehlerdiagnose vorgenommen wird, vorübergehend zu deaktivieren. Durch Verwenden von Kommentaren zum Dokumentieren von Code können Sie die künftige Wartung des Programmcodes vereinfachen. In Kommentaren werden häufig der Programmname, der Verfassername sowie Datumsangaben wichtiger Codeänderungen festgehalten. Sie können auch Kommentare zum Beschreiben komplexer Berechnungen oder zum Erklären einer Programmiermethode verwenden.  
  
 Für Kommentare in MDX gelten folgende Richtlinien:  
  
-   Im Kommentar können sämtliche alphanumerischen Zeichen oder Symbole verwendet werden.  Es werden alle Zeichen in einem Kommentar ignoriert.  
  
-   Es gibt keine Längenbeschränkung für einen Kommentar innerhalb einer Anweisung oder eines Skripts. Ein Kommentar kann aus einer oder mehreren Zeilen bestehen.  
  
 MDX unterstützt drei Arten von Kommentarzeichen:  
  
 // (doppelte Schrägstriche)  
 Diese Kommentarzeichen können in derselben Zeile wie der auszuführende Code oder in einer gesonderten Zeile verwendet werden. Der gesamte Text ab den beiden Schrägstrichen bis zum Ende der Zeile ist Teil des Kommentars. Bei einem Kommentar, der sich über mehrere Zeilen erstreckt, muss jede der Kommentarzeilen mit doppelten Schrägstrichen beginnen. Weitere Informationen finden Sie unter [ &#40;Kommentar&#41; &#40;MDX&#41;](../mdx/comment-mdx-double-slash.md).  
  
 -- (doppelte Bindestriche)  
 Diese Kommentarzeichen können in derselben Zeile wie der auszuführende Code oder in einer gesonderten Zeile verwendet werden. Der gesamte Text zwischen den doppelten Bindestrichen und dem Ende der Zeile ist Teil des Kommentars. Bei einem Kommentar, der sich über mehrere Zeilen erstreckt, muss jede der Kommentarzeilen mit doppelten Bindestrichen beginnen. Weitere Informationen finden Sie unter [-- &#40;Kommentar&#41; &#40;MDX&#41;](../mdx/comment-mdx-operator-reference.md).  
  
 /* ... \*/ (Schrägstrich / Sternchen-Zeichenpaare)  
 Diese Kommentarzeichen können in der gleichen Zeile wie Code ausgeführt werden, in den Zeilen, die eigenständig oder sogar innerhalb von ausführbarem Code verwendet werden. Alles, was aus dem öffnenden kommentarzeichenpaar (/\*), zum schließenden kommentarzeichenpaar (\*/) wird als Teil des Kommentars betrachtet. Für einen mehrzeiligen Kommentar, der Open kommentarzeichenpaar (/\*) muss der Kommentar, und das Schließen Kommentarzeichen beginnen (\*/) Enden des Kommentars. Die Zeilen des Kommentars dürfen keine anderen Kommentarzeichen enthalten. Weitere Informationen finden Sie unter [/ *... \*/ (Kommentar)](../mdx/comment-mdx.md).  
  
## <a name="example"></a>Beispiel  
 Die folgende Abfrage zeigt Beispiele für alle drei Kommentartypen:  
  
 `//An example of a comment using the double-forward slash`  
  
 `--An example of a comment using the double-hypen`  
  
 `/*An example of a`  
  
 `multi-line`  
  
 `comment*/`  
  
 `SELECT`  
  
 `{[Measures].[Internet Sales Amount]}`  
  
 `ON Columns,`  
  
 `[Date].[Calendar].MEMBERS`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Syntaxelemente &#40;MDX&#41;](../mdx/mdx-syntax-elements-mdx.md)  
  
  
