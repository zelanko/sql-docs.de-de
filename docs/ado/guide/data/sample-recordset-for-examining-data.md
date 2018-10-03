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
manager: craigg
ms.openlocfilehash: bfae67a14fb312f1b396cfc60f69e8cbe8babdf7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47811438"
---
# <a name="sample-recordset-for-examining-data"></a>Beispiel-Recordset zum Untersuchen von Daten
Zunächst sehen wir uns die **Recordset** Objekt zurückgegeben, mit der folgenden SQL-Abfrage, für die Daten der Northwind-Beispiel Basis in Microsoft SQL Server ausgeführt.  
  
```  
SELECT ProductID,ProductName,UnitPrice   
FROM Products   
WHERE CategoryID = 7    
```  
  
 Die resultierenden **Recordset** Objekt enthält alle erzeugt in der Datenbank, die in der folgenden Tabelle gezeigt.  
  
|ProductID|ProductName|UnitPrice|  
|---------------|-----------------|---------------|  
|7|Onkel Bobs Trockenbirnen|30.0000|  
|14|Tofu|23.2500|  
|28|Rssle Sauerkraut|45.6000|  
|51|Manjimup getrocknet Äpfel|53.0000|  
|74|Longlife Tofu|10.0000|  
  
 Wenn Sie interessiert, diese Ergebnisse selbst sind, versuchen Sie es im folgende JScript-Beispiel:  
  
-   [JScript-Beispiel zum Zurückgeben eines Recordsets](../../../ado/guide/data/jscript-code-example-to-return-a-recordset.md)
