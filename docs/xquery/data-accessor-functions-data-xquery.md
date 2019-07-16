---
title: Data-Funktion (XQuery) | Microsoft-Dokumentation
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
- fn:data function
- data function [XQuery]
ms.assetid: 511b5d7d-c679-4cb2-a3dd-170cc126f49d
author: rothja
ms.author: jroth
ms.openlocfilehash: 7376c57f809fa97168b27b158678d931a696b5df
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68038967"
---
# <a name="data-accessor-functions---data-xquery"></a>Data Accessor-Funktionen – data (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Gibt den typisierten Wert für jedes Element anhand des *$arg*.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
fn:data ($arg as item()*) as xdt:untypedAtomic*  
```  
  
## <a name="arguments"></a>Argumente  
 *$arg*  
 Sequenz der Items, deren typisierte Werte zurückgegeben werden.  
  
## <a name="remarks"></a>Hinweise  
 Für typisierte Werte gilt Folgendes:  
  
-   Der typisierte Wert eines atomaren Werts ist der atomare Wert.  
  
-   Der typisierte Wert eines Textknotens ist der Zeichenfolgenwert des Textknotens.  
  
-   Der typisierte Wert eines Kommentars ist der Zeichenfolgenwert des Kommentars.  
  
-   Der typisierte Wert einer Verarbeitungsanweisung ist der Inhalt der Verarbeitungsanweisung, ohne den Namen des Verarbeitungsanweisungsziels.  
  
-   Der typisierte Wert eines Dokumentknotens ist dessen Zeichenfolgenwert.  
  
 Für Attribut- und Elementknoten gilt Folgendes:  
  
-   Wenn ein Attributknoten mit einem XML-Schematyp typisiert wird, ist dessen typisierter Wert der entsprechende typisierte Wert.  
  
-   Wenn der Attributknoten nicht typisiert ist, entspricht dessen typisierte Wert seinem Zeichenfolgenwert, der als eine Instanz von zurückgegeben wird **xdt: UntypedAtomic**.  
  
-   Wenn der Elementknoten nicht typisiert wurde, entspricht dessen typisierte Wert seinem Zeichenfolgenwert, der als eine Instanz von zurückgegeben wird **xdt: UntypedAtomic**.  
  
 Für typisierte Elementknoten gilt Folgendes:  
  
-   Wenn das Element einen einfachen Inhaltstyp hat **data()** gibt den typisierten Wert des Elements.  
  
-   Wenn der Knoten des komplexen Typs, einschließlich xs: anyType, **data()** einen statischen Fehler zurück.  
  
 Obwohl durch die Verwendung der **data()** Funktion ist häufig optional ist, wie gezeigt in den folgenden Beispielen wird die Angabe der **data()** Funktion einer expliziten Erhöhung der abfragelesbarkeit. Weitere Informationen finden Sie unter [XQuery-Grundlagen](../xquery/xquery-basics.md).  
  
 Sie können keine angeben **data()** auf erstellt XML, wie im folgenden dargestellt:  
  
```  
declare @x xml  
set @x = ''  
select @x.query('data(<SomeNode>value</SomeNode>)')  
```  
  
## <a name="examples"></a>Beispiele  
 In diesem Thema stellt XQuery-Beispiele für XML-Instanzen in verschiedenen gespeicherten **Xml** Spalten vom Typ, in der AdventureWorks-Datenbank.  
  
### <a name="a-using-the-data-xquery-function-to-extract-typed-value-of-a-node"></a>A. Verwenden der XQuery-Funktion data() XQuery zum Extrahieren des typisierten Werts eines Knotens.  
 Die folgende Abfrage veranschaulicht, wie die **data()** Funktion wird verwendet, um die Werte der ein Attribut, ein Element, und ein Textknoten abrufen:  
  
```  
WITH XMLNAMESPACES (  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS p1,  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
  
SELECT CatalogDescription.query(N'  
 for $pd in //p1:ProductDescription  
 return   
    <Root   
      ProductID = "{ data( ($pd//@ProductModelID)[1] ) }"   
      Feature =   "{ data( ($pd/p1:Features/wm:Warranty/wm:Description)[1] ) }" >  
    </Root>  
 ') as Result  
FROM Production.ProductModel  
WHERE ProductModelID = 19  
```  
  
 Dies ist das Ergebnis:  
  
```  
<Root ProductID="19" Feature="parts and labor"/>  
```  
  
 Wie bereits erwähnt, die **data()** -Funktion ist optional, wenn Sie Attribute konstruieren. Wenn Sie keinen angeben der **data()** -Funktion, wird Sie implizit angenommen. Die folgende Abfrage führt zu denselben Ergebnissen wie die vorherige Abfrage:  
  
```  
WITH XMLNAMESPACES (  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS p1,  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
  
SELECT CatalogDescription.query('  
      for $pd in //p1:ProductDescription  
         return   
          <Root    
                ProductID = "{ ($pd/@ProductModelID)[1] }"    
                Feature =   "{ ($pd/p1:Features/wm:Warranty/wm:Description)[1] }" >  
           </Root>  
 ') as Result  
FROM Production.ProductModel  
WHERE ProductModelID = 19  
```  
  
 Die folgenden Beispiele veranschaulichen Fälle, in denen die **data()** ist erforderlich.  
  
 In der folgenden Abfrage **$pd / P1: Specifications / Material** gibt die <`Material`> Element. Darüber hinaus **Data ($pd/P1: Specifications/Material)** Daten des Typs xdt: UntypedAtomic, gibt Zeichendaten zurück, da <`Material`> nicht typisiert ist. Wenn die Eingabe nicht typisiert ist, das Ergebnis des **data()** typisiert ist, als **xdt: UntypedAtomic**.  
  
```  
SELECT CatalogDescription.query('  
declare namespace p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
      for $pd in //p1:ProductDescription  
         return   
          <Root>  
             { $pd/p1:Specifications/Material }  
             { data($pd/p1:Specifications/Material) }  
           </Root>  
 ') as Result  
FROM Production.ProductModel  
WHERE ProductModelID = 19  
```  
  
 Dies ist das Ergebnis:  
  
```  
<Root>  
  <Material>Almuminum Alloy</Material>Almuminum Alloy  
</Root>  
```  
  
 In der folgenden Abfrage **data($pd/p1:Features/wm:Warranty)** einen statischen Fehler zurück, da <`Warranty`> ist ein Element mit komplexem Typ.  
  
```  
WITH XMLNAMESPACES (  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS p1,  
'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS wm)  
  
SELECT CatalogDescription.query('  
 <Root>  
   {     /p1:ProductDescription/p1:Features/wm:Warranty }  
   { data(/p1:ProductDescription/p1:Features/wm:Warranty) }  
 </Root>  
 ') as Result  
FROM  Production.ProductModel  
WHERE ProductModelID = 23  
```  
  
## <a name="see-also"></a>Siehe auch  
 [XQuery Functions against the xml Data Type (XQuery-Funktionen für den xml-Datentyp)](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
