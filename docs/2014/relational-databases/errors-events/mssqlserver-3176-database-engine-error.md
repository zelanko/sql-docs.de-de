---
title: MSSQLSERVER_3176 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 3176 (Database Engine error)
ms.assetid: 4be24c64-2d52-4cb4-b4d7-36efbe4555b6
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f6ecd8482645db1cf8b070de8d82ed0012dae01f
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37417389"
---
# <a name="mssqlserver3176"></a>MSSQLSERVER_3176
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Ereignis-ID|3176|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|LDDB_FILE_CLAIM|  
|Meldungstext|Die Datei '%ls' wird von '%ls'(%d) und '%ls'(%d) beansprucht. Mithilfe der WITH MOVE-Klausel kann nach einer oder mehreren Dateien gesucht werden.|  
  
## <a name="explanation"></a>Erklärung  
 Es wird versucht, eine Datei für mehr als einen Zweck zu verwenden.  
  
### <a name="possible-causes"></a>Mögliche Ursachen  
 Der Dateiname wird bereits von einer anderen Datenbank verwendet.  
  
## <a name="user-action"></a>Benutzeraktion  
 Stellen Sie die Datenbankdateien an einem anderen Speicherort wieder her. Verwenden Sie in einer RESTORE-Anweisung eine WITH MOVE-Klausel, um die einzelnen Dateien zu verschieben. Ändern Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] auf der Seite Optionen die Dateispeicherorte im Raster **Datenbankdateien wiederherstellen als** des Dialogfelds **Datenbank wiederherstellen**.  
  
## <a name="see-also"></a>Siehe auch  
 [Wiederherstellen einer Datenbank an einem neuen Speicherort &#40;SQL Server&#41;](../backup-restore/restore-a-database-to-a-new-location-sql-server.md)   
 [Wiederherstellen von Dateien auf einem neuen Speicherort &#40;SQLServer&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
