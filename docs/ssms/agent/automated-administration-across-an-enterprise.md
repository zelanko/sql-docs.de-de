---
title: Automatisierte Verwaltung in einem Unternehmen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- enterprise automatic administration [SQL Server]
- multiserver administration [SQL Server]
- SQL Server Agent jobs, multiserver administration
- jobs [SQL Server Agent], multiserver administration
- master servers [SQL Server], about master servers
- target servers [SQL Server], about target servers
- master servers [SQL Server]
- multiple instances of SQL Server
- target servers [SQL Server]
ms.assetid: 44d8365b-42bd-4955-b5b2-74a8a9f4a75f
author: markingmyname
ms.author: maghan
manager: jroth
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: c186794989d89eff38975ca57908a5da1fcaa987
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2019
ms.locfileid: "67688901"
---
# <a name="automated-administration-across-an-enterprise"></a>Automatisierte Verwaltung in einem Unternehmen
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> In einer [verwalteten Azure SQL-Datenbank-Instanz](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) werden die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Weitere Informationen finden Sie unter [T-SQL-Unterschiede zwischen einer verwalteten Azure SQL-Datenbank-Instanz und SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Das Automatisieren der Verwaltung über mehrere Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hinweg wird *Multiserververwaltung*genannt. Verwenden Sie die Multiserveradministration für folgende Aufgaben:  
  
-   Verwalten von zwei oder mehr Servern.  
  
-   Erstellen von Zeitplänen für den Informationsfluss zwischen Unternehmensservern für Dataware Housing.  
  
Für die Multiserveradministration benötigen Sie mindestens einen Masterserver und mindestens einen Zielserver. Ein Masterserver verteilt Aufträge an die Zielserver und empfängt Ereignisse von ihnen. Auf dem Masterserver ist zudem die zentrale Kopie der Auftragsdefinitionen für Aufträge gespeichert, die auf Zielservern ausgeführt werden. Zielserver stellen in regelmäßigen Abständen Verbindungen mit dem Masterserver her, um den Zeitplan der Aufträge zu aktualisieren. Ist ein neuer Auftrag auf dem Masterserver vorhanden, lädt der Zielserver den Auftrag herunter. Nach dem Beenden des Auftrags stellt der Zielserver erneut eine Verbindung mit dem Masterserver her und berichtet den Status des Auftrags. Beachten Sie, dass Sie dieselbe Auftragsdefinition verwenden müssen, wenn Sie datenbankbezogene Aktivitäten ausführen.  
  
Die folgende Abbildung stellt die Beziehung zwischen Master- und Zielserver dar:  
  
![Multiserver-Verwaltungskonfiguration](../../ssms/agent/media/multisvr.gif "Multiserver administration configuration")  
  
Wenn Sie Abteilungsserver in einem großen Unternehmen verwalten, können Sie Folgendes definieren:  
  
-   Einen Sicherungsauftrag mit Auftragsschritten.  
  
-   Operatoren, die bei einem Sicherungsfehler zu benachrichtigen sind.  
  
-   Einen Ausführungszeitplan für den Sicherungsauftrag.  
  
Richten Sie diesen Sicherungsauftrag einmal auf dem Masterserver ein, und tragen Sie anschließend alle Abteilungsserver als Zielserver ein. Ab dem Zeitpunkt der Eintragung können alle Abteilungsserver denselben Sicherungsauftrag ausführen, obwohl Sie ihn nur ein einziges Mal definiert haben.  
  
> [!NOTE]  
> Die Funktionen der Multiserveradministration sind für Mitglieder der sysadmin-Serverrolle bestimmt. Ein Mitglied der sysadmin-Rolle auf dem Zielserver kann jedoch die Vorgänge nicht bearbeiten, die auf dem Zielserver vom Masterserver ausgeführt werden. Durch diese Sicherheitsmaßnahme soll das versehentliche Löschen von Auftragsschritten und die Unterbrechung von Operationen auf dem Zielserver verhindert werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
[Erstellen einer Multiserverumgebung](../../ssms/agent/create-a-multiserver-environment.md)  
Enthält Informationen zum Erstellen und Verwalten von Master- und Zielservern.  
  
[Auswählen des richtigen SQL Server-Agent-Dienstkontos für Multiserverumgebungen](../../ssms/agent/choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md)  
Enthält Informationen dazu, wie sich die Verwendung von Windows-Konten ohne Administratorberechtigungen oder des Kontos LocalSystem für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst auf Multiserverumgebungen auswirken kann.  
  
[Festlegen von Verschlüsselungsoptionen auf Zielservern](../../ssms/agent/set-encryption-options-on-target-servers.md)  
Enthält Informationen zum Festlegen des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Registrierungsunterschlüssels MsxEncryptChannelOptions auf Zielservern.  
  
[Verwalten von Aufträgen über ein gesamtes Unternehmen](../../ssms/agent/manage-jobs-across-an-enterprise.md)  
Enthält Informationen zum Überprüfen des Auftragsstatus, Ändern der Zielserver für Aufträge, Synchronisieren von Zielserveruhren, Abrufen des aktuellen Auftragsstatus von Masterservern.  
  
[Problembehandlung von proxybasierten Multiserveraufträgen](../../ssms/agent/troubleshoot-multiserver-jobs-that-use-proxies.md)  
Enthält Informationen zur Problembehandlung von Multiserveraufträgen, die Proxys verwenden, bei denen ein Fehler auftritt.  
  
[Abfragen von Servern](../../ssms/agent/poll-servers.md)  
Enthält Informationen zum impliziten und expliziten Abfragen des Masterservers durch Zielserver zum Synchronisieren von Auftragsinformationen.  
  
[Verwalten von Ereignissen](../../ssms/agent/manage-events.md)  
Enthält Informationen zur Weiterleitung von Ereignissen von den Zielservern auf die Masterserver.  
  
[Optimieren der automatischen Verwaltung in einem Unternehmen](../../ssms/agent/tune-automated-administration-across-an-enterprise.md)  
Enthält Informationen dazu, wie die automatisierte Verwaltung in einer Multiserverumgebung die Selbstoptimierungsfunktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]nutzt.  
  
## <a name="see-also"></a>Weitere Informationen  
[Themen zur Abwärtskompatibilität zum Installieren der SQL Server-Datenbank-Engine](../../database-engine/sql-server-database-engine-backward-compatibility.md)  
[Registrieren von Servern](../register-servers/register-servers.md)  
[sp_add_targetservergroup](../../relational-databases/system-stored-procedures/sp-add-targetservergroup-transact-sql.md)  
[sp_delete_targetserver](../../relational-databases/system-stored-procedures/sp-delete-targetserver-transact-sql.md)  
[sp_delete_targetservergroup](../../relational-databases/system-stored-procedures/sp-delete-targetservergroup-transact-sql.md)  
[sp_help_downloadlist](../../relational-databases/system-stored-procedures/sp-help-downloadlist-transact-sql.md)  
[sp_help_jobserver](../../relational-databases/system-stored-procedures/sp-help-jobserver-transact-sql.md)  
[sp_help_targetservergroup](../../relational-databases/system-stored-procedures/sp-help-targetservergroup-transact-sql.md)  
[sp_resync_targetserver](../../relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql.md)  
[sp_update_targetservergroup](../../relational-databases/system-stored-procedures/sp-update-targetservergroup-transact-sql.md)  
[sysjobservers](../../relational-databases/system-tables/dbo-sysjobservers-transact-sql.md)  
[syslogins](../../relational-databases/system-compatibility-views/sys-syslogins-transact-sql.md)  
[systargetservers](../../relational-databases/system-tables/dbo-systargetservers-transact-sql.md)  
  
