---
title: Migrieren einer Installation von Reporting Services (SharePoint-Modus) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 61290949-690a-4e19-b078-57c99b6b30fa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 46b689a3eee612bdeb5bac5e0706574e21493635
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63260988"
---
# <a name="migrate-a-reporting-services-installation-sharepoint-mode"></a>Migrieren einer Installation von Reporting Services (SharePoint-Modus)
  Dieses Thema bietet eine Übersicht über die Schritte, die erforderlich sind, um eine Bereitstellung von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus zwischen SharePoint-Umgebungen zu migrieren. Die jeweiligen Schritte können sich abhängig von der Version unterscheiden, von der aus Sie migrieren. Weitere Informationen zu Upgrade- und Migrationsszenarien für den SharePoint-Modus finden Sie unter [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md). Wenn Sie nur die Berichtselemente von einem Server auf einen anderen kopieren möchten, finden Sie entsprechende Informationen unter [Reporting Services-Beispielskript rs.exe zum Migrieren von Inhalten zwischen Berichtsservern](../tools/sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).  
  
 Informationen zum Migrieren einer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Bereitstellung im einheitlichen Modus finden Sie unter [Migrieren einer Reporting Services-Installation &#40;einheitlicher Modus&#41;](../../reporting-services/install-windows/migrate-a-reporting-services-installation-native-mode.md).  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2010 und SharePoint 2013|  
  
 Ein häufiger Grund für eine Migration liegt vor, wenn Sie Ihre SharePoint 2010-Bereitstellung auf SharePoint 2013 aktualisieren möchten. SharePoint 2013 unterstützt keine direkten Upgrades von SharePoint 2010. Daher müssen Sie die Schritte für ein **Upgrade mit Anfügen der Datenbanken** oder eine reine Migration von Inhalten ausführen.  
  
 Weitere Informationen zum Aktualisieren von SharePoint 2013 finden Sie unter:  
  
-   [Übersicht über die Verfahren beim Upgrade auf SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256688).  
  
-   [Aktualisieren von Datenbanken von SharePoint 2010 auf SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256690).  
  
-   [Verschieben von Inhaltsdatenbanken in SharePoint 2013](https://technet.microsoft.com/library/cc262792.aspx).  
  
 
  
##  <a name="bkmk_prior_versions"></a> Migrieren von Reporting Services-Versionen im SharePoint-Modus vor SQL Server 2012  
 Die Architektur von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus wurde in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]geändert. Die Änderungen betreffen auch das Datenbankschema der Dienstanwendung. Wenn Sie von einer Version vor [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] auf [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]im SharePoint-Modus migrieren möchten, erstellen Sie zuerst die neue SharePoint-Umgebung, indem Sie SharePoint und [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint-Modus installieren. Weitere Informationen finden Sie unter [Reporting Services SharePoint-Modus-Installation &#40;SharePoint 2010 und SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md).  
  
 Sobald die neue SharePoint-Umgebung ausgeführt wird, können Sie zwischen der reinen Migration von Inhalten oder einer vollständigen Migration auf Datenbankebene (einschließlich Inhaltsdatenbanken) auswählen.  
  
###  <a name="bkmk_content_only_migration"></a> Reine Inhaltsmigration  
 **Nur Reporting Services-Inhalt migrieren:** Wenn Sie den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Inhalt in eine neue Farm kopieren möchten, benötigen Sie Tools wie **rs.exe**, um den Inhalt in die neue SharePoint-Installation zu kopieren. Weitere Informationen zur reinen Migration von Inhalten finden Sie unter:  
  
-   **[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-RSS-Skripts:** Die Skripts können Inhalte und Ressourcen zwischen einheitlichem und Berichtsservern im SharePoint-Modus migrieren. Weitere Informationen finden Sie unter [Reporting Services-Beispielskript rs.exe zum Migrieren von Inhalten zwischen Berichtsservern](../tools/sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md) und [Reporting Services-Skript "RS.exe" zum Migrieren von Inhalten von einem Berichtsserver zu einem anderen](http://azuresql.codeplex.com/releases/view/115207).  
  
-   **Reporting Services-Migrationstool:** Das Tool kann Ihre Berichtselemente von einem Server im einheitlichen Modus zu einem Server der SharePoint-Modus kopieren. Weitere Informationen finden Sie unter [Reporting Services-Migrationstool](https://www.microsoft.com/download/details.aspx?id=29560).  
  
###  <a name="bkmk_full_migration"></a> Vollständige Migration  
 **Vollständige Migration:** Wenn Sie SharePoint-Inhaltsdatenbanken zusammen mit Migrieren der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Katalogdatenbanken zu einer neuen Farm führen Sie eine Reihe von Optionen zum Sichern und Wiederherstellen in diesem Thema zusammengefasst. In einigen Fällen müssen Sie in der Wiederherstellungsphase ein anderes Tool verwenden als in der Sicherungsphase. Beispielsweise können Sie den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager verwenden, um Verschlüsselungsschlüssel einer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Vorgängerversion zu sichern. In diesem Fall müssen Sie jedoch die SharePoint-Zentraladministration oder PowerShell verwenden, um die Verschlüsselungsschlüssel in einer [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Installation im SharePoint-Modus wiederherzustellen.  
  
####  <a name="bkmk_databases"></a> Datenbanken, die in der abgeschlossenen Migration angezeigt werden  
 In der folgenden Tabelle sind die SQL Server-Datenbanken von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] beschrieben, die nach der erfolgreichen Migration der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Installation im SharePoint-Modus zur Verfügung stehen:  
  
|Datenbank|Beispielname||  
|--------------|------------------|-|  
|Katalogdatenbank|ReportingService_[GUID der Dienstanwendung] **(\*)**|Wird vom Benutzer migriert.|  
|Temporäre Datenbank|ReportingService_[GUID der Dienstanwendung]TempDB **(\*)**|Wird vom Benutzer migriert.|  
|Warnungsdatenbank|ReportingService_[GUID der Dienstanwendung]_Alerting|Wird zusammen mit einer [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung erstellt.|  
  
 **(\*)** Die in der Tabelle angezeigten Beispielnamen folgen der Namenskonvention, die von SSRS beim Erstellen einer neuen SSRS-Dienstanwendung verwendet wird. Wenn Sie von einem anderen Server migrieren, verfügen Ihr Katalog und die tempDBs über die entsprechenden Namen der ursprünglichen Installation.  
  
####  <a name="bkmk_backup_operations"></a> Sicherungsvorgänge  
 In diesem Abschnitt werden die zu migrierenden Informationstypen und die Tools bzw. die Vorgehensweise zum Abschließen des Sicherungsvorgangs beschrieben.  
  
 ![Einfaches Diagramm der SSRS SharePoint-Migration](../../../2014/sql-server/install/media/rs-sharepoint-migration.gif "Basic diagram of SSRS SharePoint Migration")  
  
||Objekte|Methode|Hinweise|  
|-|-------------|------------|-----------|  
|**1**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Verschlüsselungsschlüssel.|**Rskeymgmt.exe** oder [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurations-Manager. Weitere Informationen finden Sie unter [Sichern und Wiederherstellen von Reporting Services-Verschlüsselungsschlüsseln](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md).|Die angegebenen Tools können für die Sicherung verwendet werden, für die Wiederherstellung werden jedoch die Verwaltungsseiten für die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung oder PowerShell verwendet.|  
|**2**|SharePoint-Inhaltsdatenbanken.||Sichern Sie die Datenbank, und trennen Sie sie.<br /><br /> Weitere Informationen finden Sie im Abschnitt „Upgrade mit Anfügen der Datenbanken“ unter [Bestimmen der Upgrademethode (SharePoint Server 2010) (https://technet.microsoft.com/library/cc263447.aspx)](https://technet.microsoft.com/library/cc263447.aspx).|  
|**3**|SQL Server-Datenbank, die der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Katalogdatenbank entspricht.|Sichern und Wiederherstellen von SQL Server-Datenbanken<br /><br /> oder<br /><br /> Trennen und erneutes Anfügen der SQL Server-Datenbank||  
|**4**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationsdateien|Einfacher Dateikopiervorgang|Wenn Sie Änderungen an der Datei vorgenommen haben, müssen Sie nur „rsreportserver.config“ kopieren. Beispiel der Standardspeicherort der Dateien: C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\15\WebServices\Reporting<br /><br /> RSReportServer.config<br /><br /> Rssvrpolicy.config<br /><br /> "Web.config" für die Berichtsserver-ASP.NET-Anwendung.<br /><br /> "Machine.config" für ASP.NET.|  
  
####  <a name="bkmk_restore_operations"></a> Wiederherstellungsvorgänge  
 In diesem Abschnitt werden die zu migrierenden Informationstypen und die Tools bzw. die Vorgehensweise zum Abschließen des Wiederherstellungsvorgangs beschrieben. Die zur Wiederherstellung verwendeten Tools können sich von den Tools unterscheiden, die Sie für die Sicherung verwendet haben.  
  
 Bevor Sie die Wiederherstellungsschritte ausführen, müssen Sie die neue SharePoint-Farm und [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] im SharePoint Modus installieren und konfigurieren. Weitere Informationen zu einer Basisinstallation von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint-Modus finden Sie unter [Reporting Services SharePoint-Modus-Installation &#40;SharePoint 2010 und SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md).  
  
||Objekte|Methode|Hinweise|  
|-|-------------|------------|-----------|  
|**1**|Stellen Sie SharePoint-Inhaltsdatenbanken in der neuen Farm wieder her.|SharePoint-Methode „Upgrade mit Anfügen der Datenbanken“.|Grundlegende Schritte:<br /><br /> 1) Stellen Sie die Datenbank auf dem neuen Server wieder her.<br /><br /> 2) Fügen Sie die Inhaltsdatenbank an eine Webanwendung an, indem Sie die URL angeben.<br /><br /> 3) "Get-SPWebapplication" listet alle Webanwendungen und die URLs auf.<br /><br /> Weitere Informationen finden Sie im Abschnitt „Upgrade mit Anfügen der Datenbanken“ unter [Bestimmen der Upgrademethode (SharePoint Server 2010) (https://technet.microsoft.com/library/cc263447.aspx)](https://technet.microsoft.com/library/cc263447.aspx) und [Anfügen von Datenbanken und Upgrade auf SharePoint Server 2010 (https://technet.microsoft.com/library/cc263299.aspx)](https://technet.microsoft.com/library/cc263299.aspx).|  
|**2**|Stellen Sie die SQL-Datenbank wieder her, die der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Katalogdatenbank (ReportServer) entspricht.|Sichern und Wiederherstellen von SQL-Datenbanken<br /><br /> **oder**<br /><br /> Anfügen und Trennen von SQL Server-Datenbanken|Wenn die Datenbank erstmalig verwendet wird, aktualisiert [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] das Datenbankschema nach Bedarf, damit es in der [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Umgebung funktioniert.|  
|**3**|Erstellen Sie eine neue [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung.|SharePoint-Zentraladministration|Wenn Sie die neue Dienstanwendung erstellen, konfigurieren Sie sie für die Verwendung der kopierten Berichtsserver-Datenbank.<br /><br /> Weitere Informationen zur Verwendung der SharePoint-Zentraladministration finden Sie im Abschnitt „Schritt 3: Abschnitt erstellen eine Reporting Services-Dienstanwendung"unter [installieren Sie Reporting Services SharePoint Mode for SharePoint 2013](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md).<br /><br /> Beispiele für die Verwendung von PowerShell finden Sie im Abschnitt „Erstellen einer Reporting Services-Dienstanwendung mit PowerShell“ unter [Reporting Services-SharePoint-Dienst und -Dienstanwendungen](../../../2014/reporting-services/reporting-services-sharepoint-service-and-service-applications.md).|  
|**4**|Stellen Sie die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Konfigurationsdateien wieder her.|Einfacher Dateikopiervorgang|Beispiel der Standardspeicherort der Dateien: C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\15\WebServices\Reporting.|  
|**5**|Stellen Sie die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Verschlüsselungsschlüssel wieder her.|Über die Seite „SystemSettings“ der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Dienstanwendung können Sie die Hauptsicherungsdatei wiederherstellen.<br /><br /> **oder**<br /><br /> PowerShell|Weitere Informationen finden Sie im Abschnitt „Schlüsselverwaltung“ des Themas [Verwalten einer Reporting Services-SharePoint-Dienstanwendung](../../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md).|  
  
#####  <a name="bkmk_additional_configuration"></a> Zusätzliche Konfiguration  
 Abhängig von der Konfiguration der vorherigen SharePoint-Umgebung kann es erforderlich sein, einen oder mehrere der folgenden Schritte auszuführen:  
  
1.  Konfigurieren Sie die NTLM-Authentifizierung für eine [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Dienstanwendung. Weitere Informationen finden Sie unter [Konfigurieren von E-Mail für eine Reporting Services-Dienstanwendung &#40;SharePoint 2010 und SharePoint 2013&#41;](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md).  
  
##  <a name="bkmk_migrate_from_ctp"></a> Migrieren von einer SQL Server 2012-Bereitstellung  
 In einer aus mehreren Servern bestehenden Farm befinden sich die Inhalts- und die Katalogdatenbank wahrscheinlich auf unterschiedlichen Computern. In diesem Fall müssen Sie der SharePoint-Farm nur einen neuen Server mit installiertem [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienst hinzufügen und den alten Server entfernen. Das Kopieren der Datenbanken ist nicht erforderlich.  
  
### <a name="backup-operations"></a>Sicherungsvorgänge  
  
1.  Sichern Sie die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Verschlüsselungsschlüssel.  
  
2.  Sichern Sie die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung in der SharePoint-Zentraladministration (oder verwenden Sie PowerShell). Auf diese Weise sichern Sie auch die Datenbanken der Dienstanwendung in SharePoint. Weitere Informationen finden Sie im Artikel  [Sichern und Wiederherstellen von Reporting Services-SharePoint-Dienstanwendungen](../../../2014/reporting-services/backup-and-restore-reporting-services-sharepoint-service-applications.md).  
  
3.  Wenn Sie über ein Konto für die unbeaufsichtigte Ausführung (Unattended Execution Account, UEA) verfügen und die Windows-Authentifizierung verwenden, sollten Sie sich die Anmeldeinformationen für den Wiederherstellungsvorgang notieren.  
  
4.  Weitere Informationen finden Sie unter [Sichern von Dienstanwendungen in SharePoint 2013](https://technet.microsoft.com/library/ee428318.aspx).  
  
### <a name="restore-operations"></a>Wiederherstellungsvorgänge  
  
1.  Stellen Sie die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Dienstanwendung mithilfe der SharePoint-Zentraladministration wieder her. Alternativ können Sie PowerShell verwenden.  
  
2.  Stellen Sie die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Verschlüsselungsschlüssel wieder her.  
  
     Weitere Informationen finden Sie im Abschnitt „Schlüsselverwaltung“ des Themas [Verwalten einer Reporting Services-SharePoint-Dienstanwendung](../../../2014/reporting-services/manage-a-reporting-services-sharepoint-service-application.md)  
  
3.  Konfigurieren Sie die Anmeldeinformationen für UEA und Windows in der Dienstanwendung.  
  
4.  Weitere Informationen finden Sie unter [Wiederherstellen von Dienstanwendungen in SharePoint 2013](https://technet.microsoft.com/library/ee428305.aspx).  
  
##  <a name="bkmk_additional_resources"></a> Zusätzliche Ressourcen  
  
-   [Erste Schritte beim Upgrade auf SharePoint 2013 (https://technet.microsoft.com/library/ee833948.aspx)](https://technet.microsoft.com/library/ee833948.aspx).  
  
-   [Übersicht über die Verfahren beim Upgrade auf SharePoint 2013 (https://technet.microsoft.com/library/cc262483.aspx)](https://technet.microsoft.com/library/cc262483.aspx).  
  
## <a name="see-also"></a>Siehe auch  
 [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)   
 [Migrieren einer Reporting Services-Installation &#40;einheitlicher Modus&#41;](../../reporting-services/install-windows/migrate-a-reporting-services-installation-native-mode.md)  
  
  
