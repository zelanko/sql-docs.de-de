---
title: query()-Methode (xml-Datentyp) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- query method
- query() method
ms.assetid: f48f6f7b-219f-463a-bf36-bc10f21afaeb
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: eb7f52a1861567630229b31679b3d84cb42eaeae
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51703928"
---
# <a name="query-method-xml-data-type"></a>query()-Methode (xml-Datentyp)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt eine XQuery für eine Instanz des **xml**-Datentyps an. Das Ergebnis ist vom Typ **xml**. Die Methode gibt eine Instanz nicht typisierten XMLs zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
query ('XQuery')  
```  
  
## <a name="arguments"></a>Argumente  
 XQuery  
 Ist eine Zeichenfolge (ein XQuery-Ausdruck), die XML-Knoten wie z. B. element- und attribute-Knoten in einer XML-Instanz abfragt.  
  
## <a name="examples"></a>Beispiele  
 Dieser Abschnitt enthält Beispiele für das Verwenden der query()-Methode des **xml**-Datentyps.  
  
### <a name="a-using-the-query-method-against-an-xml-type-variable"></a>A. Verwenden der query()-Methode mit einer Variablen vom Typ XML  
 Das folgende Beispiel deklariert eine Variable **@myDoc** vom Typ **xml** und weist dieser dann eine XML-Instanz zu. Die **query()**-Methode wird anschließend zum Angeben einer XQuery für das Dokument verwendet.  
  
 Die Abfrage ruft das untergeordnete <`Features`>-Element des <`ProductDescription`>-Elements ab:  
  
```  
declare @myDoc xml  
set @myDoc = '<Root>  
<ProductDescription ProductID="1" ProductName="Road Bike">  
<Features>  
  <Warranty>1 year parts and labor</Warranty>  
  <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
</Features>  
</ProductDescription>  
</Root>'  
SELECT @myDoc.query('/Root/ProductDescription/Features')  
```  
  
 Dies ist das Ergebnis:  
  
```  
<Features>  
  <Warranty>1 year parts and labor</Warranty>  
  <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
</Features>        
```  
  
### <a name="b-using-the-query-method-against-an-xml-type-column"></a>B. Verwenden der query()-Methode für eine Spalte vom Typ XML  
 Im folgenden Beispiel wird die **query()**-Methode zum Angeben einer XQuery für die **CatalogDescription**-Spalte vom Typ **xml** in der **AdventureWorks**-Datenbank verwendet:  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
<Product ProductModelID="{ /PD:ProductDescription[1]/@ProductModelID }" />  
') as Result  
FROM Production.ProductModel  
where CatalogDescription.exist('  
declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
declare namespace wm="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
     /PD:ProductDescription/PD:Features/wm:Warranty ') = 1  
```  
  
 Beachten Sie hinsichtlich der vorherigen Abfrage Folgendes:  
  
-   Die CatalogDescription-Spalte ist eine typisierte **xml**-Spalte. Dies bedeutet, dass ihr eine Schemaauflistung zugeordnet wurde. Im [XQuery-Prolog](../../xquery/modules-and-prologs-xquery-prolog.md) wird das **namespace**-Schlüsselwort zum Definieren des Präfixes verwendet, das später im Abfragetext verwendet wird.  
  
-   Die **query()**-Methode erstellt in XML ein <`Product`>-Element mit einem **ProductModelID**-Attribut, dessen **ProductModelID**-Attributwert aus der Datenbank abgerufen wird. Weitere Informationen zur XML-Konstruktion finden Sie unter [XML Construction &#40;XQuery&#41; (XML-Konstruktion (XQUERY))](../../xquery/xml-construction-xquery.md).  
  
-   Die [exist() Method (xml Data Type)](../../t-sql/xml/exist-method-xml-data-type.md) (exist()-Methode (XML-Datentyp)) in der WHERE-Klausel wird verwendet, um nur Zeilen zu suchen, die das <`Warranty`>-Element im XML-Code enthalten. Auch hier wird das **namespace**-Schlüsselwort zum Definieren von zwei Namespacepräfixen verwendet.  
  
 Dies ist das Teilergebnis:  
  
```  
<Product ProductModelID="19"/>   
<Product ProductModelID="23"/>   
...  
```  
  
 Beachten Sie, dass die query()- und exist()-Methoden beide das PD-Präfix deklarieren. In diesen Fällen können Sie WITH XMLNAMESPACES verwenden, um zuerst die Präfixe zu definieren und dann in der Abfrage zu verwenden.  
  
```  
WITH XMLNAMESPACES 
(  
   'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS PD,  
   'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain' AS WM
)  
SELECT CatalogDescription.query('<Product ProductModelID="{ /PD:ProductDescription[1]/@ProductModelID }" />')
       AS Result  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('/PD:ProductDescription/PD:Features/WM:Warranty ') = 1;

```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Hinzufügen von Namespaces zu Abfragen mit WITH XMLNAMESPACES](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [Vergleichen von typisiertem XML mit nicht typisiertem XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Erstellen von Instanzen der XML-Daten](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [XML-Datentypmethoden](../../t-sql/xml/xml-data-type-methods.md)   
 [XML DML &#40;Data Modification Language&#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
