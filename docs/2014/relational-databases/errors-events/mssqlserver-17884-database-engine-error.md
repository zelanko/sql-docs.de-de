---
title: MSSQLSERVER_17884 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17884 (Database Engine error)
ms.assetid: 8d05ba05-3f71-4dc3-bd81-2ea5ac9fe843
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bd5beca2a7dfd20afbf9eff196d89452ef3533d2
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84967775"
---
# <a name="mssqlserver_17884"></a>MSSQLSERVER_17884
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|17884|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SRV_SCHEDULER_DEADLOCK|  
|Meldungstext|Neue Abfragen, die dem Prozess im %d-Knoten zugewiesen sind, wurden in den letzten %d Sekunden von keinem Arbeitsthread abgerufen. Die Ursache hierfür können blockierende Abfragen oder Abfragen mit langer Ausführungszeit sein, wodurch die Clientantwortzeit beeinträchtigt wird. Erhöhen Sie mithilfe der Konfigurationsoption „Max. Anzahl von Arbeitsthreads“ die Anzahl zulässiger Threads, oder optimieren Sie aktuell ausgeführte Abfragen.  SQL-Prozessnutzung: %d%%. Leerlauf des Systems: %d%%.|  
  
## <a name="explanation"></a>Erklärung  
 In den Zeitplanungsmodulen gibt es kein Anzeichen von Fortschritt. Die Ursache können Deadlocks sein, bei denen keine Threads fortgeführt werden können und/oder keine neue Arbeit aufgenommen und verarbeitet werden kann. Wenn die Prozessnutzung niedrig ist, können andere Prozesse auf dem Computer möglicherweise dazu führen, dass auf die Serverprozess-CPU nicht mehr zugegriffen werden kann.  
  
## <a name="user-action"></a>Benutzeraktion  
 Bestimmen Sie die Ursache für die Blockierung und den fehlenden Fortschritt, und lösen Sie die Situation entsprechend. Wenn die Prozessnutzung niedrig ist, prüfen Sie die Systemlast, die von anderen Prozessen verursacht wird.  
  
  
