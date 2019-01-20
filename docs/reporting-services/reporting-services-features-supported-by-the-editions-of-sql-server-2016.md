---
title: Von den SQL Server-Editionen unterstützte SQL Server Reporting Services-Features
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.date: 11/01/2018
ms.openlocfilehash: 1b46c6cec15f3a229892116758fe7f147f24c9ac
ms.sourcegitcommit: 1c01af5b02fe185fd60718cc289829426dc86eaa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2019
ms.locfileid: "54185036"
---
# <a name="sql-server-reporting-services-features-supported-by-its-editions"></a>Von den SQL Server-Editionen unterstützte SQL Server Reporting Services-Features

[!INCLUDE[ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../includes/ssrs-appliesto-pbirs.md)]

In diesem Thema sind die Microsoft SQL Server Reporting Services-Features (SSRS) beschrieben, die von verschiedenen Editionen von SQL Server unterstützt werden. SQL Server Evaluation Edition steht für einen Testzeitraum von 180 Tagen zur Verfügung.  
  
 Die neuesten Versionshinweise zu SQL Server finden Sie unter [SQL Server 2017 Versionshinweise](../sql-server/sql-server-2017-release-notes.md). Die letzten Informationen zu Neuigkeiten finden Sie unter [Neues in SQL Server Reporting Services (SSRS)](~/reporting-services/what-s-new-in-sql-server-reporting-services-ssrs.md).

 ## <a name="try-sql-server-2017"></a>Testen Sie SQL Server 2017

> [![Download von SQL Server 2017](../analysis-services/media/download.png)](https://go.microsoft.com/fwlink/?LinkID=829477) **[Download von SQL Server 2017 aus dem Evaluation Center](https://go.microsoft.com/fwlink/?LinkID=829477)**    
>
> ![Virtueller Azure-Computer (klein)](../analysis-services/media/azure-virtual-machine-small.png) **[Starten eines virtuellen Computers, auf dem SQL Server 2017 bereits installiert ist](https://azure.microsoft.com/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm)**    

Informationen über Funktionen, die von den Evaluation- und Developer-Editionen unterstützt werden, finden Sie in der folgenden Tabelle in der Spalte für die SQL Server-Edition Enterprise.

##  <a name="SSRS"></a> SQL Server Reporting Services  
  
|Feature name|Enterprise|Standard|Web|Express mit Advanced Services|Entwickler|  
|------------------|---------|------------------------------------|------------------------|-------------|---------------|  
|Mobile Berichte und Analysen|Ja||||Ja|  
|Unterstützte [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Edition für Katalogdatenbanken|Standard oder höher|Standard oder höher|Web|Express|Standard oder höher|  
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
|Erweiterbarkeit von Datenquellen, Übermittlung, Rendering und RDCE|Ja|Ja|||Ja|  
|Benutzerdefiniertes Branding|Ja||||Ja|  
|Datengesteuertes Berichtsabonnement|Ja||||Ja|  
|Bereitstellung für horizontale Skalierung (Webfarmen)|Ja||||Ja|  
|Warnungen<sup>2</sup> (SSRS 2016) |Ja||||Ja|  
|Power View<sup>2</sup> (SSRS 2016) |Ja||||Ja| 
|Kommentare<sup>3</sup> |Ja|Ja|Ja|Ja|Ja|  

 <sup>1</sup> Weitere Informationen zu unterstützten Datenquellen in SQL Server Reporting Services (SSRS) finden Sie unter [Von Reporting Services &#40;SSRS&#41; unterstützte Datenquellen](../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md).  
  
 <sup>2</sup> Erfordert SQL Server 2016 Reporting Services im SharePoint-Modus. Weitere Informationen finden Sie unter [Installieren von Reporting Services 2016 im SharePoint-Modus](../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md). Ab SQL Server 2017 Reporting Services ist die Integration in SharePoint nicht mehr verfügbar. 

<sup>3</sup> Nur in Power BI-Berichtsserver sowie in SQL Server 2017 Reporting Services und höher.

> [!NOTE]
> SQL Server Reporting Services werden nicht von SQL Server Express und SQL Server Express mit Tools unterstützt.
  
## <a name="edition-requirements-for-the-report-server-database"></a>Editionsanforderungen für die Berichtsserver-Datenbankserver
 Wenn Sie eine Berichtsserver-Datenbank erstellen, können nicht alle Editionen von SQL Server [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] verwendet werden, um die Datenbank zu hosten. In der folgenden Tabelle ist gezeigt, welche Editionen von [!INCLUDE[ssDE](../includes/ssde-md.md)] Sie für spezielle Editionen von SQL Server [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] verwenden können.  
  
|Für diese Edition von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Reporting Services|Verwenden von dieser Edition der Datenbank-Engine-Instanz als Host für die Datenbank|  
|----------------------------------------------------------------------|---------------------------------------------------------------------------|  
|Enterprise|Enterprise oder Standard Edition (lokal oder remote)|  
|Standard|Enterprise oder Standard Edition (lokal oder remote)|  
|Web|Web Edition (nur lokal)|  
|Express mit Advanced Services|Express mit Advanced Services (nur lokal)|  
|Evaluation|Evaluation|  
  
##  <a name="BIC"></a> Business Intelligence-Clients  
Die folgenden Softwareclientanwendungen sind im Microsoft Download Center verfügbar. Mit diesen Anwendungen können Sie Business Intelligence-Dokumente erstellen, die mit einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanz ausgeführt werden. Wenn Sie diese Dokumente in einer Serverumgebung hosten, verwenden Sie eine Edition von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , die diesen Dokumenttyp unterstützt. In der folgenden Tabelle wird dargestellt, welche [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Editionen die Serverfunktionen zum Hosten der in den Clientanwendungen erstellten Dokumente besitzen.  
  
|Name des Tools|Enterprise|Standard|Web|Express mit Advanced Services|Entwickler|  
|---------------|----------------|--------------|------------------------|-------------|---------------|  
|[!INCLUDE[ssRBnoversion](../includes/ssrbnoversion.md)], **.rdl** und **.rds**|Ja|Ja|Ja|Ja|Ja|  
|[!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long.md)], **.rsmobile**|Ja||||Ja|  
|Power BI-Apps für mobile Geräte (iOS, Windows 10 und Android), **.rsmobile**|Ja||||Ja|  
  
> [!NOTE]  
> * In der vorherige Tabelle sind die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Editionen aufgeführt, die erforderlich sind, damit diese Clienttools verwendet werden können. Mit diesen Tools kann aber auf Daten zugegriffen werden, die in einer beliebigen Edition von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] gehostet werden.  
> * [!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long.md)] ist der einzige Punkt für die Erstellung von mobilen Berichten. Stellen Sie eine Verbindung mit einem SSRS-Server her, um auf Datenquellen zuzugreifen und Berichte zu erstellen. Anschließend veröffentlichen Sie diese auf dem SSRS-Server, sodass andere Benutzer in der Organisation entweder auf dem Server oder auf mobilen Geräten auf sie zugreifen können. Sie können auch [!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long.md)] eigenständig mit lokalen Datenquellen verwenden.  
> * Unabhängig davon, ob Sie ein [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] lokal, [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] in der Cloud oder beides als Ihre Lösung für die Bereitstellung von Berichten verwenden, benötigen Sie nur eine mobile App für den Zugriff auf Dashboards und mobile Berichte auf mobilen Geräten. Die [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] -Apps stehen zum Download in den App-Stores für Windows, iOS oder Android bereit.  

## <a name="next-steps"></a>Nächste Schritte

* Lesen Sie [Editionen und unterstützte Funktionen von SQL Server 2017](~/sql-server/editions-and-components-of-sql-server-2017.md). 

* [Planen einer SQL Server-Installation](../sql-server/install/planning-a-sql-server-installation.md).

* Haben Sie dazu Fragen? Informieren Sie sich im [SQL Server Reporting Services-Forum](https://go.microsoft.com/fwlink/?LinkId=620231).
