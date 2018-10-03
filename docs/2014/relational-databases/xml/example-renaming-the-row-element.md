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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 92308ee94df30ad14b752b6cd55877dc784ab22b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48057110"
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
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden des RAW-Modus mit FOR XML](use-raw-mode-with-for-xml.md)  
  
  
