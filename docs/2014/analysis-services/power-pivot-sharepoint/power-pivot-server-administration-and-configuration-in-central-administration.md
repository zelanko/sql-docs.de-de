---
title: Power Pivot-Server Verwaltung und-Konfiguration in der zentral Administration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 2cdbfdc5-45a9-4000-a03d-318cc7ac8fe9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0bea6bb558e6ccafefbbb068fa3799eddff748a5
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547806"
---
# <a name="powerpivot-server-administration-and-configuration-in-central-administration"></a>PowerPivot-Serververwaltung und -konfiguration in der Zentraladministration
  Die PowerPivot-Serververwaltung und -konfiguration wird mithilfe der SharePoint-Zentraladministration von SharePoint Service-Anwendungsadministratoren ausgeführt.  
  
 PowerPivot für SharePoint muss konfiguriert werden, bevor es verwendet werden kann. Nachdem Sie PowerPivot für SharePoint mithilfe des SQL Server-Setups installiert haben, können Sie es wie folgt konfigurieren:  
  
-   PowerPivot-Konfigurationstool oder PowerPivot für SharePoint 2013-Konfigurationstool  
  
-   SharePoint-Zentraladministration  
  
-   PowerShell-Cmdlets  
  
 Alle drei Ansätze sorgen für einen vollständig konfigurierten Server.  
  
 Dieser Abschnitt umfasst Tasks zum Konfigurieren der Software mit Zentraladministration. Sie müssen sämtliche drei der erforderlichen unten in der Liste aufgeführten Konfigurationstasks ausführen.  
  
> [!IMPORTANT]  
>  Für SharePoint 2010 muss SharePoint 2010 Service Pack 1 (SP1) installiert sein, bevor Sie PowerPivot für SharePoint oder eine SharePoint-Farm konfigurieren können, die einen [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]"-Datenbankserver verwendet. Wenn Sie das Service Pack noch nicht installiert haben, holen Sie dies jetzt nach, bevor Sie mit der Serverkonfiguration beginnen.  
  
## <a name="benefits-of-configuring-powerpivot-for-sharepoint-using-central-administration"></a>Vorteile der Konfiguration von PowerPivot für SharePoint mithilfe der zentral Administration  
 SharePoint-Zentraladministration ist die Administratoranwendung einer SharePoint-Farm. Wenn Sie Farmadministrator sind, ziehen Sie es beim Hinzufügen einer PowerPivot für SharePoint-Instanz zur Farm eventuell vor, ein vertrautes Tool zu verwenden.  
  
 Im Gegensatz zu PowerPivot-Konfigurationstools oder PowerShell-Cmdlets, bietet die Zentraladministration Seiten, über die beim Konfigurieren einer Anwendung oder eines Servers alle Optionen angegeben werden, die Sie festlegen können. Andere Ansätze komprimieren entweder den Konfigurationsworkflow in eine geringere Anzahl von Schritten oder erfordern vorheriges Wissen darüber, wie ein SharePoint-Server mit PowerShell konfiguriert wird.  
  
## <a name="related-content"></a>Verwandte Inhalte  
 [PowerPivot-Konfiguration mit Windows PowerShell](power-pivot-configuration-using-windows-powershell.md)  
  
 [PowerPivot Configuration Tools](power-pivot-configuration-tools.md)  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Link|type|Taskbeschreibung|  
|----------|----------|----------------------|  
|[Bereitstellen von PowerPivot-Lösungen in SharePoint](deploy-power-pivot-solutions-to-sharepoint.md)|Erforderlich|Bei diesem Schritt werden die Projektmappendateien installiert, über die der Farm und den Websitesammlungen Programmdateien und Anwendungsseiten hinzugefügt werden.|  
|[Erstellen und Konfigurieren von PowerPivot-Dienstanwendungen in der Zentraladministration](create-and-configure-power-pivot-service-application-in-ca.md)|Erforderlich|Mit diesem Schritt wird der PowerPivot-Systemdienst bereitgestellt.|  
|[Aktivieren der PowerPivot-Funktionsintegration für Websitesammlungen in der Zentraladministration](activate-power-pivot-integration-for-site-collections-in-ca.md)|Erforderlich|Mit diesem Schritt werden PowerPivot-Funktionen auf Websitesammlungsebene aktiviert.|  
|[Hinzufügen von MSOLAP.5 als vertrauenswürdigen Datenanbieter in Excel Services](add-msolap-5-as-a-trusted-data-provider-in-excel-services.md)|Erforderlich|Mit diesem Schritt wird der OLE DB-Anbieter für Analysis Services als vertrauenswürdiger Anbieter in Excel Services hinzugefügt.|  
|[PowerPivot-Datenaktualisierung mit SharePoint 2010](../powerpivot-data-refresh-with-sharepoint-2010.md)|Empfohlen|Eine Datenaktualisierung ist optional, wird aber empfohlen. Dies ermöglicht es Ihnen, unbeaufsichtigte Updates der PowerPivot-Daten in veröffentlichten Excel-Arbeitsmappen zu planen.|  
|[Konfigurieren Sie das unbeaufsichtigte Daten Aktualisierungs Konto für Power Pivot &#40;PowerPivot für SharePoint&#41;](../configure-unattended-data-refresh-account-powerpivot-sharepoint.md)|Empfohlen|Mit diesem Schritt wird ein zweckgebundenes Konto bereitgestellt. Dieses kann dazu verwendet werden, um Datenaktualisierungsaufträge auf dem Server auszuführen.|  
|[Konfigurieren der Sammlung von Verwendungs Daten für &#40;PowerPivot für SharePoint](configure-usage-data-collection-for-power-pivot-for-sharepoint.md)|Optional|Die Verwendung der Datensammlung wird standardmäßig konfiguriert. Sie können die Standardeinstellungen mithilfe dieser Schritte ändern.|  
|[Konfigurieren der dedizierten Datenaktualisierung oder der reinen Abfrage Verarbeitung &#40;PowerPivot für SharePoint&#41;](../configure-dedicated-data-refresh-query-only-processing-powerpivot-sharepoint.md)|Optional|Eine PowerPivot-Instanz kann ausschließlich Datenaktualisierungsaufträgen oder Abfragen zugeordnet sein. Außerdem können Sie Standardeinstellungen zu parallelen Datenaktualisierungsaufträgen ändern.|  
|[Konfigurieren von PowerPivot-Dienstkonten](configure-power-pivot-service-accounts.md)|Optional|Hier wird erläutert, wie Kennwörter oder Änderungsdienstkonten aktualisiert werden.|  
|[Verbinden einer Power Pivot-Dienst Anwendung mit einer SharePoint-Webanwendung in der zentral Administration](connect-power-pivot-service-app-to-sharepoint-web-app-in-ca.md)|Optional|Hier wird erläutert, wie Dienstzuordnungen geändert werden.|  
|[Erstellen eines vertrauenswürdigen Speicherorts für PowerPivot-Websites in der Zentraladministration](create-a-trusted-location-for-power-pivot-sites-in-central-administration.md)|Optional|Hier wird erläutert, wie der PowerPivot-Katalog als vertrauenswürdiger Speicherort hinzugefügt wird.|  
|[Konfigurieren und Anzeigen von SharePoint-Protokolldateien und-Diagnoseprotokollierung &#40;PowerPivot für SharePoint&#41;](configure-and-view-sharepoint-and-diagnostic-logging.md)|Optional|Die Ereignisprotokollierung wird standardmäßig konfiguriert. Sie können die Standardeinstellungen mithilfe dieser Schritte ändern.|  
|[PowerPivot-Integritätsregeln − Konfigurieren](configure-power-pivot-health-rules.md)|Optional|Serverintegritätsregeln werden standardmäßig konfiguriert. Sie können mithilfe dieser Schritte einige der Standardeinstellungen ändern.|  
|[Erstellen und Anpassen von PowerPivot-Katalogen](create-and-customize-power-pivot-gallery.md)|Optional|Hinsichtlich der Installationen, die Sie manuell konfigurieren, wird über diese Prozedur erläutert, wie eine PowerPivot-Katalogbibliothek erstellt wird, die Bildminiaturansichten der in ihr enthaltenen PowerPivot-Arbeitsmappen anzeigt.|  
|[Hinzufügen eines BI-Semantik Modell-Verbindungs-Inhaltstyps zu einer Bibliothek &#40;PowerPivot für SharePoint&#41;](add-bi-semantic-model-connection-content-type-to-library.md)|Optional|Hier wird erläutert, wie eine Dokumentbibliothek erweitert wird, um die Erstellung von Verbindungsdateien des BI-Semantikmodells zu unterstützen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [PowerPivot für SharePoint 2010-Installation](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md)   
 [Die Konfigurations Einstellungs Referenz &#40;PowerPivot für SharePoint&#41;](configuration-setting-reference-power-pivot-for-sharepoint.md)   
 [Notfall Wiederherstellung für PowerPivot für SharePoint](https://go.microsoft.com/fwlink/p/?LinkId=389570)  
  
  
