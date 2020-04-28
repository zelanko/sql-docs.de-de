---
title: 'Seite „Replikate angeben“ (Assistent für neue Verfügbarkeitsgruppen: Assistent zum Hinzufügen von Replikaten) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.newagwizard.listeners.f1
- sql12.swb.newagwizard.specifyreplicas.f1
- sql12.swb.addreplicawizard.specifyreplicas.f1
ms.assetid: 2d90fc12-a67b-4bd0-b0ab-899b73017196
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2a552b5847f1abda254da1d6c7348088ee0e8a03
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "76923042"
---
# <a name="specify-replicas-page-new-availability-group-wizard-add-replica-wizard"></a>Seite „Replikate angeben“ (Assistent für neue Verfügbarkeitsgruppen: Assistent zum Hinzufügen von Replikaten)
  In diesem Thema werden die Optionen auf der Seite **Replikate angeben** beschrieben. Diese Seite gilt für: [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] und [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] von [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Verwenden Sie die Seite **Replikate angeben** , um mindestens ein Verfügbarkeitsreplikat anzugeben und zu konfigurieren und die Verfügbarkeitsgruppe hinzuzufügen. Diese Seite enthält vier Registerkarten, die in der folgenden Tabelle vorgestellt werden. Klicken Sie auf den Namen einer Registerkarte in der Tabelle, um zum entsprechenden Abschnitt weiter unten in diesem Thema zu wechseln.  
  
|Registerkarte|Kurzbeschreibung|  
|---------|-----------------------|  
|[Replikate](#ReplicasTab)|Geben Sie mit dieser Registerkarte jede Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] an, die ein sekundäres Replikat hosten wird oder derzeit hostet. Beachten Sie, dass die Serverinstanz, mit der Sie gerade verbunden sind, das primäre Replikat hosten muss.<br /><br /> Tipp: Bevor Sie zu den anderen Registerkarten übergehen, sollten Sie alle Replikate auf der Registerkarte **Replikate** angegeben haben.|  
|[Endpunkte](#EndpointsTab)|Auf dieser Registerkarte können Sie vorhandene Endpunkte für die Datenbankspiegelung überprüfen und automatisch einen Endpunkt erstellen, falls er auf einer Serverinstanz fehlt, deren Dienstkonten die Windows-Authentifizierung nutzen.|  
|[Sicherungseinstellungen](#BackupPreferencesTab)|Geben Sie mit dieser Registerkarte die Sicherungseinstellungen für die Verfügbarkeitsgruppe als Ganzes und die Sicherungsprioritäten für die einzelnen Verfügbarkeitsreplikate an.|  
|[Listener](#Listener)|Verwenden Sie diese Registerkarte (falls verfügbar), um einen Verfügbarkeitsgruppenlistener zu erstellen. Standardmäßig wird kein Listener erstellt.<br /><br /> Hinweis: Diese Registerkarte ist nur verfügbar, wenn Sie den [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] ausführen.|  
  
##  <a name="replicas-tab"></a><a name="ReplicasTab"></a>Replikate  
 **Serverinstanz**  
 Zeigt den Namen der Serverinstanz an, die als Host für das Verfügbarkeitsreplikat fungiert.  
  
 Falls eine Serverinstanz, mit der Sie ein sekundäres Replikat hosten, nicht im Raster **Verfügbarkeitsreplikate** aufgeführt ist, klicken Sie auf die Schaltfläche **Replikat hinzufügen** . Wenn Sie eine Verfügbarkeitsgruppe in einer hybriden IT-Umgebung konfigurieren (siehe [Hochverfügbarkeit und Notfallwiederherstellung für SQL Server auf Azure Virtual Machines](https://msdn.microsoft.com/library/windowsazure/jj870962.aspx)), können Sie auf die Schaltfläche **Azure-Replikat hinzufügen** klicken, um virtuelle Computer mit sekundären Replikaten in Azure zu erstellen.  
  
 **Anfängliche Rolle**  
 Gibt die Rolle an, die das neue Replikat anfangs aufweist: **Primär** oder **Sekundär**.  
  
 **Automatisches Failover (max. 2)**  
 Aktivieren Sie dieses Kontrollkästchen nur, wenn dieses Verfügbarkeitsreplikat ein automatischer Failoverpartner sein soll. Sie müssen zum Konfigurieren eines automatischen Failovers diese Option für das ursprüngliche primäre Replikat und ein sekundäres Replikat auswählen. Beide Replikate verwenden den Verfügbarkeitsmodus für synchrone Commits. Nur zwei Replikate können automatisches Failover unterstützen.  
  
 Weitere Informationen zum Verfügbarkeits Modus mit synchronem Commit finden Sie unter [Verfügbarkeits Modi (AlwaysOn-Verfügbarkeitsgruppen)](availability-modes-always-on-availability-groups.md). Informationen über das automatische Failover finden Sie unter [Failover und Failovermodi &#40;AlwaysOn-Verfügbarkeitsgruppen&#41;](failover-and-failover-modes-always-on-availability-groups.md).  
  
 **Synchroner Commit (max. 3)**  
 Wenn Sie **Automatisches Failover (max. 2)** für das Replikat ausgewählt haben, wird auch **Synchroner Commit (max. 3)** aktiviert. Ist das Kontrollkästchen deaktiviert, aktivieren Sie es nur, wenn von diesem Replikat der Modus für synchrone Commits nur mit geplantem manuellem Failover verwendet werden soll. Nur drei Replikate können den Modus für synchrone Commits verwenden.  
  
 Wenn von diesem Replikat der Verfügbarkeitsmodus für asynchrone Commits verwendet werden soll, lassen Sie dieses Kontrollkästchen deaktiviert. Das Replikat unterstützt nur erzwungenes manuelles Failover (mit möglichem Datenverlust). Weitere Informationen zum Verfügbarkeits Modus mit asynchronem Commit finden Sie unter [Verfügbarkeits Modi (AlwaysOn-Verfügbarkeitsgruppen)](availability-modes-always-on-availability-groups.md). Informationen über das geplante manuelle Failover und das erzwungene manuelle Failover finden Sie unter [Failover und Failovermodi &#40;AlwaysOn-Verfügbarkeitsgruppen&#41;](failover-and-failover-modes-always-on-availability-groups.md).  
  
 **Lesbare sekundäre Rolle**  
 Wählen Sie aus der Dropdownliste **Lesbare sekundäre Rolle** folgendermaßen einen Wert aus:  
  
 **No**  
 Es werden keine direkten Verbindungen mit sekundären Datenbanken dieses Replikats zugelassen. Sie sind für den Lesezugriff nicht verfügbar. Dies ist die Standardeinstellung.  
  
 **Nur beabsichtigte Lesevorgänge**  
 Es sind nur direkte, schreibgeschützte Verbindungen mit sekundären Datenbanken dieses Replikats zulässig. Die sekundären Datenbanken sind alle für Lesezugriff verfügbar.  
  
 **Ja**  
 Alle Verbindungen zu sekundären Datenbanken dieses Replikats sind zugelassen, aber nur für Lesezugriff. Die sekundären Datenbanken sind alle für Lesezugriff verfügbar.  
  
 **Replikat hinzufügen**  
 Klicken Sie, um ein sekundäres Replikat zur Verfügbarkeitsgruppe hinzuzufügen.  
  
 **Azure-Replikat hinzufügen**  
 Klicken Sie auf diese Option, um einen virtuellen Azure-Computer zu erstellen, auf dem ein sekundäres Replikat in der Verfügbarkeitsgruppe ausgeführt wird. Diese Option ist nur auf eine Verfügbarkeitsgruppe in der hybriden IT-Umgebung anwendbar, die lokale Replikate enthält. Weitere Informationen finden Sie unter [Hochverfügbarkeit und Notfallwiederherstellung für SQL Server auf Azure Virtual Machines](https://msdn.microsoft.com/library/windowsazure/jj870962.aspx).  
  
 **Replikat entfernen**  
 Klicken Sie, um das ausgewählte sekundäre Replikat aus der Verfügbarkeitsgruppe zu entfernen.  
  
##  <a name="endpoints-tab"></a><a name="EndpointsTab"></a>Registerkarte Endpunkte  
 Für jede Serverinstanz, die ein Verfügbarkeitsreplikat hostet, zeigt die Registerkarte **Endpunkte** ggf. tatsächliche Werte des vorhandenen Datenbankspiegelungs-Endpunkts an bzw. empfohlene Werte für einen potenziellen neuen Endpunkt, der die Windows-Authentifizierung verwenden würde. Sowohl für vorhandene als auch für potenzielle Endpunkte enthält das Raster für die Endpunktwerte die folgenden Informationen:  
  
 **Server Name**  
 Zeigt den Namen einer Serverinstanz an, die als Host für ein Verfügbarkeitsreplikat fungiert.  
  
 **Endpunkt-URL**  
 Zeigt die tatsächliche oder vorgeschlagene URL des Datenbankspiegelungs-Endpunkts an. Für einen vorgeschlagenen neuen Endpunkt können Sie diesen Wert ändern. Informationen über das Format dieser URLs finden Sie unter [Angeben der Endpunkt-URL beim Hinzufügen oder Ändern eines Verfügbarkeitsreplikats &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md).  
  
 **Port Nummer**  
 Zeigt die tatsächliche oder vorgeschlagene Portnummer des Endpunkts an. Für einen vorgeschlagenen neuen Endpunkt können Sie diesen Wert ändern.  
  
 **Endpoint Name (Endpunktname)**  
 Zeigt den tatsächlichen oder vorgeschlagenen Namen des Endpunkts an. Für einen vorgeschlagenen neuen Endpunkt können Sie diesen Wert ändern.  
  
 **Verschlüsseln von Daten**  
 Gibt an, ob über diesen Endpunkt gesendete Daten verschlüsselt werden. Für einen vorgeschlagenen neuen Endpunkt können Sie diese Einstellung ändern.  
  
 **SQL Server Dienst Konto**  
 Benutzername des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Dienstkontos.  
  
 Damit eine Serverinstanz einen Endpunkt verwendet, der die Windows-Authentifizierung verwendet, muss dessen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Dienstkonto ein Domänenkonto sein.  
  
 Durch diese Anforderung wird der nächste Konfigurationsschritt wie folgt bestimmt:  
  
-   Wenn jede Serverinstanz unter einem Domänendienstkonto ausgeführt wird, d. h, wenn in der Spalte **SQL Server-Dienstkonto** ein Domänendienstkonto für jede Serverinstanz angezeigt wird, klicken Sie auf **Weiter**.  
  
-   Wenn eine Serverinstanz unter einem Nicht-Domänendienstkonto ausgeführt wird, müssen Sie eine manuelle Änderung an der Serverinstanz vornehmen, bevor Sie den Assistenten fortsetzen können. Wenn Sie in diesem Fall auf **weiter** klicken, wird ein Warn Dialogfeld angezeigt. Sie sollten auf **Nein**klicken, sodass Sie zur Registerkarte**Endpunkte** zurückkehren. Wenn Sie den Assistenten auf der Seite **Replikate angeben** belassen, nehmen Sie eine der folgenden Änderungen an jeder Serverinstanz vor, für die in der Spalte **SQL Server Dienst Konto** ein nicht-Domänen Dienst Konto angezeigt wird:  
  
    -   Verwenden Sie den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Konfigurations-Manager zum Ändern des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Dienstkontos in ein Domänenkonto. Weitere Informationen finden Sie unter [Ändern des Dienststartkontos für SQL Server &#40;SQL Server-Konfigurations-Manager&#41;](../../configure-windows/scm-services-change-the-service-startup-account.md).  
  
    -   Verwenden Sie [!INCLUDE[tsql](../../../includes/tsql-md.md)] oder PowerShell, um manuell einen Datenbankspiegelungs-Endpunkt zu erstellen, der ein Zertifikat verwendet. Weitere Informationen finden Sie unter [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) oder [Erstellen eines Datenbankspiegelungs-Endpunkts für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server PowerShell&#41;](database-mirroring-always-on-availability-groups-powershell.md).  
  
     Wenn Sie die Seite **Verfügbarkeitsreplikate angeben** geöffnet lassen, während Sie Endpunkte konfigurieren, kehren Sie zur Registerkarte **Endpunkte** zurück, und klicken Sie auf **Aktualisieren** , um das Raster **Endpunktwerte** zu aktualisieren.  
  
##  <a name="backup-preferences-tab"></a><a name="BackupPreferencesTab"></a>Registerkarte Sicherungs Einstellungen  
 Wählen Sie eine der folgenden Optionen aus, um anzugeben, wo Sicherungen erfolgen sollen:  
  
 **Sekundär bevorzugen**  
 Gibt an, dass Sicherungen auf einem sekundären Replikat erfolgen müssen, außer wenn es sich beim primären Replikat um das einzige Onlinereplikat handelt. In diesem Fall muss die Sicherung auf dem primären Replikat erfolgen. Dies ist die Standardoption.  
  
 **Nur sekundär**  
 Gibt an, dass Sicherungen nie auf dem primären Replikat ausgeführt werden dürfen. Wenn es sich beim primären Replikat um das einzige Onlinereplikat handelt, darf keine Sicherung erfolgen.  
  
 **Primär**  
 Gibt an, dass die Sicherungen immer auf dem primären Replikat erfolgen müssen. Diese Option ist hilfreich, wenn Sie Sicherungsfunktionen benötigen, z. B. das Erstellen differenzieller Sicherungen, die nicht unterstützt werden, wenn die Sicherung auf einem sekundären Replikat ausgeführt wird.  
  
 **Beliebiges Replikat**  
 Gibt an, dass Sicherungsaufträge die Rolle der Verfügbarkeitsreplikate ignorieren sollen, wenn sie das Replikat zum Durchführen der Sicherungen auswählen. Sicherungsaufträge können andere Faktoren auswerten, wie z. B. die Sicherungspriorität jedes Verfügbarkeitsreplikats in Verbindung mit seinem Betriebszustand und Verbindungsstatus.  
  
> [!IMPORTANT]  
>  Die Einstellung "backup-preference" wird nicht erzwungen. Die Interpretation dieser Einstellung hängt von der Logik ab, die Sie ggf. per Skript in Sicherungsaufträge für die Datenbanken in einer angegebenen Verfügbarkeitsgruppe integriert haben. Weitere Informationen finden Sie unter [aktive sekundäre Replikate: Sicherung auf sekundären Replikaten (AlwaysOn-Verfügbarkeitsgruppen)](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md).  
  
### <a name="replica-backup-priorities-grid"></a>Raster "Sicherungsprioritäten für Replikate"  
 Verwenden Sie das Raster **Sicherungsprioritäten für Replikate** , um Sicherungsprioritäten für alle Replikate der Verfügbarkeitsgruppe anzugeben. Dieses Raster enthält die folgenden Spalten:  
  
 **Serverinstanz**  
 Zeigt den Namen der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] an, auf der das Verfügbarkeitsreplikat gehostet wird.  
  
 **Sicherungspriorität (niedrigste = 1, höchste = 100)**  
 Weisen Sie die Priorität für die Ausführung von Sicherungen auf diesem Replikat in Relation zu den anderen Replikaten in derselben Verfügbarkeitsgruppe zu. Der Standardwert lautet "50". Sie können im Bereich von 0 bis 100 eine beliebige andere ganze Zahl auswählen. 1 gibt die niedrigste Priorität und 100 die höchste Priorität an. Wenn Sie die **Sicherungspriorität** auf 1 festlegen, wird das Verfügbarkeitsreplikat für die Ausführung von Sicherungen nur ausgewählt, wenn derzeit kein Verfügbarkeitsreplikat mit höherer Priorität verfügbar ist.  
  
 **Replikat ausschließen**  
 Mit dieser Option wird verhindert, dass dieses Verfügbarkeitsreplikat je zum Ausführen von Sicherungen ausgewählt wird. Dies ist zum Beispiel für ein Remoteverfügbarkeitsreplikat hilfreich, für das keine Failover bei Sicherungen auftreten sollen.  
  
##  <a name="listener-tab"></a><a name="Listener"></a>Listenerregister Karte  
 Geben Sie die Einstellung für einen[Verfügbarkeitsgruppenlistener](../../listeners-client-connectivity-application-failover.md)an, der einen Clientverbindungspunkt bereitstellt. Folgende Werte sind möglich:  
  
 **Jetzt keinen Verfügbarkeitsgruppenlistener erstellen**  
 Überspringen Sie diesen Schritt. Sie können später einen Listener erstellen. Weitere Informationen finden Sie unter [Erstellen oder Konfigurieren eines Verfügbarkeitsgruppenlisteners &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md).  
  
 **Verfügbarkeitsgruppenlistener erstellen**  
 Geben Sie folgendermaßen die Listenereinstellungen für diese Verfügbarkeitsgruppe an:  
  
 **DNS-Name des Listeners**  
 Geben Sie den Netzwerknamen des Listeners an. Dieser Name muss in der Domäne eindeutig sein und darf nur alphanumerische Zeichen, Bindestriche (**-**) und Bindestriche (**_**) in beliebiger Reihenfolge enthalten. Wird der DNS-Name mit der Registerkarte **Listener** angegeben, kann er bis zu 15 Zeichen lang sein.  
  
> [!IMPORTANT]  
>  Wenn Sie einen ungültigen DNS-Listenernamen (oder eine ungültige Portnummer) auf der Registerkarte **Listener** eingeben, wird die Schaltfläche **Weiter** auf der Seite **Replikate angeben** deaktiviert.  
  
 **Port**  
 Geben Sie den von diesem Listener verwendeten TPC-Port an.  
  
> [!NOTE]  
>  Wenn Sie eine ungültige Portnummer (oder einen ungültigen DNS-Listenernamen) auf der Registerkarte **Listener** eingeben, wird die Schaltfläche **Weiter** auf der Seite **Replikate angeben** deaktiviert.  
  
 **Netzwerkmodus**  
 Wählen Sie mit der Dropdownliste den Netzwerkmodus aus, der von diesem Listener verwendet werden soll. Folgende Werte sind möglich:  
  
 **Statische IP**  
 Wählen Sie diese Option aus, wenn der Listener an mehr als einem Subnetz lauschen soll. Zur Verwendung des Netzwerkmodus mit statischer IP muss ein Verfügbarkeitsgruppenlistener an allen Subnetzen lauschen, die ein Verfügbarkeitsreplikat für die Verfügbarkeitsgruppe hosten. Klicken Sie für jedes Subnetz auf **Hinzufügen** , um eine Subnetzadresse auszuwählen und eine IP-Adresse anzugeben.  
  
 Wenn **Statische IP** als Netzwerkmodus ausgewählt wird (Standardauswahl), werden in einem Raster die Spalten **Subnetz** und **IP-Adresse** sowie die zugehörigen Schaltflächen **Hinzufügen** und **Entfernen** angezeigt. Beachten Sie, dass das Raster leer ist, bis Sie das erste Subnetz hinzufügen.  
  
 Spalte**Subnetz**  
 Zeigt die Subnetzadresse an, die Sie für alle Subnetze ausgewählt haben, die Sie für den Listener hinzugefügt haben.  
  
 Spalte**IP-Adresse**  
 Zeigt die IPv4- oder IPv6-Adresse an, die Sie für ein bestimmtes Subnetz angegeben haben.  
  
 **Add (Hinzufügen)**  
 Klicken Sie hier, um diesem Listener ein Subnetz hinzuzufügen. Das Dialogfeld **IP-Adresse hinzufügen** wird geöffnet. Weitere Informationen finden Sie im Hilfethema [Dialogfeld IP-Adresse hinzufügen&#40;SQL Server Management Studio&#41;](add-ip-address-dialog-box-sql-server-management-studio.md).  
  
 **Remove**  
 Klicken Sie hier, um das derzeit im Raster ausgewählte Subnetz zu entfernen.  
  
 **DHCP**  
 Aktivieren Sie diese Option, wenn der Listener an einem einzelnen Subnetz lauschen und eine dynamische IPv4-Adresse verwenden soll, die von einem Server mit dem Dynamic Host Configuration-Protokoll (DHCP) zugewiesen wird. DHCP ist auf ein einzelnes Subnetz beschränkt, das für alle Serverinstanzen gilt, die ein Verfügbarkeitsreplikat für die Verfügbarkeitsgruppe hosten.  
  
> [!IMPORTANT]  
>  DHCP wird in einer Produktionsumgebung nicht empfohlen. Wenn die DHCP-IP-Leasedauer bei einer Downtime abläuft, ist eine Verlängerung erforderlich, um die neue IP-Adresse des DHCP-Netzwerks zu registrieren, die dem DNS-Namen des Listeners zugeordnet ist, was sich auf die Clientkonnektivität auswirkt. DHCP eignet sich jedoch gut zum Einrichten der Entwicklungs- und Testumgebung, um grundlegende Funktionen von Verfügbarkeitsgruppen und die Integration in Ihre Anwendungen zu überprüfen.  
  
 Wenn **DHCP** ausgewählt ist, wird das Feld **Subnetz** angezeigt.  
  
 **Subnetz**  
 Wenn Sie **DHCP** als Netzwerkmodus ausgewählt haben, verwenden Sie die Dropdownliste **Subnetz** , um eine Adresse für das Subnetz auszuwählen, das die Verfügbarkeitsreplikate der Verfügbarkeitsgruppe hostet.  
  
> [!IMPORTANT]
>  Nach der Definition eines Verfügbarkeitsgruppenlisteners werden folgende Schritte empfohlen:  
> 
>  -   Bitten Sie den Netzwerkadministrator, die IP-Adresse des Listeners zur exklusiven Verwendung zu reservieren. Geben Sie den DNS-Hostnamen des Listeners an Anwendungsentwickler weiter, damit diese den Namen in Verbindungszeichenfolgen zum Anfordern von Clientverbindungen mit dieser Verfügbarkeitsgruppe verwenden.  
> -   Geben Sie den DNS-Hostnamen des Listeners an Anwendungsentwickler weiter, damit diese den Namen in Verbindungszeichenfolgen zum Anfordern von Clientverbindungen mit dieser Verfügbarkeitsgruppe verwenden.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Verwandte Aufgaben  
  
-   [Verwenden des Assistenten für Verfügbarkeitsgruppen &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Verwenden des Assistenten zum Hinzufügen von Replikaten zu Verfügbarkeitsgruppen &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Erstellen oder konfigurieren Sie einen verfügbarkeitsgruppenlistener &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Verwenden von Zertifikaten für einen Datenbankspiegelungs-Endpunkt (Transact-SQL)](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)  
  
-   [Erstellen Sie einen Datenbankspiegelungs-Endpunkt für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server PowerShell&#41;](database-mirroring-always-on-availability-groups-powershell.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Übersicht über AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Erstellen einer Verfügbarkeits Gruppe &#40;Transact-SQL-&#41;](/sql/t-sql/statements/create-availability-group-transact-sql)   
 [Voraussetzungen, Einschränkungen und Empfehlungen für AlwaysOn-Verfügbarkeitsgruppen &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)  
  
  
