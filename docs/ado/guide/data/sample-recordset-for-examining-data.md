---
title: Beispiel-Recordset zum Untersuchen von Daten | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- record location [ADO]
- current record [ADO]
ms.assetid: e770e626-68b1-4ddf-a217-d7b30311e2ee
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1882c5298d92e17a7ddaa165288fddfab7fdb02b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67924306"
---
# <a name="sample-recordset-for-examining-data"></a>Beispiel-Recordset zum Untersuchen von Daten
Betrachten wir zuerst das **Recordset** -Objekt, das mit der folgenden SQL-Abfrage zurückgegeben wird, die für die Northwind-Beispiel Datenbasis in Microsoft SQL Server ausgeführt wird.  
  
```  
SELECT ProductID,ProductName,UnitPrice   
FROM Products   
WHERE CategoryID = 7    
```  
  
 Das resultierende **Recordset** -Objekt enthält alle in der Datenbank in der folgenden Tabelle dargestellten.  
  
|ProductID|ProductName|UnitPrice|  
|---------------|-----------------|---------------|  
|7|Die organischen getrockneten Birnen von Onkel Bob|30,0000|  
|14|Dazugeben|23,2500|  
|28|Rssle-Sauerkraut|45,6000|  
|51|Von Manjimup getrocknete Äpfel|53,0000|  
|74|Longlife-Tofu|10,0000|  
  
 Wenn Sie diese Ergebnisse selbst erhalten möchten, versuchen Sie es mit dem folgenden JScript-Beispiel:  
  
-   [JScript-Beispiel für das Zurückgeben eines Recordsets](../../../ado/guide/data/jscript-code-example-to-return-a-recordset.md)
