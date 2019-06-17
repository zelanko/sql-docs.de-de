---
title: Teilsicherungen (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- full backups [SQL Server]
- partial backups [SQL Server]
- READ_WRITE_FILEGROUPS option
- database backups [SQL Server], about backing up databases
ms.assetid: fe6b6bb1-38d0-46c4-bab8-31df14e8999c
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4213bcee1d17d27bf63da9eb286b21dea4cc5a02
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62921929"
---
# <a name="partial-backups-sql-server"></a>Teilsicherungen (SQL Server)
  Alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Wiederherstellungsmodelle unterstützen Teilsicherungen, deshalb ist dieses Thema für alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbanken relevant. Teilsicherungen wurden jedoch für die Verwendung mit dem einfachen Sicherungsmodell konzipiert, und zwar mit der Absicht, die Flexibilität bei der Sicherung sehr großer Datenbanken mit einer oder mehreren schreibgeschützten Dateigruppen zu verbessern.  
  
 Teilsicherungen erweisen sich besonders dann als nützlich, wenn Sie bestimmte schreibgeschützte Dateigruppen aus der Sicherung ausschließen möchten. Eine *Teilsicherung* ähnelt einer vollständigen Datenbanksicherung. Sie enthält jedoch nicht alle Dateigruppen. Stattdessen enthält eine Teilsicherung für eine Datenbank mit Lese-/Schreibzugriff alle Daten in der primären Dateigruppe, alle Lese-/Schreibdateigruppen sowie alle optional angegebenen schreibgeschützten Dateien. Eine Teilsicherung einer schreibgeschützten Datenbank enthält nur die primäre Dateigruppe.  
  
> [!NOTE]  
>  Wenn eine schreibgeschützte Datenbank nach einer Teilsicherung in eine Datenbank mit Lese-/Schreibzugriff geändert wird, können sekundäre Dateigruppen mit Lese-/Schreibzugriff vorhanden sein, die nicht in der Teilsicherung enthalten sind. Wenn Sie in diesem Fall versuchen, eine differenzielle Teilsicherung zu erstellen, tritt bei der Sicherung ein Fehler auf. Bevor Sie eine differenzielle Teilsicherung der Datenbank erstellen können, müssen Sie eine weitere Teilsicherung erstellen. Die neue Teilsicherung enthält alle sekundären Dateigruppen mit Lese-/Schreibzugriff und kann als Basis für differenzielle Teilsicherungen dienen.  
  
 Dateisicherungen von schreibgeschützten Dateigruppen können mit Teilsicherungen kombiniert werden. Informationen zu Dateisicherungen finden Sie unter [Vollständige Dateisicherungen &#40;SQL Server&#41;](full-file-backups-sql-server.md).  
  
 Eine Teilsicherung kann als *differenzielle Basis* für differenzielle Teilsicherungen verwendet werden. Weitere Informationen finden Sie unter [Differenzielle Sicherungen &#40;SQL Server&#41;](differential-backups-sql-server.md).  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
> [!NOTE]  
>  Teilsicherungen werden nicht von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder vom Wartungsplanungs-Assistenten unterstützt.  
  
 **So erstellen Sie eine Teilsicherung**  
  
-   [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) (READ_WRITE_FILEGROUPS; FILEGROUP-Option nach Bedarf)  
  
 **So verwenden Sie eine Teilsicherung in einer Wiederherstellungssequenz**  
  
-   [Beispiel: Schrittweise Wiederherstellung einer Datenbank &#40;Einfaches Wiederherstellungsmodell&#41;](example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [Beispiel: Schrittweise Wiederherstellung nur bestimmter Dateigruppen &#40;einfaches Wiederherstellungsmodell&#41;](example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über Sicherungen &#40;SQL Server&#41;](backup-overview-sql-server.md)   
 [Dateiwiederherstellungen &#40;einfaches Wiederherstellungsmodell&#41;](file-restores-simple-recovery-model.md)   
 [Schrittweise Wiederherstellungen &#40;SQL Server&#41;](piecemeal-restores-sql-server.md)  
  
  
