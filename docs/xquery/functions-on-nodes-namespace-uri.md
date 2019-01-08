---
title: Namespace-Uri-Funktion (XQuery) | Microsoft-Dokumentation
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
- fn:namespace-uri function
- namespace-uri function
ms.assetid: 9b48d216-26c8-431d-9ab4-20ab187917f4
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 78d3d96e1340bb3cd8e57a930129e2c70157e61b
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52512410"
---
# <a name="functions-on-nodes---namespace-uri"></a>Funktionen für Knoten – namespace-uri
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt den Namespace-URI des QName in angegebenen *$arg* als xs: String.  
  
## <a name="syntax"></a>Syntax  
  
```  
fn:namespace-uri() as xs:string  
fn:namespace-uri($arg as node()?) as xs:string  
```  
  
## <a name="arguments"></a>Argumente  
 *$arg*  
 Knotenname, dessen Namespace-URI-Teil abgerufen wird.  
  
## <a name="remarks"></a>Hinweise  
  
-   Wird das Argument nicht angegeben, wird standardmäßig der Kontextknoten verwendet.  
  
-   In SQL Server **Fn:Namespace-URI()** ohne Argument nur im Kontext eines kontextabhängigen Prädikats verwendet werden kann. Insbesondere kann die Funktion nur innerhalb von Klammern ([ ]) verwendet werden.  
  
-   Wenn *$arg* ist die leere Sequenz ist, wird die Zeichenfolge der Länge 0 (null) zurückgegeben.  
  
-   Wenn *$arg* ein Element- oder Attributknoten, dessen expanded-QName nicht in einem Namespace, der die Funktion ist, gibt die Zeichenfolge der Länge 0 (null) zurück.  
  
## <a name="examples"></a>Beispiele  
 In diesem Thema stellt XQuery-Beispiele für XML-Instanzen in verschiedenen gespeicherten **Xml** Spalten vom Typ, in der AdventureWorks-Datenbank.  
  
### <a name="a-retrieve-namespace-uri-of-a-specific-node"></a>A. Abrufen eines Namespace-URI eines bestimmten Knotens  
 Die folgende Abfrage wird für eine nicht typisierte XML-Instanz angegeben. Der Abfrageausdruck `namespace-uri(/ROOT[1])` ruft den Namespace-URI-Teil des angegebenen Knotens ab.  
  
```  
set @x='<ROOT><a>111</a></ROOT>'  
SELECT @x.query('namespace-uri(/ROOT[1])')  
```  
  
 Da der angegebene QName nicht über den URI-Teil des Namespace verfügt, sondern lediglich über den lokalen Teil des Namens, ist das Ergebnis eine leere Zeichenfolge.  
  
 Die folgende Abfrage wird angegeben, für die typisierte Instructions **Xml** Spalte. Der Ausdruck `namespace-uri(/AWMI:root[1]/AWMI:Location[1])` gibt den Namespace-URI des ersten untergeordneten <`Location`>-Elements des <`root`>-Elements zurück.  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
     namespace-uri(/AWMI:root[1]/AWMI:Location[1])') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Dies ist das Ergebnis:  
  
```  
https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions  
```  
  
### <a name="b-using-namespace-uri-without-argument-in-a-predicate"></a>B. Verwenden von namespace-uri() ohne Argument in einem Prädikat  
 Die folgende Abfrage wird für die CatalogDescription-Spalte vom Typ XML angegeben. Der Ausdruck gibt alle Elementknoten zurück, deren Namespace-URI `https://www.adventure-works.com/schemas/OtherFeatures` ist. Der Namespace -**uri()** -Funktion ohne Argument angegeben wird, und verwendet den Kontextknoten.  
  
```  
SELECT CatalogDescription.query('  
declare namespace p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
   /p1:ProductDescription//*[namespace-uri() = "https://www.adventure-works.com/schemas/OtherFeatures"]  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 Dies ist die Teilergebnis:  
  
```  
<p1:wheel xmlns:p1="https://www.adventure-works.com/schemas/OtherFeatures">High performance wheels.</p1:wheel>  
<p2:saddle xmlns:p2="https://www.adventure-works.com/schemas/OtherFeatures">  
  <p3:i xmlns:p3="https://www.w3.org/1999/xhtml">Anatomic design</p3:i> and made from durable leather for a full-day of riding in comfort.</p2:saddle>  
...  
```  
  
 Sie können den Namespace-URI in der vorherigen Abfrage zu `https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain` ändern. Auf diese Weise erhalten Sie alle untergeordneten Elemente des <`ProductDescription`>-Elementknotens, dessen Namespace-URI-Teil des expanded-QName `https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain` ist.  
  
### <a name="implementation-limitations"></a>Implementierungseinschränkungen  
 Die folgenden Einschränkungen sind zu beachten:  
  
-   Die **namespace-uri()** -Funktion gibt Instanzen vom Typ xs: String anstelle von xs: anyURI zurück.  
  
## <a name="see-also"></a>Siehe auch  
 [Funktionen für Knoten](https://msdn.microsoft.com/library/09a8affa-3341-4f50-aebc-fdf529e00c08)   
 [Local-Name-Funktion &#40;XQuery&#41;](../xquery/functions-on-nodes-local-name.md)  
  
  
