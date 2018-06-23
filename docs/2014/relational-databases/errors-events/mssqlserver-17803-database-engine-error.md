---
title: MSSQLSERVER_17803 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 17803 (Database Engine error)
ms.assetid: 28591a19-258d-4891-b78a-4686789bb2d7
caps.latest.revision: 14
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: b7a2ab967786eaa05c8ac393bbeaf0e42164f0f6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148138"
---
# <a name="mssqlserver17803"></a>MSSQLSERVER_17803
    
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
  
  