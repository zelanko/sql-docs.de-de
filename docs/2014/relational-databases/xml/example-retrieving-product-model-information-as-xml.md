---
title: 'Beispiel: Abrufen von Produktmodellinformationen als XML | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, retrieving XML information example
ms.assetid: 3828b4ca-3ab2-444f-9c58-8be6e7f064a6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4ec7ed358ab8c6c5f42e378a23dd4ba911800ae3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48219880"
---
# <a name="example-retrieving-product-model-information-as-xml"></a>Beispiel: Abrufen von Produktmodellinformationen als XML
  Die folgende Abfrage gibt Produktmodellinformationen zurück. `RAW` -Modus wird in der `FOR XML` -Klausel angegeben.  
  
## <a name="example"></a>Beispiel  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW;  
GO  
```  
  
 Dies ist das Teilergebnis:  
  
 `<row ProductModelID="122" Name="All-Purpose Bike Stand" />`  
  
 `<row ProductModelID="119" Name="Bike Wash" />`  
  
 Sie können elementzentrierte XML-Daten abrufen, indem Sie die `ELEMENTS` -Direktive angeben.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW, ELEMENTS;  
GO  
```  
  
 Dies ist das Ergebnis:  
  
```  
<row>  
  <ProductModelID>122</ProductModelID>  
  <Name>All-Purpose Bike Stand</Name>  
</row>  
<row>  
  <ProductModelID>119</ProductModelID>  
  <Name>Bike Wash</Name>  
</row>  
```  
  
 Sie können optional angeben, die `TYPE` Richtlinie zum Abrufen der Ergebnisse als `xml` Typ. Die `TYPE` -Direktive ändert nicht den Inhalt der Ergebnisse. Nur der Datentyp der Ergebnisse wird geändert.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW, TYPE ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden des RAW-Modus mit FOR XML](use-raw-mode-with-for-xml.md)  
  
  
