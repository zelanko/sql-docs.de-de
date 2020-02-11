---
title: not-Funktion (XQuery) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- effective Boolean value [XQuery]
- fn:not function
- not function [XQuery]
- EBV
ms.assetid: 93dfc377-45f1-4384-9392-560d9331a915
author: rothja
ms.author: jroth
ms.openlocfilehash: 8711190a6d3cbae0c716f7f62af478b70b9473e0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68038914"
---
# <a name="functions-on-boolean-values---not-function"></a>Funktionen für boolesche Werte – not Function 
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt true zurück, wenn der effektive boolesche Wert *$arg* false ist, und gibt false zurück, wenn der effektive boolesche Wert *$arg* true ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
fn:not($arg as item()*) as xs:boolean  
```  
  
## <a name="arguments"></a>Argumente  
 *$arg*  
 Eine Elementsequenz, für die es einen effektiven booleschen Wert gibt.  
  
## <a name="examples"></a>Beispiele  
 Dieses Thema stellt XQuery-Beispiele für XML-Instanzen bereit, die in verschiedenen Spalten vom Typ **XML** in der AdventureWorks-Datenbank gespeichert sind.  
  
### <a name="a-using-the-not-xquery-function-to-find-product-models-whose-catalog-descriptions-do-not-include-the-specifications-element"></a>A. Verwenden der Not ()-Funktion von XQuery zum Suchen von Produkt Modellen, deren Katalogbeschreibungen \<nicht die Spezifikationen> Element enthalten.  
 Die folgende Abfrage konstruiert XML, das Produktmodell-IDs für Produktmodelle enthält, deren Katalogbeschreibungen das <`Specifications`>-Element nicht enthalten.  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd)  
SELECT ProductModelID, CatalogDescription.query('  
       <Product   
           ProductModelID="{ sql:column("ProductModelID") }"  
        />  
') as Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('  
     /pd:ProductDescription[not(pd:Specifications/*)]  '  
     ) = 0  
```  
  
 Beachten Sie hinsichtlich der vorherigen Abfrage Folgendes:  
  
-   Da das Dokument Namespaces verwendet, wird in diesem Beispiel die WITH NAMESPACES-Anweisung verwendet. Eine weitere Option ist die Verwendung des **Declare Namespace** -Schlüssel Worts im [XQuery-Prolog](../xquery/modules-and-prologs-xquery-prolog.md) , um das Präfix zu definieren.  
  
-   Die Abfrage erstellt dann den XML-Code, der `Product` das <>-Element und dessen **ProductModelID** -Attribut enthält.  
  
-   Die WHERE-Klausel verwendet die [exist ()-Methode (XML-Datentyp)](../t-sql/xml/exist-method-xml-data-type.md) , um die Zeilen zu filtern. Die **exist ()** -Methode gibt true zurück, \<wenn ProductDescription> Elemente vorhanden sind, \<die keine Spezifikation> untergeordnete Elemente aufweisen. Beachten Sie die Verwendung der **Not ()** -Funktion.  
  
 Dieses Resultset ist leer, da jede Produktmodell-Katalogbeschreibung \<die Spezifikationen> Elements enthält.  
  
### <a name="b-using-the-not-xquery-function-to-retrieve-work-center-locations-that-do-not-have-a-machinehours-attribute"></a>B. Abrufen von Arbeitsplatzstandorten ohne MachineHours-Attribut mit der XQuery-Funktion not()  
 Die folgende Abfrage wird beispielsweise für die Instructions-Spalte angegeben. Diese Spalte speichert Anweisungen zur Fertigung der Produktmodelle.  
  
 Die Abfrage ruft Arbeitsplatzstandorte, für die kein MachineHours-Attribut angegeben ist, für ein bestimmtes Produktmodell ab. Das heißt, dass das **MachineHours** -Attribut für den \<Speicherort> Elements nicht angegeben ist.  
  
```  
SELECT ProductModelID, Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
     for $i in /AWMI:root/AWMI:Location[not(@MachineHours)]  
     return  
       <Location LocationID="{ $i/@LocationID }"   
                   LaborHrs="{ $i/@LaborHours }" >  
        </Location>  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7   
```  
  
 Beachten Sie in der vorhergehenden Abfrage Folgendes:  
  
-   Der **deklarenamespace** im [XQuery-Prolog](../xquery/modules-and-prologs-xquery-prolog.md) definiert das Namespace Präfix "Adventure Works Manufacturing Instructions". Dieser Namespace ist mit dem in dem Fertigungsanweisungsdokument verwendeten identisch.  
  
-   In der Abfrage gibt das **Not (@MachineHours)** -Prädikat true zurück, wenn kein **MachineHours** -Attribut vorhanden ist.  
  
 Dies ist das Ergebnis:  
  
```  
ProductModelID Result   
-------------- --------------------------------------------  
7              <Location LocationID="30" LaborHrs="1"/>  
               <Location LocationID="50" LaborHrs="3"/>  
               <Location LocationID="60" LaborHrs="4"/>  
```  
  
### <a name="implementation-limitations"></a>Implementierungseinschränkungen  
 Die folgenden Einschränkungen sind zu beachten:  
  
-   Die **Not ()** -Funktion unterstützt nur Argumente vom Typ xs: Boolean, Node () * oder eine leere Sequenz.  
  
## <a name="see-also"></a>Weitere Informationen  
 [XQuery-Funktionen für den xml-Datentyp](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
