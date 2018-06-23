---
title: MSSQL_ENG014005 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG014005 error
ms.assetid: f168f0d6-cb11-45d4-9781-c374d7f388ee
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: fc1d7d9cdbdf9dd5c4f573c4893e35cad7f3ae98
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046204"
---
# <a name="mssqleng014005"></a>MSSQL_ENG014005
    
## <a name="message-details"></a>Meldungsdetails  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|14005|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Symbolischer Name||  
|Meldungstext|Die Veröffentlichung konnte nicht gelöscht werden. Es besteht ein Abonnement für sie.|  
  
## <a name="explanation"></a>Erklärung  
 Sie haben versucht, eine Veröffentlichung zu löschen, der ein oder mehrere Abonnements zugeordnet sind. Eine Veröffentlichung kann aber nur gelöscht werden, wenn ihr keine Abonnements zugeordnet sind.  
  
## <a name="user-action"></a>Benutzeraktion  
 Löschen Sie erst die Abonnements, bevor Sie die Veröffentlichung löschen. Wenn Sie zum Löschen der Veröffentlichung [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verwenden, haben Sie die Möglichkeit, vor dem Löschen der Veröffentlichung automatisch alle zugeordneten Abonnements löschen zu lassen. Wenn Sie zum Löschen der Veröffentlichung gespeicherte Prozeduren verwenden, müssen Sie die Abonnements zuerst explizit löschen. Weitere Informationen finden Sie unter [Delete a Push Subscription](delete-a-push-subscription.md) und [Delete a Pull Subscription](delete-a-pull-subscription.md).  
  
 Wenn für die Veröffentlichung keine Abonnements vorhanden zu sein scheinen oder wenn dieser Fehler beim Erstellen einer Veröffentlichung angezeigt wird, könnte noch ein vorheriges Abonnement vorhanden sein, das nicht vollständig leer war, bevor versucht wurde, es zu entfernen. Führen Sie [sp_removedbreplication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) in der Datenbank aus, um alle mit der Replikation zusammenhängenden Objekte und Einstellungen zu entfernen.  
  
## <a name="see-also"></a>Siehe auch  
 [Fehler- und Ereignisreferenz &#40;Replikation&#41;](errors-and-events-reference-replication.md)  
  
  
