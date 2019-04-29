---
title: Angeben eines Speicherortpfads (SQLXML 4.0) | Microsoft-Dokumentation
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c814d1b486a7ba7736cf19119a66ab0845d33c6b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63127583"
---
# <a name="specifying-a-location-path-sqlxml-40"></a>Angeben eines Speicherortpfads (SQLXML 4.0)
  XPath-Abfragen werden in Form eines Ausdrucks angegeben. Es gibt verschiedene Arten von Ausdrücken. Ein Speicherortpfad ist ein Ausdruck, der relativ zum Kontextknoten einen Satz von Knoten auswählt. Das Ergebnis der Auswertung eines Speicherortpfads ist ein Knotensatz.  
  
## <a name="types-of-location-paths"></a>Typen von Speicherortpfaden  
 Ein Speicherortpfad kann eine dieser beiden Formen haben:  
  
-   **Absoluter Speicherortpfad**  
  
     Ein absoluter Speicherortpfad beginnt am Stammknoten des Dokuments. Er besteht aus einem Schrägstrich (/) optional gefolgt von einem relativen Speicherortpfad. Der Schrägstrich (/) wählt den Stammknoten des Dokuments aus.  
  
-   **Relativer Speicherortpfad**  
  
     Ein relativer Speicherortpfad beginnt am Kontextknoten im Dokument. Ein Speicherortpfad besteht aus einer Folge von einem oder mehreren Positionsschritten, die durch einen Schrägstrich (/) getrennt sind. Jeder Schritt wählt relativ zum Kontextknoten einen Satz von Knoten aus. Die Anfangsschrittsequenz wählt relativ zu einem Kontextknoten einen Satz von Knoten aus. Jeder Knoten in diesem Satz wird als Kontextknoten für den folgenden Schritt verwendet. Die Knotensätze, die von diesem Schritt identifiziert werden, werden verknüpft. Z. B. **Child:: Order/Child:: OrderDetail** wählt die  **\<OrderDetail >** untergeordnete Elemente des der  **\<Reihenfolge >** Element die untergeordneten Elemente des Kontextknotens aus.  
  
    > [!NOTE]  
    >  In der SQLXML 4.0-Implementierung von XPath beginnt jede XPath-Abfrage am Stammkontext, selbst wenn der XPath nicht ausdrücklich absolut ist. Zum Beispiel wird eine XPath-Abfrage, die mit "Customer" beginnt, als "/Customer" behandelt. XPath-Abfrage **Customer [Order]**, beginnt Customer am Stammkontext, Order jedoch am Customer-Kontext. Weitere Informationen finden Sie unter [Einführung in XPath-Abfragen mithilfe von &#40;SQLXML 4.0&#41;](../introduction-to-using-xpath-queries-sqlxml-4-0.md).  
  
## <a name="location-steps"></a>Positionsschritte  
 Ein Speicherortpfad (absolut oder relativ) besteht aus Positionsschritten, die drei Teile enthalten:  
  
-   **Axis**  
  
     Die Achse gibt die Strukturbeziehung zwischen den vom Positionsschritt ausgewählten Knoten und dem Kontextknoten an. Die Achsen `parent`, `child`, `attribute` und `self` werden unterstützt. Falls eine `child`-Achse im Speicherortpfad angegeben ist, sind alle von der Abfrage ausgewählten Knoten dem Kontextknoten untergeordnet. Wird eine `parent`-Achse angegeben, ist der ausgewählte Knoten der übergeordnete Knoten des Kontextknotens. Bei einer `attribute`-Achse sind die ausgewählten Knoten die Attribute des Kontextknotens.  
  
-   **Knotentest**  
  
     Ein Knotentest gibt den vom Positionsschritt ausgewählten Knotentyp an. Jede Achse (`child`, `parent`, `attribute` oder `self`) hat einen Hauptknotentyp. Für die `attribute` Achse, der primäre Knotentyp ist  **\<Attribut >**. Für die `parent`, `child`, und `self` Achsen, der primäre Knotentyp ist  **\<Element >**.  
  
     Wenn der Pfad zum Speicherort gibt an, z. B. **Child:: Customer**,  **\<Kunden >** untergeordneten-Elemente des Kontextknotens ausgewählt sind. Da die `child` Achse  **\<Element >** als Hauptknotentyp, ist der Knotentest Customer, TRUE, wenn der Kunde ist ein  **\<Element >** Knoten.  
  
-   **Auswahlprädikate (null oder mehr)**  
  
     Ein Prädikat filtert einen Knotensatz in Bezug auf eine Achse. Die Angabe von Auswahlprädikaten in einem XPath-Ausdruck entspricht der Angabe einer WHERE-Klausel in einer SELECT-Anweisung. Das Prädikat wird zwischen Klammern angegeben. Wird der in den Auswahlprädikaten angegebene Test angewendet, werden die vom Knotentest zurückgegebenen Knoten gefiltert. Für jeden Knoten in der zu filternden Knotengruppe wird der Prädikatausdruck mit dem entsprechenden Knoten als Kontextknoten ausgewertet. Die Anzahl der Knoten in der Knotengruppe dient dabei als Kontextgröße. Ergibt die Auswertung des Prädikatausdrucks für den betreffenden Knoten TRUE, wird dieser Knoten in die resultierende Knotengruppe aufgenommen.  
  
     Die Syntax für einen Positionsschritt umfasst den Achsennamen und den Knotentest, getrennt durch zwei Doppelpunkte (::) und gefolgt von null oder mehr Ausdrücken in eckigen Klammern. Z. B. der XPath-Ausdruck (Speicherortpfad) **Speicherortpfad [@CustomerID= "ALFKI"]** wählt alle dem  **\<Kunden >** untergeordneten-Elemente des Kontextknotens aus. Und klicken Sie dann der Test im Prädikat auf den Knotensatz angewendet wird, die gibt nur die  **\<Kunden >** -Elementknoten mit dem Attribut Wert "ALFKI" für die **"CustomerID"** Attribut.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Angeben einer Achse &#40;SQLXML 4.0&#41;](specifying-an-axis-sqlxml-4-0.md)  
 Enthält Beispiele zur Angabe einer Achse.  
  
 [Angeben eines Knotentests unter dem Speicherortpfad &#40;SQLXML 4.0&#41;](specifying-a-node-test-in-the-location-path-sqlxml-4-0.md)  
 Enthält Beispiele zur Angabe eines Knotentests.  
  
 [Angeben von Auswahlprädikaten im Speicherortpfad &#40;SQLXML 4.0&#41;](specifying-selection-predicates-in-the-location-path-sqlxml-4-0.md)  
 Enthält Beispiele zur Angabe von Auswahlprädikaten.  
  
  
