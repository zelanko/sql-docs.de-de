---
title: Local-Name-Funktion (XQuery) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:local-name function
- local-name function
ms.assetid: c901ef5d-89c5-482a-bf64-3eefbcf3098d
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 93f289ed165742ae8fdf8d49732186161a4a8b5d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62936478"
---
# <a name="functions-on-nodes---local-name"></a>Funktionen für Knoten – local-name
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt den lokalen Teil des Namens des *$arg* als xs: String, die werden entweder die Zeichenfolge der Länge 0 (null) oder die lexikalische Form einen xs: NCName verfügen. Wenn das Argument nicht bereitgestellt wird, ist der Standardwert der Kontextknoten.  
  
## <a name="syntax"></a>Syntax  
  
```  
fn:local-name() as xs:string  
fn:local-name($arg as node()?) as xs:string  
```  
  
## <a name="arguments"></a>Argumente  
 *$arg*  
 Knotenname, dessen lokaler Namensanteil abgerufen wird.  
  
## <a name="remarks"></a>Hinweise  
  
-   In SQL Server **Fn:Local-Name()** ohne Argument nur im Kontext eines kontextabhängigen Prädikats verwendet werden kann. Insbesondere kann die Funktion nur innerhalb von Klammern (`[ ]`) verwendet werden.  
  
-   Wenn das Argument angegeben wird und wenn es die leere Sequenz ist, gibt die Funktion die Zeichenfolge mit der Länge null zurück.  
  
-   Wenn der Zielknoten keinen Namen besitzt, weil es sich um einen Dokumentknoten, einen Kommentar oder einen Textknoten handelt, gibt die Funktion die Zeichenfolge mit der Länge null zurück.  
  
## <a name="examples"></a>Beispiele  
 In diesem Thema stellt XQuery-Beispiele für XML-Instanzen, die in verschiedenen gespeichert sind **Xml** Spalten vom Typ, in der AdventureWorks-Datenbank.  
  
### <a name="a-retrieve-local-name-of-a-specific-node"></a>A. Abrufen des lokalen Namens eines bestimmten Knotens  
 Die folgende Abfrage wird für eine nicht typisierte XML-Instanz angegeben. Der Abfrageausdruck `local-name(/ROOT[1])` ruft den lokalen Namensanteil des angegebenen Knotens ab.  
  
```  
declare @x xml  
set @x='<ROOT><a>111</a></ROOT>'  
SELECT @x.query('local-name(/ROOT[1])')  
-- result = ROOT  
```  
  
 Die folgende Abfrage wird für die Instructions-Spalte, eine typisierte xml-Spalte, der ProductModel-Tabelle angegeben. Der Ausdruck `local-name(/AWMI:root[1]/AWMI:Location[1])` gibt den lokalen Namen (`Location`) des angegebenen Knotens zurück.  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
     local-name(/AWMI:root[1]/AWMI:Location[1])') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
-- result = Location  
```  
  
### <a name="b-using-local-name-without-argument-in-a-predicate"></a>B. Verwenden von local-name ohne Argument in einem Prädikat  
 Die folgende Abfrage wird angegeben, für die Instructions-Spalte, die typisierte **Xml** Spalte der ProductModel-Tabelle. Der Ausdruck gibt alle untergeordneten-Elemente des zurück. die <`root`> Element, deren lokaler Namensbestandteil für den QName "Location". Die **local-name()** -Funktion ist im Prädikat angegeben und besitzt keine Argumente. der Kontextknoten wird von der Funktion verwendet.  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
  /AWMI:root//*[local-name() = "Location"]') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Die Abfrage gibt alle die <`Location`> der untergeordneten Elemente der <`root`> Element.  
  
## <a name="see-also"></a>Siehe auch  
 [Funktionen für Knoten](https://msdn.microsoft.com/library/09a8affa-3341-4f50-aebc-fdf529e00c08)   
 [Namespace-Uri-Funktion &#40;XQuery&#41;](../xquery/functions-on-nodes-namespace-uri.md)  
  
  
