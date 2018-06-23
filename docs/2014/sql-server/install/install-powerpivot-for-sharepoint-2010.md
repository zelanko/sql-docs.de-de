---
title: Installieren von PowerPivot für SharePoint 2010 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eec38696-5e26-46fa-bc83-aa776f470ce8
caps.latest.revision: 52
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: c77fa146f7703fb67cf0d1ad5c9aa0c042737976
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36160840"
---
# <a name="install-powerpivot-for-sharepoint-2010"></a>Installieren von PowerPivot für SharePoint 2010
  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] umfasst Dienste der mittleren Ebene sowie Back-End-Dienste, die den PowerPivot-Datenzugriff in einer SharePoint 2010-Farm ermöglichen. Falls Ihre Organisation die Clientanwendung [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] für Excel 2010 zum Erstellen von Arbeitsmappen mit analytischen Daten nutzt, benötigen Sie [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], um in einer Serverumgebung auf diese Daten zuzugreifen. In diesem Thema wird der grundlegende Installationsvorgang erläutert. Zusätzlich enthält es Links zu weiteren Themen, die Sie bei der Konfiguration von PowerPivot unterstützen.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010|  
  
 
  
 Anweisungen zum Installieren von [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] und [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] auf demselben Server finden Sie unter [Bereitstellungsprüfliste: Reporting Services, Power View und PowerPivot für SharePoint](deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
  
1.  Sie müssen lokaler Administrator sein, um SQL Server-Setup auszuführen.  
  
2.  SharePoint Server 2010 Enterprise Edition ist erforderlich für [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]. Sie können auch die Evaluation Enterprise Edition verwenden.  
  
3.  SharePoint Server 2010 SP2 muss installiert sein. Ist dies nicht der Fall, können Sie die Farm nicht konfigurieren, um [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Funktionen zu verwenden.  
  
4.  Der Computer muss einer Domäne hinzugefügt werden.  
  
5.  Sie müssen ein Domänenbenutzerkonto besitzen, um [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] bereitzustellen. In einer [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]-Installation muss das Analysis Services-Dienstkonto einem Domänenbenutzerkonto entsprechen, damit Sie es über die Zentraladministration verwalten können. Sie werden auf das Konto und die Anmeldeinformationen eingeben den **Serverkonfiguration** Seite im Rahmen der Schritte in diesem Dokument.  
  
6.  Der Name der [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Instanz muss verfügbar sein. Es darf keine benannte [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Instanz auf dem Computer vorhanden sein, auf dem Sie PowerPivot für SharePoint installieren.  
  
7.  Die [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]-Instanz darf nicht Teil eines SQL Server-Failoverclusters sein. Verwenden Sie die Hochverfügbarkeitsfunktionen des SharePoint-Produkts. Der Lastenausgleich unter PowerPivot für SharePoint-Servern wird beispielsweise von Excel Services verwaltet. Weitere Informationen finden Sie unter [-modelleinstellungen Verwalten von Excel Services (SharePoint Server 2013)](http://technet.microsoft.com/library/jj219780.aspx) (http://technet.microsoft.com/library/jj219780.aspx).  
  
8.  Wenn Sie [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] auf einer vorhandenen Farm installieren, benötigen Sie mindestens eine SharePoint-Webanwendung, die für die Authentifizierung im klassischen Modus konfiguriert ist. Der [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Datenzugriff wird nur unterstützt, wenn die Webanwendung die Authentifizierung im klassischen Modus unterstützt. Weitere Informationen zu Anforderungen für den klassischen Modus finden Sie unter [PowerPivot Authentication and Authorization](../../analysis-services/power-pivot-sharepoint/power-pivot-authentication-and-authorization.md).  
  
9. Überprüfen Sie die folgenden weiteren Themen, um System- und Versionsanforderungen zu verstehen:  
  
    -   [Leitfaden zum Verwenden von SQL Server BI-Features in einer SharePoint 2010-Farm](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
##  <a name="InstallSQL"></a> Schritt 1: Installieren von PowerPivot für SharePoint  
 Im diesem Schritt führen Sie SQL Server-Setup aus, um [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] zu installieren. In einem nachfolgenden Schritt konfigurieren Sie den Server in einem Task nach der Installation.  
  
1.  Legen Sie das Installationsmedium, oder öffnen Sie einen Ordner, der die Setupdateien für SQL Server enthält, und doppelklicken Sie dann auf **setup.exe**.  
  
2.  Klicken Sie auf **Installation** im linken Navigationsbereich.  
  
3.  Klicken Sie auf **Neue eigenständige SQL Server-Installation oder Hinzufügen von Funktionen zu einer vorhandenen Installation**.  
  
4.  Auf der **Product Key** Seite, geben Sie die Evaluation Edition aus, oder geben Sie einen Product Key für eine lizenzierte Kopie der Enterprise Edition.  
  
     Klicken Sie auf **Weiter**.  
  
5.  Akzeptieren Sie die Microsoft-Software-Lizenzbedingungen. Wir würden uns freuen, wenn Sie zusätzlich das Programm zur Verbesserung der Benutzerfreundlichkeit und die Komponente für Fehlerberichte aktivieren. Klicken Sie auf **Weiter**.  
  
6.  Aktualisieren Sie die Setupdateien, falls Sie dazu aufgefordert werden.  
  
7.  Auf der **Installationsregeln** Seite Setup identifiziert Probleme, die Installation möglicherweise verhindern. Überprüfen Sie die Liste, um zu ermitteln, ob Setup auf dem System potenzielle Probleme erkannt hat.  
  
    > [!NOTE]  
    >  Da die Windows-Firewall aktiviert ist, werden Sie davor gewarnt, Ports zu öffnen, um den Remotezugriff zu ermöglichen. Diese Warnung gilt im Allgemeinen nicht für [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Installationen. Verbindungen mit [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Diensten und -Datendateien werden über die SharePoint-Ports hergestellt, die bereits für die Dienst-zu-Dienst-Kommunikation von SharePoint geöffnet sind.  
  
     Klicken Sie auf **Weiter**. Warten Sie, während SQL Server-Setupprogrammdateien auf dem Server installiert werden.  
  
8.  Wählen Sie auf der Seite **Setuprolle** die Option **SQL Server PowerPivot für SharePoint**aus.  
  
9. Optional können Sie der Installation eine Instanz der Datenbank-Engine hinzufügen. Sie können so vorgehen, wenn Sie eine neue Farm einrichten und einen Datenbankserver benötigen, um die Konfiguration und die Inhaltsdatenbanken der Farm auszuführen. Wenn Sie die Datenbank-Engine hinzufügen, wird sie als benannte PowerPivot-Instanz installiert. Wenn Sie müssen eine Verbindung mit dieser Instanz (z. B. im Assistenten für die Farmkonfiguration Wenn Sie diese Assistenten zum Konfigurieren der Farm verwenden), geben Sie den Datenbanknamen im folgenden Format angeben: <`servername`> \PowerPivot.  
  
     ![GMNI_SetupUI_FeatureRole](../../../2014/sql-server/install/media/gmni-setupui-featurerole.gif "GMNI_SetupUI_FeatureRole")  
  
10. Klicken Sie auf **Weiter**.  
  
11. Auf der **Funktionsauswahl** Seite, eine schreibgeschützte Liste der Funktionen, die zu installierenden wird zu Informationszwecken angezeigt. Sie können keine Elemente hinzufügen oder entfernen, die vorab für diese Rolle ausgewählt wurden. Klicken Sie auf **Weiter**.  
  
12. Auf der **Funktionsregeln** auf **Weiter**. Die Seite kann übersprungen werden.  
  
13. Auf der Seite **Instanzkonfiguration** wird der schreibgeschützte Instanzname 'PowerPivot' zu Informationszwecken angezeigt. Dieser Instanzname von **POWERPIVOT** ist **erforderlich und kann nicht geändert werden**. Sie können jedoch eine eindeutige Instanz-ID eingeben, um einen beschreibenden Verzeichnisnamen und Registrierungsschlüssel anzugeben. Klicken Sie auf **Weiter**.  
  
14. Auf der **Serverkonfiguration** Seite, und geben Sie die gewünschten Kontoinformationen.  
  
     Für SQL Server Analysis Services müssen Sie ein Domänenbenutzerkonto angeben. Geben Sie kein integriertes Konto an. Domänenkonten sind erforderlich für die Verwaltung von der Analysis Services-Dienstkonto als ein *verwaltetes Konto* in SharePoint-Zentraladministration.  
  
     ![SSAS-Serverkonfiguration](../../../2014/sql-server/install/media/ssas-powerpivotsetupsql2012sp1-serverconfiguration.gif "SSAS-Serverkonfiguration")  
  
     Wenn Sie die SQL Server-Datenbank-Engine und den SQL Server-Agent hinzugefügt haben, können Sie die Dienste zur Ausführung unter Domänenbenutzerkonten oder unter dem standardmäßigen virtuellen Konto konfigurieren.  
  
     Verwenden Sie niemals Ihr eigenes Domänenbenutzerkonto für die Bereitstellung von Diensten. Dies gewährt dem Server die gleichen Berechtigungen, über die Sie für die Ressourcen im Netzwerk verfügen. Wenn der Server von einem böswilligen Benutzer angegriffen wird, wird dieser Benutzer mit Ihren Domänenanmeldeinformationen angemeldet und kann die gleichen Daten und Anwendungen herunterladen oder nutzen wie Sie.  
  
15. Klicken Sie auf **Weiter**.  
  
16. Wenn Sie die Datenbank-Engine installieren, wird die Datenbank-Engine-Konfigurationsseite angezeigt. Klicken Sie in Datenbankmodulkonfiguration auf **aktuellen Benutzer hinzufügen** zu Ihrem Benutzerkonto Administratorberechtigungen für die Datenbankmodulinstanz zu gewähren. Klicken Sie auf **hinzufügen** zusätzliche Konten hinzufügen. Klicken Sie auf **Weiter**.  
  
17. Klicken Sie auf der Seite **Analysis Services-Konfiguration** auf **Aktuellen Benutzer hinzufügen** , um Ihrem Benutzerkonto Administratorberechtigungen zu gewähren. Sie benötigen die Administratorberechtigung, um den Server nach Abschluss von Setup zu konfigurieren.  
  
18. Fügen Sie auf derselben Seite das Windows-Benutzerkonto einer Person hinzu, die ebenfalls Administratorberechtigungen benötigt. Jeder Benutzer, der in SQL Server Management Studio eine Verbindung mit der [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)]-Instanz herstellen möchte, um Datenbankverbindungsprobleme zu beheben oder Versionsinformationen abzurufen, muss beispielsweise über Systemadministratorberechtigungen für den Server verfügen. Fügen Sie das Benutzerkonto einer Person hinzu, die möglicherweise jetzt die Problembehandlung oder Verwaltung des Servers ausführen möchte.  
  
19. Klicken Sie auf **Weiter**.  
  
20. Klicken Sie auf **Weiter** auf jedem der verbleibenden Seiten, bis Sie auf der Seite Installationsbereit gelangen.  
  
21. Klicken Sie auf **Installieren**.  
  
> [!TIP]  
>  Wenn Sie behandeln müssen Fotografieren von SQL Server-Installation, finden Sie unter [anzeigen und Read SQL Server Setup Log Files](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).  
  
##  <a name="bkmk_config"></a> Schritt 2: Konfigurieren des Servers  
  
> [!IMPORTANT]  
>  SharePoint 2010 SP2 muss installiert sein, bevor Sie [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] oder eine SharePoint-Farm konfigurieren können, die einen [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Datenbankserver verwendet. Wenn Sie das Service Pack noch nicht installiert haben, holen Sie dies jetzt nach, bevor Sie mit der Serverkonfiguration beginnen.  
  
 Die Installation ist erst abgeschlossen, wenn der Server konfiguriert ist. In dieser Version wird die Serverkonfiguration immer im Anschluss an die Installation ausgeführt. Dabei verwenden Sie eine der folgenden Komponenten: [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Konfigurationstool, Zentraladministration oder PowerShell. Wählen Sie eine der folgenden Vorgehensweisen aus, um den Vorgang fortzusetzen:  
  
-   [Konfigurieren oder Reparieren von PowerPivot für SharePoint 2010 &#40;PowerPivot-Konfigurationstool&#41;](../../../2014/analysis-services/configure-repair-powerpivot-sharepoint-2010.md)  
  
-   [PowerPivot-Serververwaltung und -konfiguration in der Zentraladministration](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
-   [PowerPivot-Konfiguration mit Windows PowerShell](../../analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell.md)  
  
 **Verbindung mit der Instanz des Datenbankmoduls.** Als Sie [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] installiert haben, hatten Sie in SQL Server-Setup die Möglichkeit, der Installation eine Instanz der Datenbank-Engine hinzuzufügen. Sie haben möglicherweise der Installation eine Instanz der Datenbank-Engine hinzugefügt, wenn Sie eine neue Farm einrichten und einen Datenbankserver benötigen, um die Konfiguration und die Inhaltsdatenbanken der Farm auszuführen. Wenn Sie die Datenbank-Engine hinzugefügt haben, wurde sie als benannte [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Instanz installiert. Wenn Sie eine Verbindung mit dieser Instanz (z. B. im Assistenten für die Farmkonfiguration Wenn Sie diese Assistenten zum Konfigurieren der Farm verwenden), denken Sie daran, geben Sie den Datenbanknamen im folgenden Format angeben müssen: <`servername`> \PowerPivot.  
  
##  <a name="bkmk_redist"></a> Schritt 3: Installieren Sie Analysis Services OLE DB-Anbietern auf Excel Services-Anwendungsservern  
 Zusätzliche Installationsschritte sind erforderlich, wenn Sie Dienste für Excel-Berechnungen und [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] auf separaten Anwendungsservern ausführen. Installieren Sie auf den Anwendungsservern, auf denen Dienste für Excel-Berechnungen ausgeführt werden, die geeignete Version des Analysis Services OLE DB-Anbieters (MSOLAP).  
  
-   Die [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Version von MSOLAP ist in SQL Server-Setup enthalten. Folglich muss die MSOLAP-Version aus [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] nur explizit installiert werden, wenn der Anwendungsserver kein PowerPivot-Anwendungsserver ist.  
  
    > [!NOTE]  
    >  Die Excel Calculation Services Anwendungsserver benötigt außerdem eine Instanz der Datei **Microsoft.AnalysisServices.Xmla.dll** im globalen Assemblycache. Zur Installation der DLL-Datei auf dem Anwendungsserver installieren Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Wählen Sie die "Verwaltungstools – vollständig" auf die **Funktionsauswahl** Seite des SQL Server-Setup-Assistenten.  
  
-   Wenn der Anwendungsserver ältere [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]-Arbeitsmappen unterstützen soll, müssen Sie die SQL Server 2008 R2-Version von MSOLAP installieren.  
  
 Weitere Informationen zum Installieren des Anbieters, einschließlich der Überprüfungsschritte, finden Sie unter [installieren Sie die Analysis Services-OLE DB-Anbieter auf SharePoint-Servern](../../../2014/sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)  
  
##  <a name="bkmk_verify"></a> Schritt 4: Überprüfen der Installations  
 In diesem letzten Schritt überprüfen Sie, ob SharePoint 2010 und [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] voll funktionsfähig sind. Anweisungen hierzu finden Sie unter [Verify a PowerPivot für SharePoint-Installation](../../analysis-services/instances/install-windows/verify-a-power-pivot-for-sharepoint-installation.md).  
  
## <a name="see-also"></a>Siehe auch  
 [PowerPivot für SharePoint 2010-Installation](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)   
 [Bereitstellungsprüfliste: Reporting Services, Power View und PowerPivot für SharePoint](deployment-checklist-reporting-services-power-view-power-pivot-for-sharepoint.md)   
 [Bereitstellungsprüfliste: Horizontales durch Hinzufügen von PowerPivot-Servern zu einer SharePoint 2010-farm](../../../2014/sql-server/install/deployment-checklist-scale-out-adding-powerpivot-servers-sharepoint-2010-farm.md)   
 [Bereitstellungsprüfliste: Multiserverinstallation von PowerPivot für SharePoint 2010](../../../2014/sql-server/install/deployment-checklist-multiserver-installation-powerpivot-sharepoint-2010.md)  
  
  