---
title: Funktionsauswahl | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- feature selection, Setup
helpviewer_keywords:
- SQL Server Installation Wizard, Components to Install page
- Components to Install page [SQL Server Installation Wizard]
ms.assetid: 73182088-153b-4634-a060-d14d1fd23b70
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d20a8ea8a4e05b455a4c69a867504e82bdce014a
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53365832"
---
# <a name="feature-selection"></a>Funktionsauswahl
  Mit den Kontrollkästchen auf der Seite **Funktionsauswahl** des Installations-Assistenten für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können Sie die Komponenten für Ihre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Installation auswählen.  
  
## <a name="installing-includessnoversionincludesssnoversion-mdmd-features"></a>Installieren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktionen  
 Auf der **Funktionsauswahl** Seite die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Funktionen werden in zwei Hauptabschnitte unterteilt: **Instanzfunktionen** und **freigegebene Funktionen**.  
  
 **Instanzfunktionen** verweist auf die Komponenten, die einmal für jede Instanz installiert sind, damit Sie über mehrere Kopien von ihnen (einer für jede Instanz) verfügen. Jede Instanz kann eine separate Version sein, die eine andere Patchebene aufweist. Bei der Installation eines Patches werden unabhängig davon, ob es sich um einen Service Pack, Hotfix oder ein kumulatives Update handelt, nur die Dateien für eine Instanz auf einem bestimmten Computer sowie die gemeinsam verwendeten Funktionen aktualisiert, falls diese nicht bereits aktualisiert wurden.  
  
 **Freigegebene Funktionen** verweist auf Funktionen, die von allen Instanzen auf einem bestimmten Computer gemeinsam verwendet werden. Diese freigegebenen Funktionen werden so entworfen, dass sie abwärtskompatibel mit unterstützten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Versionen (Service Packs, kumulative Updates und Hotfixes) sind, die nebeneinander installiert werden können.  
  
> [!NOTE]  
>  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Failovercluster:** Die [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Komponente und die [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Komponente sind die einzigen [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Funktionen mit Failoverclustering. Sie können weitere Komponenten, z. B. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] oder [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], auf einem Failoverclusterknoten installieren, doch diese sind nicht clusterabhängig, und für ihre Dienste wird kein Failover ausgeführt, wenn der Failoverclusterknoten offline geschaltet wird. Weitere Informationen finden Sie unter [ AlwaysOn-Failoverclusterinstanzen &#40;SQL Server&#41;](../failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md).  
  
### <a name="instance-features"></a>Instanzfunktionen  
 Im Bereich **Beschreibung** wird eine Beschreibung für jede Komponentengruppe angezeigt, wenn Sie sie ausgewählt haben. Sie können jede beliebige Kombination von Kontrollkästchen aktivieren. Um fortzufahren, müssen Sie eine Auswahl treffen.  
  
|-Funktionen|Description|  
|--------------|-----------------|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] -Dienste|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] enthält die [!INCLUDE[ssDE](../../includes/ssde-md.md)], den Basisdienst für speichern, verarbeiten und Sichern von Daten, Replikation, Volltextsuche, Tools zum Verwalten von relationalen und XML-Daten, und die [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS)-Server. Die folgenden Elemente sind Funktionen der Datenbank-Engine:<br /><br /> [!INCLUDE[ssDE](../../includes/ssde-md.md)] ist der Kerndienst zum Speichern, Verarbeiten und Sichern von Daten.<br /><br /> Replikation: Optional: Bei der Replikation handelt es sich um eine Reihe von Technologien zum Kopieren und Verteilen von Daten und Datenbankobjekten aus einer Datenbank in eine andere und das anschließende Synchronisieren zwischen den Datenbanken, um die Konsistenz der Daten sicherzustellen.<br /><br /> Volltextsuche: Optional: Die Volltextsuche enthält die Funktionalität zum Ausführen von Volltextabfragen für rein zeichenbasierte Daten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabellen.<br /><br /> [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]: Optional: Bei [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) handelt es sich um eine Datenbereinigungslösung, die die Ermittlung inkonsistenter und falscher Daten in Ihrer Datenquelle ermöglicht und computergestützte und interaktive Methoden zur Datenbereinigung bereitstellt. Aktivieren Sie dieses Kontrollkästchen, um den DQS-Server zu installieren. Nachdem die Installation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abgeschlossen ist, muss die Datei „DQSInstaller.exe“ ausgeführt werden, um die *vollständige* Installation von DQS-Server sicherzustellen. Wenn Sie die Standardinstanz von SQLServer installiert haben, steht diese Datei unter C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12. MSSQLSERVER\MSSQL\Binn.<br /><br /> <br /><br /> **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Failovercluster:** Wenn Sie „Datenbank-Engine-Dienste“ für Failoverclustering-Installationen auswählen, sind die Komponenten Replikation und Volltextsuche erforderlich und werden vom Setup für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] automatisch ausgewählt.|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] enthält Tools zum Erstellen und Verwalten der analytischen Onlineverarbeitung (OLAP, Online Analytical Processing) sowie Data Mining-Anwendungen.|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Native|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Einheitlicher Modus enthält Server- und Clientkomponenten, mit denen Berichte in Form einer Tabelle, Matrix, Grafik oder Freiform erstellt, verwaltet und bereitgestellt werden können. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ist gleichzeitig eine erweiterbare Plattform, die Sie zum Entwickeln von Berichtsanwendungen verwenden können.|  
  
> [!IMPORTANT]
>  1.  Der Lastenausgleich und die Adressierung mit einer einzelnen URL für mehrere Knoten werden vom Setupprogramm in einer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Bereitstellung für dezentrales Skalieren nicht konfiguriert. Zur Durchführung einer Bereitstellung für horizontales Skalieren müssen Sie Windows Server, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Application Center oder eine Clusterverwaltungssoftware eines Drittanbieters verwenden. Weitere Informationen zum Einrichten der webfarmbereitstellung finden Sie unter [Konfigurieren von Reporting Services für die Bereitstellung für horizontales Skalieren](https://go.microsoft.com/fwlink/?LinkId=199448) (https://go.microsoft.com/fwlink/?LinkId=199448).  
> 2.  Informationen zu den Browseranforderungen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Komponenten finden Sie unter [Planen der Browserunterstützung für Reporting Services und Power View &#40;Reporting Services 2014&#41;](../../../2014/reporting-services/browser-support-for-reporting-services-and-power-view.md).  
> 3.  Bei einer gleichzeitigen Konfiguration auf der 64-Bit-Plattform und dem 32-Bit-Subsystem (WOW64) eines 64-Bit-Servers wird [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nicht unterstützt.  
  
### <a name="shared-features"></a>Freigegebene Funktionen  
 Funktionen, die von allen Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf einem einzelnen Computer gemeinsam verwendet werden, werden in einem einzelnen Verzeichnis installiert. Dabei handelt es sich um folgende Elemente:  
  
|Funktion|Description|  
|-------------|-----------------|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] – SharePoint|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint-Modus ist eine serverbasierte Anwendung zum Erstellen, verwalten und Bereitstellen von Berichten in e-Mail-Adresse, mehrere Dateiformate sowie interaktiven webbasierten Formaten. Im SharePoint-Modus werden die Funktionen für die Berichtsanzeige und -verwaltung in SharePoint-Produkte integriert. Weitere Informationen finden Sie unter [Reporting Services-Berichtsserver &#40;SharePoint-Modus&#41;](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md).|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-In für SharePoint-Produkte|Das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Add-In für SharePoint-Produkte enthält Verwaltungs- und Benutzeroberflächenkomponenten zur Integration eines SharePoint-Produkts in einen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Berichtsserver im SharePoint-Modus. Weitere Informationen finden Sie unter [Verfügbarkeit des Reporting Services-Add-Ins für SharePoint-Produkte](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).|  
|Data Quality Client|Data Quality Client ist eine eigenständige Anwendung, die eine Verbindung mit dem DQS-Server herstellt und eine intuitive grafische Benutzeroberfläche bereitstellt, um Datenbereinigungs- und Datenabgleichsvorgänge sowie Verwaltungsaufgaben in DQS auszuführen.|  
|Konnektivität der Clienttools|Die Clienttools umfassen Komponenten für die Kommunikation zwischen Clients und Servern, einschließlich Netzwerkbibliotheken für DB-Library, OLEDB für OLAP, ODBC, ADODB und ADOMD+.|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] stellt eine Gruppe grafischer Tools und programmierbarer Objekte zum Verschieben, Kopieren und Transformieren von Daten bereit.|  
|Clienttools-Abwärtskompatibilität|In der Clienttools-Abwärtskompatibilität sind die folgenden Komponenten enthalten:<br /><br /> SQL Distributed Management Objects (SQL-DMO). Weitere Informationen finden Sie unter [Nicht mehr unterstützte SQL Server-Funktionen in SQL Server 2014](../../../2014/getting-started/discontinued-sql-server-features-in-sql-server-2014.md).<br /><br /> Decision Support Objects (DSO). Weitere Informationen finden Sie unter [Wichtige Änderungen von Analysis Services-Funktionen in SQL Server 2014](../../../2014/analysis-services/breaking-changes-to-analysis-services-features-in-sql-server-2014.md).|  
|Clienttools SDK|Enthält das Software Development Kit, das Ressourcen für Programmierer enthält.|  
|Dokumentationskomponenten|Dokumentationskomponenten enthalten die Komponenten zum Anzeigen und Verwalten von Hilfeinhalten.|  
|Verwaltungstools - Einfach|**Verwaltungstools - einfach:** Dazu gehören:<br /><br /> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Unterstützung für die [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], **Sqlcmd** -Hilfsprogramm und die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell-Anbieter<br /><br /> **Verwaltungstools – vollständig:** Dies umfasst die folgenden Komponenten zusätzlich zu den Komponenten der Standardversion:<br /><br /> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]-Unterstützung für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] und [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]<br /><br /> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]<br /><br /> Datenbankoptimierungsratgeber<br /><br /> Verwaltung mit dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Hilfsprogramm|  
|Distributed Replay Controller|Der Distributed Replay Controller koordiniert die Aktionen der Distributed Replay Clients. Es kann in jeder Distributed Replay-Umgebung jeweils nur eine Controllerinstanz geben. Weitere Informationen finden Sie unter [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md).|  
|Distributed Replay Client|Die Distributed Replay Clients simulieren gemeinsam Arbeitsauslastungen auf einer Instanz von SQL Server. In jeder Distributed Replay-Umgebung kann sich mindestens ein Client befinden. Weitere Informationen finden Sie unter [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md).|  
|SQL Client Connectivity SDK|Enthält [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (ODBC/OLE DB) SDK für die Entwicklung von Datenbankanwendungen.|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] ist eine Plattform, mit der für Genauigkeits- und Überwachungszwecke Daten aus unterschiedlichen Systemen einer gesamten Organisation in einer einzelnen Quelle von Masterdaten integriert werden. Mit der [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] -Option werden der [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)], Assemblys, das Windows PowerShell-Snap-In sowie Ordner und Dateien für Webanwendungen und Dienste installiert.|  
  
 Standardmäßig werden freigegebene Komponenten unter „%Program Files%Microsoft SQL Server\\“ installiert. Um den Installationspfad zu ändern, klicken Sie auf die Schaltfläche **Durchsuchen** . Wenn Sie den Installationspfad einer freigegebenen Komponente ändern, wirkt sich diese Änderung auch auf andere freigegebene Komponenten aus. Bei allen zukünftigen Installationen werden die freigegebenen Komponenten wieder am gleichen Speicherort installiert wie bei der ursprünglichen Installation.  
  
 **Instanzstammverzeichnis:** Standardmäßig lautet das Instanzstammverzeichnis „C:\Programme\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\“. Um ein nicht standardmäßiges Stammverzeichnis anzugeben, klicken Sie auf die Schaltfläche **Durchsuchen** , oder geben Sie einen Pfadnamen an.  
  
 Unter x64-basierten Betriebssystemen können Sie angeben, wo 64-Bit-Komponenten installiert werden sollen und wo im WOW64-Subsystem 32-Bit-Komponenten installiert werden sollen.  
  
## <a name="disk-space-requirements"></a>Anforderungen an den Datenträgerspeicher  
 Untersuchen Sie auf der Seite Speicherplatzzusammenfassung die Speicherplatzanforderungen für die zur Installation ausgewählten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Funktionen.  
  
### <a name="options"></a>Optionen  
 Wenn die Speicherplatzanforderungen zu hoch sind, erwägen Sie die folgenden Optionen:  
  
-   Erstellen Sie die Installationsverzeichnisse auf einem Laufwerk mit mehr Speicherplatz.  
  
-   Ändern Sie die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Funktionen für die Installation.  
  
-   Vergrößern Sie den freien Speicherplatz auf dem angegebenen Laufwerk, indem Sie andere Dateien oder Anwendungen verschieben.  
  
## <a name="installing-adventureworks-sample-databases"></a>Installieren der AdventureWorks-Beispieldatenbanken  
 Standardmäßig werden Beispieldatenbanken und Beispielcode nicht als Teil des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setups installiert. Weitere Informationen zum Installieren von Beispieldatenbanken und Beispielcode finden Sie unter den [Microsoft SQL Server Community Projects & Samples](https://go.microsoft.com/fwlink/?LinkId=87843) (https://go.microsoft.com/fwlink/?LinkId=87843).  
  
 Weitere Informationen zu Beispielen stehen nach der Installation von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] zur Verfügung. Von der **starten** Menü klicken Sie auf **Programme**, klicken Sie auf **[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**, klicken Sie auf **Dokumentation und Lernprogramme** , und klicken Sie dann auf  **[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Samples Overview**.  
  
## <a name="see-also"></a>Siehe auch  
 [Editionen und Komponenten von SQL Server 2014](../editions-and-components-of-sql-server-2016.md)  
  
  
