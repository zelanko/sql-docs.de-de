---
title: MSSQLSERVER_41399 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 41399 (Database Engine error)
ms.assetid: 5e5acb07-16ca-4329-8210-cd2bab0c904f
caps.latest.revision: 6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 05467da9c9e8cacea86b12adfbadd9e7961db77f
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver41399"></a>MSSQLSERVER_41399
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Ereignis-ID|41399|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|MAX_SORT_ROW_WIDTH_EXCEEDED|  
|Meldungstext|Der Sortiervorgang ist zu komplex. Weitere Informationen finden Sie in der SQL Server-Onlinedokumentation.|  
  
## <a name="explanation"></a>Erklärung  
Durch das Sortieren der Ergebnisse eines Join -und Aggregationsvorgangs erhöht sich die Komplexität des Sortiervorgangs, da die Größe der Zeile im Sortierungspuffer zunimmt. Dieser Fehler bewirkt, dass die Größe der Zeile größer als die maximale Größe ist, die vom SORT-Operator in systemintern kompilierten gespeicherten Prozeduren unterstützt wird. Beachten Sie, dass die Größe einer Zeile im Sortierungspuffer ausschließlich von der Anzahl der Joins sowie der Anzahl und dem Typ der Aggregatfunktionen bestimmt wird. Die Größe der Zeilen in den Basistabellen wirkt sich nicht auf die Größe der Zeile im Puffer aus.  
  
## <a name="user-action"></a>Benutzeraktion  
Verringern Sie die Komplexität der Abfrage, indem Sie Joins oder Aggregatfunktionen entfernen.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
