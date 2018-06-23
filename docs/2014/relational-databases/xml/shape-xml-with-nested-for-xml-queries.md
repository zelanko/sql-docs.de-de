---
title: Gestalten von XML mit geschachtelten FOR XML-Abfragen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FOR XML query
- queries [XML in SQL Server], nested FOR XML
- XML [SQL Server], FOR XML queries
ms.assetid: 8dc42c05-16e8-4b7b-a5d3-550b55acae26
caps.latest.revision: 11
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: af69cc7956717388f9a8f97a8220e7ffe02db76a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160609"
---
# <a name="shape-xml-with-nested-for-xml-queries"></a>Gestalten von XML mit geschachtelten FOR XML-Abfragen
  Das folgende Beispiel ist eine Abfrage der `Production.Product`-Tabelle zum Abrufen der Werte von `ListPrice` und `StandardCost` eines bestimmten Produkts. Damit die Abfrage interessant wird, werden beide Preise in einem <`Price`>-Element zurückgegeben, und jedes <`Price`>-Element verfügt über ein `PriceType`-Attribut.  
  
## <a name="example"></a>Beispiel  
 Der erwartete XML-Code hat die folgende Form:  
  
```  
<xsd:schema xmlns:schema="urn:schemas-microsoft-com:sql:SqlRowSet2" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:sqltypes="http://schemas.microsoft.com/sqlserver/2004/sqltypes" targetNamespace="urn:schemas-microsoft-com:sql:SqlRowSet2" elementFormDefault="qualified">  
  <xsd:import namespace="http://schemas.microsoft.com/sqlserver/2004/sqltypes" schemaLocation="http://schemas.microsoft.com/sqlserver/2004/sqltypes/sqltypes.xsd" />  
  <xsd:element name="Production.Product" type="xsd:anyType" />  
</xsd:schema>  
<Production.Product xmlns="urn:schemas-microsoft-com:sql:SqlRowSet2" ProductID="520">  
  <Price xmlns="" PriceType="ListPrice">133.34</Price>  
  <Price xmlns="" PriceType="StandardCost">98.77</Price>  
</Production.Product>  
```  
  
 Dies ist die geschachtelte FOR XML-Abfrage:  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Product.ProductID,   
          (SELECT 'ListPrice' as PriceType,   
                   CAST(CAST(ListPrice as NVARCHAR(40)) as XML)   
           FROM    Production.Product Price   
           WHERE   Price.ProductID=Product.ProductID   
           FOR XML AUTO, TYPE),  
          (SELECT  'StandardCost' as PriceType,   
                   CAST(CAST(StandardCost as NVARCHAR(40)) as XML)   
           FROM    Production.Product Price   
           WHERE   Price.ProductID=Product.ProductID   
           FOR XML AUTO, TYPE)  
FROM Production.Product  
WHERE ProductID=520  
for XML AUTO, TYPE, XMLSCHEMA  
```  
  
 Beachten Sie hinsichtlich der vorherigen Abfrage Folgendes:  
  
-   Die äußere SELECT-Anweisung konstruiert das <`Product`>-Element, das über ein **ProductID**-Attribut und zwei untergeordnete <`Price`>-Elemente verfügt.  
  
-   Die beiden inneren SELECT-Anweisungen konstruieren zwei <`Price`>-Elemente, von denen jedes über ein **PriceType**-Attribut verfügt, sowie XML-Code, der den Produktpreis zurückgibt.  
  
-   Die XMLSCHEMA-Direktive in der äußeren SELECT-Anweisung generiert das XSD-Inlineschema, das die Form des resultierenden XML-Codes beschreibt.  
  
 Um die Abfrage interessant zu machen, können Sie die FOR XML-Abfrage schreiben und dann eine XQuery-Abfrage für das Ergebnis schreiben, um den XML-Code umzuformen, wie das in der folgenden Abfrage gezeigt wird:  
  
```  
SELECT ProductID,   
 ( SELECT p2.ListPrice, p2.StandardCost  
   FROM Production.Product p2   
   WHERE Product.ProductID = p2.ProductID  
   FOR XML AUTO, ELEMENTS XSINIL, type ).query('  
                                   for $p in /p2/*  
                                   return   
                                    <Price PriceType = "{local-name($p)}">  
                                     { data($p) }  
                                    </Price>  
                                  ')  
FROM Production.Product  
WHERE ProductID = 520  
FOR XML AUTO, TYPE  
```  
  
 Im vorherigen Beispiel wird die `query()` Methode der `xml` Daten geben, um durch die innere FOR XML-Abfrage zurückgegebene XML-Abfragen und das erwartete Ergebnis zu konstruieren.  
  
 Dies ist das Ergebnis:  
  
```  
<Production.Product ProductID="520">  
  <Price PriceType="ListPrice">133.3400</Price>  
  <Price PriceType="StandardCost">98.7700</Price>  
</Production.Product>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden von geschachtelten FOR XML-Abfragen](use-nested-for-xml-queries.md)  
  
  