---
title: Angeben eines Speicherort Pfads (SQLXML 4,0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- absolute location path
- node-set [SQLXML]
- XPath queries [SQLXML], location paths
- relative location path [SQLXML]
- location path for XPath query
ms.assetid: a23a2b75-bc69-49f0-99db-05e14dc15bc0
author: rothja
ms.author: jroth
ms.openlocfilehash: 01e1a7f897bae25c6cf483e822a6572528e44913
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85015262"
---
# <a name="specifying-a-location-path-sqlxml-40"></a>Angeben eines Speicherortpfads (SQLXML 4.0)
  XPath-Abfragen werden in Form eines Ausdrucks angegeben. Es gibt verschiedene Arten von Ausdrücken. Ein Speicherortpfad ist ein Ausdruck, der relativ zum Kontextknoten einen Satz von Knoten auswählt. Das Ergebnis der Auswertung eines Speicherortpfads ist ein Knotensatz.  
  
## <a name="types-of-location-paths"></a>Typen von Speicherortpfaden  
 Ein Speicherortpfad kann eine dieser beiden Formen haben:  
  
-   **Absoluter Speicherortpfad**  
  
     Ein absoluter Speicherortpfad beginnt am Stammknoten des Dokuments. Er besteht aus einem Schrägstrich (/) optional gefolgt von einem relativen Speicherortpfad. Der Schrägstrich (/) wählt den Stammknoten des Dokuments aus.  
  
-   **Relativer Speicherortpfad**  
  
     Ein relativer Speicherortpfad beginnt am Kontextknoten im Dokument. Ein Speicherortpfad besteht aus einer Folge von einem oder mehreren Positionsschritten, die durch einen Schrägstrich (/) getrennt sind. Jeder Schritt wählt relativ zum Kontextknoten einen Satz von Knoten aus. Die Anfangsschrittsequenz wählt relativ zu einem Kontextknoten einen Satz von Knoten aus. Jeder Knoten in diesem Satz wird als Kontextknoten für den folgenden Schritt verwendet. Die Knotensätze, die von diesem Schritt identifiziert werden, werden verknüpft. Beispielsweise wählt **Child:: Order/Child:: OrderDetail** die untergeordneten-Elemente der untergeordneten- **\<OrderDetail>** **\<Order>** Elemente des Kontext Knotens aus.  
  
    > [!NOTE]  
    >  In der SQLXML 4.0-Implementierung von XPath beginnt jede XPath-Abfrage am Stammkontext, selbst wenn der XPath nicht ausdrücklich absolut ist. Zum Beispiel wird eine XPath-Abfrage, die mit "Customer" beginnt, als "/Customer" behandelt. In der XPath-Abfrage **Customer [Order]** beginnt Customer am Stamm Kontext, aber die Reihenfolge beginnt im Kunden Kontext. Weitere Informationen finden Sie unter [Einführung in die Verwendung von XPath-Abfragen &#40;SQLXML 4,0&#41;](../introduction-to-using-xpath-queries-sqlxml-4-0.md).  
  
## <a name="location-steps"></a>Positionsschritte  
 Ein Speicherortpfad (absolut oder relativ) besteht aus Positionsschritten, die drei Teile enthalten:  
  
-   **Achse**  
  
     Die Achse gibt die Strukturbeziehung zwischen den vom Positionsschritt ausgewählten Knoten und dem Kontextknoten an. Die Achsen `parent`, `child`, `attribute` und `self` werden unterstützt. Falls eine `child`-Achse im Speicherortpfad angegeben ist, sind alle von der Abfrage ausgewählten Knoten dem Kontextknoten untergeordnet. Wird eine `parent`-Achse angegeben, ist der ausgewählte Knoten der übergeordnete Knoten des Kontextknotens. Bei einer `attribute`-Achse sind die ausgewählten Knoten die Attribute des Kontextknotens.  
  
-   **Knoten Test**  
  
     Ein Knotentest gibt den vom Positionsschritt ausgewählten Knotentyp an. Jede Achse (`child`, `parent`, `attribute` oder `self`) hat einen Hauptknotentyp. Für die- `attribute` Achse ist der Haupt Knotentyp **\<attribute>** . Für die `parent` `child` Achsen, und `self` ist der Haupt Knotentyp **\<element>** .  
  
     Wenn der Speicherort Pfad z. b. **Child:: Customer**angibt, werden die untergeordneten- **\<Customer>** Elemente des Kontext Knotens ausgewählt. Da die `child` Achse **\<element>** als Hauptknotentyp gilt, ist der Knoten Test Customer, wenn Customer ein **\<element>** Knoten ist.  
  
-   **Auswahlprädikate (Null oder mehr)**  
  
     Ein Prädikat filtert einen Knotensatz in Bezug auf eine Achse. Die Angabe von Auswahlprädikaten in einem XPath-Ausdruck entspricht der Angabe einer WHERE-Klausel in einer SELECT-Anweisung. Das Prädikat wird zwischen Klammern angegeben. Wird der in den Auswahlprädikaten angegebene Test angewendet, werden die vom Knotentest zurückgegebenen Knoten gefiltert. Für jeden Knoten in der zu filternden Knotengruppe wird der Prädikatausdruck mit dem entsprechenden Knoten als Kontextknoten ausgewertet. Die Anzahl der Knoten in der Knotengruppe dient dabei als Kontextgröße. Ergibt die Auswertung des Prädikatausdrucks für den betreffenden Knoten TRUE, wird dieser Knoten in die resultierende Knotengruppe aufgenommen.  
  
     Die Syntax für einen Positionsschritt umfasst den Achsennamen und den Knotentest, getrennt durch zwei Doppelpunkte (::) und gefolgt von null oder mehr Ausdrücken in eckigen Klammern. Beispielsweise wählt der XPath-Ausdruck (Speicherort Pfad) **Child:: Customer [ @CustomerID = ' ALFKI ']** alle untergeordneten **\<Customer>** Elemente des Kontext Knotens aus. Anschließend wird der Test im Prädikat auf den Knoten Satz angewendet, der nur die **\<Customer>** Elementknoten mit dem Attribut Wert "ALFKI" für das zugehörige **CustomerID-** Attribut zurückgibt.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Angeben einer Achse &#40;SQLXML 4,0&#41;](specifying-an-axis-sqlxml-4-0.md)  
 Enthält Beispiele zur Angabe einer Achse.  
  
 [Angeben eines Knoten Tests im Speicherort Pfad &#40;SQLXML 4,0&#41;](specifying-a-node-test-in-the-location-path-sqlxml-4-0.md)  
 Enthält Beispiele zur Angabe eines Knotentests.  
  
 [Angeben von Auswahl Prädikaten im Speicherort Pfad &#40;SQLXML 4,0&#41;](specifying-selection-predicates-in-the-location-path-sqlxml-4-0.md)  
 Enthält Beispiele zur Angabe von Auswahlprädikaten.  
  
  
