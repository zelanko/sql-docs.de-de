---
title: NOT-Funktion (XQuery) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68038914"
---
# <a name="functions-on-boolean-values---not-function"></a>Funktionen für boolesche Werte – not Function 
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt "true" zurück, wenn der effektive boolesche Wert des *$arg* ist "false", und gibt "false" zurück, wenn der effektive boolesche Wert des *$arg* ist "true".  
  
## <a name="syntax"></a>Syntax  
  
```  
  
fn:not($arg as item()*) as xs:boolean  
```  
  
## <a name="arguments"></a>Argumente  
 *$arg*  
 Eine Elementsequenz, für die es einen effektiven booleschen Wert gibt.  
  
## <a name="examples"></a>Beispiele  
 In diesem Thema stellt XQuery-Beispiele für XML-Instanzen, die in verschiedenen gespeichert sind **Xml** Spalten vom Typ, in der AdventureWorks-Datenbank.  
  
### <a name="a-using-the-not-xquery-function-to-find-product-models-whose-catalog-descriptions-do-not-include-the-specifications-element"></a>A. Verwenden der NOT()-XQuery-Funktion zum Suchen nach Produktmodellen, deren katalogbeschreibungen enthalten nicht die \<Spezifikationen > Element.  
 Die folgende Abfrage konstruiert XML, das Produktmodell-IDs für Produktmodelle enthält, deren katalogbeschreibungen nicht enthalten, die <`Specifications`> Element.  
  
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
  
-   Da das Dokument Namespaces verwendet, wird in diesem Beispiel die WITH NAMESPACES-Anweisung verwendet. Eine weitere Möglichkeit ist die Verwendung der **Namespace deklarieren** -Schlüsselwort in der [XQuery-Prolog](../xquery/modules-and-prologs-xquery-prolog.md) das Präfix zu definieren.  
  
-   Anschließend konstruiert die Abfrage die XML mit der <`Product`>-Element und dessen **ProductModelID** Attribut.  
  
-   Die WHERE-Klausel verwendet die [EXIST()-Methode (XML-Datentyp)](../t-sql/xml/exist-method-xml-data-type.md) zum Filtern von Zeilen. Die **exist()** Methode gibt True zurück, wenn es gibt \<ProductDescription >-Elemente, die keine \<Spezifikation > untergeordnete Elemente. Beachten Sie die Verwendung der **"NOT()" "** Funktion.  
  
 Dieses Resultset ist leer, da jedes Produktmodell-katalogbeschreibung enthält die \<Spezifikationen > Element.  
  
### <a name="b-using-the-not-xquery-function-to-retrieve-work-center-locations-that-do-not-have-a-machinehours-attribute"></a>B. Abrufen von Arbeitsplatzstandorten ohne MachineHours-Attribut mit der XQuery-Funktion not()  
 Die folgende Abfrage wird beispielsweise für die Instructions-Spalte angegeben. Diese Spalte speichert Anweisungen zur Fertigung der Produktmodelle.  
  
 Die Abfrage ruft Arbeitsplatzstandorte, für die kein MachineHours-Attribut angegeben ist, für ein bestimmtes Produktmodell ab. Das heißt, dass das Attribut **MachineHours** für nicht angegeben ist die \<Speicherort > Element.  
  
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
  
 Beachten Sie in der vorherigen Abfrage gibt Folgendes an:  
  
-   Die **Declarenamespace** in [XQuery-Prolog](../xquery/modules-and-prologs-xquery-prolog.md) definiert das Namespacepräfix der fertigungsanweisungen in Adventure Works. Dieser Namespace ist mit dem in dem Fertigungsanweisungsdokument verwendeten identisch.  
  
-   In der Abfrage die **nicht (@MachineHours)** -Prädikat True zurück, wenn es ist keine **MachineHours** Attribut.  
  
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
  
-   Die **"NOT()" "** Funktion unterstützt nur Argumente vom Typ xs: Boolean, oder node() *, oder eine leere Sequenz.  
  
## <a name="see-also"></a>Siehe auch  
 [XQuery Functions against the xml Data Type (XQuery-Funktionen für den xml-Datentyp)](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
