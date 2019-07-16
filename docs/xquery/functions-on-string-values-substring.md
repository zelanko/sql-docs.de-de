---
title: SUBSTRING-Funktion (XQuery) | Microsoft-Dokumentation
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
- substring function [XQuery]
- fn:substring function
ms.assetid: 2b3b8651-de51-46dc-af82-c86c45eac871
author: rothja
ms.author: jroth
ms.openlocfilehash: 2188cff20411fe90d4858763f65cff7f6fe9c9d1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68004639"
---
# <a name="functions-on-string-values---substring"></a>Funktionen für Zeichenfolgenwerte – substring
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt einen Teil der Wert des zurück *$sourceString*, beginnend ab der durch den Wert der angegebenen Position *$startingLoc,* und die Anzahl der Zeichen, die durch den Wert der angegebenen *$ Länge*.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
fn:substring($sourceString as xs:string?,  
                          $startingLoc as xs:decimal?) as xs:string?  
  
fn:substring($sourceString as xs:string?,  
                          $startingLoc as xs:decimal?,  
                          $length as xs:decimal?) as xs:string?  
```  
  
## <a name="arguments"></a>Argumente  
 *$sourceString*  
 Quellzeichenfolge.  
  
 *$startingLoc*  
 Ausgangspunkt in der Quellzeichenfolge, an dem die Unterzeichenfolge beginnt. Wenn dieser Wert negativ oder 0 ist, werden nur die Zeichen an Positionen größer null zurückgegeben. Wenn sie größer als die Länge des ist der *$sourceString*, wird die Zeichenfolge der Länge 0 (null) zurückgegeben.  
  
 *$length*  
 [optional] Anzahl der abzurufenden Zeichen. Wenn nicht angegeben, wird alle Zeichen aus dem Speicherort im angegebenen *$startingLoc* bis zum Ende der Zeichenfolge.  
  
## <a name="remarks"></a>Hinweise  
 Die Version der Funktion mit drei Argumenten gibt die Zeichen in `$sourceString` zurück, deren Position `$p` genügt:  
  
 `fn:round($startingLoc) <= $p < fn:round($startingLoc) + fn:round($length)`  
  
 Der Wert des *$length* kann größer sein als die Anzahl der Zeichen im Wert des *$sourceString* der Startposition. In diesem Fall gibt die Teilzeichenfolge zurück, die Zeichen bis zum Ende des *$sourceString*.  
  
 Das erste Zeichen einer Zeichenfolge befindet sich an Position 1.  
  
 Wenn der Wert des *$sourceString* ist die leere Sequenz ist, als die Zeichenfolge der Länge 0 (null) behandelt. Wenn *$startingLoc* oder *$length* leere Sequenz ist, wird die leere Sequenz zurückgegeben.  
  
## <a name="supplementary-characters-surrogate-pairs"></a>Ergänzende Zeichen (Ersatzpaare)  
 Das Verhalten von Ersatzzeichenpaaren in XQuery-Funktionen hängt vom Kompatibilitätsgrad der Datenbank ab und in einigen Fällen vom Standardnamespace-URI für Funktionen. Weitere Informationen finden Sie im Abschnitt "XQuery-Funktionen sind Ersatzzeichenabhängig" im Thema [wichtige Änderungen an Funktionen der Datenbank-Engine in SQL Server 2016](../database-engine/breaking-changes-to-database-engine-features-in-sql-server-2016.md). Siehe auch [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41; ](../t-sql/statements/alter-database-transact-sql-compatibility-level.md) und [Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="implementation-limitations"></a>Implementierungseinschränkungen  
 SQL Server erfordert die *$startingLoc* und *$length Parameter* vom Typ xs: decimal anstelle von xs: Double sind.  
  
 SQL Server ermöglicht *$startingLoc* und *$length* leere Sequenz ist, zu werden, weil die leere Sequenz ein möglicher Wert aus, wenn dynamische Fehler () zugeordnet werden wird.  
  
## <a name="examples"></a>Beispiele  
 In diesem Thema stellt XQuery-Beispiele für XML-Instanzen in verschiedenen gespeicherten **Xml** -Typspalten in der [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] Datenbank.  
  
### <a name="a-using-the-substring-xquery-function-to-retrieve-partial-summary-product-model-descriptions"></a>A. Verwenden der substring()-Funktion von XQuery zum Abrufen von Teilzusammenfassungsbeschreibungen der Produktmodelle  
 Die Abfrage ruft die ersten 50 Zeichen des Texts, der das Produktmodell beschreibt die <`Summary`>-Element im Dokument.  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd)  
SELECT ProductModelID, CatalogDescription.query('  
    <Prod>{ substring(string((/pd:ProductDescription/pd:Summary)[1]), 1, 50) }</Prod>  
 ') as Result  
FROM Production.ProductModel  
where CatalogDescription.exist('/pd:ProductDescription')  = 1;  
```  
  
 Beachten Sie hinsichtlich der vorherigen Abfrage Folgendes:  
  
-   Die **string()** Funktion gibt den String-Wert, der die <`Summary`> Element. Diese Funktion wird verwendet, da die <`Summary`>-Element enthält sowohl das Text-als auch die Unterelemente (html-Formatierungselemente), und da Sie diese Elemente überspringen und den gesamten Text abrufen.  
  
-   Die **substring()** Funktion ruft die ersten 50 Zeichen ab, aus dem String-Wert abgerufen, indem die **string()** .  
  
 Dies ist ein Teilergebnis gezeigt:  
  
```  
ProductModelID Result  
-------------- ----------------------------------------------------  
19      <Prod>Our top-of-the-line competition mountain bike.</Prod>   
23      <Prod>Suitable for any type of riding, on or off-roa</Prod>  
...  
```  
  
## <a name="see-also"></a>Siehe auch  
 [XQuery Functions against the xml Data Type (XQuery-Funktionen für den xml-Datentyp)](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
