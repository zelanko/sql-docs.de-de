---
title: Verwenden des Dialogfelds „Neue Verfügbarkeitsgruppe“ (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], creating
ms.assetid: 1b0a6421-fbd4-4bb4-87ca-657f4782c433
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ee729f9f2bdd0044f2897a06e93f00b7b37ca785
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "72783140"
---
# <a name="use-the-new-availability-group-dialog-box-sql-server-management-studio"></a>Verwenden des Dialogfelds Neue Verfügbarkeitsgruppe (SQL Server Management Studio)
  Dieses Thema enthält Informationen zum Verwenden des Dialogfelds **Neue Verfügbarkeitsgruppe** von [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] , um auf Instanzen von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] , die für [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]aktiviert sind, eine AlwaysOn-Verfügbarkeitsgruppe zu erstellen. Eine *Verfügbarkeitsgruppe* definiert einen Satz von Benutzerdatenbanken, für die als eine einzelne Einheit ein Failover ausgeführt wird, sowie einen Satz von Failoverpartnern, die als *Verfügbarkeitsreplikate*bezeichnet werden, die Failover unterstützen.  
  
> [!NOTE]  
>  Eine Einführung zu Verfügbarkeitsgruppen finden Sie unter [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).  
  

> [!NOTE]  
>  Informationen zu alternativen Möglichkeiten zum Erstellen einer Verfügbarkeitsgruppe finden Sie in [Verwandte Aufgaben](#RelatedTasks)später in diesem Thema.  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
 Es wird dringend empfohlen, dass Sie diesen Abschnitt lesen, bevor Sie versuchen, Ihre erste Verfügbarkeitsgruppe zu erstellen.  
  
###  <a name="PrerequisitesRestrictions"></a> Voraussetzungen  
  
-   Überprüfen Sie vor dem Erstellen einer Verfügbarkeitsgruppe, ob sich die Instanzen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , die Verfügbarkeitsreplikate hosten, auf verschiedenen WSFC-Konten (Windows Server Failover Clustering) des gleichen WSFC-Failoverclusters befinden. Stellen Sie außerdem sicher, dass alle Serverinstanzen für [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] aktiviert sind und alle anderen [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] -Voraussetzungen erfüllen. Wenn Sie weitere Informationen wünschen, sollten Sie unbedingt [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) lesen.  
  
-   Vor dem Erstellen einer Verfügbarkeitsgruppe muss gewährleistet sein, dass jede Serverinstanz, die ein Verfügbarkeitsreplikat hostet, einen voll funktionsfähigen Datenbankspiegelungs-Endpunkt besitzt. Weitere Informationen finden Sie unter [Der Datenbankspiegelungs-Endpunkt &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md).  
  
-   Zur Verwendung des Dialogfelds **Neue Verfügbarkeitsgruppe** müssen Sie die Namen der Serverinstanzen kennen, die Verfügbarkeitsreplikate hosten. Zudem müssen Sie die Namen sämtlicher Datenbanken kennen, die Sie der neuen Verfügbarkeitsgruppe hinzufügen möchten, und gewährleisten, dass diese Datenbanken die Voraussetzungen und Einschränkungen der Verfügbarkeitsdatenbank erfüllen, die unter [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) beschrieben sind. Wenn Sie ungültige Werte eingeben, funktioniert die neue Verfügbarkeitsgruppe nicht.  
  
###  <a name="Limitations"></a>Einschränken  
 Das Dialogfeld **Neue Verfügbarkeitsgruppe** führt folgende Aktionen nicht durch:  
  
-   Verfügbarkeitsgruppenlistener erstellen  
  
-   Verknüpfen sekundärer Replikate mit der Verfügbarkeitsgruppe  
  
-   Ausführen einer anfänglichen Datensynchronisierung  
  
 Informationen zu diesen Konfigurationstasks finden Sie unter [Nachverfolgung: Nach dem Erstellen einer Verfügbarkeitsgruppe](#FollowUp)später in diesem Thema.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Erfordert die Mitgliedschaft in der festen **sysadmin** -Serverrolle und die CREATE AVAILABILITY GROUP-Serverberechtigung, ALTER ANY AVAILABILITY GROUP-Berechtigung oder CONTROL SERVER-Berechtigung.  
  
##  <a name="SSMSProcedure"></a>Verwenden des Dialog Felds neue Verfügbarkeits Gruppe (SQL Server Management Studio)  
 **So erstellen Sie eine Verfügbarkeits Gruppe**  
  
1.  Stellen Sie im Objekt-Explorer eine Verbindung zur Serverinstanz her, die das primäre Replikat hostet, und klicken Sie auf den Servernamen.  
  
2.  Erweitern Sie den Knoten **Hohe Verfügbarkeit (immer aktiviert)** .  
  
3.  Klicken Sie mit der rechten Maustaste auf den Knoten **Verfügbarkeitsgruppen** , und wählen Sie den Befehl **Neue Verfügbarkeitsgruppe** aus.  
  
4.  Dieser Befehl erschließt das Dialogfeld **Neue Verfügbarkeitsgruppe** .  
  
5.  Verwenden Sie auf der Seite **Allgemein** das Feld **Name der Verfügbarkeitsgruppe** zur Eingabe eines Namens für die neue Verfügbarkeitsgruppe. Dieser Name muss ein gültiger SQL Server-Bezeichner und in allen Verfügbarkeitsgruppen im WSFC-Cluster eindeutig sein. Die maximale Länge eines Verfügbarkeitsgruppennamens beträgt 128 Zeichen.  
  
6.  Klicken Sie im Raster **Verfügbarkeitsdatenbanken** auf **Hinzufügen** , und geben Sie den Namen einer lokalen Datenbank ein, die zu dieser Verfügbarkeitsgruppe gehören soll. Wiederholen Sie dies für jede hinzuzufügende Datenbank. Wenn Sie auf **OK**klicken, überprüft das Dialogfeld, ob die angegebene Datenbank die Voraussetzungen dafür erfüllt, dass sie einer Verfügbarkeitsgruppe angehört. Informationen zur diesen Voraussetzungen finden Sie unter [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).  
  
7.  Klicken Sie im Raster **Verfügbarkeitsdatenbanken** auf **Hinzufügen** , und geben Sie den Namen einer Serverinstanz ein, um ein sekundäres Replikat zu hosten. Das Dialogfeld versucht nicht, eine Verbindung zu diesen Instanzen herzustellen. Wenn Sie einen falschen Servernamen angeben, wird zwar ein sekundäres Replikat hinzugefügt, Sie können aber keine Verbindung mit diesem Replikat herstellen.  
  
    > [!TIP]  
    >  Wenn Sie ein Replikat hinzugefügt haben und keine Verbindung zur Hostserverinstanz herstellen können, können Sie das Replikat entfernen und ein neues hinzufügen. Weitere Informationen finden Sie unter [Entfernen eines sekundären Replikats aus einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md) und [Hinzufügen eines sekundären Replikats zu einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md).  
  
8.  Klicken Sie im Bereich **Seite auswählen** des Dialogfelds auf **Sicherungseinstellungen**. Geben Sie dann auf der Seite **Sicherungseinstellungen** auf Grundlage der Replikatrolle an, wo die Sicherungen erstellt werden sollen, weisen Sie den einzelnen Serverinstanzen, die ein Verfügbarkeitsreplikat für diese Verfügbarkeitsgruppe hosten, Sicherungsprioritäten zu. Weitere Informationen finden Sie unter [Eigenschaften der Verfügbarkeitsgruppe: Neue Verfügbarkeitsgruppe &#40;Seite Sicherungseinstellungen&#41;](availability-group-properties-new-availability-group-backup-preferences-page.md).  
  
9. Klicken Sie auf **OK**, um die Verfügbarkeitsgruppe zu erstellen. Dadurch überprüft das Dialogfeld, ob die angegebenen Datenbanken die erforderlichen Komponenten erfüllen.  
  
     Um das Dialogfeld zu beenden, ohne die Verfügbarkeitsgruppe zu erstellen, klicken Sie auf **Abbrechen**.  
  
##  <a name="FollowUp"></a>Nachverfolgung: nach dem Erstellen einer Verfügbarkeits Gruppe mithilfe des Dialog Felds neue Verfügbarkeits Gruppe  
  
-   Sie wiederum müssen eine Verbindung zu jeder Serverinstanz herstellen, die ein sekundäres Replikat für die Verfügbarkeitsgruppe hostet, und die folgenden Schritte ausführen:  
  
    1.  Verknüpfen Sie das sekundäre Replikat mit der Verfügbarkeitsgruppe. Weitere Informationen finden Sie unter [Verknüpfen eines sekundären Replikats mit einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).  
  
    2.  Stellen Sie aktuelle Sicherungen jeder primären Datenbank und ihres Transaktionsprotokolls (mithilfe von RESTORE WITH NORECOVERY) wieder her. Weitere Informationen finden Sie unter [Manuelles Vorbereiten einer sekundären Datenbank auf eine Verfügbarkeitsgruppe &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)erstellt und konfiguriert wird.  
  
    3.  Verknüpfen Sie jede neu vorbereitete sekundäre Datenbank sofort mit der Verfügbarkeitsgruppe. Weitere Informationen finden Sie unter [Verknüpfen einer sekundären Datenbank mit einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)aktiviert sind, eine Always On-Verfügbarkeitsgruppe zu erstellen.  
  
-   Wir empfehlen das Erstellen eines Verfügbarkeitsgruppenlisteners für die neue Verfügbarkeitsgruppe. Dazu müssen Sie mit der Serverinstanz verbunden sein, auf der das aktuelle primäre Replikat gehostet wird. Weitere Informationen finden Sie unter [Erstellen oder Konfigurieren eines Verfügbarkeitsgruppenlisteners &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)besitzen.  
  
##  <a name="RelatedTasks"></a> Verwandte Aufgaben  
 **So konfigurieren Sie Verfügbarkeits Gruppen-und Replikat Eigenschaften**  
  
-   [Ändern des Verfügbarkeitsmodus eines Verfügbarkeitsreplikats &#40;SQL Server&#41;](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [Ändern des Failovermodus eines Verfügbarkeitsreplikats &#40;SQL Server&#41;](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [Erstellen oder Konfigurieren eines Verfügbarkeitsgruppenlisteners &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Konfigurieren der flexiblen Failoverrichtlinie zum Steuern der Bedingungen für ein automatisches Failover (AlwaysOn-Verfügbarkeitsgruppen)](configure-flexible-automatic-failover-policy.md)  
  
-   [Geben Sie die Endpunkt-URL beim Hinzufügen oder Ändern eines Verfügbarkeits Replikat &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [Konfigurieren der Sicherung auf Verfügbarkeitsreplikaten &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [Konfigurieren des schreibgeschützten Zugriffs auf ein Verfügbarkeitsreplikat &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [Konfigurieren des schreibgeschützten Routing für eine Verfügbarkeitsgruppe &#40;SQL Server&#41;](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [Ändern des Sitzungstimeouts für ein Verfügbarkeitsreplikat &#40;SQL Server&#41;](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 **So vervollständigen Sie die Verfügbarkeits Gruppenkonfiguration**  
  
-   [Verknüpfen eines sekundären Replikats mit einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Manuelles Vorbereiten einer sekundären Datenbank auf eine Verfügbarkeitsgruppe &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [Verknüpfen einer sekundären Datenbank mit einer Verfügbarkeitsgruppe &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Erstellen oder Konfigurieren eines Verfügbarkeitsgruppenlisteners &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
 **Alternative Möglichkeiten zum Erstellen einer Verfügbarkeits Gruppe**  
  
-   [Verwenden des Assistenten für Verfügbarkeitsgruppen &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Erstellen einer Verfügbarkeits Gruppe &#40;Transact-SQL-&#41;](create-an-availability-group-transact-sql.md)  
  
-   [Erstellen Sie eine Verfügbarkeits Gruppe &#40;SQL Server PowerShell&#41;](../../../powershell/sql-server-powershell.md)  
  
 **So aktivieren Sie AlwaysOn-Verfügbarkeitsgruppen**  
  
-   [Aktivieren und Deaktivieren von Always On-Verfügbarkeitsgruppen &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
 **So konfigurieren Sie einen Datenbankspiegelungs-Endpunkt**  
  
-   [Erstellen Sie einen Datenbankspiegelungs-Endpunkt für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server PowerShell&#41;](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [Erstellen eines Endpunkts der Datenbankspiegelung für Windows-Authentifizierung (Transact-SQL)](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [Verwenden von Zertifikaten für einen Datenbankspiegelungs-Endpunkt &#40;Transact-SQL&#41;](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   [Geben Sie die Endpunkt-URL beim Hinzufügen oder Ändern eines Verfügbarkeits Replikat &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 **Problembehandlung für die AlwaysOn-Verfügbarkeitsgruppenkonfiguration**  
  
-   [Problembehandlung AlwaysOn-Verfügbarkeitsgruppen Konfiguration (SQL Server) gelöscht](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [Problembehandlung bei einem fehlgeschlagenen Vorgang zum Hinzufügen einer Datei &#40;AlwaysOn-Verfügbarkeitsgruppen&#41;](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="RelatedContent"></a> Verwandte Inhalte  
  
-   [Microsoft SQL Server AlwaysOn-Lösungshandbuch zu hoher Verfügbarkeit und Notfallwiederherstellung](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Der Datenbankspiegelungs-Endpunkt &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
 [Verfügbarkeitsgruppenlistener, Clientkonnektivität und Anwendungsfailover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)   
 [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)  
