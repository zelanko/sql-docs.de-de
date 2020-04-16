---
title: sql:variable() Funktion (XQuery) | Microsoft Docs
description: Erfahren Sie, wie Sie die XQuery-Erweiterungsfunktion sql:variable() verwenden, um eine Variable verfügbar zu machen, die einen relationalen SQL-Wert in einem XQuery-Ausdruck enthält.
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- sql:variable() function
- sql:variable function
ms.assetid: 6e2e5063-c1cf-4b5a-b642-234921e3f4f7
author: rothja
ms.author: jroth
ms.openlocfilehash: 8241e15643eb4aa25912451ddfed94699954797f
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388604"
---
# <a name="xquery-extension-functions---sqlvariable"></a>XQuery-Erweiterungsfunktionen – sql:variable()
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Macht eine Variable verfügbar, die einen relationalen SQL-Wert in einem XQuery-Ausdruck enthält.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sql:variable("variableName") as xdt:anyAtomicType?  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Wie im Thema [Binding Relational Data Inside XML](../t-sql/xml/binding-relational-data-inside-xml-data.md)beschrieben, können Sie diese Funktion verwenden, wenn Sie [XML-Datentypmethoden](../t-sql/xml/xml-data-type-methods.md) verwenden, um einen relationalen Wert in XQuery verfügbar zu machen.  
  
 Beispielsweise wird die [query()-Methode](../t-sql/xml/query-method-xml-data-type.md) verwendet, um eine Abfrage für eine XML-Instanz anzugeben, die in einer **XML-Datentypvariablen** oder -spalte gespeichert ist. Manchmal sollen in einer Abfrage auch Werte aus einer [!INCLUDE[tsql](../includes/tsql-md.md)]-Variablen oder einem -Parameter verwendet werden, um relationale und XML-Daten zu verbinden. Dazu verwenden Sie die Funktion **sql:variable.**  
  
 Der SQL-Wert wird einem entsprechenden XQuery-Wert zugeordnet, und sein Typ ist ein XQuery-Basistyp, der dem entsprechenden SQL-Typ entspricht.  
  
 Sie können nur auf eine **XML-Instanz** im Kontext des Quellausdrucks einer XML-DML-Insert-Anweisung verweisen. Andernfalls können Sie nicht auf Werte vom Typ **XML** oder einen benutzerdefinierten Typ der Common Language Runtime (CLR) verweisen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-the-sqlvariable-function-to-bring-a-transact-sql-variable-value-into-xml"></a>A. Einfügen einer Transact-SQL-Variablen in XML mit der sql:variable()-Funktion  
 Im folgenden Beispiel wird eine XML-Instanz erstellt, die aus Folgendem besteht:  
  
-   Einem Wert (`ProductID`) aus einer Nicht-XML-Spalte. Die [funktion sql:column()](../xquery/xquery-extension-functions-sql-column.md) wird verwendet, um diesen Wert im XML-Code zu binden.  
  
-   Einem Wert (`ListPrice`) aus einer Nicht-XML-Spalte aus einer anderen Tabelle. Die `sql:column()`-Funktion wird auch hier zum Binden dieses Werts im XML-Code verwendet.  
  
-   Einem Wert (`DiscountPrice`) aus einer [!INCLUDE[tsql](../includes/tsql-md.md)]-Variablen. Zum Binden dieses Werts im XML-Code wird die `sql:variable()`-Methode verwendet.  
  
-   Ein Wert`ProductModelName`( ) aus einer **XML-Typspalte,** um die Abfrage interessanter zu machen.  
  
 Im Folgenden wird die Abfrage aufgeführt:  
  
```sql
DECLARE @price money  
  
SET @price=2500.00  
SELECT ProductID, Production.ProductModel.ProductModelID,CatalogDescription.query('  
declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
  
       <Product   
           ProductID="{ sql:column("Production.Product.ProductID") }"  
           ProductModelID= "{ sql:column("Production.Product.ProductModelID") }"  
           ProductModelName="{/pd:ProductDescription[1]/@ProductModelName }"  
           ListPrice="{ sql:column("Production.Product.ListPrice") }"  
           DiscountPrice="{ sql:variable("@price") }"  
        />')   
FROM Production.Product   
JOIN Production.ProductModel  
ON Production.Product.ProductModelID = Production.ProductModel.ProductModelID  
WHERE ProductID=771  
```  
  
 Beachten Sie hinsichtlich der vorherigen Abfrage Folgendes:  
  
-   Der XML-Code wird durch die XQuery-Abfrage in der `query()`-Methode erstellt.  
  
-   Das `namespace` Schlüsselwort wird verwendet, um ein Namespacepräfix im [XQuery Prolog](../xquery/modules-and-prologs-xquery-prolog.md)zu definieren. Dies geschieht, weil der `ProductModelName`-Attributwert aus der Spalte des `CatalogDescription xml`-Typs abgerufen wird, der ein Schema zugeordnet ist.  
  
 Dies ist das Ergebnis:  
  
```xml
<Product ProductID="771" ProductModelID="19"   
         ProductModelName="Mountain 100"   
         ListPrice="3399.99" DiscountPrice="2500" />  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server XQuery-Erweiterungsfunktionen](https://msdn.microsoft.com/library/4bc5d499-5fec-4c3f-b11e-5ab5ef9d8f97)   
 [Vergleichen von typisiertem XML mit nicht typisiertem XML](../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [XML-Daten &#40;SQL Server-&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [Erstellen von Instanzen von XML-Daten](../relational-databases/xml/create-instances-of-xml-data.md)   
 [xml-Datentypmethoden](../t-sql/xml/xml-data-type-methods.md)   
 [XML DML &#40;Data Modification Language&#41;](../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
