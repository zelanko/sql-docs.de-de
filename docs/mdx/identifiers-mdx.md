---
title: Bezeichner (MDX) | Microsoft-Dokumentation
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7562beb2cccd94853c346aaf2f1be1886a2e3ac5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63224953"
---
# <a name="identifiers-mdx"></a>Bezeichner (MDX)


  Ein Bezeichner ist der Name eines Analysis Services-Objekts. Jedes Objekt kann und muss einen Bezeichner haben. Dies gilt für Cubes, Dimensionen, Hierarchien, Ebenen, Elemente usw. Sie verwenden den Bezeichner eines Objekts, um in MDX-Anweisungen (Multidimensional Expressions) auf das Objekt zu verweisen.  
  
 Abhängig davon, wie Sie ein Objekt benennen, ist der Objektbezeichner ein regulärer oder ein Begrenzungsbezeichner.  
  
> [!NOTE]  
>  Sowohl reguläre als auch begrenzungsezeichner müssen zwischen 1 und 100 Zeichen enthalten.  
  
## <a name="using-regular-identifiers"></a>Verwenden von regulären Bezeichnern  
 Ein regulärer Bezeichner ist ein Objektname, der folgenden Formatierungsregeln für reguläre Bezeichner entspricht. Ein regulärer Bezeichner kann mit oder ohne Trennzeichen verwendet werden.  
  
### <a name="formatting-rules-for-regular-identifiers"></a>Formatierungsregeln für reguläre Bezeichner  
  
1.  Das erste Zeichen muss eines der folgenden Zeichen sein:  
  
    -   Ein Buchstabe gemäß Unicode-Standard 2.0. Neben Buchstaben aus anderen Sprachen enthält die Unicode-Definition von Buchstaben die lateinischen Buchstaben von a bis z und von A bis Z.  
  
    -   Der Unterstrich (_).  
  
2.  Im Anschluss daran können die folgenden Zeichen verwendet werden:  
  
    -   Buchstaben, wie in Unicode-Standard 2.0 definiert.  
  
    -   Dezimalzahlen aus dem lateinischen Grundalphabet oder anderen nationalen Schriften.  
  
    -   Der Unterstrich (_).  
  
3.  Der Bezeichner darf kein reserviertes MDX-Schlüsselwort sein. Für reservierte Schlüsselwörter erfolgt in MDX keine Unterscheidung nach Groß-/Kleinschreibung. Weitere Informationen finden Sie unter [reservierte Schlüsselwörter &#40;MDX-Syntax&#41;](../mdx/reserved-keywords-mdx-syntax.md).  
  
4.  Eingebettete Leerzeichen oder Sonderzeichen sind nicht zulässig.  
  
### <a name="examples-of-regular-identifiers"></a>Beispiele zu regulären Bezeichnern  
 In der folgenden MDX-Anweisung entsprechen die Bezeichner `Measures`, `Product` und `Style` den Formatierungsregeln für reguläre Bezeichner. Für diese regulären Bezeichner sind keine Trennzeichen erforderlich.  
  
 `SELECT Measures.MEMBERS ON COLUMNS,`  
  
 `Product.Style.CHILDREN ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 ``  
  
 Für reguläre Bezeichner können auch, obwohl nicht erforderlich, Trennzeichen verwendet werden. In der folgenden MDX-Anweisung wurden die regulären Bezeichner `Measures`, `Product` und `Style` mithilfe von eckigen Klammern ordnungsgemäß begrenzt.  
  
 `SELECT [Measures].MEMBERS ON COLUMNS,`  
  
 `[Product].[Style].CHILDREN ON ROWS`  
  
 `FROM [Adventure Works]`  
  
 ``  
  
## <a name="using-delimited-identifiers"></a>Verwenden von Begrenzungsbezeichnern  
 Ein Bezeichner, der nicht den Formatierungsregeln für reguläre Bezeichner entspricht, muss immer mit eckigen Klammern ([]) begrenzt sein.  
  
> [!NOTE]  
>  Trennzeichen werden ausschließlich für Bezeichner verwendet. Trennzeichen können nicht für Schlüsselwörter verwendet werden, wobei es keine Rolle spielt, ob die Schlüsselwörter in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] als reserviert gekennzeichnet sind oder nicht.  
  
 Einen Begrenzungsbezeichner verwenden Sie in folgenden Zusammenhängen:  
  
-   Wenn der Name eines Objekts oder ein Teil des Namens ein reserviertes Wort ist.  
  
     Es wird empfohlen, dass reservierte Schlüsselwörter nicht als Objektnamen verwendet werden. Datenbanken, die ein Upgrade von früheren Versionen von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] enthalten möglicherweise Bezeichner, die keine reservierten Wörter in der früheren Version enthalten, aber nun reserviert sind. So lange, bis Sie den Bezeichner des Objekts ändern können, können Sie mit dem Begrenzungsbezeichner auf das Objekt verweisen.  
  
-   Wenn für den Namen eines Objekts Zeichen verwendet werden, die nicht als qualifizierte Bezeichner aufgeführt sind.  
  
     In [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] kann für einen Begrenzungsbezeichner jedes Zeichen verwendet werden, das zur aktuellen Codepage gehört. Ein unbedachtes Verwenden von Sonderzeichen in einem Objektnamen kann allerdings dazu führen, dass MDX-Anweisungen schwierig zu lesen und zu pflegen sind.  
  
### <a name="formatting-rules-for-delimited-identifiers"></a>Formatierungsregeln für Begrenzungsbezeichner  
 Der Hauptteil eines Begrenzungsbezeichners kann jede Kombination aus Zeichen der aktuellen Codepage enthalten, einschließlich des Trennzeichens selbst. Enthält der Hauptteil eines Begrenzungsbezeichners Trennzeichen, kann ein spezieller Schritt erforderlich sein:  
  
-   Enthält der Hauptteil des Bezeichners nur eine linke eckige Klammer ([), ist kein zusätzlicher Schritt erforderlich.  
  
-   Enthält der Hauptteil des Bezeichners eine rechte eckige Klammer (]), müssen Sie zwei rechte eckige Klammern (]]) angeben.  
  
### <a name="examples-of-delimited-identifiers"></a>Beispiele zu Begrenzungsbezeichnern  
 In der folgenden hypothetischen Anweisung stellen `Sales Volume`, `Sales Cube` und `select` Begrenzungsbezeichner dar:  
  
 `-- The [Sales Volume] and [Sales Cube] identifiers contain a space.`  
  
 `SELECT Measures.[Sales Volume]`  
  
 `FROM [Sales Cube]`  
  
 `WHERE Product.[select]`  
  
 `-- The [select] identifier is a reserved keyword.`  
  
 Im nächsten Beispiel hat ein Objekt den Namen `Total Profit [Domestic]`. Zum Verweisen auf dieses Objekt müssen Sie den folgenden Begrenzungsbezeichner verwenden:  
  
 `[Total Profit [Domestic]]]`  
  
 Wie Sie sehen, musste für die linke eckige Klammer vor `Domestic` keine Änderung vorgenommen werden, um den Begrenzungsbezeichner zu erstellen. Dagegen musste die rechte eckige Klammer hinter `Domestic` durch zwei rechte eckige Klammern ersetzt werden.  
  
### <a name="delimiting-identifiers-with-multiple-parts"></a>Begrenzen von mehrteiligen Bezeichnern  
 Wenn Sie vollqualifizierte Objektnamen verwenden, ist es eventuell erforderlich, mehr als einen der Bezeichner, aus denen sich der Objektname zusammensetzt, zu begrenzen. Der Bezeichner Front Brakes im folgenden Code muss beispielsweise begrenzt werden.  
  
 SELECT [Measures].MEMBERS ON COLUMNS,  
  
 [Product].[Product].[Front Brakes] ON ROWS  
  
 FROM [Adventure Works]  
  
 Außerdem ist im vorherigen Beispiel der Bezeichner Measures begrenzt, um zu zeigen, wie mehrere Bezeichner begrenzt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [MDX-Sprachreferenz &#40;MDX&#41;](../mdx/mdx-language-reference-mdx.md)   
 [Grundlegendes zu MDX-Abfragen &#40;Analysis Services&#41;](../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)   
 [MDX-Syntaxelemente &#40;MDX&#41;](../mdx/mdx-syntax-elements-mdx.md)  
  
  
