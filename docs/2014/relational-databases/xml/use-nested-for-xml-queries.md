---
title: Verwenden von geschachtelten FOR XML-Abfragen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FOR XML clause, nested FOR XML queries
- queries [XML in SQL Server], nested FOR XML
- nested FOR XML queries
ms.assetid: 7604161a-a958-446d-b102-7dee432979d0
caps.latest.revision: 41
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: e8ce91a3ee069562a6a4d3f9d6aa3c02999e4dff
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050716"
---
# <a name="use-nested-for-xml-queries"></a>Verwenden von geschachtelten FOR XML-Abfragen
  Die `xml` -Datentyp und die [TYPE-Direktive in FOR XML-Abfragen](type-directive-in-for-xml-queries.md) ermöglichen von FOR XML-Abfragen zurückgegebene XML-Code sowohl auf dem Server als auch auf dem Client verarbeitet werden.  
  
## <a name="processing-with-xml-type-variables"></a>Verarbeiten mit XML-Typvariablen  
 Sie können das Ergebnis einer FOR XML-Abfrage einer `xml`-Typvariablen zuweisen oder das Ergebnis mithilfe einer XQuery-Abfrage abfragen und das daraus entstehende Ergebnis einer `xml`-Typvariablen zur weiteren Verarbeitung zuweisen.  
  
```  
DECLARE @x xml  
SET @x=(SELECT ProductModelID, Name  
        FROM Production.ProductModel  
        WHERE ProductModelID=122 or ProductModelID=119  
        FOR XML RAW, TYPE)  
SELECT @x  
-- Result  
--<row ProductModelID="122" Name="All-Purpose Bike Stand" />  
--<row ProductModelID="119" Name="Bike Wash" />  
```  
  
 Sie können außerdem in der Variablen zurückgegebene XML verarbeiten `@x`, mithilfe eines der der `xml` -Datentypmethoden. So können Sie z. B. den Attributwert von `ProductModelID` mithilfe der [value()-Methode](/sql/t-sql/xml/value-method-xml-data-type)abrufen.  
  
```  
DECLARE @i int;  
SET @i = (SELECT @x.value('/row[1]/@ProductModelID[1]', 'int'));  
SELECT @i;  
```  
  
 Im folgenden Beispiel wird das Ergebnis der `FOR XML`-Abfrage als `xml`-Typ zurückgegeben, da in der `TYPE`-Klausel die `FOR XML`-Direktive angegeben wurde.  
  
```  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=119 or ProductModelID=122  
FOR XML RAW, TYPE,ROOT('myRoot');  
  
```  
  
 Dies ist das Ergebnis:  
  
```  
<myRoot>  
  <row ProductModelID="122" Name="All-Purpose Bike Stand" />  
  <row ProductModelID="119" Name="Bike Wash" />  
</myRoot>  
```  
  
 Da das Ergebnis `xml` Typ, eine angeben von der `xml` -Datentypmethoden direkt für diesen XML-Code wie in der folgenden Abfrage gezeigt. In der Abfrage wird die [query()-Methode (XML-Datentyp)](/sql/t-sql/xml/query-method-xml-data-type) verwendet, um das erste untergeordnete <`row`>-Element des Elements <`myRoot`> abzurufen.  
  
```  
SELECT  (SELECT ProductModelID, Name  
         FROM Production.ProductModel  
         WHERE ProductModelID=119 or ProductModelID=122  
         FOR XML RAW, TYPE,ROOT('myRoot')).query('/myRoot[1]/row[1]');  
  
```  
  
 Dies ist das Ergebnis:  
  
```  
<row ProductModelID="122" Name="All-Purpose Bike Stand" />  
```  
  
## <a name="returning-inner-for-xml-query-results-to-outer-queries-as-xml-type-instances"></a>Zurückgeben von Ergebnissen innerer FOR XML-Abfragen als XML-Typinstanzen an äußere Abfragen  
 Sie können geschachtelte schreiben `FOR XML` Abfragen, in dem das Ergebnis der inneren Abfrage wird, als zurückgegeben, ein `xml` Typ für die äußere Abfrage. Zum Beispiel:  
  
```  
SELECT Col1,   
       Col2,   
       ( SELECT Col3, Col4   
        FROM  T2  
        WHERE T2.Col = T1.Col  
        ...  
        FOR XML AUTO, TYPE )  
FROM T1  
WHERE ...  
FOR XML AUTO, TYPE;  
```  
  
 Beachten Sie hinsichtlich der vorherigen Abfrage Folgendes:  
  
-   Der von der inneren `FOR XML` -Abfrage generierte XML-Code wird dem von der äußeren `FOR XML`-Abfrage generierten XML-Code hinzugefügt.  
  
-   Die innere Abfrage gibt die `TYPE` -Direktive an. Die von der inneren Abfrage zurückgegebenen XML-Daten gehören daher dem `xml`-Typ an. Wenn die TYPE-Direktive nicht angegeben wird, wird das Ergebnis der inneren `FOR XML`-Abfrage als `nvarchar(max)` zurückgegeben, und die XML-Daten werden in Entitäten geändert.  
  
## <a name="controlling-the-shape-of-resulting-xml-data"></a>Steuern der Form der resultierenden XML-Daten  
 Geschachtelte FOR XML-Abfragen ermöglichen eine bessere Steuerung der Form der resultierenden XML-Daten. Sie können jedoch mit geschachtelten FOR XML-Abfragen XML-Code erstellen, der zum Teil attributzentriert und zum Teil elementzentriert ist.  
  
 Weitere Informationen über das Angeben von attributzentrierter und elementzentrierter XML mit geschachtelten FOR XML-Abfragen finden Sie unter [FOR XML-Abfragen im Vergleich zu geschachtelten FOR XML-Abfragen](../xml/for-xml-query-compared-to-nested-for-xml-query.md) und [Gestalten von XML mit geschachtelten FOR XML-Abfragen](../xml/shape-xml-with-nested-for-xml-queries.md).  
  
 Sie können XML-Hierarchien generieren, die gleichgeordnete Elemente enthalten, indem Sie geschachtelte FOR XML-Abfragen im AUTO-Modus angeben. Weitere Informationen finden Sie unter [Generieren von gleichgeordneten Elementen mit einer geschachtelten AUTO-Modusabfrage](../xml/generate-siblings-with-a-nested-auto-mode-query.md).  
  
 Unabhängig davon, welchen Modus Sie verwenden, bieten geschachtelte FOR XML-Abfragen größere Steuerungsmöglichkeiten beim Beschreiben der Form des resultierenden XML-Codes. Diese Abfragen können anstelle von Abfragen im EXPLICIT-Modus verwendet werden.  
  
## <a name="examples"></a>Beispiele  
 Die folgenden Themen enthalten Beispiele für geschachtelte FOR XML-Abfragen.  
  
 [FOR XML-Abfragen im Vergleich zu geschachtelten FOR XML-Abfragen](../xml/for-xml-query-compared-to-nested-for-xml-query.md)  
 In diesem Thema wird eine einstufige FOR XML-Abfrage mit einer geschachtelten FOR XML-Abfrage verglichen. In diesem Beispiel wird unter Anderem veranschaulicht, wie sowohl attributzentriertes als auch elementzentriertes XML als Abfrageergebnis angegeben wird.  
  
 [Generieren von gleichgeordneten Elementen mit einer geschachtelten AUTO-Modusabfrage](../xml/generate-siblings-with-a-nested-auto-mode-query.md)  
 Zeigt, wie gleichgeordnete Elemente durch Verwenden einer geschachtelten Abfrage im AUTO-Modus generiert werden.  
  
 [Verwenden geschachtelter FOR XML-Abfragen in ASP.NET](use-nested-for-xml-queries-in-asp-net.md)  
 Veranschaulicht, wie eine ASPX-Anwendung FOR XML verwenden kann, um XML von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zurückzugeben.  
  
 [Gestalten von XML mit geschachtelten FOR XML-Abfragen](../xml/shape-xml-with-nested-for-xml-queries.md)  
 Zeigt, wie mit geschachtelten FOR XML-Abfragen die Struktur eines von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]erstellten XML-Dokuments gesteuert werden kann.  
  
  
