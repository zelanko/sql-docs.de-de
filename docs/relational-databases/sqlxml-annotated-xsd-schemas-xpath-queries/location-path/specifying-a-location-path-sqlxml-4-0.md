---
title: Angeben eines Speicherort Pfads (SQLXML)
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
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
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5e2668da10e41e997cc4d37760d79e4b66dae215
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75245592"
---
# <a name="specifying-a-location-path-sqlxml-40"></a>Angeben eines Speicherortpfads (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  XPath-Abfragen werden in Form eines Ausdrucks angegeben. Es gibt verschiedene Arten von Ausdrücken. Ein Speicherortpfad ist ein Ausdruck, der relativ zum Kontextknoten einen Satz von Knoten auswählt. Das Ergebnis der Auswertung eines Speicherortpfads ist ein Knotensatz.  
  
## <a name="types-of-location-paths"></a>Typen von Speicherortpfaden  
 Ein Speicherortpfad kann eine dieser beiden Formen haben:  
  
-   **Absoluter Speicherortpfad**  
  
     Ein absoluter Speicherortpfad beginnt am Stammknoten des Dokuments. Er besteht aus einem Schrägstrich (/) optional gefolgt von einem relativen Speicherortpfad. Der Schrägstrich (/) wählt den Stammknoten des Dokuments aus.  
  
-   **Relativer Speicherortpfad**  
  
     Ein relativer Speicherortpfad beginnt am Kontextknoten im Dokument. Ein Speicherortpfad besteht aus einer Folge von einem oder mehreren Positionsschritten, die durch einen Schrägstrich (/) getrennt sind. Jeder Schritt wählt relativ zum Kontextknoten einen Satz von Knoten aus. Die Anfangsschrittsequenz wählt relativ zu einem Kontextknoten einen Satz von Knoten aus. Jeder Knoten in diesem Satz wird als Kontextknoten für den folgenden Schritt verwendet. Die Knotensätze, die von diesem Schritt identifiziert werden, werden verknüpft. Beispielsweise wählt **Child:: Order/Child:: OrderDetail** die unter ** \<geordneten Elemente Order Detail>** der ** \<Order>** -Elemente des Kontext Knotens aus.  
  
    > [!NOTE]  
    >  In der SQLXML 4.0-Implementierung von XPath beginnt jede XPath-Abfrage am Stammkontext, selbst wenn der XPath nicht ausdrücklich absolut ist. Zum Beispiel wird eine XPath-Abfrage, die mit "Customer" beginnt, als "/Customer" behandelt. In der XPath-Abfrage **Customer [Order]** beginnt Customer am Stamm Kontext, aber die Reihenfolge beginnt im Kunden Kontext. Weitere Informationen finden Sie unter [Einführung in die Verwendung von XPath-Abfragen &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/introduction-to-using-xpath-queries-sqlxml-4-0.md).  
  
## <a name="location-steps"></a>Positionsschritte  
 Ein Speicherortpfad (absolut oder relativ) besteht aus Positionsschritten, die drei Teile enthalten:  
  
-   **Achse**  
  
     Die Achse gibt die Strukturbeziehung zwischen den vom Positionsschritt ausgewählten Knoten und dem Kontextknoten an. Die über- **, unter** **geordneten**, **Attribute**-und **Self** -Achsen werden unterstützt. Wenn eine **unter** geordnete Achse im Speicherort Pfad angegeben ist, sind alle von der Abfrage ausgewählten Knoten die untergeordneten Elemente des Kontext Knotens. Wenn eine über **geordnete** Achse angegeben wird, ist der ausgewählte Knoten der übergeordnete Knoten des Kontext Knotens. Wenn eine **Attribut** Achse angegeben wird, sind die ausgewählten Knoten die Attribute des Kontext Knotens.  
  
-   **Knoten Test**  
  
     Ein Knotentest gibt den vom Positionsschritt ausgewählten Knotentyp an. Jede**Achse (unter**geordnetes Element, über **geordnetes**Element, **Attribut**und **Self**) verfügt über einen Prinzipal Knotentyp. Für die **Attribut** Achse ist ** \< **der Haupt Knotentyp Attribute>. Für die übergeordnete **, unter** **geordnete**und die **Self** -Achse ist ** \< **der Haupt Knotentyp Element>.  
  
     Wenn der Speicherort Pfad z. b. **Child:: Customer**angibt, werden die ** \<** untergeordneten Elemente des Kunden>des Kontext Knotens ausgewählt. Da die untergeordnete Achse ** \<Element>** als Prinzipal Knotentyp hat, **ist der Knoten** Test Customer, true, wenn Customer ein ** \<Element>** Knoten ist.  
  
-   **Auswahlprädikate (Null oder mehr)**  
  
     Ein Prädikat filtert einen Knotensatz in Bezug auf eine Achse. Die Angabe von Auswahlprädikaten in einem XPath-Ausdruck entspricht der Angabe einer WHERE-Klausel in einer SELECT-Anweisung. Das Prädikat wird zwischen Klammern angegeben. Wird der in den Auswahlprädikaten angegebene Test angewendet, werden die vom Knotentest zurückgegebenen Knoten gefiltert. Für jeden Knoten in der zu filternden Knotengruppe wird der Prädikatausdruck mit dem entsprechenden Knoten als Kontextknoten ausgewertet. Die Anzahl der Knoten in der Knotengruppe dient dabei als Kontextgröße. Ergibt die Auswertung des Prädikatausdrucks für den betreffenden Knoten TRUE, wird dieser Knoten in die resultierende Knotengruppe aufgenommen.  
  
     Die Syntax für einen Positionsschritt umfasst den Achsennamen und den Knotentest, getrennt durch zwei Doppelpunkte (::) und gefolgt von null oder mehr Ausdrücken in eckigen Klammern. Beispielsweise wählt der XPath-Ausdruck (Speicherort Pfad) **Child::@CustomerIDCustomer [= ' ALFKI ']** alle unter ** \<** geordneten Elemente des Kunden>-Elements des Kontext Knotens aus. Anschließend wird der Test im Prädikat auf den Knoten Satz angewendet, der nur die ** \<Customer->** Elementknoten mit dem Attribut Wert "ALFKI" für das zugehörige **CustomerID-** Attribut zurückgibt.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Angeben einer Achse &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/location-path/specifying-an-axis-sqlxml-4-0.md)  
 Enthält Beispiele zur Angabe einer Achse.  
  
 [Angeben eines Knoten Tests im Speicherort Pfad &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/location-path/specifying-a-node-test-in-the-location-path-sqlxml-4-0.md)  
 Enthält Beispiele zur Angabe eines Knotentests.  
  
 [Angeben von Auswahl Prädikaten im Speicherort Pfad &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/location-path/specifying-selection-predicates-in-the-location-path-sqlxml-4-0.md)  
 Enthält Beispiele zur Angabe von Auswahlprädikaten.  
  
  
