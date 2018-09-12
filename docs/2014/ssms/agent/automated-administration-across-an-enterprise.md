---
title: Automatisierte Verwaltung in einem Unternehmen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 40
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c3b9d1885aefc738355f9f891680ebcfaf9d19a2
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/06/2018
ms.locfileid: "43813066"
---
# <a name="automated-administration-across-an-enterprise"></a>Automatisierte Verwaltung in einem Unternehmen
  Das Automatisieren der Verwaltung über mehrere Instanzen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hinweg wird *Multiserververwaltung* genannt. Verwenden Sie die Multiserveradministration für folgende Aufgaben:  
  
-   Verwalten von zwei oder mehr Servern.  
  
-   Erstellen von Zeitplänen für den Informationsfluss zwischen Unternehmensservern für Dataware Housing.  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] ist ständig bestrebt, die Gesamtbetriebskosten zu senken, und führt zu diesem Zweck in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] zwei neue Funktionen ein: eine Methode zur Serververwaltung, die als richtlinienbasierte Verwaltung bezeichnet wird, und Multiserverabfragen, die Konfigurationsserver und Servergruppen verwenden. Diese Funktionen können in Verbindung mit oder anstelle einiger der Funktionen verwendet werden, die in diesem Thema beschrieben werden. Weitere Informationen finden Sie unter [Verwalten von Servern mit der richtlinienbasierten Verwaltung](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md) und [Verwalten mehrerer Server mithilfe von zentralen Verwaltungsservern](../../relational-databases/administer-multiple-servers-using-central-management-servers.md).  
  
 Für die Multiserveradministration benötigen Sie mindestens einen Masterserver und mindestens einen Zielserver. Ein Masterserver verteilt Aufträge an die Zielserver und empfängt Ereignisse von ihnen. Auf dem Masterserver ist zudem die zentrale Kopie der Auftragsdefinitionen für Aufträge gespeichert, die auf Zielservern ausgeführt werden. Zielserver stellen in regelmäßigen Abständen Verbindungen mit dem Masterserver her, um den Zeitplan der Aufträge zu aktualisieren. Ist ein neuer Auftrag auf dem Masterserver vorhanden, lädt der Zielserver den Auftrag herunter. Nach dem Beenden des Auftrags stellt der Zielserver erneut eine Verbindung mit dem Masterserver her und berichtet den Status des Auftrags.  
  
 Die folgende Abbildung stellt die Beziehung zwischen Master- und Zielserver dar:  
  
 ![Multiserver-Verwaltungskonfiguration](../../database-engine/media/multisvr.gif "Multiserver administration configuration")  
  
 Wenn Sie Abteilungsserver in einem großen Unternehmen verwalten, können Sie Folgendes definieren:  
  
-   Einen Sicherungsauftrag mit Auftragsschritten.  
  
-   Operatoren, die bei einem Sicherungsfehler zu benachrichtigen sind.  
  
-   Einen Ausführungszeitplan für den Sicherungsauftrag.  
  
 Richten Sie diesen Sicherungsauftrag einmal auf dem Masterserver ein, und tragen Sie anschließend alle Abteilungsserver als Zielserver ein. Ab dem Zeitpunkt der Eintragung können alle Abteilungsserver denselben Sicherungsauftrag ausführen, obwohl Sie ihn nur ein einziges Mal definiert haben.  
  
> [!NOTE]  
>  Die Funktionen der Multiserveradministration sind für Mitglieder der sysadmin-Serverrolle bestimmt. Ein Mitglied der sysadmin-Rolle auf dem Zielserver kann jedoch die Vorgänge nicht bearbeiten, die auf dem Zielserver vom Masterserver ausgeführt werden. Durch diese Sicherheitsmaßnahme soll das versehentliche Löschen von Auftragsschritten und die Unterbrechung von Operationen auf dem Zielserver verhindert werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Erstellen einer Multiserverumgebung](create-a-multiserver-environment.md)  
 Enthält Informationen zum Erstellen und Verwalten von Master- und Zielservern.  
  
 [Auswählen des richtigen SQL Server-Agent-Dienstkontos für Multiserverumgebungen](choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md)  
 Enthält Informationen dazu, wie sich die Verwendung von Windows-Konten ohne Administratorberechtigungen oder des Kontos LocalSystem für den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agent-Dienst auf Multiserverumgebungen auswirken kann.  
  
 [Festlegen von Verschlüsselungsoptionen auf Zielservern](set-encryption-options-on-target-servers.md)  
 Enthält Informationen zum Festlegen des[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agent-Registrierungsunterschlüssels „MsxEncryptChannelOptions“ auf Zielservern.  
  
 [Verwalten von Aufträgen über ein gesamtes Unternehmen](manage-jobs-across-an-enterprise.md)  
 Enthält Informationen zum Überprüfen des Auftragsstatus, Ändern der Zielserver für Aufträge, Synchronisieren von Zielserveruhren, Abrufen des aktuellen Auftragsstatus von Masterservern.  
  
 [Problembehandlung von proxybasierten Multiserveraufträgen](troubleshoot-multiserver-jobs-that-use-proxies.md)  
 Enthält Informationen zur Problembehandlung von Multiserveraufträgen, die Proxys verwenden, bei denen ein Fehler auftritt.  
  
 [Abfragen von Servern](poll-servers.md)  
 Enthält Informationen zum impliziten und expliziten Abfragen des Masterservers durch Zielserver zum Synchronisieren von Auftragsinformationen.  
  
 [Verwalten von Ereignissen](manage-events.md)  
 Enthält Informationen zur Weiterleitung von Ereignissen von den Zielservern auf die Masterserver.  
  
 [Optimieren der automatischen Verwaltung in einem Unternehmen](tune-automated-administration-across-an-enterprise.md)  
 Enthält Informationen dazu, wie die automatisierte Verwaltung in einer Multiserverumgebung die Selbstoptimierungsfunktionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]nutzt.  
  
## <a name="see-also"></a>Siehe auch  
 [Abwärtskompatibilität der SQL Server-Datenbank-Engine](../../database-engine/sql-server-database-engine-backward-compatibility.md)   
 [Registrieren von Servern](../register-servers/register-servers.md)   
 [sp_add_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-targetservergroup-transact-sql)   
 [sp_delete_targetserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-targetserver-transact-sql)   
 [sp_delete_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-targetservergroup-transact-sql)   
 [sp_help_downloadlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-downloadlist-transact-sql)   
 [sp_help_jobserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobserver-transact-sql)   
 [sp_help_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-targetservergroup-transact-sql)   
 [sp_resync_targetserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-resync-targetserver-transact-sql)   
 [sp_update_targetservergroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-targetservergroup-transact-sql)   
 [dbo.sysjobservers &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-sysjobservers-transact-sql)   
 [Sys.syslogins &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-syslogins-transact-sql)   
 [dbo.systargetservers &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/dbo-systargetservers-transact-sql)  
  
  
