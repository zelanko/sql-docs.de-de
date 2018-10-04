---
title: String-Funktion (XQuery) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- string function
- fn:string function
ms.assetid: 7baa2959-9340-429b-ad53-3df03d8e13fc
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a5b98660cb803c2cb3e17ee8be1d4b619de394c9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47836448"
---
# <a name="data-accessor-functions---string-xquery"></a>Data Accessor-Funktionen – string (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt den Wert der *$arg* als Zeichenfolge dargestellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
fn:string() as xs:string  
fn:string($arg as item()?) as xs:string  
```  
  
## <a name="arguments"></a>Argumente  
 *$arg*  
 Ist ein Knoten oder ein atomarer Wert.  
  
## <a name="remarks"></a>Hinweise  
  
-   Wenn *$arg* ist die leere Sequenz ist, wird die Zeichenfolge der Länge 0 (null) zurückgegeben.  
  
-   Wenn *$arg* ist ein Knoten, die Funktion gibt den Zeichenfolgenwert des Knotens, der mit dem Zeichenfolgenwert-Accessors abgerufen wird. Dies wurde in der W3C XQuery 1.0- und XPath 2.0-Datenmodellspezifikation definiert.  
  
-   Wenn *$arg* ein atomarer Wert ist, wird die Funktion gibt zurück, die gleiche Zeichenfolge, die durch den Ausdruck, der umgewandelte zurückgegeben wird **xs: String**, *$arg*, außer wenn nichts anderes angegeben ist.  
  
-   Wenn der Typ des *$arg* ist **xs: anyURI**, der URI ohne Escapezeichen für Sonderzeichen in eine Zeichenfolge konvertiert wird.  
  
-   In dieser Implementierung kann **Fn:String()** ohne Argument nur im Kontext eines kontextabhängigen Prädikats verwendet werden kann. Insbesondere kann die Funktion nur innerhalb von Klammern ([ ]) verwendet werden.  
  
## <a name="examples"></a>Beispiele  
 In diesem Thema stellt XQuery-Beispiele für XML-Instanzen, die in verschiedenen gespeichert sind **Xml** Spalten vom Typ, in der AdventureWorks-Datenbank.  
  
### <a name="a-using-the-string-function"></a>A. Verwenden der Zeichenfolgenfunktion  
 Die folgende Abfrage ruft den untergeordneten <`Features`>-Elementknoten des <`ProductDescription`>-Elements ab.  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
 /PD:ProductDescription/PD:Features  
')  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 Dies ist das Teilergebnis:  
  
```  
<PD:Features xmlns:PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">  
   These are the product highlights.   
   <p1:Warranty xmlns:p1="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <p1:WarrantyPeriod>3 years</p1:WarrantyPeriod>  
    <p1:Description>parts and labor</p1:Description>  
   </p1:Warranty>  
       ...  
</PD:Features>  
```  
  
 Bei Angabe der **string()** -Funktion erhalten Sie den Zeichenfolgenwert des angegebenen Knotens.  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
 string(/PD:ProductDescription[1]/PD:Features[1])  
')  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 Dies ist das Teilergebnis.  
  
```  
These are the product highlights.   
3 yearsparts and labor...    
```  
  
### <a name="b-using-the-string-function-on-various-nodes"></a>B. Verwenden der Zeichenfolgenfunktion für verschiedene Knoten  
 Im folgenden Beispiel wird eine XML-Instanz einer Variablen des Typs xml zugewiesen. Abfragen werden angegeben, um das Ergebnis der Anwendung veranschaulichen **string()** auf verschiedenen Knoten.  
  
```  
declare @x xml  
set @x = '<?xml version="1.0" encoding="UTF-8" ?>  
<!--  This is a comment -->  
<root>  
  <a>10</a>  
just text  
  <b attr="x">20</b>  
</root>  
'  
```  
  
 Die folgende Abfrage ruft den Zeichenfolgenwert des Dokumentknotens ab. Dieser Wert wird generiert, indem die Zeichenfolgenwerte aller seiner Nachfolgertextknoten verkettet werden.  
  
```  
select @x.query('string(/)')  
```  
  
 Dies ist das Ergebnis:  
  
```  
This is a comment 10  
just text  
 20  
```  
  
 Die folgende Abfrage versucht, den Zeichenfolgenwert eines Verarbeitungsanweisungsknotens abzurufen. Das Ergebnis ist eine leere Sequenz, weil kein Textknoten enthalten ist.  
  
```  
select @x.query('string(/processing-instruction()[1])')  
```  
  
 Die folgende Abfrage ruft den Zeichenfolgenwert des Kommentarknotens ab und gibt den Textknoten zurück.  
  
```  
select @x.query('string(/comment()[1])')  
```  
  
 Dies ist das Ergebnis:  
  
```  
This is a comment   
```  
  
## <a name="see-also"></a>Siehe auch  
 [XQuery Functions against the xml Data Type (XQuery-Funktionen für den xml-Datentyp)](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
