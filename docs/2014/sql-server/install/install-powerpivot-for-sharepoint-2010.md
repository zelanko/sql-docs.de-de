---
title: Installieren von PowerPivot für SharePoint 2010 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: eec38696-5e26-46fa-bc83-aa776f470ce8
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 4eab56329c2b51f792394ffc37921e8a1ed8e117
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "71952253"
---
# <a name="install-powerpivot-for-sharepoint-2010"></a>Installieren von PowerPivot für SharePoint 2010
  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] umfasst Dienste der mittleren Ebene sowie Back-End-Dienste, die den PowerPivot-Datenzugriff in einer SharePoint 2010-Farm ermöglichen. Falls Ihre Organisation die Clientanwendung [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für Excel 2010 zum Erstellen von Arbeitsmappen mit analytischen Daten nutzt, benötigen Sie [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], um in einer Serverumgebung auf diese Daten zuzugreifen. In diesem Thema wird der grundlegende Installationsvorgang erläutert. Zusätzlich enthält es Links zu weiteren Themen, die Sie bei der Konfiguration von PowerPivot unterstützen.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010|  
  
 
  
 Anweisungen zum Installieren von [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] und [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] auf demselben Server finden Sie unter [Deployment Checkliste: Reporting Services, Power View und PowerPivot für SharePoint](deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md).  
  
## <a name="prerequisites"></a>Prerequisites  
  
1.  Sie müssen lokaler Administrator sein, um SQL Server-Setup auszuführen.  
  
2.  SharePoint Server 2010 Enterprise Edition ist erforderlich für [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]. Sie können auch die Evaluation Enterprise Edition verwenden.  
  
3.  SharePoint Server 2010 SP2 muss installiert sein. Ist dies nicht der Fall, können Sie die Farm nicht konfigurieren, um [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Funktionen zu verwenden.  
  
4.  Der Computer muss einer Domäne hinzugefügt werden.  
  
5.  Sie müssen ein Domänenbenutzerkonto besitzen, um [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bereitzustellen. In einer [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]-Installation muss das Analysis Services-Dienstkonto einem Domänenbenutzerkonto entsprechen, damit Sie es über die Zentraladministration verwalten können. Sie müssen das Konto und die Anmelde Informationen im Rahmen der Schritte in diesem Dokument auf der Seite **Server Konfiguration** eingeben.  
  
6.  Der Name der [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Instanz muss verfügbar sein. Es darf keine benannte [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Instanz auf dem Computer vorhanden sein, auf dem Sie PowerPivot für SharePoint installieren.  
  
7.  Die [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]-Instanz darf nicht Teil eines SQL Server-Failoverclusters sein. Verwenden Sie die Hochverfügbarkeitsfunktionen des SharePoint-Produkts. Der Lastenausgleich unter PowerPivot für SharePoint-Servern wird beispielsweise von Excel Services verwaltet. Weitere Informationen finden Sie unter [Verwalten von Einstellungen für das Excel Services-Datenmodell (SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780.aspx) (https://technet.microsoft.com/library/jj219780.aspx).  
  
8.  Wenn Sie [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] auf einer vorhandenen Farm installieren, benötigen Sie mindestens eine SharePoint-Webanwendung, die für die Authentifizierung im klassischen Modus konfiguriert ist. Der [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Datenzugriff wird nur unterstützt, wenn die Webanwendung die Authentifizierung im klassischen Modus unterstützt. Weitere Informationen zu den Anforderungen für den klassischen Modus finden Sie unter [Power Pivot-Authentifizierung und-Autorisierung](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-authentication-and-authorization).  
  
9. Überprüfen Sie die folgenden weiteren Themen, um System- und Versionsanforderungen zu verstehen:  
  
    -   [Leitfaden zum Verwenden von SQL Server BI-Features in einer SharePoint 2010-Farm](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
##  <a name="InstallSQL"></a>Schritt 1: Installieren von PowerPivot für SharePoint  
 Im diesem Schritt führen Sie SQL Server-Setup aus, um [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] zu installieren. In einem nachfolgenden Schritt konfigurieren Sie den Server in einem Task nach der Installation.  
  
1.  Legen Sie die Installationsmedien ein, oder öffnen Sie einen Ordner, der die Setup Dateien für SQL Server enthält, und doppelklicken Sie dann auf **Setup. exe**.  
  
2.  Klicken Sie im linken Navigationsbereich auf **Installation** .  
  
3.  Klicken Sie auf **Neue eigenständige SQL Server-Installation oder Hinzufügen von Funktionen zu einer vorhandenen Installation**.  
  
4.  Geben Sie auf der Seite **Product Key** die Evaluation Edition an, oder geben Sie eine Product Key für eine lizenzierte Kopie der Enterprise Edition ein.  
  
     Klicken Sie auf **Weiter**.  
  
5.  Akzeptieren Sie die Microsoft-Software-Lizenzbedingungen. Wir würden uns freuen, wenn Sie zusätzlich das Programm zur Verbesserung der Benutzerfreundlichkeit und die Komponente für Fehlerberichte aktivieren. Klicken Sie auf **Weiter**.  
  
6.  Aktualisieren Sie die Setupdateien, falls Sie dazu aufgefordert werden.  
  
7.  Auf der Seite **Installations Regeln** werden alle Probleme identifiziert, die die Installation von verhindern könnten. Überprüfen Sie die Liste, um zu ermitteln, ob Setup auf dem System potenzielle Probleme erkannt hat.  
  
    > [!NOTE]  
    >  Da die Windows-Firewall aktiviert ist, werden Sie davor gewarnt, Ports zu öffnen, um den Remotezugriff zu ermöglichen. Diese Warnung gilt im Allgemeinen nicht für [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Installationen. Verbindungen mit [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Diensten und -Datendateien werden über die SharePoint-Ports hergestellt, die bereits für die Dienst-zu-Dienst-Kommunikation von SharePoint geöffnet sind.  
  
     Klicken Sie auf **Weiter**. Warten Sie, während SQL Server-Setupprogrammdateien auf dem Server installiert werden.  
  
8.  Wählen Sie auf der Seite **Setuprolle** die Option **SQL Server PowerPivot für SharePoint**aus.  
  
9. Optional können Sie der Installation eine Instanz der Datenbank-Engine hinzufügen. Dies können Sie tun, wenn Sie eine neue Farm einrichten und einen Datenbankserver benötigen, um die Konfigurations-und Inhalts Datenbanken der Farm auszuführen. Wenn Sie die Datenbank-Engine hinzufügen, wird sie als benannte PowerPivot-Instanz installiert. Wenn Sie eine Verbindung mit dieser Instanz angeben müssen (wenn Sie z. b. den Assistenten für die Farm Konfiguration zum Konfigurieren der Farm verwenden), geben Sie den Datenbanknamen im folgenden Format ein: <`servername`> \powerpivot.  
  
     ![GMNI_SetupUI_FeatureRole](../../../2014/sql-server/install/media/gmni-setupui-featurerole.gif "GMNI_SetupUI_FeatureRole")  
  
10. Klicken Sie auf **Weiter**.  
  
11. Auf der Seite **Funktionsauswahl** wird eine schreibgeschützte Liste der Funktionen, die installiert werden, zu Informationszwecken angezeigt. Sie können keine Elemente hinzufügen oder entfernen, die vorab für diese Rolle ausgewählt wurden. Klicken Sie auf **Weiter**.  
  
12. Klicken Sie auf der Seite **Funktions Regeln** auf **weiter**. Die Seite kann übersprungen werden.  
  
13. Auf der Seite **Instanzkonfiguration** wird der schreibgeschützte Instanzname 'PowerPivot' zu Informationszwecken angezeigt. Dieser Instanzname von **Power Pivot** ist **erforderlich und kann nicht geändert werden**. Sie können jedoch eine eindeutige Instanz-ID eingeben, um einen beschreibenden Verzeichnisnamen und Registrierungsschlüssel anzugeben. Klicken Sie auf **Weiter**.  
  
14. Geben Sie auf der Seite **Server Konfiguration** die gewünschten Kontoinformationen ein.  
  
     Für SQL Server Analysis Services müssen Sie ein Domänenbenutzerkonto angeben. Geben Sie kein integriertes Konto an. Domänen Konten sind erforderlich, um das Analysis Services-Dienst Konto als *verwaltetes Konto* in der SharePoint-zentral Administration zu verwalten.  
  
     ![SSAS-Server Konfiguration](../../../2014/sql-server/install/media/ssas-powerpivotsetupsql2012sp1-serverconfiguration.gif "SSAS-Server Konfiguration")  
  
     Wenn Sie die SQL Server-Datenbank-Engine und den SQL Server-Agent hinzugefügt haben, können Sie die Dienste zur Ausführung unter Domänenbenutzerkonten oder unter dem standardmäßigen virtuellen Konto konfigurieren.  
  
     Verwenden Sie niemals Ihr eigenes Domänenbenutzerkonto für die Bereitstellung von Diensten. Dies gewährt dem Server die gleichen Berechtigungen, über die Sie für die Ressourcen im Netzwerk verfügen. Wenn der Server von einem böswilligen Benutzer angegriffen wird, wird dieser Benutzer mit Ihren Domänenanmeldeinformationen angemeldet und kann die gleichen Daten und Anwendungen herunterladen oder nutzen wie Sie.  
  
15. Klicken Sie auf **Weiter**.  
  
16. Wenn Sie die Datenbank-Engine installieren, wird die Datenbank-Engine-Konfigurationsseite angezeigt. Klicken Sie in Datenbank-Engine Konfiguration auf **aktuellen Benutzer hinzufügen** , um Ihrem Benutzerkonto Administrator Berechtigungen für die Datenbank-Engine Instanz zu erteilen. Klicken Sie auf **Hinzufügen** , um zusätzliche Konten hinzuzufügen. Klicken Sie auf **Weiter**.  
  
17. Klicken Sie auf der Seite **Analysis Services-Konfiguration** auf **Aktuellen Benutzer hinzufügen** , um Ihrem Benutzerkonto Administratorberechtigungen zu gewähren. Sie benötigen die Administratorberechtigung, um den Server nach Abschluss von Setup zu konfigurieren.  
  
18. Fügen Sie auf derselben Seite das Windows-Benutzerkonto einer Person hinzu, die ebenfalls Administratorberechtigungen benötigt. Jeder Benutzer, der in SQL Server Management Studio eine Verbindung mit der [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)]-Instanz herstellen möchte, um Datenbankverbindungsprobleme zu beheben oder Versionsinformationen abzurufen, muss beispielsweise über Systemadministratorberechtigungen für den Server verfügen. Fügen Sie das Benutzerkonto einer Person hinzu, die möglicherweise jetzt die Problembehandlung oder Verwaltung des Servers ausführen möchte.  
  
19. Klicken Sie auf **Weiter**.  
  
20. Klicken Sie auf jeder der verbleibenden Seiten so lange auf **weiter** , bis Sie zur Seite Installations bereit gelangen.  
  
21. Klicken Sie auf **Installieren**.  
  
> [!TIP]  
>  Wenn Sie Probleme mit der SQL Server Installation beheben müssen, finden Sie weitere Informationen unter [anzeigen und lesen SQL Server Setup-Protokolldateien](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).  
  
##  <a name="bkmk_config"></a>Schritt 2: Konfigurieren des Servers  
  
> [!IMPORTANT]  
>  SharePoint 2010 SP2 muss installiert sein, bevor Sie [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] oder eine SharePoint-Farm konfigurieren können, die einen [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Datenbankserver verwendet. Wenn Sie das Service Pack noch nicht installiert haben, holen Sie dies jetzt nach, bevor Sie mit der Serverkonfiguration beginnen.  
  
 Die Installation ist erst abgeschlossen, wenn der Server konfiguriert ist. In dieser Version wird die Serverkonfiguration immer im Anschluss an die Installation ausgeführt. Dabei verwenden Sie eine der folgenden Komponenten: [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Konfigurationstool, Zentraladministration oder PowerShell. Wählen Sie eine der folgenden Vorgehensweisen aus, um den Vorgang fortzusetzen:  
  
-   [Konfigurieren oder Reparieren von PowerPivot für SharePoint &#40;2010 Power Pivot-Konfigurations Tool&#41;](../../../2014/analysis-services/configure-repair-powerpivot-sharepoint-2010.md)  
  
-   [PowerPivot-Serververwaltung und -konfiguration in der Zentraladministration](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration)  
  
-   [PowerPivot-Konfiguration mit Windows PowerShell](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell)  
  
 **Verbindung mit der Datenbank-Engine-Instanz wird hergestellt.** Als Sie [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] installiert haben, hatten Sie in SQL Server-Setup die Möglichkeit, der Installation eine Instanz der Datenbank-Engine hinzuzufügen. Möglicherweise haben Sie Ihrer Installation eine Datenbank-Engine-Instanz hinzugefügt, wenn Sie eine neue Farm einrichten und einen Datenbankserver benötigen, um die Konfigurations-und Inhalts Datenbanken der Farm auszuführen. Wenn Sie die Datenbank-Engine hinzugefügt haben, wurde sie als benannte [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Instanz installiert. Wenn Sie eine Verbindung mit dieser Instanz angeben müssen (wenn Sie z. b. den Assistenten für die Farm Konfiguration zum Konfigurieren der Farm verwenden), geben Sie den Datenbanknamen im folgenden Format ein: <`servername`> \powerpivot.  
  
##  <a name="bkmk_redist"></a>Schritt 3: Installieren von Analysis Services OLE DB Anbietern auf Excel Services-Anwendungsservern  
 Zusätzliche Installationsschritte sind erforderlich, wenn Sie Dienste für Excel-Berechnungen und [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] auf separaten Anwendungsservern ausführen. Installieren Sie auf den Anwendungsservern, auf denen Dienste für Excel-Berechnungen ausgeführt werden, die geeignete Version des Analysis Services OLE DB-Anbieters (MSOLAP).  
  
-   Die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Version von MSOLAP ist in SQL Server-Setup enthalten. Folglich muss die MSOLAP-Version aus [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] nur explizit installiert werden, wenn der Anwendungsserver kein PowerPivot-Anwendungsserver ist.  
  
    > [!NOTE]  
    >  Der Anwendungsserver für die Excel-Berechnungs Dienste benötigt außerdem eine Instanz der Datei **Microsoft. AnalysisServices. XMLA. dll** in der globalen Assembly. Zur Installation der DLL-Datei auf dem Anwendungsserver installieren Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Wählen Sie im SQL Server Setup-Assistenten auf der Seite **Funktionsauswahl** die Option Verwaltungs Tools-fertig aus.  
  
-   Wenn der Anwendungsserver ältere [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Arbeitsmappen unterstützen soll, müssen Sie die SQL Server 2008 R2-Version von MSOLAP installieren.  
  
 Weitere Informationen zum Installieren des Anbieters, einschließlich der Überprüfungs Schritte, finden Sie unter [install the Analysis Services OLE DB-Anbieter on SharePoint Servers](../../../2014/sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)  
  
##  <a name="bkmk_verify"></a>Schritt 4: Überprüfen der Installation  
 In diesem letzten Schritt überprüfen Sie, ob SharePoint 2010 und [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] voll funktionsfähig sind. Anweisungen hierzu finden Sie unter [Überprüfen einer PowerPivot für SharePoint Installation](https://docs.microsoft.com/analysis-services/instances/install-windows/verify-a-power-pivot-for-sharepoint-installation).  
  
## <a name="see-also"></a>Siehe auch  
 [PowerPivot für SharePoint 2010-Installation](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)   
 [Bereitstellungs Prüfliste: Reporting Services, Power View und PowerPivot für SharePoint](deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md)   
 [Deployment Prüfliste: horizontales Skalieren durch Hinzufügen von Power Pivot-Servern zu einer SharePoint 2010-Farm](../../../2014/sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md)   
 [Bereitstellungs Prüfliste: Multiserverinstallation von PowerPivot für SharePoint 2010](../../../2014/sql-server/install/deployment-checklist-multiserver-installation-powerpivot-sharepoint-2010.md)  
  
  
