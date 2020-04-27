---
title: 'Beispiel: Umbenennen des &lt;row&gt;-Elements | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, renaming <row> example
ms.assetid: b042292a-0b6e-40a3-b254-71c06e626706
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 01b835696c5e64182cffb72aea80d53b3c3bb776
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62704901"
---
# <a name="example-renaming-the-ltrowgt-element"></a>Beispiel: Umbenennen des &lt;row&gt;-Elements
  Für jede Zeile im Resultset generiert der RAW-Modus ein `<row>`-Element. Sie können optional einen anderen Namen für dieses Element angeben, indem Sie ein optionales Argument für den RAW-Modus angeben, wie es in der folgenden Abfrage gezeigt wird. Die Abfrage gibt ein <`ProductModel`>-Element für jede Zeile im Rowset zurück.  
  
## <a name="example"></a>Beispiel  
  
```  
SELECT ProductModelID, Name   
FROM Production.ProductModel  
WHERE ProductModelID=122  
FOR XML RAW ('ProductModel'), ELEMENTS  
GO  
```  
  
 Dies ist das Ergebnis. Da der Abfrage die `ELEMENTS` -Direktive hinzugefügt wurde, ist das Ergebnis elementzentriert.  
  
```  
<ProductModel>  
  <ProductModelID>122</ProductModelID>  
  <Name>All-Purpose Bike Stand</Name>  
</ProductModel>   
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwenden des RAW-Modus mit FOR XML](use-raw-mode-with-for-xml.md)  
  
  
