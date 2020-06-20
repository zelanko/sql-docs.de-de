---
title: 'Beispiel: Angeben der ELEMENT-Direktive und Entitätscodierung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- ELEMENT directive
- entity encoding [XML]
ms.assetid: 50cda5c1-7293-4080-93b3-872e3b8d484e
author: rothja
ms.author: jroth
ms.openlocfilehash: cadbc9e06530706f0b1e1406af7b38b72246303f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85067833"
---
# <a name="example-specifying-the-element-directive-and-entity-encoding"></a>Beispiel: Angeben der ELEMENT-Direktive und Entitätscodierung
  Dieses Beispiel veranschaulicht den Unterschied zwischen der **ELEMENT** - und der **XML** -Direktive. Bei der **ELEMENT** -Direktive werden die Daten in Entitäten geändert, während dies bei der **XML** -Direktive nicht der Fall ist. Dem- \<Summary> Element wird `<Summary>This is summary description</Summary>` in der Abfrage XML zugewiesen.  
  
 Angenommen, die folgende Abfrage wird ausgeführt:  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID  as [ProductModel!1!ProdModelID],  
        Name            as [ProductModel!1!Name],  
        NULL            as [Summary!2!SummaryDescription!ELEMENT]  
FROM    Production.ProductModel  
WHERE   ProductModelID=19  
UNION ALL  
SELECT  2 as Tag,  
        1 as Parent,  
        ProductModelID,  
        NULL,  
       '<Summary>This is summary description</Summary>'  
FROM   Production.ProductModel  
WHERE  ProductModelID=19  
FOR XML EXPLICIT  
```  
  
 Dies ist das Ergebnis. Die Zusammenfassungsbeschreibung wird im Ergebnis in eine Entität geändert.  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription><Summary>This is summary description</Summary></SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
 Wenn Sie nun im Spaltennamen die **XML** -Direktive angeben, also `Summary!2!SummaryDescription!XML`statt der **ELEMENT** -Direktive, erhalten Sie eine zusammenfassende Beschreibung, ohne dass die Daten in Entitäten geändert werden.  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
  <Summary>  
    <SummaryDescription>  
      <Summary>This is summary description</Summary>  
    </SummaryDescription>  
  </Summary>  
</ProductModel>  
```  
  
 Die folgende Abfrage weist keinen statischen XML-Wert zu, sondern verwendet die **query()** -Methode vom **XML** -Typ, um die Produktmodell-Zusammenfassungsbeschreibung aus der CatalogDescription-Spalte vom **XML** -Typ abzurufen. Da bekannt ist, dass das Ergebnis vom Typ **xml** ist, werden die Daten nicht in Entitäten geändert.  
  
```  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID  as [ProductModel!1!ProdModelID],  
        Name            as [ProductModel!1!Name],  
        NULL            as [Summary!2!SummaryDescription]  
FROM    Production.ProductModel  
WHERE   CatalogDescription is not null  
UNION ALL  
SELECT  2 as Tag,  
        1 as Parent,  
        ProductModelID,  
        Name,  
       (SELECT CatalogDescription.query('  
            declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
          /pd:ProductDescription/pd:Summary'))  
FROM     Production.ProductModel  
WHERE    CatalogDescription is not null  
ORDER BY [ProductModel!1!ProdModelID],Tag  
FOR XML EXPLICIT  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden des EXPLICIT-Modus mit FOR XML](use-explicit-mode-with-for-xml.md)  
  
  
