---
title: MSSQLSERVER_3176 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3176 (Database Engine error)
ms.assetid: 4be24c64-2d52-4cb4-b4d7-36efbe4555b6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c5939250c530393a80246b50c46e418775547fa1
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85723686"
---
# <a name="mssqlserver_3176"></a>MSSQLSERVER_3176
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
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
  
## <a name="see-also"></a>Weitere Informationen  
[Wiederherstellen einer Datenbank an einem neuen Speicherort &#40;SQL Server&#41;](~/relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)  
[Wiederherstellen von Dateien an einem neuen Speicherort &#40;SQL Server&#41;](~/relational-databases/backup-restore/restore-files-to-a-new-location-sql-server.md)  
[RESTORE &#40;Transact-SQL&#41;](~/t-sql/statements/restore-statements-transact-sql.md)  
  
