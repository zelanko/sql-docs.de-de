---
title: Grundlegende Konzepte in MDX (Analysis Services) | Microsoft-Dokumentation
ms.date: 04/19/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a402c385be8c89f71824e5312ffc57fd6c1b0a2c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65357330"
---
# <a name="key-concepts-in-mdx-analysis-services"></a>Schlüsselkonzepte in MDX (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Bevor Sie mehrdimensionale Daten mit MDX (Multidimensional Expressions) abfragen können oder MDX-Ausdrücke zur Verwendung in einem Cubes zu erstellen, sollten Sie sich mit Konzepten und Begriffen der Mehrdimensionalität vertraut machen.  
  
 Wir beginnen hierzu mit einem Beispiel für Datenzusammenfassung, das Sie bereits kennen, und stellen anschließend den Bezug zu MDX her. Hier ist ein PivotTable in Excel, mit Daten aus einer Analysis Services-Beispielcube gefüllt.  
  
 ![PivotTable mit Measures und Dimensionen als Legende](../../../analysis-services/multidimensional-models/media/ssas-keyconcepts-pivot1-measures-dimensions.png "PivotTable mit Measures und Dimensionen als Legende")  
  
## <a name="measures-and-dimensions"></a>Measures und Dimensionen  
 Ein Analysis Services-Cube besteht aus Measures, Dimensionen und Dimensionsattributen, die allesamt im PivotTable-Beispiel vorhanden sind.  
  
 **Measures** sind numerische Datenwerte aus Zellen, die als Summe, Anzahl, Prozentsatz, min, max oder Durchschnitt aufgezählt werden. Measure-Werte sind dynamisch und werden in Echtzeit anhand der Navigation und Interaktion von Benutzern in der PivotTable berechnet. In diesem Beispiel enthalten die Zellen steigende oder sinkende Reseller Sales-Werte, je nachdem, ob Sie die Achsen erweitern oder reduzieren. Sie können Reseller Sales-Werte summiert im jeweiligen Kontext für beliebige Kombinationen aus Datum (Jahr, Quartal, Monat oder Datum) und Vertriebsgebiet (Ländergruppe, Land, Region) abrufen. Measures werden auch als Fakten (in Data Warehouses) und berechnete Felder (in Tabellen- und Exceldatenmodellen) bezeichnet.  
  
 **Dimensions** befinden sich auf den Spalten- und Zeilenachsen einer PivotTable, und geben die Bedeutung eines Measure an. Dimensionen sind das Gegenstück zu Tabellen in relationalen Datenmodellen. Typische Beispiele für Dimensionen sind Zeit, Geografie, Produkte, Kunden, Mitarbeiter usw. Das aktuelle Beispiel enthält zwei Dimensionen: Vertriebsgebiet in den Zeilen und Datum in den Spalten. Sie könnten jedoch jederzeit weitere Dimensionen für Reseller Sales per Ziehen und Ablegen hinzufügen, um die Vertriebsleistung für diese Dimensionen anzuzeigen, wie z. B. Angebote oder Produkte. Die Möglichkeit zur Erkundung der Daten auf interessante Arten hängt von Ihren Dimensionen sowie von deren Verknüpfung mit Faktentabellen in Ihrer Datenquelle ab.  
  
 **Dimension-Attribute** sind benannte Elemente innerhalb einer Dimension, ähnlich wie Spalten in einer Tabelle. In diesem Fall bestehen die Dimensionsattribute für das Vertriebsgebiet aus Ländergruppen (Europa, Nordamerika, Pazifik), Ländern (Kanada, USA) und Regionen (Zentral, Nordost, Nordwest, Südost, Südwest).  
  
 Mit jedem Attribut ist eine Sammlung von Datenwerten oder Elementen verknüpft. Elemente des Ländergruppen-Attributs sind in diesem Fall Europa, Nordamerika und Pazifik. **Members** beziehen sich auf die tatsächlichen Datenwerte eines Attributs.  
  
> [!NOTE]  
>  Ein Aspekt der Datenmodellierung ist die Formalisierung von Mustern und Beziehungen, die bereits zwischen den eigentlichen Daten existieren. Bei der Arbeit mit Daten, die eine natürliche Hierarchie haben, wie im aktuellen Beispiel Länder-Regionen-Städte, können Sie diese Beziehung durch die Erstellung einer **Attributbeziehung**formalisieren. Eine attributbeziehung ist eine 1: n Beziehung zwischen Attributen, z. B. eine Beziehung zwischen einem Land- und einem Stadt - ein Land enthält viele Städte, aber jede Stadt gehört zu genau einem Land. Attributbeziehungen im Modell beschleunigt die abfrageleistung verbessert werden, daher ist es eine bewährte Methode, die sie erstellen, wenn die Daten dies unterstützen. Sie können Attributbeziehungen auch im Dimensions-Designer in den SQL Server Data Tools erstellen. Siehe [Define Attribute Relationships](../../../analysis-services/multidimensional-models/attribute-relationships-define.md).  
  
 Modell-Metadaten werden in Excel in der Feldliste der PivotTable angezeigt.  Vergleichen Sie die obige PivotTable mit der folgenden Feldliste. Beachten Sie, dass die Feldliste Vertriebsgebiet, Gruppe, Land, Region (Metadaten) enthält, und die PivotTable dagegen nur die Elemente (Datenwerte). Wenn Sie die Symbole kennen, können Sie die Teile von mehrdimensionalen Modellen schnell und einfach einer PivotTable in Excel zuordnen.  
  
 ![PivotTable-Feldliste](../../../analysis-services/multidimensional-models/mdx/media/ssas-keyconcepts-ptfieldlist.png "PivotTable-Feldliste")  
  
## <a name="attribute-hierarchies"></a>Attributhierarchien  
 Sie wissen beinahe intuitiv, welche Werte in einer PivotTable steigen oder fallen, wenn Sie die Werte auf den Achsen erweitern und reduzieren. Warum ist dies so? Die Antwort liegt in den Attributhierarchien.  
  
 Reduzieren Sie alle Achsenwerte und sehen Sie sich die Gesamtsummen der einzelnen Ländergruppen und Kalenderjahre an. Dieser Wert wird vom sogenannten **(Alle-) Element** innerhalb einer Hierarchie abgeleitet. Das (Alle)-Element ist der berechnete Wert aller Elemente in einer Attributhierarchie .  
  
-   Das (Alle)-Element für alle Ländergruppen und Daten kombiniert ist $80.450.596,98  
  
-   Das (Alle)-Element für CY2008 ist $16,038.062,60  
  
-   Das (Alle)-Element für Pazifik ist $1,594,335.38  
  
 Diese Art von Aggregationen werden vorberechnet und gespeichert, was einen Teil zur schnellen Abfrageleistung von Analysis Services beiträgt.  
  
 ![PivotTable mit alle-Element als Legende](../../../analysis-services/multidimensional-models/mdx/media/ssas-keyconcepts-pivot2-allmember.png "PivotTable mit alle-Element als Legende")  
  
 Erweitern Sie die Hierarchie, um bis zur niedrigsten Ebene vorzudringen. Dieses Element wird als **Blattelement**bezeichnet. Ein Blattelement ist ein Element einer Hierarchie, das keine untergeordneten Elemente besitzt. In diesem Beispiel hat das Blattelement Südwesten ist.  
  
 ![PivotTable mit untergeordneten Element als Legende](../../../analysis-services/multidimensional-models/mdx/media/ssas-keyconcepts-pivot3-leafparent.PNG "PivotTable mit untergeordneten Element als Legende")  
  
 Alle übergeordneten Elemente nennt man einfach **übergeordnetes Element**. Vereinigte Staaten ist das übergeordnete Element des Südwesten.  
  
 **Komponenten einer Attributhierarchie**  
  
 All diese Konzepte zusammen ergeben das Konzept einer **Attributhierarchie**. Eine Attributhierarchie ist eine Hierarchie von Attributelementenmit den folgenden Ebenen:  
  
-   Eine Blattebene, die die verschiedenen Attributelemente enthält. Die Elemente der Blattebene werden auch als **Blattelemente**bezeichnet.  
  
-   Zwischenebenen, wenn es sich bei der Attributhierarchie um eine Über-/Unterordnungshierarchie handelt (mehr dazu später).  
  
-   Ein (Alle)-Element, das die aggregierten Werte aller untergeordneten Attribute enthält. Sie können optional ausblenden oder Deaktivieren der Ebene (alle), wenn es sinnvoll für die Daten nicht. Angenommen, obwohl der Produktcode numerisch ist, wäre nicht es sinnvoll, sum, average oder alle Produktcodes.  
  
> [!NOTE]  
>  BI-Entwickler verwenden oft Eigenschaften in der Attributhierarchie, um ein bestimmtes Verhalten in Clientanwendungen zu erreichen oder um Leistungsvorzüge umzusetzen. Legen Sie z. B. AttributeHierarchyEnabled = False für Attribute, die für die das (alle)-Element keinen Sinn. Alternativ können Sie das (Alle)-Element einfach ausblenden. In diesem Fall würden Sie AttributeHierarchyVisible=False setzen. Weitere Details zu Eigenschaften finden Sie unter [Dimension Attribute Properties Reference](../../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md) .  
  
## <a name="navigation-hierarchies"></a>Navigationshierarchien  
 In der PivotTable (zumindest in diesem Beispiel) werden Zeilen- und Spaltenachsen erweitert, um niedrigere Ebenen von Attributen anzuzeigen. Sie können Navigationshierarchien in einem Modell erstellen, um einen erweiterbaren Baum zu erhalten.  Im AdventureWorks-Beispielmodell hat die Vertriebsgebiet-Dimension eine Hierarchie mit mehreren Ebenen von Ländergruppe über Land zu Region.  
  
 Hierarchien werden also verwendet, um einen Navigationspfad in einer PivotTable oder anderen Objekten für die Datenzusammenfassung anzugeben. Es gibt zwei grundlegende Typen von Hierarchien: ausgeglichene und unausgeglichene Hierarchien.  
  
 **Ausgeglichene Hierarchien**  
  
|||  
|-|-|  
|![PivotTable mit ausgeglichener Hierarchie als Legende](../../../analysis-services/multidimensional-models/mdx/media/ssas-keyconcepts-pivot4-balancedhierarchy.PNG "PivotTable mit ausgeglichener Hierarchie als Legende")|Eine **ausgeglichene Hierarchie** ist eine Hierarchie, in der zwischen der obersten Ebene und jedem Blattelement die gleiche Anzahl von Ebenen liegen.<br /><br /> Eine **natürliche Hierarchie** entsteht natürlich aus den zugrunde liegenden Daten. Typische Beispiele sind Land-Region-Stadt, Jahr-Monat-Tag oder Kategorie-Unterkategorie-Modell. In diesen Fällen wird jede untergeordnete Ebene auf absehbare Weise von der vorherigen Ebene abgeleitet.<br /><br /> Mehrdimensionale Modelle enthalten hauptsächlich ausgeglichene Hierarchien, von denen viele außerdem auch natürliche Hierarchien sind.<br /><br /> Ein weiterer Modellierungsbegriff ist **benutzerdefinierte Hierarchie**, der oft als Kontrast zu Attributhierarchien verwendet werden. Dies bezeichnet alle vom BI-Entwickler erstellten Hierarchien im Gegensatz zu den automatisch von Analysis Services bei der Defintion von Attributen erstellten Attributhierarchien.|  
  
 **Unausgeglichene Hierarchien**  
  
|||  
|-|-|  
|![PivotTable mit unregelmäßiger Hierarchie als Legende](../../../analysis-services/multidimensional-models/mdx/media/ssas-keyconcepts-pivot15-raggedhierarchy.PNG "PivotTable mit unregelmäßiger Hierarchie als Legende")|Eine **unregelmäßige Hierarchie** oder **unausgeglichene Hierarchie** ist eine Hierarchie, in der zwischen der obersten Ebene und den Blattelementen unterschiedlich viele Ebenen liegen. In diesem Fall es ist eine Hierarchie von BI-Entwickler erstellt, aber in diesem Fall Lücken in den Daten vorhanden sind.<br /><br /> Im AdventureWorks-Beispielmodell enthält das Vertriebsgebiet eine unregelmäßige Hierarchie, da in den USA eine zusätzliche Ebene existiert (Regionen), die für die anderen Länder in diesem Beispiel nicht gilt.<br /><br /> Unregelmäßige Hierarchien sind eine Herausforderung für BI-Entwickler, wenn die Clientanwendung diese nicht auf elegante Art verarbeiten kann. Im Analysis Services-Modell können Sie eine **Über-/Unterordnungshierarchie** erstellen, die eine Beziehung zwischen mehreren Datenebenen explizit definiert und somit Mehrdeutigkeiten bzgl. der Abfolge der Ebenen ausräumt. Details finden Sie unter [Über- und untergeordnete Dimensionen](../../../analysis-services/multidimensional-models/parent-child-dimension.md) .|  
  
## <a name="key-attributes"></a>Schlüsselattribute  
 Modelle sind Sammlungen miteinander verwandter Objekte, deren Zuordnungen mit Schlüsseln und Indizes verwaltet werden. Analysis Services-Modelle funktionieren auf dieselbe Weise. Für jede Dimension (Äquivalent zu Tabellen im relationalen Modell) existiert ein Schlüsselattribut. Das **Schlüsselattribut** wird in Fremdschlüssel-Beziehungen zur Faktentabelle (Measuregruppe) verwendet. Alle nicht-Schlüsselattribute in der Dimension werden (direkt oder indirekt) mit dem Schlüsselattribut verknüpft.  
  
 Das Schlüsselattribut ist oft, jedoch nicht immer, gleichzeitig auch das **Granularitätsattribut**. Granularität bezieht sich auf die Detail- oder Genauigkeitsebene der Daten. Ein schnelles Beispiel hilft auch hier beim besseren Verständnis. Berücksichtigen Sie Datumswerte aus: Für die täglichen Verkäufe müssen Sie die Werte, die bis zum Tag Datum; für Kontingente vierteljährlich kann ausreichend sein, aber wenn Ihre Analysedaten aus rennergebnissen von Sportereignissen besteht, die Auflösung möglicherweise sehr gut Millisekunden. Die Genauigkeitsebene Ihrer Datenwerte nennt man auch die Körnung.  
  
 Währung ist ein weiteres Beispiel: eine finanzanwendung kann monetärer Werte aus vielen Dezimalstellen, verfolgen, während Ihrer lokalen Schule Kurator nur Werte vollständigen Dollarbetrag möglicherweise. Das Konzept der Körnung ist wichtig, um die Speicherung unnötiger Daten zu vermeiden. Indem Sie Millisekunden von einem Zeitstempel oder Cents von einem Verkaufsbetrag abschneiden, können Sie Speicherungs- und Verarbeitungszeit sparen, wenn der jeweilige Detailgrad für Ihre Analyse nicht relevant ist.  
  
 Sie können das Granularitätsattribut in der Registerkarte Dimensionsverwendung im Cube-Designer in den SQL Server Data Tools einstellen. Im AdventureWorks-Beispielmodell ist das Schlüsselattribut der Datums-Dimension der Datums-Schlüssel. Für Verkaufsaufträge ist das Granularitätsattribut gleich dem Schlüsselattribut. Für Vertriebsziele wird die Granularität vierteljährlich verwendet, und das Granularitätsattribut wird entsprechend auf Kalenderquartal gesetzt.  
  
 ![Modell zur Anzeige des granularitätsattributs](../../../analysis-services/multidimensional-models/mdx/media/ssas-keyconcepts-granularityattrib.png "Modell zur Anzeige des granularitätsattributs")  
  
> [!NOTE]  
>  Wenn Granularitätsattribut und Schlüsselattribut unterschiedlich sind, müssen alle Nichtschlüsselattribute direkt oder indirekt mit dem Granularitätsattribut verlinkt sein. Innerhalb eines Cubes definiert das Granularitätsattribut die Granularität einer Dimension.  
  
## <a name="query-scope-cube-space"></a>Abfragebereich (Cuberaum)  
 Der Bereich einer Abfrage gibt die Grenzen für die auszuwählenden Daten an. Der Bereich kann vom gesamten Cube (Cubes sind die größten Abfrageobjekte) zu einer einzelnen Zelle reichen.  
  
 Der**Cuberaum** ist das Produkt aus den Elementen der Attributhierarchien eines Cubes und den Measures des Cubes.  
  
 **Subcube** ist ein Teilsatz eines Cubes, der eine gefilterte Ansicht des Cubes darstellt. Teilcubes können mithilfe von SCOPE-Anweisungen in einem MDX-Berechnungsskript oder mithilfe untergeordneter SELECT-Klauseln in einer MDX-Abfrage oder als ein Sitzungscube definiert werden.  
  
 **Cell** bezieht sich auf den Abstand an einem Schnittpunkt eines Elements des Measuedimensionselements und eines Elements der einzelnen Attributhierarchien in einem Cube.  
  
## <a name="other-modeling-terms"></a>Weitere Modellierungsbegriffe  
 In diesem Abschnitt ist eine Sammlung von Konzepten und Begriffen, die nicht einfach in die anderen Abschnitte passen, jedoch müssen Sie dennoch kennen.  
  
 **Berechnetes Element** bezeichnet ein Dimensionselement, das zum Abfragezeitpunkt definiert und berechnet wird. Ein berechnetes Element kann in einer Benutzerabfrage oder in einem MDX-Berechnungsskript definiert und auf dem Server gespeichert werden. Ein berechnetes Element entspricht Zeilen in der Dimensionstabelle der Dimension, in der diese definiert sind.  
  
 **Distinct Count** ist ein spezieller Measuretyp, der für Datenelemente verwendet wird, die nur einmal gezählt werden sollen. Das AdventureWorks-Beispielmodell enthält Distinct Count Measures für Internetbestellungen, Wiederverkäuferbestellungen und Verkaufsaufträge.  
  
 **Measuregruppen** sind eine Sammlung von einem oder mehreren Measures. Diese Gruppen sind normalerweise benutzerdefiniert und werden zum Gruppieren verwandter Measures verwendet. Distinct Count Measures sind eine Ausnahme. Diese Measures sind immer Teil einer speziellen Measuregruppe, die nur distinct Measures enthält. Die Measuregruppe, in der PivotTable-beispielabbildung nicht angezeigt, aber es wird als eine benannte Auflistung von Measures in einer PivotTable-Feldliste angezeigt.  
  
 **Measuredimension** ist die Dimension, die alle Measures in einem Cube enthält. Es ist nicht verfügbar in einem mehrdimensionalen Modell, die Sie in SQL Server Data Tools erstellen, aber es genauso vorhanden ist. Da diese Dimension Measures enthält, werden alle Elemente einer Measuredimension normalerweise aggregiert (typischerweise als Summe oder Anzahl).  
  
 **Datenbankdimensionen und Cubedimensionen**. In Modellen können Sie eigenständige Dimensionen definieren, die anschließend in einer beliebigen Anzahl von Cubes im gleichen Modell integriert werden. Wenn Sie eine Dimension einem Cube hinzufügen, es eine Cubedimension genannt. Selbst in einem Projekt als eigenständiges Element im Objekt-Explorer wird dies eine Datenbankdimension bezeichnet. Warum die Unterscheidung? Da Sie Eigenschaften der Dimensionen unabhängig voneinander setzen können. In der Produktdokumentation sehen Sie beide Begriffe verwendet, daher ist es sinnvoll sein, zu deren Bedeutung kennen.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Sie kennen nun die wichtigsten Konzepte und Begriffe und können mit diesen zusätzlichen Themen fortfahren, in denen grundlegende Konzepte von Analysis Services weiter erläutert werden:  
  
-   [Die grundlegende MDX-Abfrage &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-the-basic-query.md)  
  
-   [Grundlegendes MDX-Skript &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/the-basic-mdx-script-mdx.md)  
  
-   [Mehrdimensionale Modellierung &#40;Adventure Works-Tutorial&#41;](../../../analysis-services/multidimensional-tutorial/multidimensional-modeling-adventure-works-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Cube Space](../../../analysis-services/multidimensional-models/mdx/cube-space.md)   
 [Tupel](../../../analysis-services/multidimensional-models/mdx/tuples.md)   
 [Autoexists](../../../analysis-services/multidimensional-models/mdx/autoexists.md)   
 [Verwenden von Elementen, Tupeln und Mengen &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)   
 [Sichtbare Gesamtwerte und nicht sichtbare Gesamtwerte](../../../analysis-services/multidimensional-models/mdx/visual-totals-and-non-visual-totals.md)   
 [Grundlegendes zu MDX-Abfragen &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)   
 [Grundlegendes zu MDX-Skripts &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)   
 [MDX-Sprachreferenz &#40;MDX&#41;](../../../mdx/mdx-language-reference-mdx.md)   
 [Mehrdimensionale Ausdrücke &#40;MDX&#41; – Referenz](../../../mdx/multidimensional-expressions-mdx-reference.md)  
  
  
