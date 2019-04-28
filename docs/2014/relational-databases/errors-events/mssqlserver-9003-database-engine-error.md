---
title: MSSQLSERVER_9003 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 9003 (Database Engine error)
ms.assetid: 7fdfb391-5c6f-428b-b434-6c3d0b30fd7b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c3d994f2166ae468a731203211eeb7a784118e65
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62912462"
---
# <a name="mssqlserver9003"></a>MSSQLSERVER_9003
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|9003|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|LOG_INVALID_LSN|  
|Meldungstext|Die Protokollscannummer %S_LSN, die an den Protokollscan in der '%.*ls'-Datenbank übergeben wurde, ist ungültig. Dieser Fehler kann darauf hinweisen, dass Daten beschädigt sind oder dass die Protokolldatei (LDF) nicht mit der Datendatei (MDF) übereinstimmt. Falls dieser Fehler während der Replikation aufgetreten ist, müssen Sie die Veröffentlichung neu erstellen. Andernfalls stellen Sie die Datenbank von einer Sicherung wieder her, falls das Problem zu einem Fehler beim Starten führt.|  
  
## <a name="explanation"></a>Erklärung  
Eine Komponente hat eine ungültige Protokollfolgenummer an den Protokoll-Manager für die Datenbank übergeben. Die Ursache kann eine Replikation, eine Beschädigung oder eine mangelnde Übereinstimmung zwischen der primären Datendatei und dem Protokoll sein.  
  
## <a name="user-action"></a>Benutzeraktion  
Falls dieser Fehler während der Replikation aufgetreten ist, erstellen Sie die Veröffentlichung neu. Stellen Sie sie andernfalls aus einer Sicherungskopie wieder her.  
  
