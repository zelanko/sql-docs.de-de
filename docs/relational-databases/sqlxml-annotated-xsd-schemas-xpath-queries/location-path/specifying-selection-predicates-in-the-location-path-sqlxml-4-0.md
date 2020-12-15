---
title: Festlegen von Auswahl Prädikaten im Speicherort Pfad (SQLXML)
description: Erfahren Sie, wie Sie Auswahl Prädikate im Speicherort Pfad Ausdruck einer XPath-Abfrage (SQLXML 4,0) durch das Angeben der Knotengruppe filtern, die abgefragt wird.
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], predicates
- predicates [SQLXML]
- position-based filtering [SQLXML]
- XPath queries [SQLXML], location paths
- filtering [SQLXML]
- location path for XPath query
ms.assetid: dbef4cf4-a89b-4d7e-b72b-4062f7b29a80
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8c02a33e76fd478e77e2b5a743b5cc6e1d32f1ff
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97414481"
---
# <a name="specifying-selection-predicates-in-the-location-path-sqlxml-40"></a>Angeben von Auswahlprädikaten im Speicherortpfad (SQLXML 4.0) 
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  Ein Prädikat filtert eine Knotengruppe in Bezug auf eine Achse (ähnlich einer WHERE-Klausel in einer SELECT-Anweisung). Das Prädikat wird zwischen Klammern angegeben. Für jeden Knoten in der zu filternden Knotengruppe wird der Prädikatausdruck mit dem entsprechenden Knoten als Kontextknoten ausgewertet. Die Anzahl der Knoten in der Knotengruppe dient dabei als Kontextgröße. Ergibt die Auswertung des Prädikatausdrucks für den betreffenden Knoten TRUE, wird dieser Knoten in die resultierende Knotengruppe aufgenommen.  
  
 XPath ermöglicht auch die positionsbasierte Filterung. Ein Prädikatausdruck, der eine Zahl ergibt, wählt diesen Ordinalzahlenknoten aus. Beispielsweise gibt der Speicherortpfad `Customer[3]` den dritten Kunden zurück. Solche numerische Prädikate werden nicht unterstützt. Nur Prädikatausdrücke, die ein boolesches Ergebnis zurückgeben, werden unterstützt.  
  
> [!NOTE]  
>  Informationen zu den Einschränkungen dieser XPath-Implementierung von XPath und den Unterschieden zwischen der XPath-Implementierung und der W3C-Spezifikation finden Sie unter [Einführung in die Verwendung von XPath-Abfragen &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/introduction-to-using-xpath-queries-sqlxml-4-0.md).  
  
## <a name="selection-predicate-example-1"></a>Auswahl Prädikat: Beispiel 1  
 Der folgende XPath-Ausdruck (Speicherort Pfad) wählt alle untergeordneten Elemente des aktuellen Kontext Knotens aus **\<Customer>** , die das **CustomerID-** Attribut mit dem Wert "ALFKI" aufweisen:  
  
```  
/child::Customer[attribute::CustomerID="ALFKI"]  
```  
  
 In dieser XPath-Abfrage sind `child` und `attribute` die Achsennamen. `Customer` ist der Knoten Test (true `Customer` , wenn ein ist **\<element node>** , da **\<element>** der Haupt Knotentyp für die-Achse ist `child` ). `attribute::CustomerID="ALFKI"` ist das Prädikat. Im Prädikat `attribute` ist die Achse und `CustomerID` ist der Knoten Test (true, wenn **CustomerID** ein Attribut des Kontext Knotens ist, da **\<attribute>** der Haupt Knotentyp der **Attribut** Achse ist).  
  
 In abgekürzter Syntax kann die XPath-Abfrage auch wie folgt angegeben werden:  
  
```  
/Customer[@CustomerID="ALFKI"]  
```  
  
## <a name="selection-predicate-example-2"></a>Auswahl Prädikat: Beispiel 2  
 Der folgende XPath-Ausdruck (Speicherort Pfad) wählt alle untergeordneten Knoten aus dem aktuellen Kontext Knoten aus **\<Order>** , die über das **SalesOrderID** -Attribut mit dem Wert 1 verfügen:  
  
```  
/child::Customer/child::Order[attribute::SalesOrderID="1"]  
```  
  
 In diesem XPath-Ausdruck sind `child` und `attribute` die Achsennamen. `Customer`, `Order` und `SalesOrderID` sind die Knotentests. `attribute::OrderID="1"` ist das Prädikat.  
  
 In abgekürzter Syntax kann die XPath-Abfrage auch wie folgt angegeben werden:  
  
```  
/Customer/Order[@SalesOrderID="1"]  
```  
  
## <a name="selection-predicate-example-3"></a>Auswahl Prädikat: Beispiel 3  
 Der folgende XPath-Ausdruck (Speicherort Pfad) wählt alle untergeordneten Elemente aus dem aktuellen Kontext Knoten aus **\<Customer>** , die über ein oder mehrere untergeordnete Elemente verfügen **\<ContactName>** :  
  
```  
child::Customer[child::ContactName]  
```  
  
 In diesem Beispiel wird davon ausgegangen, dass ein untergeordnetes **\<ContactName>** Element des- **\<Customer>** Elements im XML-Dokument ist, das in einem XSD-Schema mit Anmerkungen als *Element zentrierte Zuordnung* bezeichnet wird.  
  
 In diesem XPath-Ausdruck ist `child` der Achsenname. `Customer` ist der Knoten Test (true `Customer` , wenn ein- **\<element>** Knoten ist, da **\<element>** der Haupt Knotentyp für die- `child` Achse ist). `child::ContactName` ist das Prädikat. Im Prädikat `child` ist die Achse und `ContactName` ist der Knoten Test (true, wenn `ContactName` ein- **\<element>** Knoten ist).  
  
 Dieser Ausdruck gibt nur die untergeordneten **\<Customer>** Elemente des Kontext Knotens zurück, die über untergeordnete **\<ContactName>** Elemente verfügen.  
  
 In abgekürzter Syntax kann die XPath-Abfrage auch wie folgt angegeben werden:  
  
```  
Customer[ContactName]  
```  
  
## <a name="selection-predicate-example-4"></a>Auswahl Prädikat: Beispiel 4  
 Der folgende XPath-Ausdruck wählt untergeordnete- **\<Customer>** Elemente des Kontext Knotens aus, die keine untergeordneten **\<ContactName>** Elemente aufweisen:  
  
```  
child::Customer[not(child::ContactName)]  
```  
  
 In diesem Beispiel wird davon ausgegangen, dass ein untergeordnetes **\<ContactName>** Element des **\<Customer>** -Elements im XML-Dokument ist und das ContactName-Feld in der Datenbank nicht erforderlich ist.  
  
 In diesem Beispiel ist `child` die Achse. `Customer` ist der Knoten Test (true, wenn `Customer` ein- \<element> Knoten ist). `not(child::ContactName)` ist das Prädikat. Im Prädikat `child` ist die Achse und `ContactName` ist der Knoten Test (true, wenn `ContactName` ein- \<element> Knoten ist).  
  
 In abgekürzter Syntax kann die XPath-Abfrage auch wie folgt angegeben werden:  
  
```  
Customer[not(ContactName)]  
```  
  
## <a name="selection-predicate-example-5"></a>Auswahl Prädikat: Beispiel 5  
 Der folgende XPath-Ausdruck wählt alle untergeordneten Elemente mit **\<Customer>** dem **CustomerID-** Attribut aus dem aktuellen Kontext Knoten aus:  
  
```  
child::Customer[attribute::CustomerID]  
```  
  
 In diesem Beispiel `child` ist die Achse und der `Customer` Knoten Test (true, wenn `Customer` ein- \<element> Knoten ist). `attribute::CustomerID` ist das Prädikat. Im Prädikat `attribute` ist die Achse und `CustomerID` das Prädikat (true, wenn ein- `CustomerID` Knoten ist **\<attribute>** ).  
  
 In abgekürzter Syntax kann die XPath-Abfrage auch wie folgt angegeben werden:  
  
```  
Customer[@CustomerID]  
```  
  
## <a name="selection-predicate-example-6"></a>Auswahlprädikat: Beispiel 6  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 unterstützt XPath-Abfragen mit einem Kreuzprodukt im Prädikat, wie im folgenden Beispiel gezeigt:  
  
```  
Customer[Order/@OrderDate=Order/@ShipDate]  
```  
  
 Durch diese Abfrage werden alle Kunden mit einer `Order` ausgewählt, bei der `OrderDate` dem `ShipDate` für eine beliebige `Order`entspricht.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Einführung in XSD-Schemas mit Anmerkungen &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)   
 [Client seitige XML-Formatierung &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml/formatting/client-side-xml-formatting-sqlxml-4-0.md)  
  
  
