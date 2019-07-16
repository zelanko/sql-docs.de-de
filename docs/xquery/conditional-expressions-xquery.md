---
title: Bedingte Ausdrücke (XQuery) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- XQuery, conditional expressions
- expressions [XQuery], conditional
- effective Boolean value [XQuery]
- if-then-else statement [XQuery]
- conditional expressions [XQuery]
- EBV
ms.assetid: b280dd96-c80f-4c51-bc06-a88d42174acb
author: rothja
ms.author: jroth
ms.openlocfilehash: f593455269b8c005a3b4d3725f4360db77ea48f2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68039007"
---
# <a name="conditional-expressions-xquery"></a>Bedingte Ausdrücke (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  XQuery unterstützt die folgende **If-Then-else** Anweisung:  
  
```  
if (<expression1>)  
then  
  <expression2>  
else  
  <expression3>  
```  
  
 Abhängig vom effektiven booleschen Wert von `expression1` wird entweder `expression2` oder `expression3` ausgewertet. Zum Beispiel:  
  
-   Wenn der Testausdruck `expression1` eine leere Sequenz ergibt, ist das Ergebnis "False".  
  
-   Wenn der Testausdruck `expression1` einen einfachen booleschen Wert ergibt, gilt dieser Wert als Ergebnis des Ausdrucks.  
  
-   Wenn der Testausdruck `expression1` eine Sequenz aus einem oder mehreren Knoten ergibt, ist das Ergebnis des Ausdrucks "True".  
  
-   Anderenfalls wird ein statischer Fehler ausgegeben.  
  
 Beachten Sie dabei außerdem Folgendes:  
  
-   Der Testausdruck muss in Klammern stehen.  
  
-   Die **else** -Ausdruck erforderlich ist. Falls Sie ihn nicht benötigen, können Sie " ( ) " zurückgeben, wie dies in den Beispielen der Fall ist.  
  
 Die folgende Abfrage wird beispielsweise angegeben, für die **Xml** Variablen vom Typ. Die **Wenn** -Bedingung testet den Wert der SQL-Variablen (@v) innerhalb des XQuery-Ausdrucks mit der [SQL:Variable()-Funktion](../xquery/xquery-extension-functions-sql-variable.md) -Erweiterungsfunktion. Wenn der Wert der Variable "FirstName" ist, wird die <`FirstName`> Element. Andernfalls wird die <`LastName`> Element.  
  
```  
declare @x xml  
declare @v varchar(20)  
set @v='FirstName'  
set @x='  
<ROOT rootID="2">  
  <FirstName>fname</FirstName>  
  <LastName>lname</LastName>  
</ROOT>'  
SELECT @x.query('  
if ( sql:variable("@v")="FirstName" ) then  
  /ROOT/FirstName  
 else  
   /ROOT/LastName  
')  
```  
  
 Dies ist das Ergebnis:  
  
```  
<FirstName>fname</FirstName>  
```  
  
 Die folgende Abfrage ruft die beiden ersten Funktionsbeschreibungen der Produktkatalogbeschreibung eines bestimmten Produktmodells ab. Wenn Sie weitere Features in das Dokument vorhanden sind, fügt es eine <`there-is-more`>-Element ohne Inhalt.  
  
```  
SELECT CatalogDescription.query('  
     declare namespace p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     <Product>   
          { /p1:ProductDescription/@ProductModelID }  
          { /p1:ProductDescription/@ProductModelName }   
          {  
            for $f in /p1:ProductDescription/p1:Features/*[position()\<=2]  
            return  
            $f   
          }  
          {  
            if (count(/p1:ProductDescription/p1:Features/*) > 2)  
            then \<there-is-more/>  
            else ()  
          }   
     </Product>          
') as x  
FROM Production.ProductModel  
WHERE ProductModelID = 19  
```  
  
 In der vorherigen Abfrage, die die Bedingung in der **Wenn** Ausdruck überprüft, ob es mehr als zwei untergeordnete Elemente <`Features`>. Wenn dies der Fall ist, wird als Ergebnis ein `\<there-is-more/>`-Element zurückgegeben.  
  
 Dies ist das Ergebnis:  
  
```  
<Product ProductModelID="19" ProductModelName="Mountain 100">  
  \<p1:Warranty xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    \<p1:WarrantyPeriod>3 years\</p1:WarrantyPeriod>  
    \<p1:Description>parts and labor\</p1:Description>  
  \</p1:Warranty>  
  \<p2:Maintenance xmlns:p2="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    \<p2:NoOfYears>10 years\</p2:NoOfYears>  
    \<p2:Description>maintenance contract available through your dealer or any AdventureWorks retail store.\</p2:Description>  
  \</p2:Maintenance>  
  \<there-is-more />  
</Product>  
```  
  
 In der folgenden Abfrage wird eine <`Location`>-Element mit einem LocationID-Attribut wird zurückgegeben, wenn arbeitsplatzstandort nicht setupzeiten angibt.  
  
```  
SELECT Instructions.query('  
     declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
        for $WC in //AWMI:root/AWMI:Location  
        return  
        if ( $WC[not(@SetupHours)] )  
        then  
          <WorkCenterLocation>  
             { $WC/@LocationID }   
          </WorkCenterLocation>  
         else  
           ()  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
 Dies ist das Ergebnis:  
  
```  
<WorkCenterLocation LocationID="30" />  
<WorkCenterLocation LocationID="45" />  
<WorkCenterLocation LocationID="60" />  
```  
  
 Diese Abfrage geschrieben werden kann, ohne die **Wenn** -Klausel, wie im folgenden Beispiel gezeigt:  
  
```  
SELECT Instructions.query('  
     declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
for $WC in //AWMI:root/AWMI:Location[not(@SetupHours)]   
        return  
          <Location>  
             { $WC/@LocationID }   
          </Location>  
') as Result  
FROM Production.ProductModel  
where ProductModelID=7  
```  
  
## <a name="see-also"></a>Siehe auch  
 [XQuery Expressions (XQuery-Ausdrücke)](../xquery/xquery-expressions.md)  
  
  
