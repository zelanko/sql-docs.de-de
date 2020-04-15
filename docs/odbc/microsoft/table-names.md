---
title: Tabellennamen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 91a415cd456186f18ef358b9d504145f78152774
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303121"
---
# <a name="table-names"></a>Tabellennamen
Wenn der Treiber dBASE, Microsoft Excel, Paradox oder Text verwendet wird, können Tabellennamen, die in der FROM-Klausel von SELECT oder DELETE nach der INTO-Klausel in INSERT und nach UPDATE, CREATE TABLE und DROP TABLE vorkommen, einen gültigen Pfad, einen primären Namen und eine Dateinamenerweiterung enthalten.  
  
 Die Verwendung eines Tabellennamens an anderer Stelle in einer SQL-Anweisung unterstützt nicht die Verwendung von Pfaden oder Erweiterungen, akzeptiert jedoch nur den primären Namen (z. B. EMP FROM C:-ABC-EMP).  
  
 Korrelationsnamen (Aliase) können verwendet werden. Beispiel:  
  
```  
SELECT *    
FROM C:\ABC\EMP T1    
WHERE T1.COL1 = 'aaa'  
```
