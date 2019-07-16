---
title: Angeben von Prädikaten in einem Schritt eines Pfadausdrucks | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- axis step [XQuery]
- predicates [XQuery]
- qualifiers [XQuery]
- path expressions [XQuery]
ms.assetid: 2660ceca-b8b4-4a1f-98a0-719ad5f89f81
author: rothja
ms.author: jroth
ms.openlocfilehash: 4e8ba9bb523d4ce7aed76f61c569f5e8b1775972
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67946425"
---
# <a name="path-expressions---specifying-predicates"></a>Pfadausdrücke – Angeben von Prädikaten
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Im Thema beschriebene [Pfadausdrücke in XQuery](../xquery/path-expressions-xquery.md), ein achsenschritt in einem Pfadausdruck umfasst die folgenden Komponenten:  
  
-   [Eine Achse](../xquery/path-expressions-specifying-axis.md).  
  
-   Einen Knotentest. Weitere Informationen finden Sie unter [Knotentest angeben, in einem Schritt eines Pfadausdrucks](../xquery/path-expressions-specifying-node-test.md).  
  
-   Null oder mehr Prädikate. Diese Eingabe ist optional.  
  
 Das optionale Prädikat ist der dritte Teil des Achsenschritts in einem Pfadausdruck.  
  
## <a name="predicates"></a>Prädikate  
 Ein Prädikat wird zum Filtern einer Knotensequenz durch Anwenden eines angegebenen Tests verwendet. Der Prädikatausdruck ist in eckige Klammern eingeschlossen und an den letzten Knoten in einem Pfadausdruck gebunden.  
  
 Nehmen wir beispielsweise an, die ein SQL-Parameterwert (X) von der **Xml** -Datentyp deklariert, wie im folgenden gezeigt:  
  
```  
declare @x xml  
set @x = '  
<People>  
  <Person>  
    <Name>John</Name>  
    <Age>24</Age>  
  </Person>  
  <Person>  
    <Name>Goofy</Name>  
    <Age>54</Age>  
  </Person>  
  <Person>  
    <Name>Daffy</Name>  
    <Age>30</Age>  
  </Person>  
</People>  
'  
```  
  
 In diesem Fall sind die folgenden Ausdrücke gültig, die einen Prädikatwert von [1] für jede der drei unterschiedlichen Knotenebenen verwenden:  
  
```  
select @x.query('/People/Person/Name[1]')  
select @x.query('/People/Person[1]/Name')  
select @x.query('/People[1]/Person/Name')  
```  
  
 Beachten Sie, dass in jedem Fall das Prädikat an den Knoten im Pfadausdruck gebunden wird, für den es angewendet wird. Der erste Pfadausdruck wählt z. B. das erste <`Name`>-Element innerhalb jeder/People/Person-Knoten und mit der bereitgestellten XML-Instanz gibt Folgendes zurück:  
  
```  
<Name>John</Name><Name>Goofy</Name><Name>Daffy</Name>  
```  
  
 Aber der zweite Pfadausdruck wählt alle <`Name`>-Elemente, die unter den ersten/People/Person-Knoten befinden. Deshalb gibt er das folgende Ergebnis zurück:  
  
```  
<Name>John</Name>  
```  
  
 Es können auch Klammern verwendet werden, um die Auswertungsreihenfolge des Prädikats zu ändern. So wird z. B. im folgenden Ausdruck ein Klammernsatz verwendet, um den Pfad von (/People/Person/Name) vom Prädikat [1] zu trennen:  
  
```  
select @x.query('(/People/Person/Name)[1]')  
```  
  
 In diesem Beispiel ändert sich die Reihenfolge, in der das Prädikat angewendet wird. Das liegt daran, dass der in Klammern eingeschlossene Pfad (/People/Person/Name) zuerst ausgewertet und anschließend der Prädikatoperator [1] für das Set angewendet wird, das alle mit dem eingeschlossenen Pfad übereinstimmenden Knoten enthält. Ohne die Klammern wäre die Reihenfolge des Vorgangs anders: Der Prädikatoperator [1] würde dann als ein `child::Name`-Knotentest angewendet werden, wie das im ersten Beispiel für den Pfadausdruck der Fall war.  
  
### <a name="quantifiers-and-predicates"></a>Quantifizierer und Prädikate  
 Quantifizierer können innerhalb der Klammern des Prädikats mehrfach verwendet und hinzugefügt werden. So wäre z. B. unter Nutzung des vorigen Beispiels folgende Verwendung von mehreren Quantifizierern innerhalb eines komplexen Prädikatunterausdrucks gültig.  
  
```  
select @x.query('/People/Person[contains(Name[1], "J") and xs:integer(Age[1]) < 40]/Name/text()')  
```  
  
 Das Ergebnis eines Prädikatausdrucks wird in einen booleschen Wert konvertiert und wird als Wahrheitswert des Prädikats bezeichnet. Im Ergebnis werden nur die Knoten in der Sequenz zurückgegeben, deren Prädikatwahrheitswert True ist. Alle anderen Knoten werden verworfen.  
  
 Beim folgenden Pfadausdruck ist z. B. ein Prädikat in den zweiten Schritt eingeschlossen:  
  
```  
/child::root/child::Location[attribute::LocationID=10]  
```  
  
 Die von diesem Prädikat angegebene Bedingung gilt für alle die <`Location`> untergeordneten Elementknoten. Das führt dazu, dass als Ergebnis nur solche Arbeitsplatzstandorte zurückgegeben werden, bei denen der Attributwert der Standortkennung (LocationID) 10 ist.  
  
 Der vorige Pfadausdruck wird in der folgenden SELECT-Anweisung ausgeführt:  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
 /child::AWMI:root/child::AWMI:Location[attribute::LocationID=10]  
')  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
### <a name="computing-predicate-truth-values"></a>Berechnen des Prädikatwahrheitswerts  
 Gemäß den XQuery-Spezifikationen werden die folgenden Regeln angewendet, um den Prädikatwahrheitswert zu ermitteln:  
  
1.  Wenn der Wert des Prädikatausdrucks eine leere Sequenz ist, ist der Prädikatwahrheitswert False.  
  
     Zum Beispiel:  
  
    ```  
    SELECT Instructions.query('  
    declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
     /child::AWMI:root/child::AWMI:Location[attribute::LotSize]  
    ')  
    FROM Production.ProductModel  
    WHERE ProductModelID=7  
    ```  
  
     Der Pfadausdruck in dieser Abfrage gibt nur die <`Location`> Element-Knoten, die über ein LotSize-Attribut verfügen. Wenn das Prädikat für eine bestimmte eine leere Sequenz zurückgibt <`Location`>, dass arbeitsplatzstandort nicht im Ergebnis zurückgegeben wird.  
  
2.  Werte können nur xs: Integer, xs: Boolean oder ein Knoten sein.-Prädikat\*. Für Knoten\*, das Prädikat "true", wenn alle Knoten vorhanden sind, und "false" für eine leere Sequenz ergibt. Alle anderen numerischen Typen wie z. B. double und float generieren einen statischen Typisierungsfehler. Der Prädikatwahrheitswert eines Ausdrucks ist ausschließlich dann True, wenn die resultierende ganze Zahl gleich dem Wert der Kontextposition ist. Darüber hinaus nur Integer-Literalwerte und die **last()** -Funktion verringern die Kardinalität des gefilterten schrittausdrucks auf 1.  
  
     Die folgende Abfrage ruft beispielsweise den dritten untergeordneten Elementknoten, von der <`Features`> Element.  
  
    ```  
    SELECT CatalogDescription.query('  
    declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
    declare namespace wm="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
     /child::PD:ProductDescription/child::PD:Features/child::*[3]  
    ')  
    FROM Production.ProductModel  
    WHERE ProductModelID=19  
    ```  
  
     Beachten Sie hinsichtlich der vorherigen Abfrage Folgendes:  
  
    -   Der dritte Schritt im Ausdruck gibt einen Prädikatausdruck mit dem Wert 3 an. Daher ist der Prädikatwahrheitswert dieses Ausdrucks nur für die Knoten True, deren Kontextposition 3 ist.  
  
    -   Der dritte Schritt gibt auch ein Platzhalterzeichen (*) an, das alle Knoten im Knotentest anzeigt. Das Prädikat filtert jedoch die Knoten und gibt nur den Knoten in der dritten Position zurück.  
  
    -   Die Abfrage gibt den dritten untergeordneten Elementknoten des der <`Features`> untergeordnete Elemente des der <`ProductDescription`>-Elemente für den Dokumentenstamm.  
  
3.  Wenn der Wert des Prädikatausdrucks ein einfacher Werttyp des booleschen Datentyps ist, entspricht der Prädikatwahrheitswert dem Wert des Prädikatausdrucks.  
  
     Die folgende Abfrage wird beispielsweise angegeben, für eine **Xml**Variablen vom Typ, der eine XML-Instanz, die Kunden Umfrage XML-Instanz enthält. Die Abfrage ruft solche Kunden ab, die über untergeordnete Elemente verfügen. In dieser Abfrage wird das wäre \<HasChildren > 1\</HasChildren >.  
  
    ```  
    declare @x xml  
    set @x='  
    <Survey>  
      <Customer CustomerID="1" >  
      <Age>27</Age>  
      <Income>20000</Income>  
      <HasChildren>1</HasChildren>  
      </Customer>  
      <Customer CustomerID="2" >  
      <Age>27</Age>  
      <Income>20000</Income>  
      <HasChildren>0</HasChildren>  
      </Customer>  
    </Survey>  
    '  
    declare @y xml  
    set @y = @x.query('  
      for $c in /child::Survey/child::Customer[( child::HasChildren[1] cast as xs:boolean ? )]  
      return   
          <CustomerWithChildren>  
              { $c/attribute::CustomerID }  
          </CustomerWithChildren>  
    ')  
    select @y  
    ```  
  
     Beachten Sie hinsichtlich der vorherigen Abfrage Folgendes:  
  
    -   Der Ausdruck in der **für** -Schleife umfasst zwei Schritte aus, und der zweite Schritt gibt ein Prädikat. Der Wert dieses Prädikats ist ein Wert des booleschen Datentyps. Wenn dieser Wert True ist, so ist auch der Wahrheitswert des Prädikats True.  
  
    -   Die Abfrage gibt die <`Customer`> Element untergeordnete Elemente, die dem Prädikatwert ist "true", der die \<Umfrage > untergeordneten Elemente des Basisverzeichnisses. Dies ist das Ergebnis:  
  
        ```  
        <CustomerWithChildren CustomerID="1"/>   
        ```  
  
4.  Wenn der Wert des Prädikatausdrucks eine Sequenz ist, die mindestens einen Knoten enthält, so ist der Wahrheitswert des Prädikats True.  
  
 Die folgende Abfrage ruft z. B. ProductModelID für Produktmodelle, deren XML-katalogbeschreibung mindestens eine Funktion, die ein untergeordnetes Element von enthält, der <`Features`> Element, aus dem Namespace zugeordnete der **Wm**Präfix.  
  
```  
SELECT ProductModelID  
FROM   Production.ProductModel  
WHERE CatalogDescription.exist('  
             declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
             declare namespace wm="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
             /child::PD:ProductDescription/child::PD:Features[wm:*]  
             ') = 1  
```  
  
 Beachten Sie hinsichtlich der vorherigen Abfrage Folgendes:  
  
-   Gibt an, die WHERE-Klausel der [EXIST()-Methode (XML-Datentyp)](../t-sql/xml/exist-method-xml-data-type.md).  
  
-   Der Pfadausdruck in der **exist()** Methode gibt ein Prädikat im zweiten Schritt. Wenn der Prädikatausdruck eine Sequenz von mindestens einer Funktion zurückgibt, ist der Wahrheitswert dieses Prädikatausdrucks True. In diesem Fall, da die **exist()** Methode True zurückgibt, wird die Produktmodell-ID zurückgegeben.  
  
## <a name="static-typing-and-predicate-filters"></a>Statische Typisierung und Prädikatfilter  
 Die Prädikate können sich auch auf den statisch abgeleiteten Typ eines Ausdrucks auswirken. Integer-Literalwerte und die **last()** -Funktion verringern die Kardinalität des gefilterten schrittausdrucks zumeist auf 1.  
  
  
