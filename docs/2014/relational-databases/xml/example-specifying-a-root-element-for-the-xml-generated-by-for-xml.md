---
title: 'Beispiel: Angeben eines Stammelements für das durch FOR XML generierte XML | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, specifying root element example
- RAW mode, with FOR XML example
ms.assetid: bcc54b11-0713-4e43-8dbe-d6f3ad1993b5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e98a5918eaff3dcf1cadbff1795ae94a73a789f4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48172031"
---
# <a name="example-specifying-a-root-element-for-the-xml-generated-by-for-xml"></a>Beispiel: Angeben eines Stammelements für das durch FOR XML generierte XML
  Indem Sie die Option `ROOT` in der `FOR XML` -Abfrage angeben, können Sie ein einzelnes Element der obersten Ebene für die resultierenden XML-Daten anfordern, wie es in der folgenden Abfrage gezeigt wird. Das für die `ROOT` -Direktive angegebene Argument stellt den Namen des Stammelements bereit.  
  
## <a name="example"></a>Beispiel  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name   
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119 or ProductModelID=115  
FOR XML RAW, ROOT('MyRoot')  
go  
```  
  
 Dies ist das Ergebnis:  
  
```  
<MyRoot>  
  <row ProductModelID="122" Name="All-Purpose Bike Stand" />  
  <row ProductModelID="119" Name="Bike Wash" />  
  <row ProductModelID="115" Name="Cable Lock" />  
</MyRoot>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden des RAW-Modus mit FOR XML](use-raw-mode-with-for-xml.md)  
  
  
