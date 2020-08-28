---
description: Beispiel-Recordset zum Untersuchen von Daten
title: Beispiel-Recordset zum Untersuchen von Daten | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- record location [ADO]
- current record [ADO]
ms.assetid: e770e626-68b1-4ddf-a217-d7b30311e2ee
author: rothja
ms.author: jroth
ms.openlocfilehash: ec44c25bba9c792415c462e3028bbf20d8d3f84e
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88979741"
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
