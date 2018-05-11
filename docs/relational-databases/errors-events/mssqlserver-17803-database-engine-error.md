---
title: MSSQLSERVER_17803 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 17803 (Database Engine error)
ms.assetid: 28591a19-258d-4891-b78a-4686789bb2d7
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a96b9970406ee7da627ac955e1fe280a12b7f90e
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver17803"></a>MSSQLSERVER_17803
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|17803|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SRV_NOMEMORY|  
|Meldungstext|Bei der Verbindungsherstellung ist ein Fehler bei der Speicherbelegung aufgetreten. Reduzieren Sie die vermeidbare Arbeitsspeicherlast, oder vergrößern Sie den Systemarbeitsspeicher. Die Verbindung wurde geschlossen.%.*ls|  
  
## <a name="explanation"></a>Erklärung  
Der Server verfügt nicht über genügend Arbeitsspeicher.  
  
## <a name="user-action"></a>Benutzeraktion  
Bestimmen Sie, warum der Server nicht über genügend Arbeitsspeicher verfügt. Allgemeine Schritte zur Behandlung von Problemen mit dem Arbeitsspeicher sind möglicherweise nützlich.  
  
