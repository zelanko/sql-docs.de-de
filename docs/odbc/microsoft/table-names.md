---
title: Tabellennamen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL grammar [ODBC], table names
- table names [ODBC]
ms.assetid: f7a5cb0a-3be7-4f46-82f9-64ffdbceaa9b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5dd8de055521f4a1831d20a9a34bedb9309d1de6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67939786"
---
# <a name="table-names"></a>Tabellennamen
Wenn Dateinamenerweiterung dBASE, Microsoft Excel, Paradox, oder Text Treiber verwendet wird, Tabellennamen, die in der FROM-Klausel von SELECT oder DELETE, nachdem die INTO-Klausel in INSERT- und UPDATE auftreten CREATE TABLE und DROP TABLE einen gültigen Pfad enthalten kann, Primärschlüssel, und Datei .  
  
 Verwenden eines Tabellennamens ein an anderer Stelle in einer SQL-Anweisung unterstützt nicht die Verwendung von Pfaden oder Erweiterungen jedoch akzeptiert nur den primären Namen (z. B. von EMP aus C:\ABC\EMP).  
  
 Abhängige Namen (Aliase) können verwendet werden. Zum Beispiel:  
  
```  
SELECT *    
FROM C:\ABC\EMP T1    
WHERE T1.COL1 = 'aaa'  
```
