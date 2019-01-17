---
title: Von den SQL Server-Editionen unterstützte Reporting Services-Features
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.date: 11/01/2018
ms.openlocfilehash: 37dec44c539db86f8f0d239fffe0ca28699f2799
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53645329"
---
# <a name="reporting-services-features-supported-by-the-editions-of-sql-server"></a>Von den SQL Server-Editionen unterstützte Reporting Services-Features

[!INCLUDE[ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../includes/ssrs-appliesto-pbirs.md)]

Dieses Thema bietet detaillierte Informationen zu den von verschiedenen Versionen von SQL Server unterstützten Reporting Services-Funktionen. SQL Server Evaluation Edition steht für einen Testzeitraum von 180 Tagen zur Verfügung.  
  
 Die neuesten Versionshinweise zu SQL Server finden Sie unter [SQL Server 2017 Versionshinweise](../sql-server/sql-server-2017-release-notes.md). Die letzten Informationen zu Neuigkeiten finden Sie unter [Neues bei Reporting Services (SSRS)](~/reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md).

 **Probieren Sie SQL Server 2017 aus!**    

> [![Download von SQL Server 2017](../analysis-services/media/download.png)](https://go.microsoft.com/fwlink/?LinkID=829477) **[Download von SQL Server 2017 aus dem Evaluation Center](https://go.microsoft.com/fwlink/?LinkID=829477)**    
>
> ![Virtueller Azure-Computer (klein)](../analysis-services/media/azure-virtual-machine-small.png) **[Starten eines virtuellen Computers, auf dem SQL Server 2017 bereits installiert ist](https://azure.microsoft.com/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm)**    

Informationen über Funktionen, die von den Evaluation- und Developer-Editionen unterstützt werden, finden Sie in der Spalte „SQL Server Enterprise Edition“.

##  <a name="SSRS"></a> Reporting Services  
  
|Funktionsname|Enterprise|Standard|Web|Express mit Advanced Services|Entwickler|  
|------------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Mobile Berichte und KPIs|Ja||||Ja|  
|Unterstützte [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Edition für Katalogdatenbanken|Standard oder höher|Standard oder höher|Web|Express|Standard oder höher|  
|Unterstützte [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Edition für Datenquellen|Alle   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Editionen|Alle [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Editionen|Web|Express|Alle [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Editionen|  
|Berichtsserver|Ja|Ja|Ja|Ja|Ja|  
|Berichts-Designer|Ja|Ja|Ja|Ja|Ja|  
|Berichts-Designer-Webportal|Ja|Ja|Ja|Ja|Ja|  
|Rollenbasierte Sicherheit|Ja|Ja|Ja|Ja|Ja|  
|Export in Excel, PowerPoint, Word, PDF und Bilder|Ja|Ja|Ja|Ja|Ja|  
|Verbesserte Messgeräte und Diagramme|Ja|Ja|Ja|Ja|Ja|  
|Anheften von Berichtselementen an [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)]-Dashboards|Ja|Ja|Ja|Ja|Ja|  
|Benutzerdefinierte Authentifizierung|Ja|Ja|Ja||Ja|  
|Berichte als Datenfeeds|Ja|Ja|Ja|Ja|Ja|  
|Modellunterstützung|Ja|Ja|Ja||Ja|  
|Erstellen von benutzerdefinierten Rollen für rollenbasierte Sicherheit|Ja|Ja|||Ja|  
|Modellelementsicherheit|Ja|Ja|||Ja|  
|Uneingeschränktes Durchklicken|Ja|Ja|||Ja|  
|Bibliothek freigegebener Komponenten|Ja|Ja|||Ja|  
|Abonnements und Zeitplanung für E-Mail und Dateifreigabe|Ja|Ja|||Ja|  
|Berichtsverlauf, Ausführungs-Momentaufnahmen und Zwischenspeichern|Ja|Ja|||Ja|  
|SharePoint-Integration|Ja|Ja|||Ja|  
|Unterstützung von Remotedatenquellen und Nicht-SQL-Datenquellen<sup>1</sup>|Ja|Ja|||Ja|  
|RDCE-Erweiterbarkeit von Datenquellen, Übermittlung und Rendering|Ja|Ja|||Ja|  
|Benutzerdefiniertes Branding|Ja||||Ja|  
|Datengesteuerte Berichtsabonnements|Ja||||Ja|  
|Bereitstellung für horizontales Skalieren (Webfarmen)|Ja||||Ja|  
|Warnungen<sup>2</sup> (SSRS 2016) |Ja||||Ja|  
| Power View<sup>2</sup> (SSRS 2016) |Ja||||Ja| 
|Kommentare<sup>3</sup> |Ja|Ja|Ja|Ja|Ja|  

 <sup>1</sup> Weitere Informationen zu unterstützten Datenquellen in SQL Server Reporting Services (SSRS) finden Sie unter [Von Reporting Services &#40;SSRS&#41; unterstützte Datenquellen](../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md).  
  
 <sup>2</sup> Erfordert Reporting Services 2016 im SharePoint-Modus. Weitere Informationen finden Sie unter [Installieren des SharePoint-Modus von Reporting Services](../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md). Die Integration von Reporting Services in SharePoint wird ab Reporting Services 2017 nicht mehr möglich sein. 

<sup>3</sup> Nur im Power BI-Berichtsserver sowie Reporting Services 2017 und höher.

> [!NOTE]
> SQL Server Reporting Services werden nicht von SQL Server Express und SQL Server Express mit Tools unterstützt.
  
## <a name="report-server-database-server-edition-requirements"></a>Anforderungen für die Berichtsserver-Datenbankserver-Edition
 Wenn Sie eine Berichtsserver-Datenbank erstellen, können nicht alle Editionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] zum Hosten der Datenbank verwendet werden. Folgende Tabelle zeigt, welche Editionen von [!INCLUDE[ssDE](../includes/ssde-md.md)] Sie für spezielle Editionen von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]verwenden können.  
  
|Für diese Edition von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Reporting Services|Verwendung dieser Edition der Datenbank-Engine-Instanz als Host für die Datenbank|  
|----------------------------------------------------------------------|---------------------------------------------------------------------------|  
|Enterprise|Enterprise oder Standard Editions (lokal oder remote)|  
|Standard|Enterprise oder Standard Editions (lokal oder remote)|  
|Web|Web Edition (nur lokal)|  
|Express mit Advanced Services|Express mit Advanced Services (nur lokal)|  
|Evaluation|Evaluation|  
  
##  <a name="BIC"></a> Business Intelligence-Clients  
 Die folgenden Softwareclientanwendungen sind im Microsoft Download Center verfügbar und bieten Unterstützung beim Erstellen von Business Intelligence-Dokumenten, die in einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz ausgeführt werden. Wenn Sie diese Dokumente in einer Serverumgebung hosten, verwenden Sie eine Edition von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , die diesen Dokumenttyp unterstützt. In der folgenden Tabelle wird dargestellt, welche [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Editionen die Serverfunktionen zum Hosten der in den Clientanwendungen erstellten Dokumente besitzen.  
  
|Name des Tools|Enterprise|Standard|Web|Express mit Advanced Services|Entwickler|  
|---------------|----------------|--------------|------------------------|-------------|---------------|  
|[!INCLUDE[ssRBnoversion](../includes/ssrbnoversion.md)] (RDL und RDS)|Ja|Ja|Ja|Ja|Ja|  
|[!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long.md)] (RSMOBILE)|Ja||||Ja|  
|Power BI-Apps für mobile Geräte (iOS, Windows 10, Android) (RSMOBILE)|Ja||||Ja|  
  
> [!NOTE]  
> 1. In der oben aufgeführten Tabelle sind die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Editionen angegeben, die zur Aktivierung dieser Clienttools erforderlich sind. Über diese Tools kann jedoch auf Daten zugegriffen werden, die von beliebigen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Editionen gehostet werden.  
> 2. [!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long.md)] ist der einzige Punkt für die Erstellung von mobilen Berichten. Stellen Sie eine Verbindung mit einem [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Server her, um auf Datenquellen zuzugreifen und Berichte zu erstellen. Anschließend veröffentlichen Sie sie auf dem [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Server für den Zugriff durch andere Benutzer in der Organisation auf dem Server oder auf mobilen Geräten. Sie können auch das eigenständige [!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long.md)] mit lokalen Datenquellen verwenden.  
> 3. Unabhängig davon, ob Sie ein lokales  [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] , [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] in der Cloud oder beides als Lösung für die Bereitstellung von Berichten verwenden, benötigen Sie nur eine mobile App für den Zugriff auf Dashboards und mobile Berichte auf mobilen Geräten. Die [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] -Apps stehen zum Download in den App-Stores für Windows, iOS oder Android bereit.  

## <a name="next-steps"></a>Nächste Schritte

[Von den SQL Server 2017-Editionen unterstützte Funktionen](~/sql-server/editions-and-components-of-sql-server-2017.md)  
[Planen einer SQL Server-Installation](../sql-server/install/planning-a-sql-server-installation.md) 

Haben Sie dazu Fragen? [Stellen Sie eine Frage im Reporting Services-Forum](https://go.microsoft.com/fwlink/?LinkId=620231)
