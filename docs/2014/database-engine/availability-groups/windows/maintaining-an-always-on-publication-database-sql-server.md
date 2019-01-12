---
title: Warten einer Always On-Veröffentlichungsdatenbank (SQLServer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], interoperability
- replication [SQL Server], AlwaysOn Availability Groups
ms.assetid: 55b345fe-2eb9-4b04-a900-63d858eec360
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a862c5c9cea1087f54a4dbff13b6c39eb5e39385
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54126981"
---
# <a name="maintaining-an-alwayson-publication-database-sql-server"></a>Warten einer AlwaysOn-Veröffentlichungsdatenbank (SQL Server)
  In diesem Thema werden besondere Überlegungen zum Verwalten einer Veröffentlichungsdatenbank bei Verwendung von AlwaysOn-Verfügbarkeitsgruppen erläutert.  
  
 
  
##  <a name="MaintainPublDb"></a> Verwalten einer veröffentlichten Datenbank in einer Verfügbarkeitsgruppe  
 Die Wartung einer AlwaysOn-Veröffentlichungsdatenbank entspricht im Wesentlichen der Wartung einer standardmäßigen Veröffentlichungsdatenbank, wobei jedoch die folgenden Überlegungen zu berücksichtigen sind:  
  
-   Die Verwaltung muss beim primären Replikathost erfolgen. In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]werden Veröffentlichungen unter dem Ordner **Lokale Veröffentlichungen** für den primären Replikathost und auch für lesbare sekundäre Replikate angezeigt. Nach einem Failover müssen Sie unter Umständen [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] manuell aktualisieren, um die Änderung widerzuspiegeln, wenn das sekundäre Replikat, das zum primären Replikat höher gestuft wurde, nicht lesbar war.  
  
-   Der Replikationsmonitor zeigt immer Veröffentlichungsinformationen unter dem ursprünglichen Verleger an. Diese Informationen können jedoch von einem beliebigen Replikat aus im Replikationsmonitor angezeigt werden, indem der ursprüngliche Verleger als Server hinzugefügt wird.  
  
-   Bei Verwendung von gespeicherten Prozeduren oder Replikationsverwaltungsobjekten (RMO, Replication Management Objects) zum Verwalten der Replikation im primären Replikat müssen Sie in Fällen, in denen Sie den Verlegernamen angeben, den Namen der Instanz angeben, auf der die Datenbank für die Replikation aktiviert wurde. Den entsprechenden Namen ermitteln Sie mithilfe der `PUBLISHINGSERVERNAME`-Funktion. Wenn eine Veröffentlichungsdatenbank einer Verfügbarkeitsgruppe beitritt, sind die in den sekundären Datenbankreplikaten gespeicherten Replikationsmetadaten mit denen im primären Replikat identisch. Demzufolge entspricht für Veröffentlichungsdatenbanken, die in der primären Replikatdatenbank zur Replikation aktiviert wurden, der in den Systemtabellen des sekundären Replikats gespeicherte Verlegerinstanzname dem Namen der primären Replikatdatenbank und nicht dem Namen der sekundären Replikatdatenbank. Dies wirkt sich auf die Replikationskonfiguration und -wartung aus, wenn ein Failover der Veröffentlichungsdatenbank zur sekundären Replikatdatenbank erfolgt. Z. B. Wenn Sie Replikation mit gespeicherten Prozeduren bei einem sekundären Replikat nach einem Failover konfigurieren und Sie möchten ein Pullabonnement für eine Veröffentlichungsdatenbank, die bei einem anderen Replikat aktiviert wurde, geben Sie den Namen des ursprünglichen Verlegers statt der aktuellen Verlegers als die *@publisher* Parameter `sp_addpullsubscription` oder `sp_addmergepulllsubscription`. Wenn Sie jedoch eine Veröffentlichungsdatenbank nach einem Failover aktivieren, entspricht der in den Systemtabellen gespeicherte Verlegerinstanzname dem Namen des aktuellen primären Hosts. In diesem Fall würden Sie den Hostnamen des aktuellen primären Replikats für den *@publisher* -Parameter verwenden.  
  
    > [!NOTE]  
    >  Bei einigen Prozeduren wie z. B. `sp_addpublication`, wird die *@publisher* Parameter wird nur für Verleger, die keine Instanzen von sind unterstützt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]; in diesen Fällen ist es nicht relevant für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] AlwaysOn.  
  
-   Synchronisieren Sie die Pullabonnements vom Abonnenten und die Pushabonnements vom aktiven Verleger aus, um ein Abonnement in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] nach einem Failover zu synchronisieren.  
  
##  <a name="RemovePublDb"></a> Entfernen einer veröffentlichten Datenbank aus einer Verfügbarkeitsgruppe  
 Berücksichtigen Sie die folgenden Probleme, wenn eine veröffentlichte Datenbank aus einer Verfügbarkeitsgruppe entfernt wird, oder wenn eine Verfügbarkeitsgruppe, die eine veröffentlichte Elementdatenbank aufweist, gelöscht wird.  
  
-   Wenn die Veröffentlichungsdatenbank beim ursprünglichen Verleger aus einem primären Replikat der verfügbarkeitsgruppe entfernt wird, müssen Sie ausführen `sp_redirect_publisher` ohne Angabe eines Werts für die *@redirected_publisher* Parameter zum Entfernen der Umleitung für das Verleger-/Datenbankpaar.  
  
    ```  
    EXEC sys.sp_redirect_publisher   
        @original_publisher = 'MyPublisher',  
        @published_database = 'MyPublishedDB';  
    ```  
  
     Die Datenbank wird auf dem primären Replikat im Wiederherstellungsstatus belassen und muss wiederhergestellt werden. Sobald Sie dies tun, sollte die Replikation unverändert mit dem ursprünglichen Verleger funktionieren.  
  
-   Wenn für die Veröffentlichungsdatenbank ein Failover vom ursprünglichen Verleger zu einem Replikat ausgeführt und die Datenbank aus dem primären Replikat der Verfügbarkeitsgruppe entfernt wird, führen Sie die gespeicherte Prozedur `sp_redirect_publisher` aus, um den ursprünglichen Verleger zum neuen Verleger umzuleiten. Die Datenbank wird im Wiederherstellungsstatus belassen und muss wiederhergestellt werden. Sobald Sie dies tun, sollte die Replikation weiterhin so funktionieren wie zuvor in der Verfügbarkeitsgruppe.  
  
    ```  
    EXEC sys.sp_redirect_publisher   
        @original_publisher = 'MyPublisher',  
        @published_database = 'MyPublishedDB',  
        @redirected_publisher = 'MyNewPublisher';  
    ```  
  
     Entfernen Sie den Remoteserver für den ursprünglichen Verleger selbst dann nicht aus dem Verteiler, wenn nicht mehr auf den Server zugegriffen werden kann. Die Servermetadaten für den ursprünglichen Verleger werden beim Verteiler benötigt, um Abfragen von Veröffentlichungsmetadaten beantworten zu können  
  
-   Wenn eine vollständige Verfügbarkeitsgruppe entfernt wird, wirkt sich dies auf eine replizierte Mitgliedsdatenbank auf die gleiche Weise aus, wie das Entfernen einer veröffentlichten Datenbank aus einer Verfügbarkeitsgruppe. Die Replikation kann vom letzten primären Replikat fortgesetzt werden, sobald die Datenbank wiederhergestellt und die Umleitung geändert wurde. Wenn die Datenbank auf ihrem ursprünglichen Verleger wiederhergestellt wird, sollte die Umleitung entfernt werden. Wenn die Datenbank bei einem anderen Host wiederhergestellt wird, sollte Umleitung explizit an den neuen Host umgeleitet werden.  
  
    > [!NOTE]  
    >  Wenn eine Verfügbarkeitsgruppe entfernt wird, die über veröffentlichte Mitgliedsdatenbanken verfügt, oder wenn eine veröffentlichte Datenbank aus einer Verfügbarkeitsgruppe entfernt wird, werden alle Kopien der veröffentlichten Datenbanken im Wiederherstellungsstatus belassen. Nach der Wiederherstellung wird jede Datenbank als veröffentlichte Datenbank angezeigt. Nur eine Kopie sollte mit Veröffentlichungsmetadaten beibehalten werden. Um die Replikation für eine veröffentlichte Datenbankkopie zu deaktivieren, entfernen Sie zuerst alle Abonnements und Veröffentlichungen aus der Datenbank.  
  
     Führen Sie `sp_dropsubscription` aus, um die Veröffentlichungsabonnements zu entfernen. Vergessen Sie nicht, den Parameter *@ignore_distributributor* auf 1 festzulegen, um die Metadaten beim Verteiler für die aktive Veröffentlichungsdatenbank beizubehalten.  
  
    ```  
    USE MyDBName;  
    GO  
  
    EXEC sys.sp_dropsubscription   
        @subscriber = 'MySubscriber',  
        @publication = 'MyPublication',  
        @article = 'all',  
        @ignore_distributor = 1;  
    ```  
  
     Führen Sie `sp_droppublication` aus, um alle Veröffentlichungen zu entfernen. Auch hier dürfen Sie nicht vergessen, den Parameter *@ignore_distributor* auf 1 festzulegen, um die Metadaten beim Verteiler für die aktive Veröffentlichungsdatenbank beizubehalten.  
  
    ```  
    EXEC sys.sp_droppublication   
        @publication = 'MyPublication',  
        @ignore_distributor = 1;  
    ```  
  
     Führen Sie `sp_replicationdboption` aus, um die Replikation für die Datenbank zu deaktivieren.  
  
    ```  
    EXEC sys.sp_replicationdboption  
        @dbname = 'MyDBName',  
        @optname = 'publish',  
        @value = 'false';  
    ```  
  
     An diesem Punkt kann die Kopie der veröffentlichten Datenbank beibehalten oder gelöscht werden.  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Konfigurieren der Replikation für AlwaysOn-Verfügbarkeitsgruppen (SQLServer)](always-on-availability-groups-sql-server.md)  
  
-   [Replikation, Änderungsnachverfolgung, Change Data Capture und AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](replicate-track-change-data-capture-always-on-availability.md)  
  
-   [Replikationsverwaltung – häufig gestellte Fragen](../../../relational-databases/replication/administration/frequently-asked-questions-for-replication-administrators.md)  
  
-   [Replikationsabonnenten und AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](replication-subscribers-and-always-on-availability-groups-sql-server.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](prereqs-restrictions-recommendations-always-on-availability.md)   
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQLServer&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [AlwaysOn-Verfügbarkeitsgruppen: Interoperabilität (SQLServer)](always-on-availability-groups-interoperability-sql-server.md)   
 [SQL Server-Replikation](../../../relational-databases/replication/sql-server-replication.md)  
  
  
