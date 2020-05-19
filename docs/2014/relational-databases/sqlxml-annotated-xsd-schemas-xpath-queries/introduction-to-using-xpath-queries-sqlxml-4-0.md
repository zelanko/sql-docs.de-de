---
title: Einführung in die Verwendung von XPath-Abfragen (SQLXML 4,0) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], about XPath queries
- W3C XPath specification
- XPath queries [SQLXML], functionality
ms.assetid: 01050a8e-0ccc-4a02-a4eb-b48be5c3f4f3
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 69fe9c7decd7521ca752b0b5092748c907036f40
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82703120"
---
# <a name="introduction-to-using-xpath-queries-sqlxml-40"></a>Einführung in die Verwendung von XPath-Abfragen (SQLXML 4.0)
  XPath (XML Path Language)-Abfragen können als Teil einer URL oder in einer Vorlage angegeben werden. Das Zuordnungsschema bestimmt die Struktur des resultierenden Fragments, und die Werte werden aus der Datenbank abgerufen. Dieser Vorgang ähnelt prinzipiell dem Erstellen von Sichten mit der CREATE VIEW-Anweisung und dem Schreiben von SQL-Abfragen für diese Sichten.  
  
> [!NOTE]  
>  Um XPath-Abfragen in SQLXML 4.0 verstehen zu können, müssen Sie XML-Sichten und verwandte Konzepte wie Vorlagen und Zuordnungsschemas kennen. Weitere Informationen finden Sie unter [Einführung in XSD-Schemas mit Anmerkungen &#40;SQLXML 4,0&#41;](../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md)und im vom World Wide Web Consortium (W3C) definierten XPath-Standard.  
  
 Ein XML-Dokument besteht aus Knoten, z. B. Elementknoten, Attributknoten, Textknoten usw. Betrachten Sie z. B. folgendes XML-Dokument:  
  
```  
<root>  
  <Customer cid= "C1" name="Janine" city="Issaquah">  
      <Order oid="O1" date="1/20/1996" amount="3.5" />  
      <Order oid="O2" date="4/30/1997" amount="13.4">Customer was  
          very satisfied</Order>  
   </Customer>  
   <Customer cid="C2" name="Ursula" city="Oelde" >  
      <Order oid="O3" date="7/14/1999" amount="100" note="Wrap it blue white red">  
          <Urgency>Important</Urgency>  
      </Order>  
      <Order oid="O4" date="1/20/1996" amount="10000"/>  
   </Customer>  
</root>  
```  
  
 In diesem Dokument ist ** \< Customer>** ein Elementknoten, **CID** ein Attribut Knoten und **"Important"** ein Textknoten.  
  
 XPath ist eine Diagrammnavigationssprache, die verwendet wird, um eine Gruppe von Knoten aus einem XML-Dokument auszuwählen. Jeder XPath-Operator wählt eine Knotengruppe aus, die auf einer von einem vorherigen XPath-Operator ausgewählten Knotengruppe basiert. Wenn beispielsweise ein Satz von ** \< Customer->** Knoten angezeigt wird, kann XPath alle ** \< Order>** Knoten mit dem **Date** -Attribut Wert **"7/14/1999"** auswählen. Die resultierende Knotengruppe enthält alle Bestellungen mit dem Bestelldatum 14.7.1999.  
  
 Die XPath-Sprache wurde vom World Wide Web Consortium (W3C) als Standardnavigationssprache definiert. SQLXML 4,0 implementiert eine Teilmenge der W3C-XPath-Spezifikation, die sich unter befindet http://www.w3.org/TR/1999/PR-xpath-19991008.html .  
  
 Nachfolgend werden die Hauptunterschiede zwischen der XPath-Implementierung des W3C und der SQLXML 4.0-Implementierung beschrieben.  
  
-   **Abfragen des Stammelements**  
  
     In SQLXML 4.0 werden Abfragen des Stammelements (/) nicht unterstützt. Jede XPath-Abfrage muss bei einem ** \< ElementType** der obersten Ebene>im Schema beginnen.  
  
-   **Fehler melden**  
  
     Die XPath-Spezifikation des W3C definiert keine Fehlerbedingungen. XPath-Abfragen, die keine Knoten auswählen, geben eine leere Knotengruppe zurück. In SQLXML 4.0 kann eine Abfrage viele Arten von Fehlermeldungen zurückgeben.  
  
-   **Dokument Reihenfolge**  
  
     In SQLXML 4.0 ist die Dokumentreihenfolge nicht immer bestimmt. Daher sind numerische Prädikate und Achsen, welche die Dokumentreihenfolge verwenden (z. B. `following`), nicht implementiert.  
  
     Das Fehlen einer Dokumentreihenfolge bedeutet auch, dass der Zeichenfolgenwert eines Knotens nur dann ausgewertet werden kann, wenn der betreffende Knoten nur einer Spalte in nur einer Zeile zugeordnet werden kann. Ein Element mit untergeordneten Elementen oder einem IDREFS-Knoten oder NMTOKENS-Knoten kann nicht in eine Zeichenfolge konvertiert werden.  
  
    > [!NOTE]  
    >  In einigen Fällen können die `key-fields`-Anmerkung oder Schlüssel aus der `relationship`-Anmerkung in einer deterministischen Dokumentreihenfolge resultieren. Dies ist jedoch nicht die primäre Verwendung dieser Anmerkungen, um weitere Informationen zu erhalten. Weitere Informationen finden [Sie unter Identifizieren von Schlüssel Spalten mithilfe von SQL: key-fields &#40;SQLXML 4,0&#41;](../sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md) und [Angeben von Beziehungen mithilfe von SQL: Relationship &#40;SQLXML 4,0&#41;](../sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md).  
  
-   **Datentypen**  
  
     SQLXML 4.0 weist Einschränkungen hinsichtlich der Implementierung der XPath-Datentypen `string`, `number` und `boolean` auf. Weitere Informationen finden Sie unter [XPath-Datentypen &#40;SQLXML 4,0&#41;](xpath-data-types-sqlxml-4-0.md).  
  
-   **Produktübergreifende Abfragen**  
  
     SQLXML 4.0 unterstützt keine produktübergreifende XPath-Abfragen wie `Customers[Order/@OrderDate=Order/@ShipDate]`. Mit dieser Abfrage werden alle Order-Datensätze aus der Datenbank Customers ausgewählt, bei denen der OrderDate-Wert dem ShipDate-Wert entspricht.  
  
     Allerdings unterstützt SQLXML 4.0 keine Abfragen wie `Customer[Order[@OrderDate=@ShippedDate]]`, mit der alle Customer-Datensätze ausgewählt werden, für die Order-Datensätze vorhanden sind, bei denen der OrderDate-Wert dem ShipDate-Wert entspricht.  
  
-   **Fehlerbehandlung und Sicherheit**  
  
     Je nachdem, welches Schema und welcher XPath-Abfrageausdruck verwendet werden, können [!INCLUDE[tsql](../../includes/tsql-md.md)]-Fehler unter bestimmten Bedingungen für die Benutzer verfügbar gemacht werden.  
  
 Die Tabellen in den folgenden Abschnitten enthalten nähere Angaben dazu, in welcher Hinsicht sich die Implementierung von XPath-Abfragen in SQLXML 4.0 von der betreffenden W3C-Spezifikation unterscheidet.  
  
## <a name="supported-functionality"></a>Unterstützte Funktionalität  
 In der folgenden Tabelle werden die Funktionen der XPath-Sprache aufgeführt, die in SQLXML 4.0 implementiert sind.  
  
|Feature|Artikel|Link zu Beispielabfragen|  
|-------------|----------|----------------------------|  
|Achsen|`attribute`-, `child`-, `parent` und `self`-Achsen|[Angeben von Achsen in XPath-Abfragen &#40;SQLXML 4,0&#41;](samples/specifying-axes-in-xpath-queries-sqlxml-4-0.md)|  
|Prädikate mit booleschen Werten einschließlich aufeinander folgender und geschachtelter Prädikate||[Angeben arithmetischer Operatoren in XPath-Abfragen &#40;SQLXML 4,0&#41;](samples/specifying-arithmetic-operators-in-xpath-queries-sqlxml-4-0.md)|  
|Alle relationalen Operatoren|=,! =, <, \< =, >, >=|[Angeben von relationalen Operatoren in XPath-Abfragen &#40;SQLXML 4,0&#41;](samples/specifying-relational-operators-in-xpath-queries-sqlxml-4-0.md)|  
|Arithmetische operatoren|+, -, *, div|[Angeben arithmetischer Operatoren in XPath-Abfragen &#40;SQLXML 4,0&#41;](samples/specifying-arithmetic-operators-in-xpath-queries-sqlxml-4-0.md)|  
|Explizite Konvertierungsfunktionen|`number()`, `string()`, `Boolean()`|[Angeben von expliziten Konvertierungs Funktionen in XPath-Abfragen &#40;SQLXML 4,0&#41;](samples/specifying-explicit-conversion-functions-in-xpath-queries-sqlxml-4-0.md)|  
|Boolesche Operatoren|AND, OR|[Angeben von booleschen Operatoren in XPath-Abfragen &#40;SQLXML 4,0&#41;](samples/specifying-boolean-operators-in-xpath-queries-sqlxml-4-0.md)|  
|Boolesche Funktionen|`true()`, `false()`, `not()`|[Angeben von booleschen Funktionen in XPath-Abfragen &#40;SQLXML 4,0&#41;](samples/specifying-boolean-functions-in-xpath-queries-sqlxml-4-0.md)|  
|XPath-Variablen||[Angeben von XPath-Variablen in XPath-Abfragen &#40;SQLXML 4,0&#41;](samples/specifying-xpath-variables-in-xpath-queries-sqlxml-4-0.md)|  
  
## <a name="unsupported-functionality"></a>Nicht unterstützte Funktionalität  
 In der folgenden Tabelle werden die Funktionen der XPath-Sprache aufgeführt, die in SQLXML 4.0 nicht implementiert sind.  
  
|Feature|Artikel|  
|-------------|----------|  
|Achsen|`ancestor`, `ancestor-or-self`, `descendant`, `descendant-or-self (//)`, `following`, `following-sibling`, `namespace`, `preceding`, `preceding-sibling`|  
|Prädikate mit numerischen Werten||  
|Arithmetische operatoren|mod|  
|Knotenfunktionen|`ancestor`, `ancestor-or-self`, `descendant`, `descendant-or-self (//)`, `following`, `following-sibling`, `namespace`, `preceding`, `preceding-sibling`|  
|Zeichenfolgenfunktionen|`string()`, `concat()`, `starts-with()`, `contains()`, `substring-before()`, `substring-after()`, `substring()`, `string-length()`, `normalize()`, `translate()`|  
|Boolesche Funktionen|`lang()`|  
|Numerische Funktionen|`sum()`, `floor()`, `ceiling()`, `round()`|  
|Union-Operator|&#124;|  
  
 Bei der Angabe von XPath-Abfragen in einer Vorlage ist Folgendes zu beachten:  
  
-   XPath kann Zeichen wie < oder & enthalten, die in XML eine besondere Bedeutung haben (und die Vorlage ist ein XML-Dokument). Sie müssen diese Zeichen mithilfe von XML-& Codierungen mit Escapezeichen versehen oder den XPath in der URL angeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden von XPath-Abfragen in SQLXML 4.0](using-xpath-queries-in-sqlxml-4-0.md)  
  
  
