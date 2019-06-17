---
title: Problembehandlung bei einem fehlerhaften Dateihinzufügungsvorgängen-Vorgang (AlwaysOn-Verfügbarkeitsgruppen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- secondary databases [SQL Server], Availability Groups
- Availability Groups [SQL Server], troubleshooting
ms.assetid: 31ceaebf-864b-4dd0-9112-0d047b0316ad
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6940e9e40a09e5bd0c7afc591b34c17129350d74
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62813440"
---
# <a name="troubleshoot-a-failed-add-file-operation-alwayson-availability-groups"></a>Problembehandlung bei einem fehlgeschlagenen Vorgang zum Hinzufügen einer Datei (AlwaysOn-Verfügbarkeitsgruppen)
  In einigen Bereitstellungen von AlwaysOn-Verfügbarkeitsgruppen unterscheiden sich Dateipfade zwischen dem System, das das primäre Replikat hostet, und Systemen, die ein sekundäres Replikat hosten. Wenn der Dateipfad eines Vorgangs zum Hinzufügen einer Datei auf einem sekundären Replikat nicht vorhanden ist, dann ist dieser Vorgang auf der primären Datenbank erfolgreich. Der Vorgang zum Hinzufügen einer Datei bewirkt jedoch, dass die sekundäre Datenbank angehalten wird. Dies bewirkt dann, dass das sekundäre Replikat den Status NOT SYNCHRONIZING erhält.  
  
> [!NOTE]  
>  Außerdem sollte der Dateipfad (einschließlich des Laufwerkbuchstabens) einer sekundären Datenbank nach Möglichkeit mit dem Pfad der entsprechenden primären Datenbank übereinstimmen.  
  
## <a name="problem-resolution"></a>Mögliche Lösung  
 Um dieses Problem zu beheben, muss der Datenbankbesitzer die folgenden Schritte ausführen:  
  
1.  Entfernen Sie die sekundäre Datenbank aus der Verfügbarkeitsgruppe. Weitere Informationen finden Sie unter [Entfernen einer sekundären Datenbank aus einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md).  
  
2.  Stellen Sie in der vorhandenen sekundären Datenbank eine vollständige Sicherung der Dateigruppe wieder her, die die zur sekundären Datenbank hinzugefügte Datei enthält. Verwenden Sie hierzu WITH NORECOVERY und WITH MOVE (geben Sie den Dateipfad auf der Serverinstanz an, die das sekundäre Replikat hostet). Weitere Informationen finden Sie unter [Wiederherstellen einer Datenbank an einem neuen Speicherort &#40;SQL Server&#41;](../../../relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md).  
  
3.  Sichern Sie das Transaktionsprotokoll, das den Vorgang zum Hinzufügen der Datei auf der primären Datenbank enthält, und stellen Sie die Protokollsicherung auf der sekundären Datenbank manuell mit WITH NORECOVERY und WITH MOVE wieder her.  
  
4.  Bereiten Sie die sekundäre Datenbank auf das erneute Hinzufügen zur Verfügbarkeitsgruppe vor, indem Sie mit WITH NO RECOVERY alle sonstigen ausstehenden Protokollsicherungen von der primären Datenbank wiederherstellen.  
  
5.  Fügen Sie die sekundäre Datenbank wieder zur Verfügbarkeitsgruppe hinzu. Weitere Informationen finden Sie unter [Verknüpfen einer sekundären Datenbank mit einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Manuelles Vorbereiten einer sekundären Datenbank auf eine Verfügbarkeitsgruppe (SQL Server)](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)   
 [Problembehandlung bei verwaisten Benutzern &#40;SQL Server&#41;](../../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md)   
 [Problembehandlung bei AlwaysOn-Verfügbarkeitsgruppenkonfiguration &#40;SQL Server&#41;gelöscht](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
  
