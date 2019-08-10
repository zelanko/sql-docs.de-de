---
title: 'Bereitstellungs Checkliste: Multiserverinstallation von PowerPivot für SharePoint 2010 | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 4380040a-1368-4a47-8930-47c65a192e59
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 33bbaf46bb4dee5e0e7b58f6dc179ae5647ee3e7
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68890738"
---
# <a name="deployment-checklist-multi-server-installation-of-powerpivot-for-sharepoint-2010"></a>Bereitstellungs Checkliste: Multiserverinstallation von PowerPivot für SharePoint 2010
  Diese Prüfliste führt Sie durch die Schritte [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] zum Hinzufügen von für SharePoint zu einer dreistufigen SharePoint 2010-Farm, die Sie von Grund auf erstellen. Eine dreistufige Farm enthält Datenbank-, Anwendungs- und Webebenen. Das [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] hinzufügen zu dieser Topologie erfordert, dass Sie SQL Server- [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] Setup ausführen, um auf der Anwendungsebene zu installieren. Power Pivot-Programmdateien werden der webeebene hinzugefügt, jedoch nur als Task nach der Installation, wenn Sie die Webanwendungslösung bereitstellen. Es gibt Bereitstellungsschritte, jedoch keinen separaten Installationsschritt auf der Webebene oder Datenebene, die Sie ausführen müssen. Der einzige Installationsschritt, den Sie durchführen müssen, [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] ist die Installation von auf den Anwendungsservern.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010|  
  
  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Sie müssen ein lokaler Administrator sein, um SQL Server und SharePoint 2010 zu installieren.  
  
 Die Person, die SharePoint installiert, muss auch die Farm konfigurieren. Sie müssen über eine SQL Server-Anmeldung auf dem Datenbankserver verfügen, um die Farm zu konfigurieren. Die Anmeldung muss den folgenden Rollen zugewiesen werden: `dbcreator`, `securityadmin` und `public`.  
  
 Sie müssen über die Enterprise oder Enterprise Evaluation Edition von SharePoint Server 2010 verfügen.  
  
 Der Computer muss einer Domäne hinzugefügt werden.  
  
 Sie müssen wissen, mit welchen Konten die Datenbank-Engine, die Dienste in der Farm und Analysis Services im integrierten SharePoint-Modus ausgeführt werden. Diese Konten können später geändert werden. Sie müssen sie jedoch bei der Installation angeben.  
  
 Die bei der Installation angegebenen Dienstkonten müssen Domänenbenutzerkonten sein.  
  
 Überprüfen Sie vor der Installation die Browsereinstellungen, um sicherzustellen, dass Sie über eine Internetverbindung verfügen. Über das erforderliche Installationsprogramm wird eine Internetverbindung geöffnet, um die benötigte Software herunterzuladen. Sie sollten die folgenden Änderungen vornehmen, um sicherzustellen, dass die erforderliche Software vollständig verfügbar ist:  
  
-   Deaktivieren Sie in Server-Manager vorübergehend die verstärkte Sicherheitskonfiguration für Internet Explorer, um Downloads auf den Server zuzulassen. Für das Herunterladen der erforderlichen Software können Sie die Option ESC für Administratoren in Internet Explorer deaktivieren.  
  
-   In Internet Explorer müssen Sie möglicherweise den Browser so konfigurieren, dass ein Proxyserver umgangen werden kann, um den localhost-Zugriff auf URLs im Internet zuzulassen.  
  
    1.  Klicken Sie in Internet Explorer im Menü Extras auf Internetoptionen.  
  
    2.  Klicken Sie auf der Registerkarte Verbindungen im Bereich LAN-Einstellungen auf LAN-Einstellungen.  
  
    3.  Deaktivieren Sie im Bereich Automatische Konfiguration das Kontrollkästchen Automatische Suche der Einstellungen.  
  
    4.  Wählen Sie im Bereich Proxyserver das Kontrollkästchen Proxyserver für LAN verwenden aus.  
  
    5.  Geben Sie die Adresse des Proxyservers in das Feld Adresse ein.  
  
    6.  Geben Sie die Portnummer des Proxyservers in das Feld  ein.  
  
    7.  Aktivieren Sie das Kontrollkästchen Proxyserver für lokale Adressen umgehen.  
  
    8.  Klicken Sie auf OK, um das Dialogfeld LAN-Einstellungen zu schließen.  
  
    9. Klicken Sie auf OK, um das Dialogfeld Internetoptionen zu schließen.  
  
##  <a name="installdb"></a>Installieren eines Datenbankservers  
 In diesem Thema wird davon ausgegangen, dass die Farm Topologie auf der basiert, die im Artikel [mehrere Server für eine dreistufige Farm](https://go.microsoft.com/fwlink/?LinkId=182771)beschrieben wird. Wenn Sie bereits über eine operative Farm verfügen, fahren Sie mit [Installieren von PowerPivot für SharePoint](#installppapp)fort.  
  
 Wenn Sie mit der Topologie noch am Anfang stehen, beginnen Sie, indem Sie eine SQL Server-Datenbank-Engine installieren. Wenn Sie diese Anweisungen ausführen, erhalten Sie einen Datenbankserver, auf den die Benutzer von den SharePoint-Servern in der Farm zugreifen können.  
  
1.  Führen Sie auf dem Computer, den Sie für den Datenbankserver verwenden, SQL Server Setup aus, um SQL Server Datenbank-Engine zu installieren (Weitere Informationen finden Sie unter [Install SQL Server 2014 from the Installation &#40;Wizard Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)).  
  
     Wählen Sie folgende Funktionen aus, die installiert werden sollen:  
  
    -   -Datenbank-Engine-Dienste  
  
    -   Konnektivität der Clienttools  
  
    -   Verwaltungstools - Vollständig (Einfach ist automatisch enthalten)  
  
2.  Aktivieren Sie nach der Installation der Datenbank-Engine TCP/IP für Remoteverbindungen, und starten Sie den Dienst neu:  
  
    1.  Starten Sie den SQL Server-Konfigurations-Manager.  
  
    2.  Öffnen Sie SQL Server-Netzwerkkonfiguration.  
  
    3.  Wählen Sie **Protokolle für MSSQLSERVER**aus.  
  
    4.  Klicken Sie mit der rechten Maustaste auf **TCP/IP** , und wählen Sie **aktivieren**  
  
    5.  Klicken Sie auf **SQL Server Dienste**.  
  
    6.  Klicken Sie mit der rechten Maustaste auf **SQL Server (MSSQLSERVER)** , und klicken Sie auf **neu starten**.  
  
3.  Aktivieren Sie den eingehenden Zugriff auf den Datenbankserver durch die Windows-Firewall. Auf diese Weise können die SharePoint-Server in der Farm eine Verbindung mit den SharePoint-Datenbanken herstellen. Weitere Informationen finden Sie unter [Konfigurieren der Windows-Firewall für den SQL Server-Zugriff](../../../2014/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access.md).  
  
    1.  Klicken Sie in der Windows-Systemsteuerung unter Verwaltung auf **Windows-Firewall mit**erweiterter Sicherheit.  
  
    2.  Klicken Sie auf **Eingehende Regeln**.  
  
    3.  Klicken Sie auf **neue Regel**.  
  
    4.  Klicken Sie unter Regeltyp auf **Benutzer**definiert.  
  
    5.  Klicken Sie auf **Weiter**.  
  
    6.  Klicken Sie Unterprogramm im Abschnitt Dienste auf **Anpassen**.  
  
    7.  Klicken Sie **auf auf diesen Dienst anwenden**.  
  
    8.  Wählen Sie **SQL Server (MSSQLSERVER)** aus, wenn Sie SQL Server als Standard Instanz installiert haben, und klicken Sie dann auf **OK**.  
  
    9. Klicken Sie auf **Weiter**.  
  
    10. Übernehmen Sie unter Protokoll und Ports die Standardeinstellungen, und klicken Sie auf **weiter**.  
  
    11. Übernehmen Sie Unterbereich die Standardeinstellungen, und klicken Sie auf **weiter**.  
  
    12. Übernehmen Sie in Aktion die Standardeinstellungen, und klicken Sie auf **weiter**.  
  
    13. Deaktivieren Sie unter Profil die Kontrollkästchen **Privat** und **öffentlich**, und klicken Sie dann auf **weiter**.  
  
    14. Geben Sie unter Name einen beschreibenden Namen für die eingehende Regel ein (z. b. **SQL Server**).  
  
    15. Klicken Sie auf **Fertig stellen**.  
  
##  <a name="installsp"></a>Installieren und Konfigurieren einer dreistufigen SharePoint 2010-Farm  
 Führen Sie auf allen Computern, die als SharePoint-Server dienen sollen, das erforderliche SharePoint-Installationsprogramm und danach das SharePoint Server-Setup aus.  
  
 Verwenden Sie die folgenden Anweisungen in der SharePoint 2010-Dokumentation zur Installation und Konfiguration einer SharePoint 2010-Farm mit zwei Webservern und einem Anwendungsserver:  
  
 [Mehrere Server für eine dreistufige Farm (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?LinkId=182771)  
  
 Wenn Sie zur Angabe eines Datenbankservers aufgefordert werden, geben Sie den Datenbankserver an, den Sie zuvor installiert haben.  
  
 Bei den folgenden Schritten wird davon ausgegangen, dass die Farm mithilfe der Anweisungen für das Setup einer dreistufigen Farm konfiguriert wurde. Die Farm sollte die folgenden Dienste und Funktionen einschließen:  
  
-   Excel Services, Suchdienst und Secure Store Service  
  
-   Eine Webanwendung und eine Websitesammlung  
  
-   Nutzungs- und Zustandsdatensammlung  
  
-   Diagnoseprotokollierung  
  
##  <a name="installppapp"></a>Installieren von PowerPivot für SharePoint auf einem Anwendungsserver  
 Führen Sie SQL Server-Setup aus, um einer SharePoint-Farm PowerPivot für SharePoint hinzuzufügen. Wenn die Farm aus mehreren SharePoint-Servern besteht, müssen Sie SQL Server-Setup auf einem Anwendungsserver ausführen, der der Farm bereits hinzugefügt wurde.  
  
 Installieren Sie PowerPivot für SharePoint immer auf einem Anwendungsserver. Obwohl die Web-Front-End-Server auch PowerPivot für SharePoint-Server-Komponenten ausführen, werden Komponenten, die auf dem Web-Front-End ausgeführt werden, während des PowerPivot für SharePoint-Konfigurationsschritts installiert, wenn Sie Lösungen in der Farm bereitstellen. Weitere Informationen zum Setup finden Sie unter [Install PowerPivot für SharePoint 2010](../../../2014/sql-server/install/install-powerpivot-for-sharepoint-2010.md).  
  
 Wenn die Bereitstellungstopologie zwei PowerPivot für SharePoint-Instanzen erfordert, führen Sie SQL Server-Setup auf jedem Anwendungsserver aus. Es kann nur eine Instanz von PowerPivot für SharePoint auf einem einzelnen Computer vorhanden sein. Wenn Sie mehrere Instanzen benötigen, müssen Sie zusätzliche Server verwenden. Weitere Informationen zum Hinzufügen mehrerer PowerPivot für SharePoint Server zur gleichen Farm finden [Sie unter Deployment Checkliste: Horizontales Skalieren durch Hinzufügen von Power Pivot-Servern zu einer](../../../2014/sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md)SharePoint 2010-Farm.  
  
##  <a name="installclientlib"></a>Installieren Sie Analysis Services Client Bibliotheken auf SharePoint-Anwendungsservern, die nicht über eine Installation von verfügen PowerPivot für SharePoint  
 In einer Farmtopologie, die ein Web-Front-End oder einen Anwendungsserver umfasst, auf denen die folgenden Anwendungen ausgeführt werden, ohne dass PowerPivot für SharePoint auf dem gleichen Computer installiert ist, wird zur Unterstützung von PowerPivot-Datenzugriff und -Funktionen zusätzliche Software benötigt:  
  
-   Excel-Dienste oder PerformancePoint-Dienste  
  
-   Zentraladministration, die als eigenständige Anwendung auf einem eigenen Server ausgeführt wird  
  
 Sowohl für Excel-Dienste als auch für PerformancePoint-Dienste wird zur Unterstützung des PowerPivot-Datenzugriffs eine neuere Version des OLE DB-Anbieter für Analysis Services benötigt. Wenn Sie eine dieser Anwendungen auf einem Computer ausführen, auf dem nicht der neueste OLE DB-Anbieter vorhanden ist, müssen Sie diesen Anbieter manuell installieren. Weitere Informationen finden Sie unter [install the Analysis Services OLE DB-Anbieter on SharePoint Servers](../../../2014/sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)  
  
 Ähnlich gilt: Ein Computer, der nur über die Zentraladministration verfügt, ohne dass PowerPivot für SharePoint auf eben diesem Computer installiert ist, benötigt die ADOMD.NET-Clientbibliothek. Diese Bibliothek wird vom PowerPivot-Management-Dashboard für den Zugriff auf interne Daten zum Auffüllen des Dashboards verwendet. Weitere Informationen finden Sie unter [Installieren von ADOMD.NET auf Web-Front-End-Servern, auf denen die Zentraladministration ausgeführt wird](../../../2014/sql-server/install/install-adomd-net-on-web-front-end-servers-running-central-administration.md).  
  
##  <a name="configsrvr"></a>Konfigurieren des Servers  
 Verwenden Sie das PowerPivot-Konfigurationstool zum Konfigurieren von PowerPivot für SharePoint. Das Tool scannt die vorhandene Konfiguration der Farm und bietet Optionen für die Installation oder Aktivierung der SharePoint-Funktionen, die von PowerPivot für SharePoint benötigt werden. Während dieses Schritts wird der Claims to Windows Token Service gestartet. Wurden darüber hinaus andere erforderliche SharePoint-Funktionen noch nicht aktiviert, fügt das Konfigurationstool diese der Liste hinzu und schließt Aktionen zu ihrer Aktivierung ein.  
  
 Weitere Informationen finden Sie unter [konfigurieren oder reparieren PowerPivot für SharePoint 2010 &#40;Power Pivot-Konfigurations&#41;Tools](../../../2014/analysis-services/configure-repair-powerpivot-sharepoint-2010.md).  
  
##  <a name="AAM"></a>Konfigurieren einer alternativen Zugriffs Zuordnung für Web-Front-End-Server  
 Um sicherzustellen, dass Anforderungen für den PowerPivot-Datenzugriff oder die Datenaktualisierung von den einzelnen Web-Front-End-Servern behandelt werden, müssen Sie die verschiedenen URLs der einzelnen Server derselben Webanwendung zuordnen.  
  
1.  Klicken Sie in der zentral Administration unter Anwendungs Verwaltung auf **Alternative Zugriffs Zuordnungen konfigurieren**.  
  
2.  Wählen Sie unter Alternative Zugriffszuordnungssammlung die Webanwendung aus.  
  
3.  Klicken Sie auf **interne URL hinzufügen**.  
  
4.  Geben Sie die URL des ersten Web-Front-End-Servers an.  
  
5.  Wiederholen Sie diese Schritte, um die URL des zweiten Web-Front-End-Servers hinzuzufügen.  
  
##  <a name="activatePP"></a>Aktivieren der Power Pivot-Funktions Integration für Website Sammlungen  
 Die Funktionsaktivierung auf der Ebene der Websitesammlung stellt Anwendungsseiten und Vorlagen zur Verfügung, z. B. Konfigurationsseiten für geplante Datenaktualisierungen und Anwendungsseiten für den PowerPivot-Katalog und Datenfeedbibliotheken.  
  
 Das PowerPivot-Konfigurationstool aktiviert Funktionsintegration für die von Ihnen angegebene Websitesammlung. Sie können das Tool mehrmals ausführen, um zusätzliche Websitesammlungen auszuwählen. Alternativ können Websiteadministratoren Funktionsaktivierung von innerhalb SharePoint konfigurieren. Weitere Informationen finden Sie unter [Aktivieren der Power Pivot-Funktions Integration für Website Sammlungen in der zentral Administration](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/activate-power-pivot-integration-for-site-collections-in-ca).  
  
##  <a name="verify"></a>Überprüfen der Integration und Serververfügbarkeit  
 Die PowerPivot-Abfrageverarbeitung in der Farm tritt auf, wenn ein Benutzer oder eine Anwendung eine Excel-Arbeitsmappe öffnet, die PowerPivot-Daten enthält. Sie können Seiten auf SharePoint-Sites kontrollieren, um zu überprüfen, ob PowerPivot-Funktionen verfügbar sind. Um jedoch eine Installation vollständig zu überprüfen, müssen Sie eine PowerPivot-Arbeitsmappe haben, die Sie in SharePoint veröffentlichen können und auf die Sie über eine Bibliothek zugreifen können. Zu Testzwecken können Sie eine Beispielarbeitsmappe veröffentlichen, die bereits PowerPivot-Daten enthält, und damit überprüfen, ob die SharePoint-Integration ordnungsgemäß konfiguriert wurde.  
  
 Um die PowerPivot-Integration in eine SharePoint-Website zu überprüfen, gehen Sie wie folgt vor:  
  
1.  Öffnen Sie in einem Browser die Webanwendung, die Sie erstellt haben. Wenn Sie Standardwerte verwendet haben, können Sie http://\<Ihren Computernamen in der URL-Adresse > angeben.  
  
2.  Überprüfen Sie, ob der PowerPivot-Datenzugriff und die Verarbeitungsfunktionen in der Anwendung verfügbar sind. Überprüfen Sie hierzu das Vorhandensein von durch PowerPivot bereitgestellte Bibliotheksvorlagen:  
  
    1.  Klicken Sie unter Website Aktionen auf **Weitere Optionen..** .  
  
    2.  In Bibliotheken sollten die **datenfeedbibliothek** und der **Power Pivot**-Katalog angezeigt werden. Diese Bibliotheksvorlagen werden von der PowerPivot-Funktion bereitgestellt und sind in der Bibliothekenliste sichtbar, falls die Funktion ordnungsgemäß integriert wurde.  
  
 Um den PowerPivot-Datenzugriff auf dem Server zu überprüfen, gehen Sie wie folgt vor:  
  
1.  [Laden Sie das Datenbeispiel „Picnic“ herunter](https://go.microsoft.com/fwlink/?LinkID=219108) , das zu einem Reporting Services-Tutorial gehört. Sie verwenden die Beispielarbeitsmappe in diesem Download, um den PowerPivot-Datenzugriff zu überprüfen. Extrahieren Sie die Dateien.  
  
2.  Laden Sie eine PowerPivot-Arbeitsmappe in den PowerPivot-Katalog oder in eine beliebige SharePoint-Bibliothek hoch.  
  
3.  Klicken Sie auf das Dokument, um es von der Bibliothek aus zu öffnen.  
  
4.  Klicken Sie auf einen Slicer, oder filtern Sie die Daten, um eine PowerPivot-Abfrage zu starten. Der Server lädt PowerPivot-Daten im Hintergrund und gibt die Ergebnisse zurück. Im nächsten Schritt stellen Sie eine Verbindung mit dem Server her, um zu überprüfen, ob die Daten geladen und zwischengespeichert wurden.  
  
5.  Starten Sie SQL Server Management Studio im Startmenü in der Programmgruppe Microsoft SQL Server 2008 R2. Wenn dieses Tool nicht auf dem Server installiert ist, können Sie mit dem letzten Schritt fortfahren, um das Vorhandensein zwischengespeicherter Dateien zu bestätigen.  
  
6.  Wählen Sie unter Servertyp die Option **Analysis Services**aus.  
  
7.  Geben Sie  **\<**  **\<unter Servername den Namen Servername > \powerpivot**ein, wobei Servername > der Name des Computers ist, auf dem sich die PowerPivot für SharePoint Installation befindet.  
  
8.  Klicken Sie auf **Verbinden**.  
  
9. Klicken Sie in Objekt-Explorer auf **Datenbanken** , um die Liste der Power Pivot-Datendateien anzuzeigen, die geladen werden.  
  
10. Überprüfen Sie im Computerdateisystem den folgenden Ordner, um zu bestimmen, ob Dateien auf dem Datenträger zwischengespeichert wurden. Das Vorhandensein zwischengespeicherter Dateien ist eine weitere Bestätigung, dass die Bereitstellung betriebsbereit ist. Um den Dateicache anzuzeigen, wechseln Sie zum Ordner \Programme\Microsoft SQL Server\MSAS10_50.POWERPIVOT\OLAP\Backup.  
  
##  <a name="nextsteps"></a>Schritte nach der Installation  
 Nachdem Sie die Installation überprüft haben, beenden Sie die Dienstkonfiguration durch das Erstellen eines PowerPivot-Katalogs oder durch Anpassen einzelner Konfigurationseinstellungen. Um die Serverkomponenten, die Sie gerade installiert haben, vollständig zu nutzen, können Sie [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] herunterladen und dann Ihre erste PowerPivot-Arbeitsmappe erstellen und veröffentlichen.  
  
####  <a name="bkmk_disk"></a>Festlegen der Obergrenze für die Speicherplatz Verwendung  
 Sie können eine maximale Grenze festlegen, wie viel Speicherplatz für PowerPivot-Datendateien verwendet wird, die auf dem Datenträger zwischengespeichert werden. Standardmäßig wird der gesamte verfügbare Speicherplatz verwendet. Anweisungen zum Einschränken der Speicherplatz Nutzung finden Sie unter [Konfigurieren der Speicherplatz Verwendung &#40;PowerPivot für SharePoint&#41;](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-disk-space-usage-power-pivot-for-sharepoint).  
  
####  <a name="Upload"></a>Vergrößern der maximalen Uploadgröße für SharePoint-Webanwendungen  
 Da PowerPivot-Arbeitsmappen sehr groß werden können, kann es sinnvoll sein, die maximale Dateiuploadgröße zu erhöhen. Es gibt zwei Einstellungen für die Dateigröße, die konfiguriert werden müssen: Maximale Uploadgröße für die Webanwendung und maximale Arbeitsmappengröße in Excel Services. Die maximale Dateigröße sollte in beiden Anwendungen auf den gleichen Wert festgelegt werden. Anweisungen finden Sie unter [Konfigurieren der maximalen &#40;Dateiuploadgröße PowerPivot für SharePoint&#41;](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-maximum-file-upload-size-power-pivot-for-sharepoint).  
  
#### <a name="grant-sharepoint-permissions-to-workbook-users"></a>Gewähren von SharePoint-Berechtigungen für Arbeitsmappenbenutzer  
 Benutzer benötigen SharePoint-Berechtigungen, bevor sie Arbeitsmappen veröffentlichen oder anzeigen können. Stellen Sie sicher, dass Sie Benutzern, die veröffentlichte Arbeitsmappen anzeigen müssen, Berechtigungen **anzeigen** gewähren und Benutzern, die Arbeitsmappen veröffentlichen oder verwalten, Berechtigungen **leisten** . Sie müssen Websitesammlungsadministrator sein, um Berechtigungen erteilen zu können.  
  
1.  Klicken Sie in der Website auf **Website Aktionen**.  
  
2.  Klicken Sie auf **Website Berechtigungen**.  
  
3.  Aktivieren Sie das Kontrollkästchen für die Gruppe Website Sammlungs **Mitglieder** .  
  
4.  Klicken Sie im Menüband auf **Berechtigungen erteilen**.  
  
5.  Geben Sie die Windows-Domänenbenutzerkonten oder -Gruppenkonten ein, die über die Berechtigung zum Hinzufügen oder Entfernen von Dokumenten verfügen sollen.  
  
6.  Klicken Sie auf **OK**.  
  
7.  Aktivieren Sie das Kontrollkästchen für die Gruppe **Besucher** der Website Sammlung.  
  
8.  Klicken Sie im Menüband auf **Berechtigungen erteilen**.  
  
9. Geben Sie die Windows-Domänenbenutzerkonten oder -Gruppenkonten ein, die über die Berechtigung zum Anzeigen von Dokumenten verfügen sollen. Verwenden Sie wie zuvor keine E-Mail-Adressen bzw. keine Verteilergruppe, wenn die Anwendung für die klassische Authentifizierung konfiguriert wurde.  
  
10. Klicken Sie auf **OK**.  
  
#### <a name="install-adonet-data-services-35-sp1"></a>Installieren von ADO.NET Data Services 3.5 SP1  
 ADO.NET Data Services sind für einen Datenfeedexport von SharePoint-Listen erforderlich. Da diese Komponente nicht im Programm PrerequisiteInstaller von SharePoint 2010 enthalten ist, müssen Sie sie manuell installieren. Weitere Informationen zum Installieren von ADO.NET Data Services finden [Sie unter Install ADO.NET Data Services to Support Data Feed Exports of SharePoint Lists](../../../2014/sql-server/install/install-ado-net-data-services-to-support-data-feed-exports-of-sharepoint-lists.md).  
  
#### <a name="install-data-providers-used-in-data-refresh-and-check-user-permissions"></a>Installieren von in der Datenaktualisierung verwendeten Datenanbietern und Überprüfen von Benutzerberechtigungen  
 Die serverseitige Datenaktualisierung ermöglicht Benutzern das erneute Importieren aktualisierter Daten in ihre Arbeitsmappen in unbeaufsichtigtem Modus. Für die erfolgreiche Ausführung der Datenaktualisierung muss auf dem Server der gleiche Datenanbieter wie für den ursprünglichen Import der Daten vorhanden sein. Darüber hinaus sind für das Benutzerkonto, unter dem die Datenaktualisierung ausgeführt wird, oft Leseberechtigungen für die externen Datenquellen erforderlich. Überprüfen Sie die Anforderungen für das Aktivieren und Konfigurieren der Datenaktualisierung, um ein erfolgreiches Ergebnis sicherzustellen. Weitere Informationen finden Sie unter [Power Pivot-Datenaktualisierung mit SharePoint 2010](../../../2014/analysis-services/powerpivot-data-refresh-with-sharepoint-2010.md).  
  
#### <a name="create-a-powerpivot-gallery"></a>Erstellen eines PowerPivot-Katalogs  
 Der PowerPivot-Katalog ist eine Bibliothek, die Vorschau- und Präsentationsoptionen zum Anzeigen von PowerPivot-Arbeitsmappen auf einer SharePoint-Website enthält. Das Verwenden des PowerPivot-Katalogs zum Veröffentlichen und Anzeigen von PowerPivot-Arbeitsmappen wird für die Vorschaufunktion empfohlen. Wenn Sie überdies auch Reporting Services auf dem gleichen SharePoint-Server bereitgestellt haben, bietet ein PowerPivot-Katalog Benutzerfreundlichkeit beim Erstellen von Berichten. Sie können den Berichts-Generator innerhalb des PowerPivot-Katalogs starten, um als Grundlage für einen neuen Bericht eine veröffentlichte PowerPivot-Arbeitsmappe zu verwenden. Weitere Informationen zum Erstellen und Verwenden der Bibliothek finden Sie unter [Erstellen und Anpassen des Power Pivot](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/create-and-customize-power-pivot-gallery) -Katalogs und [Verwenden des Power Pivot](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/use-power-pivot-gallery)-Katalogs.  
  
#### <a name="tune-configuration-settings"></a>Optimieren von Konfigurationseinstellungen  
 Eine PowerPivot-Dienstanwendung wird mit Standardeigenschaften und -werten erstellt. Sie können Konfigurationseinstellungen für einzelne Dienstanwendungen ändern, um die Methodik zu ändern, anhand der die Anforderungen zugeordnet werden. Außerdem können Sie Servertimeouts festlegen, die Schwellenwerte für Abfrageantwortberichtsereignisse ändern oder festlegen, wie lange die Verwendungsdaten beibehalten werden sollen. Weitere Informationen zur Konfiguration in der zentral Administration oder zum Verwenden von Power Pivot-Funktionen in SharePoint-Webanwendungen finden Sie unter [Power Pivot-Server Verwaltung und-Konfiguration in der zentral Administration](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration).  
  
## <a name="see-also"></a>Siehe auch  
 [Von den-Editionen unterstützte Funktionen SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473)   
 [Installieren von PowerPivot für SharePoint 2010](../../../2014/sql-server/install/install-powerpivot-for-sharepoint-2010.md)   
 [Bereitstellungs Checkliste: Horizontales Skalieren durch Hinzufügen von Power Pivot-Servern zu einer SharePoint 2010-Farm](../../../2014/sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md)  
  
  
