---
title: 'Aktive sekundäre Replikate: Sicherung auf sekundären Replikaten (Always On-Verfügbarkeitsgruppen) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- backup priority
- backup on secondary replicas
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], backup on secondary replicas
- active secondary replicas [SQL Server], backup on
- automated backup preference
- Availability Groups [SQL Server], active secondary replicas
ms.assetid: 82afe51b-71d1-4d5b-b20a-b57afc002405
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a94db154042f2cc6314459b6af4b52a43c2c9966
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62790679"
---
# <a name="active-secondaries-backup-on-secondary-replicas-always-on-availability-groups"></a>Aktive sekundäre Replikate: Sicherung auf sekundären Replikaten (Always On-Verfügbarkeitsgruppen)
  Die Funktionen für aktive sekundäre [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -Replikate umfassen auch die Unterstützung von Sicherungsvorgängen auf sekundären Replikaten. Sicherungsvorgänge können E/A und CPU (mit Sicherungskomprimierung) erheblich belasten. Durch die Auslagerung von Sicherungen auf ein sekundäres Replikat mit dem Status SYNCHRONIZED oder SYNCHRONIZING können Sie die Ressourcen auf der Serverinstanz verwenden, die das primäre Replikat für Arbeitsauslastungen erster Ebene hostet.  
  
> [!NOTE]  
>  RESTORE-Anweisungen sind in den primären und sekundären Datenbanken einer Verfügbarkeitsgruppe nicht zulässig.  
  
  
  
##  <a name="SupportedBuTypes"></a> Auf sekundären Replikaten unterstützte Sicherungstypen  
  
-   `BACKUP DATABASE` unterstützt vollständige Kopiesicherungen von Datenbanken, Dateien oder Dateigruppen nur bei der Ausführung auf sekundären Replikaten. Beachten Sie, dass sich Kopiesicherungen nicht auf die Protokollkette auswirken bzw. kein differenzielles Bitmuster löschen.  
  
-   Differenzielle Sicherungen werden auf sekundären Replikaten nicht unterstützt.  
  
-   **BACKUP LOG** unterstützt nur reguläre Protokollsicherungen (die COPY_ONLY-Option wird für Protokollsicherungen auf sekundären Replikaten nicht unterstützt).  
  
     Bei sämtlichen Protokollsicherungen von Replikaten (primär oder sekundär) wird ungeachtet ihres Verfügbarkeitsmodus (mit synchronem Commit oder mit asynchronem Commit) eine konsistente Protokollkette sichergestellt.  
  
-   Zum Sichern einer sekundären Datenbank muss ein sekundäres Replikat mit dem primären Replikat kommunizieren können und den Status `SYNCHRONIZED` oder `SYNCHRONIZING` aufweisen.  
  
##  <a name="WhereBuJobsRun"></a> Konfigurieren, wo Sicherungsaufträge ausgeführt werden  
 Das Ausführen von Sicherungen auf einem sekundären Replikat zum Auslagern der Sicherungsarbeitsauslastung vom primären Produktionsserver ist ein großer Vorteil. Durch die Ausführung von Sicherungen auf sekundären Replikaten wird es jedoch wesentlich komplexer, den Ausführungsort von Sicherungsaufträgen zu bestimmen. Um diesen Vorgang zu vereinfachen, konfigurieren Sie den Ausführungsort von Sicherungsaufträgen wie folgt:  
  
1.  Konfigurieren Sie die Verfügbarkeitsgruppe, um anzugeben, welche Verfügbarkeitsreplikate am Ort, an dem Sie Sicherungen wünschen, ausgeführt werden sollen. Weitere Informationen finden Sie unter den Parametern *AUTOMATED_BACKUP_PREFERENCE* und *BACKUP_PRIORITY* in [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql) oder [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql)aufweisen.  
  
2.  Erstellen Sie skriptbasierte Sicherungsaufträge für jede Verfügbarkeitsdatenbank auf jeder Serverinstanz, die ein Verfügbarkeitsreplikat hostet, das für das Ausführen von Sicherungen infrage kommt. Weitere Informationen finden Sie im Abschnitt „Nächster Schritt: Nach dem Konfigurieren einer Sicherung auf sekundären Replikaten“ unter [Konfigurieren der Sicherung auf Verfügbarkeitsreplikaten &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md).  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
 **So konfigurieren Sie die Sicherung auf sekundären Replikaten**  
  
-   [Konfigurieren der Sicherung auf Verfügbarkeitsreplikaten &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
 **So bestimmen Sie, ob es sich beim aktuellen Replikat um ein bevorzugtes Sicherungsreplikat handelt**  
  
-   [sys.fn_hadr_backup_is_preferred_replica](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)  
  
 **So erstellen Sie einen Sicherungsauftrag**  
  
-   [Verwenden des Wartungsplanungs-Assistenten](../../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
-   [Implementieren von Aufträgen](../../../ssms/agent/implement-jobs.md)  
  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Kopiesicherungen &#40;SQL Server&#41;](../../../relational-databases/backup-restore/copy-only-backups-sql-server.md)   
 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql)   
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql)  
  
  
