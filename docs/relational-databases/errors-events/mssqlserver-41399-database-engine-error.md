---
title: MSSQLSERVER_41399 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41399 (Database Engine error)
ms.assetid: 5e5acb07-16ca-4329-8210-cd2bab0c904f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8f1dd8f616de43a0442e4110ba755cc66e397c43
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47832988"
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
  
