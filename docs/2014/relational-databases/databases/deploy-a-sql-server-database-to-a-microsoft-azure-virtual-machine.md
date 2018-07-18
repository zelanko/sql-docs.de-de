---
title: Bereitstellen einer SQL Server-Datenbank auf einem virtuellen Microsoft Azure-Computer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.deploymentwizard.deploymentsettings.f1
- sql12.swb.deploymentwizard.progress.f1
- sql11.swb.usevmdialog.f1
- sql11.swb.deploymentwizard.f1
- sql12.swb.deploymentwizard.azuresignin.f1
- sql11.swb.deploymentwizard.summary.f1
- sql11.swb.deploymentwizard.azuresignin.f1
- sql12.swb.deploymentwizard.f1
- sql12.swb.sqlvmdialog.f1
- sql11.swb.newvmdialog.f1
- sql12.swb.deploymentwizard.results.f1
- sql11.swb.deploymentwizard.progress.f1
- sql12.swb.newvmdialog.f1
- sql12.swb.deploymentwizard.sourcesettings.f1
- sql12.swb.usevmdialog.f1
- sql11.swb.deploymentwizard.sourcesettings.f1
- sql11.swb.deploymentwizard.results.f1
- sql12.swb.deploymentwizard.summary.f1
- sql11.swb.deploymentwizard.deploymentsettings.f1
helpviewer_keywords:
- Deploy a database
- Deploy to Azure VM
- Migrate to Azure
- Windows Azure virtual machine
- Migrate to Azure VM
- Migrate to the cloud
- SQL Server Management Studio
- SSMS
- Deploy database wizard
- Deploy a SQL Server database to Azure
- Azure VM
ms.assetid: 5e82e66a-262e-4d4f-aa89-39cb62696d06
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: dc5399a395a53f2e37103b5516b0e707eb8c0335
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37158511"
---
# <a name="deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine"></a>Bereitstellen einer SQL Server-Datenbank auf einem virtuellen Microsoft Azure-Computer
  Verwenden Sie den Assistenten **SQL Server-Datenbank auf Microsoft Azure-VM bereitstellen**, um eine Datenbank von einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf einem virtuellen Microsoft Azure-Computer (VM) bereitzustellen. Der Assistent führt eine vollständige Datenbanksicherung durch und kopiert somit immer das vollständige Datenbankschema und alle Daten einer SQL Server-Benutzerdatenbank. Der Assistent übernimmt außerdem die gesamte Azure-VM-Konfiguration, sodass keine Vorkonfiguration der VM erforderlich ist.  
  
 Sie können den Assistenten nicht für differenzielle Sicherungen verwenden, da der Assistent keine vorhandene Datenbank überschreibt, die denselben Datenbanknamen hat. Um eine vorhandene Datenbank auf der VM zu ersetzen, müssen Sie zuerst die vorhandene Datenbank löschen oder den Datenbanknamen ändern. Falls ein Namenskonflikt zwischen dem Datenbanknamen eines aktiven Bereitstellungsvorgangs und dem einer vorhandenen Datenbank auf der VM auftritt, schlägt der Assistent ein Namenssuffix für den Namen der bereitzustellenden Datenbank vor, sodass der Vorgang erfolgreich abgeschlossen werden kann.  
  
##  <a name="before_you_begin"></a> Vorbereitungen  
 Für diesen Assistenten sind die folgenden Informationen und Konfigurationseinstellungen verfügbar sein:  
  
-   Die Microsoft-Kontodetails, die dem Windows Azure-Abonnement zugeordnet sind.  
  
-   Ihr Windows Azure-Veröffentlichungsprofil.  
  
    > [!CAUTION]  
    >  SQL Server unterstützt derzeit die Version 2.0 des Veröffentlichungsprofils. Weitere Informationen zum Herunterladen der unterstützten Version des Veröffentlichungsprofils finden Sie unter [Herunterladen des Veröffentlichungsprofils 2.0](http://go.microsoft.com/fwlink/?LinkId=396421).  
  
-   Das Verwaltungszertifikat wurde in das Windows Azure-Abonnement hochgeladen.  
  
-   Das Verwaltungszertifikat wurde im persönlichen Zertifikatspeicher auf dem Computer gespeichert, auf dem der Assistent ausgeführt wird.  
  
-   Ein temporärer Speicherort muss für den Computer verfügbar sein, auf dem die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbank gehostet wird. Der temporäre Speicherort muss zudem auch für den Computer verfügbar sein, auf der der Assistent ausgeführt wird.  
  
-   Wenn Sie die Datenbank auf einer vorhandenen virtuellen Maschine bereitstellen, muss die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für das Abhören eines TCP/IP-Ports konfiguriert werden.  
  
-   Für die Windows Azure-VM oder das Katalog-Image, das Sie für die Erstellung der VM verwenden möchten, muss der SQL Server-Cloud-Adapter konfiguriert sein und ausgeführt werden.  
  
-   Sie müssen einen geöffneten Endpunkt für den SQL Server-Cloud-Adapter auf dem Windows Azure-Gateway mit privatem Port 11435 festlegen.  
  
 Wenn Sie planen, Ihre Datenbank in einer vorhandenen Windows Azure-VM bereitzustellen, sind zudem die folgenden Informationen erforderlich:  
  
-   Der DNS-Name des Cloud-Diensts, der die VM hostet.  
  
-   Administrator-Anmeldeinformationen für die VM.  
  
-   Anmeldeinformationen mit Sicherungsoperatorprivilegien für die bereitzustellende Datenbank, aus der Zielinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Weitere Informationen zu SQL Server auf Windows Azure-Computern ausgeführt wird, finden Sie unter [bereit für die Migration zu SQL Server in Windows Azure Virtual Machines](http://msdn.microsoft.com/library/dn133142.aspx).  
  
 Auf Computern, auf denen ein Windows Server-Betriebssystem ausgeführt wird, müssen Sie zur Ausführung dieses Assistenten die folgenden Konfigurationseinstellungen vornehmen:  
  
-   Deaktivieren Sie die verstärkte Sicherheitskonfiguration: Wählen Sie „Server-Manager > Lokaler Server“, und geben Sie für „Verstärkte Sicherheitskonfiguration für Internet Explorer“ den Wert **AUS** an.  
  
-   Aktivieren Sie JavaScript: Internet Explorer > Internetoptionen > Sicherheit > Stufe anpassen > Skripting > Active Scripting: **Aktivieren**.  
  
###  <a name="limitations"></a> Einschränkungen  
 Die Datenbankgröße für diesen Vorgang ist auf 1 TB beschränkt.  
  
 Diese Bereitstellungsfunktion ist in SQL Server Management Studio für [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]verfügbar.  
  
 Diese Bereitstellungsfunktion ist nur für die Verwendung mit Benutzerdatenbanken vorgesehen. Das Bereitstellen von Systemdatenbanken wird nicht unterstützt.  
  
 Die Bereitstellungsfunktion unterstützt keine gehosteten Dienste, die einer Affinitätsgruppe zugeordnet sind. Beispielsweise können Speicherkonten, die einer Affinitätsgruppe zugeordnet sind, nicht auf der Seite **Bereitstellungseinstellungen** dieses Assistenten nicht zur Verwendung ausgewählt werden.  
  
 Die SQL Server-Version auf dem virtuellen Computer muss gleich oder höher sein als die SQL Server-Version des Quellservers. Die folgenden SQL Server-Datenbank-Versionen können mit diesem Assistenten in einer Windows Azure-VM bereitgestellt werden:  
  
-   SQL Server 2008  
  
-   SQL Server 2008 R2  
  
-   SQL Server 2012  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
 In einer Windows Azure-VM ausgeführte SQL Server-Datenbankversionen können wie folgt bereitgestellt werden:  
  
-   SQL Server 2012  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
 Falls ein Namenskonflikt zwischen dem Datenbanknamen eines aktiven Bereitstellungsvorgangs und dem einer vorhandenen Datenbank auf der VM auftritt, schlägt der Assistent ein Namenssuffix für den Namen der bereitzustellenden Datenbank vor, sodass der Vorgang erfolgreich abgeschlossen werden kann.  
  
###  <a name="filestream"></a> Überlegungen zur Bereitstellung einer FILESTREAM-aktivierten Datenbank in einer Azure-VM  
 Beachten Sie die folgenden Richtlinien und Einschränkungen, wenn Sie Datenbanken bereitstellen, in denen BLOBs in FILESTREAM-Objekten gespeichert sind:  
  
-   Die Bereitstellungsfunktion kann eine FILESTREAM-aktivierte Datenbank nicht in einer neuen VM bereitstellen. Wenn FILESTREAM vor dem Ausführen des Assistenten in der VM nicht aktiviert wurde, schlägt der Vorgang zur Datenbankwiederherstellung fehl, und der Assistentenvorgang kann nicht erfolgreich abgeschlossen werden. Um eine Datenbank, die FILESTREAM verwendet, erfolgreich bereitzustellen, aktivieren Sie FILESTREAM in der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf der Host-VM, bevor Sie den Assistenten starten. Weitere Informationen finden Sie unter [FILESTREAM (SQL Server)](http://msdn.microsoft.com/library/gg471497.aspx).  
  
-   Wenn die Datenbank In-Memory OLTP verwendet, können Sie die Datenbank ohne Änderungen an der Datenbank in einer Azure-VM bereitstellen. Weitere Informationen finden Sie unter [In-Memory OLTP (Speicheroptimierung)](http://msdn.microsoft.com/library/dn133186\(SQL.120\).aspx).  
  
###  <a name="geography"></a> Überlegungen zur geografischen Verteilung von Ressourcen  
 Beachten Sie, dass sich die folgenden Ressourcen in der gleichen geografischen Region befinden müssen:  
  
-   Cloud-Dienst  
  
-   VM-Speicherort  
  
-   Datenträgerspeicherdienst  
  
 Wenn sich die oben genannten Ressourcen nicht in derselben Region befinden, kann der Assistent nicht erfolgreich abgeschlossen werden.  
  
###  <a name="configuration_settings"></a> Konfigurationseinstellungen des Assistenten  
 Verwenden Sie die folgenden Konfigurationsdetails, um die Einstellungen für eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datenbankbereitstellung in einer Azure-VM zu ändern.  
  
-   **Standardpfad für die Konfigurationsdatei** – %LOCALAPPDATA%\SQL Server\Deploy to SQL in WA VM\DeploymentSettings.xml  
  
-   **Struktur der Konfigurationsdatei**  
  
    -   \<DeploymentSettings>  
  
        -   <OtherSettings  
  
            -   TraceLevel="Debug" \<!-- Protokolliergrad -->  
  
            -   BackupPath="\\\\[server name]\\[volume]\\" \<!-- Der zuletzt verwendete Pfad für die Sicherung. Wird als Standard im Assistenten verwendet. -->  
  
            -   CleanupDisabled = False /> \<!-- Der Assistent löscht keine Zwischendateien und Microsoft Azure-Objekte (VM, CS, SA). -->  
  
        -   <PublishProfile \<!-- Die zuletzt verwendeten Veröffentlichungsprofilinformationen. -->  
  
            -   Certificate="12A34B567890123ABCD4EF567A8" \<!-- Das Zertifikat für die Verwendung im Assistenten. -->  
  
            -   Subscription="1a2b34c5-67d8-90ef-ab12-xxxxxxxxxxxxx" \<!-- Das Abonnement für die Verwendung im Assistenten. -->  
  
            -   Name="Mein Abonnement" \<!-- Der Name des Abonnements. -->  
  
            -   Publisher="" />  
  
    -   \</DeploymentSettings>  
  
 **Konfigurationsdateiwerte**  
  
###  <a name="permissions"></a> Berechtigungen  
 Die bereitzustellende Datenbank muss sich in einem normalen Status befinden. Außerdem muss das Benutzerkonto, über das der Assistent ausgeführt wird, Zugriff auf die Datenbank haben und über die Berechtigung verfügen, einen Sicherungsvorgang auszuführen.  
  
##  <a name="launch_wizard"></a> Verwenden der Datenbankbereitstellung auf Windows Azure-VM-Assistenten  
 **Gehen Sie folgendermaßen vor, um den Assistenten zu starten:**  
  
1.  Verbinden Sie die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe von SQL Server Management Studio mit der bereitzustellenden Datenbank.  
  
2.  Erweitern Sie im **Objekt-Explorer**den Instanznamen und dann den Knoten **Datenbanken** .  
  
3.  Klicken Sie mit der rechten Maustaste auf die Datenbank, die Sie bereitstellen möchten, wählen Sie **Tasks**und dann **Datenbank in Windows Azure-VM bereitstellen**aus.  
  

  
##  <a name="Introduction"></a> Seite "Einführung"  
 Auf dieser Seite wird der Assistent **SQL Server-Datenbank auf Windows Azure-VM bereitstellen** beschrieben.  
  
 **Optionen**  
  
-   **Diese Seite nicht mehr anzeigen.** – Aktivieren Sie dieses Kontrollkästchen, damit die Einführungsseite in Zukunft nicht mehr angezeigt wird.  
  
-   Durch**Weiter** gelangen Sie zur Seite **Quelleinstellungen** .  
  
-   **Abbrechen** – bricht den Vorgang ab und schließt den Assistenten.  
  
-   **Hilfe** – Startet das MSDN-Hilfethema für den Assistenten.  
  
##  <a name="Source_settings"></a> Quelleinstellungen  
 Auf dieser Seite stellen Sie eine Verbindung mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] her, die die Datenbank hostet, die Sie in der Windows Azure-VM bereitstellen möchten. Hier geben Sie zudem einen temporären Speicherort für die Speicherung der Dateien auf dem lokalen Computer, bevor sie mit Windows Azure übertragen werden. Dies kann ein freigegebener Netzwerkspeicherort sein.  
  
 **Optionen**  
  
-   Klicken Sie auf **Verbinden…** und geben Sie Verbindungsdetails für die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] an, die die bereitzustellende Datenbank hostet.  
  
-   Wählen Sie in der Dropdownliste **Datenbank auswählen** diejenige Datenbank aus, die bereitgestellt werden soll.  
  
-   Geben Sie im Feld **Weitere Einstellungen** einen freigegebenen Ordner an, auf den der Windows Azure-VM-Dienst zugreifen kann.  
  
##  <a name="Azure_sign-in"></a> Windows Azure-Anmeldung  
 Über diese Seite stellen Sie eine Verbindung mit Windows Azure her und geben ein Verwaltungszertifikat oder Details zum Veröffentlichungsprofil an.  
  
 **Optionen**  
  
-   **Verwaltungszertifikat** – Mit dieser Option geben Sie ein Zertifikat aus dem lokalen Zertifikatspeicher an, das mit dem Verwaltungszertifikat von Windows Azure übereinstimmt.  
  
-   **Veröffentlichungsprofil** – Verwenden Sie diese Option, wenn auf Ihren Computer bereits ein Veröffentlichungsprofil heruntergeladen ist.  
  
-   **Anmelden** – Über diese Option melden Sie sich mit einem Microsoft-Konto bei Windows Azure an – beispielsweise mit einer Live ID oder einem Hotmail-Konto –, um ein neues Verwaltungszertifikat zu generieren und herunterzuladen. Beachten Sie, dass die Anzahl von Zertifikaten pro Abonnement beschränkt ist.  
  
-   **Abonnement** – Wählen Sie die zugehörige Windows Azure-Abonnement-ID für das Verwaltungszertifikat aus dem lokalen Zertifikatspeicher oder für ein Veröffentlichungsprofil, oder geben bzw. fügen Sie sie ein.  
  
##  <a name="Deployment_settings"></a> Bereitstellungseinstellungen (Seite)  
 Auf dieser Seite können Sie den Zielserver angeben sowie Details zur neuen Datenbank bereitstellen.  
  
 **Optionen**  
  
-   **Virtuelle Windows Azure-Maschine** – Geben Sie Details für die VM an, die die SQL Server-Datenbank hostet:  
  
-   **Clouddienstname** – Geben Sie den Namen des Diensts an, der die VM hostet. Um einen neuen Clouddienst zu erstellen, geben Sie einen Namen für den neuen Clouddienst an.  
  
-   **Name der virtuellen Machine** – Geben Sie den Namen der VM an, die die SQL Server-Datenbank hostet. Um eine neue Windows Azure-VM zu erstellen, geben Sie einen Namen für die neue VM an.  
  
-   **Einstellungen** – Erstellen Sie über die Schaltfläche Einstellungen eine neue VM, die dann die SQL Server-Datenbank hostet. Wenn Sie eine vorhandene VM verwenden, werden die angegebenen Informationen verwendet, um Ihre Anmeldeinformationen zu authentifizieren.  
  
-   **Speicherkonto** – Wählen Sie aus der Dropdownliste das Speicherkonto aus. Um ein neues Speicherkonto zu erstellen, geben Sie einen Namen für das neue Konto an. Beachten Sie, dass Speicherkonten, die einer Affinitätsgruppe zugeordnet sind, nicht in der Dropdownliste verfügbar sind.  
  
-   **Zieldatenbank** – Geben Sie Details zur Zieldatenbank an.  
  
-   **Serververbindung** – Verbindungsdetails für den Server.  
  
-   **Datenbank** – Bestätigen oder geben Sie den Namen einer neuen Datenbank an. Wenn der Datenbankname auf der SQL Server-Zielinstanz bereits vorhanden ist, wird empfohlen, einen anderen Datenbanknamen anzugeben.  
  
##  <a name="Summary"></a> Seite "Zusammenfassung"  
 Auf dieser Seite können Sie die für den Vorgang angegebenen Einstellungen überprüfen. Klicken Sie auf **Fertig stellen**, um den Bereitstellungsvorgang mithilfe der angegebenen Einstellungen abzuschließen. Klicken Sie auf **Abbrechen**, um den Bereitstellungsvorgang abzubrechen und den Assistenten zu beenden.  
  
 Möglicherweise sind manuelle Schritte erforderlich, um Datenbankdetails an die SQL Server-Datenbank auf der Windows Azure-VM bereitzustellen. Diese Schritte werden detailliert für Sie beschriebenen.  
  
##  <a name="Results"></a> Ergebnisse (Seite)  
 Auf dieser Seite wird angegeben, ob der Bereitstellungsvorgang erfolgreich war oder ob dabei Fehler auftraten, dabei werden die Ergebnisse jeder Aktion angezeigt. Für alle Aktionen, die fehlerhaft waren, wird dies in der Spalte **Ergebnis** entsprechend angezeigt. Klicken Sie auf den Link, um einen Bericht des für diese Aktion aufgetretenen Fehlers anzuzeigen.  
  
 Klicken Sie auf **Fertig stellen** , um den Assistenten zu schließen.  
  
## <a name="see-also"></a>Siehe auch  
 [Cloud-Adapter für SQL Server](../../database-engine/cloud-adapter-for-sql-server.md)   
 [Datenbank-Lebenszyklusverwaltung](../database-lifecycle-management.md)   
 [Exportieren einer Datenebenenanwendung](../data-tier-applications/export-a-data-tier-application.md)   
 [Importieren einer BACPAC-Datei zum Erstellen einer neuen Benutzerdatenbank](../data-tier-applications/import-a-bacpac-file-to-create-a-new-user-database.md)   
 [Sichern und Wiederherstellen von Azure SQL-Datenbanken](https://msdn.microsoft.com/library/azure/jj650016.aspx)   
 [SQL Server-Bereitstellung in Microsoft Azure Virtual Machines](http://msdn.microsoft.com/library/dn133141.aspx)   
 [Vorbereitung auf die Migration zu SQL Server auf Microsoft Azure Virtual Machines](http://msdn.microsoft.com/library/dn133142.aspx)  
  
  
