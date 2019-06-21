---
title: Neues in Reporting Services (SSRS) | Microsoft-Dokumentation
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 05/08/2019
ms.openlocfilehash: 37c3c8b874534f3a8a649d438b26b0ee133cb371
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65993861"
---
# <a name="whats-new-in-sql-server-reporting-services-ssrs"></a>Neues in SQL Server Reporting Services (SSRS)

[!INCLUDE[ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../includes/ssrs-appliesto-not-pbirs.md)]

Erfahren Sie, was in SQL Server [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] geändert wurde. Dieser Artikel behandelt die wesentlichen Features und wird aktualisiert, sobald neue Elemente veröffentlicht wurden.

Die aktuellen Versionsanmerkungen finden Sie in den [Anmerkungen zu SQL Server 2017](../sql-server/sql-server-2017-release-notes.md). 

Weitere Informationen zu Power BI-Berichtsserver finden Sie unter [Was ist der Power BI-Berichtsserver?](https://docs.microsoft.com/power-bi/report-server/get-started).

**Herunterladen** ![download](../analysis-services/media/download.png "download")

Laden Sie SQL Server 2017 Reporting Services im **[Microsoft Download Center herunter](https://www.microsoft.com/download/details.aspx?id=55252)**.

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"

## <a name="sql-server-2019-preview-reporting-services"></a>Vorschauversion von SQL Server 2019 Reporting Services

[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)] Reporting Services ist nicht für CTP 3.0 verfügbar. Installieren Sie die aktuelle Version [SQL Server 2017 Reporting Services](install-windows/install-reporting-services.md).
::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"

## <a name="ssrs-2017"></a>SSRS 2017

### <a name="comments-on-reports"></a>Kommentare zu Berichten

Kommentare sind jetzt für Berichte verfügbar, um Perspektive und Zusammenarbeit mit anderen Benutzern hinzuzufügen. Sie können auch die Anlagen mit Ihren Kommentar einschließen.

![Kommentare in einem Berichtsserver](media/what-s-new-in-sql-server-reporting-services-ssrs/report-server-comments.png)

Weitere Informationen finden Sie unter [Hinzufügen von Kommentaren zu einem Bericht in einem Berichtsserver](https://powerbi.microsoft.com/documentation/reportserver-add-comments/).

### <a name="dax-queries-in-reporting-tools"></a>DAX-Abfragen in Berichtstools

In den neuesten Versionen von Berichts-Generator und SQL Server Data Tools können Sie native DAX-Abfragen für Tabellendatenmodelle von SQL Server Analysis Services erstellen. Sie können Felder ziehen und Ablegen in der Abfrage-Designern. Weitere Informationen finden Sie unter [Reporting Services-Blog](https://blogs.msdn.microsoft.com/sqlrsteamblog/2017/03/09/query-designer-support-for-dax-now-available-in-report-builder-and-sql-server-data-tools/).

### <a name="rest-api-support"></a>REST-API-Unterstützung

SQL Server Reporting Services unterstützt eine vollständig OpenAPI-kompatible RESTful-API, um die Entwicklung von modernen Anwendungen und Anpassungen zu ermöglichen. Die vollständige API-Spezifikation und -Dokumentation finden Sie im [SwaggerHub](https://app.swaggerhub.com/apis/microsoft-rs/SSRS/2.0).

### <a name="query-designer-support-for-dax-now-in-report-builder-and-sql-server-data-tools"></a>Unterstützung des Abfrage-Designers für DAX jetzt im Berichts-Generator und der SQL Server Data Tools

Mit dem Berichts-Generator und SQL Server Data Tools können Sie jetzt native DAX-Abfragen für unterstützte Tabellendatenmodelle von SQL Server Analysis Services erstellen. Sie können den Abfrage-Designer in beiden Tools verwenden, um die gewünschten Felder ziehen und ablegen. Die DAX-Abfrage wird für Sie generiert.

Mehr dazu erfahren Sie im [Reporting Services-Blog](https://blogs.msdn.microsoft.com/sqlrsteamblog/2017/03/09/query-designer-support-for-dax-now-available-in-report-builder-and-sql-server-data-tools/).

* [SQL Server-Berichts-Generator](https://go.microsoft.com/fwlink/?LinkId=734968) herunterladen.
* Laden Sie [SQL Server Data Tools: Release Candidate](https://docs.microsoft.com/sql/ssdt/sql-server-data-tools-ssdt-release-candidate) herunter.

> **Hinweis:** Sie können den Abfrage-Designer für DAX nur mit SSAS-Tabellendatenquellen verwenden, die in SQL Server 2016 und höher integriert sind.
::: moniker-end

## <a name="ssrs-2016"></a>SSRS 2016

### <a name="reporting-services-includessrswebportal-non-markdownincludesssrswebportal-non-markdown-mdmd"></a>Reporting Services [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)]  

Ein neues [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)] ist verfügbar. Das aktualisierte Web-Portal enthält
- KPIs (Key Performance Indicators)
- Mobile Berichte
- Paginierte Berichte
- Excel-Dateien
- Power BI Desktop-Dateien

Das [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)] ersetzt den Berichts-Manager aus früheren Versionen.

Zum Erstellen mobiler Berichte ist [!INCLUDE[SS_MobileReptPub_Short](../includes/ss-mobilereptpub-short.md)]erforderlich.

Weitere Informationen zum [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)]finden Sie unter [Webportal (einheitlicher SSRS-Modus)](../reporting-services/web-portal-ssrs-native-mode.md).  

![ssRSPortal](../reporting-services/media/ssrsportal.png "ssRSPortal")  

#### <a name="custom-branding-for-the-includessrswebportal-non-markdownincludesssrswebportal-non-markdown-mdmd"></a>Benutzerdefiniertes Branding für [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)] 

Sie können jetzt das [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)] mit dem Logo und den Farben Ihres Unternehmens mithilfe eines Brandingpakets anpassen.  

Weitere Informationen zum benutzerdefinierten Branding finden Sie unter [Branding des Webportals](https://msdn.microsoft.com/6dac97f7-02a6-4711-81a3-e850a6b40bf1).

#### <a name="key-performance-indicators-kpi-in-the-includessrswebportal-non-markdownincludesssrswebportal-non-markdown-mdmd"></a>Key Performance Indicators (KPI) im [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)] 

Sie erstellen KPIs direkt in die [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)] , im Kontext mit dem aktuellen Ordner enthalten sind. Wenn Sie KPIs erstellen, können Sie Datasetfelder wählen und deren Werte zusammenfassen. Sie können auch verwandte Inhalte auswählen, um per Drillthrough zu weiteren Details zu gelangen.

![ssrs-webportal-kpi](../reporting-services/media/ssrs-webportal-kpi.png)

Weitere Informationen finden Sie unter [Arbeiten mit KPIs im Webportal](https://msdn.microsoft.com/a28cf500-6d47-4268-a248-04837e7a09eb).

### <a name="mobile-reports"></a>Mobile Berichte

Mobile Reporting Services-Berichte sind dedizierte Berichte, die für eine Vielzahl von Formfaktoren optimiert sind und eine optimale Erfahrung für Benutzer bieten, die auf mobilen Geräten auf Berichte zugreifen. Mobile Berichte stellen eine Reihe von Visualisierungen zur Verfügung – von Zeit-, Kategorie- und Vergleichsdiagrammen über Strukturkarten bis zu benutzerdefinierten Karten. Verbinden Sie Ihre mobilen Berichte mit einer Reihe von Datenquellen, einschließlich lokalen mehrdimensionalen und tabellarischen SQL Server Analysis Services-Daten. Sie können Felder für mobile Berichte auf einer Entwurfsoberfläche mit anpassbaren Rasterzeilen platzieren. Die flexiblen Elementen zentral automatisch jede Bildschirmgröße anpassen. Sie können speichern Sie die mobilen Berichte auf einem Reporting Services-Server, und anzeigen und interagieren mit ihnen in einem Browser oder mobile Power BI-app. Unterstützte Geräte enthalten:

- iPad
- iPhones
- Android-Smartphones
- oder von einem Windows 10-Gerät

#### <a name="mobile-report-publisher"></a>Publisher für mobile Berichte  

Mit dem [!INCLUDE[SS_MobileReptPub_Long](../includes/ss-mobilereptpub-long.md)]können Sie mobile SQL Server-Berichte in Ihrem [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssRSWebPortal-Non-Markdown](../includes/ssrswebportal-non-markdown-md.md)]erstellen und veröffentlichen.  

![SS_MRP_LayoutTabSmall](../reporting-services/media/ss-mrp-layouttabsm.png "SS_MRP_LayoutTabSmall")  

Weitere Informationen finden Sie unter [Erstellen und Veröffentlichen von mobilen Berichten mit dem Publisher für mobile Berichte von SQL Server](../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md).  

#### <a name="sql-server-mobile-reports-hosted-in-reporting-services-available-in-power-bi-mobile-app"></a>In Reporting Services gehostete mobile SQL Server-Berichte sind in der Power BI Mobile-App verfügbar  

Die Power BI Mobile-App für iOS auf dem iPad und iPhone kann jetzt auf dem lokalen Berichtsserver gehostete mobile SQL Server-Berichte anzeigen.  

![SS_MRP_iPad_HomeSm](../reporting-services/media/ss-mrp-ipad-homesm.png "SS_MRP_iPad_HomeSm")  

Sie können keine Standardverbindung herstellen, ohne einige Änderungen an der Konfiguration vorzunehmen. Weitere Informationen zum Herstellen der Verbindung zwischen der Power BI Mobile-App und dem Berichtsserver finden Sie unter [Aktivieren eines Berichtsservers für einen Zugang zu Power BI von Mobilgeräten](../reporting-services/report-server/enable-a-report-server-for-power-bi-mobile-access.md).

### <a name="support-of-sharepoint-mode-and-sharepoint-2016"></a>Unterstützen des SharePoint-Modus und von SharePoint 2016  

[!INCLUDE[ssSQL15](../includes/sssql15-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] unterstützt die Integration in SharePoint 2013 und SharePoint 2016.

Weitere Informationen finden Sie in den folgenden Themen:  

- [Supported Combinations of SharePoint and Reporting Services Server and Add-in (SQL Server 2016) (Unterstützte Kombinationen von SharePoint, Reporting Services-Server und -Add-In (SQL Server 2016))](../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)  

- [Verfügbarkeit des Reporting Services-Add-Ins für SharePoint-Produkte](../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)  

- [Installieren des SharePoint-Modus von Reporting Services](../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md)  

### <a name="microsoft-net-framework-4-support"></a>Microsoft .NET Framework 4-Unterstützung  

[!INCLUDE[ssRSCurrent-md](../includes/ssrscurrent-md.md)] unterstützt die aktuellen Versionen von Microsoft .NET Framework 4, einschließlich Version 4.0 und 4.5.1. Wenn keine Version von .NET Framework 4.x bereits installiert ist, wird .NET 4.0 vom Setup von [!INCLUDE[ssNoVersion-md](../includes/ssnoversion-md.md)] während der Installation von Features installiert.  

### <a name="report-improvements"></a>Verbesserungen an Berichten

**HTML 5-Rendering-Engine**: Es wurde eine neue HTML5-Rendering-Engine hinzugefügt, das auf „vollständige“ moderne Webstandardsmodi und moderne Browser ausgerichtet ist.  Die neue Rendering-Engine beruht nicht mehr auf dem Quirksmodus, der von einigen älteren Browsern verwendet wird.

Weitere Informationen zur Browserunterstützung von finden Sie unter [Browserunterstützung für Reporting Services und Power View](../reporting-services/browser-support-for-reporting-services-and-power-view.md).  

**Moderne paginierte Berichte:** Entwerfen Sie moderne paginierte Berichte mit neuen, modernen Formatvorlagen für Diagramme, Messgeräte, Karten und andere Datenvisualisierungen.

**Treemap- und Sunburst-Diagramme:** Verbessern Sie Ihre Berichte mit Diagrammen von Treemap ![ssrs_treemap_icon](../reporting-services/media/ssrs-treemap-icon.png "ssrs_treemap_icon") und Sunburst ![ssrs_sunburst_icon](../reporting-services/media/ssrs-sunburst-icon.png "ssrs_sunburst_icon"). Diese Diagramme stellen eine gute Möglichkeit zum Anzeigen von hierarchischen Daten dar. Weitere Informationen finden Sie unter [Strukturzuordnung und Sunburst-Diagramme in Reporting Services](../reporting-services/report-design/tree-map-and-sunburst-charts-in-reporting-services.md).  

**Berichtseinbettung:** Sie können jetzt mobile und paginierte Berichte in andere Webseiten und Anwendungen unter Verwendung eines IFRAMEs zusammen mit URL-Parametern einbetten.  

**Anheften von Berichtselementen an ein Power BI-Dashboard** : Bei der Anzeige eines Berichts im [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]können Sie Berichtselemente auswählen und sie an ein [!INCLUDE[sspowerbi](../includes/sspowerbi-md.md)] -Dashboard heften.   Die Elemente, die angeheftet werden können, sind Diagramme, Messgerätbereiche, Karten und Bilder. Folgende Aktionen sind möglich:

1. Wählen Sie die Gruppe, die das Dashboard enthält, die, dem Sie anheften möchten.
2. Wählen Sie das Dashboard, dem Sie das Element anheften möchten.
3. Wählen Sie, wie oft die Kachel im Dashboard aktualisiert werden soll.

![Hinweis](../analysis-services/instances/install-windows/media/ssrs-fyi-note.png "note") Die Aktualisierung wird von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Abonnements verwaltet, und nachdem das Element angehängt wurde, können Sie das Abonnement bearbeiten und einen anderen Aktualisierungszeitplan konfigurieren.

![ssRS_Pin_to_PowerBI](../reporting-services/media/ssrs-pin-to-powerbi.png) 

Weitere Informationen finden Sie unter [Power BI Report Server Integration (Configuration Manager) (Integration von Power BI-Berichtsserver (Configuration Manager))](../reporting-services/install-windows/power-bi-report-server-integration-configuration-manager.md) und [Pin Reporting Services items to Power BI Dashboards (Anheften von Reporting Services-Elementen an Power BI-Dashboards)](../reporting-services/pin-reporting-services-items-to-power-bi-dashboards.md).  

**PowerPoint-Rendering und -Export** : Das Microsoft PowerPoint-Format (PPTX) ist eine neue [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] -Renderingerweiterung. Sie können Berichte im PPTX-Format über die üblichen Anwendungen exportieren: Berichts-Generator, Berichts-Designer (in SSDT) und [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]. Für das Beispiel zeigt die folgende Abbildung das Exportmenü des [!INCLUDE[ssRSWebPortal](../includes/ssrswebportal.md)]s. 

![ssrs-export-powerpoint](../reporting-services/media/ssrs-export-powerpoint.png) 

Sie können auch das PPTX-Format für die Abonnementausgabe auswählen und den Zugriff auf die Berichtsserver-URL zum Rendern und Exportieren eines Berichts verwenden. Der folgende URL-Befehl in Ihrem Browser exportiert z. B. einen Bericht von einer benannten Instanz des Berichtsservers.  

```https
https://servername/ReportServer_THESQLINSTANCE/Pages/ReportViewer.aspx?%2freportfolder%2freport+name+with+spaces&rs:Format=pptx  
```  

Weitere Informationen finden Sie unter [Exportieren von Berichten über URL-Zugriff](../reporting-services/export-a-report-using-url-access.md).

**PDF ersetzt ActiveX für Remotedruckvorgänge:** nun gibt der Berichts-Viewer-Symbolleiste über PDF, anstelle von ActiveX-Steuerelemente. Der neue Bericht-Viewer wird von den meisten modernen Browsern, einschließlich Microsoft Edge unterstützt. Es müssen keine ActiveX-Steuerelemente heruntergeladen werden! Abhängig von des Browsers Sie verwenden und die Anwendungen und Dienste, die Sie installiert haben, die Anzeige von PDF [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ein Druckdialogfeld wird geöffnet, um den Bericht zu drucken, oder Sie werden aufgefordert, das Herunterladen einer. PDF-Datei. Als Administrator können Sie weiterhin das clientseitige Drucken über [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]deaktivieren.

Weitere Informationen finden Sie unter [Aktivieren und Deaktivieren des clientseitigen Drucks für Reporting Services](../reporting-services/report-server/enable-and-disable-client-side-printing-for-reporting-services.md).

![ssrs-pdf-printing](../reporting-services/media/ssrs-pdf-printing.png)

### <a name="subscription-improvements"></a>Abonnementverbesserungen  

|Funktion|Unterstützter Servermodus|  
|-------------|---------------------------|  
|**Aktivieren und Deaktivieren von Abonnements**. Neue Optionen der Benutzeroberfläche ermöglichen ein schnelles Deaktivieren und Aktivieren von Abonnements. Die deaktivierten Abonnements behalten ihre anderen Konfigurationseigenschaften, z. B. den Zeitplan, bei und können leicht aktiviert werden.<br /><br /> ![ssrs-enable-disable-subscriptions](../reporting-services/media/ssrs-enable-disable-subscriptions.png)<br /><br /> Weitere Informationen finden Sie unter [Deaktivieren oder Anhalten der Berichts- und Abonnementverarbeitung](../reporting-services/subscriptions/disable-or-pause-report-and-subscription-processing.md).|Einheitlicher Modus|  
|**Abonnementbeschreibung**. Wenn Sie ein neues Abonnement erstellen, können Sie jetzt eine Beschreibung des Berichts als Teil der Abonnementeigenschaften einbeziehen. Die Beschreibung ist auf der Seite zur Abonnementzusammenfassung enthalten.|SharePoint- und einheitlicher Modus|  
|**Ändern des Abonnementbesitzers**. Verbesserte Benutzeroberfläche zum schnellen Ändern des Besitzers eines Abonnements. Bei früheren Versionen von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] konnten Administratoren die Abonnementbesitzer mithilfe eines Skripts ändern. Ab Version [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] können Sie Abonnementbesitzer über die Benutzeroberfläche oder ein Skript ändern. Das Ändern des Abonnementbesitzers ist eine häufige Verwaltungsaufgabe, wenn Benutzer Ihr Unternehmen verlassen oder eine andere Funktion übernehmen.|SharePoint- und einheitlicher Modus|  
|**Freigegebene Anmeldeinformationen für Dateifreigabeabonnements**. Es gibt jetzt zwei Workflows mit [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Dateifreigabeabonnements:<br /><br /> In diesem Release kann Ihr [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Administrator nun ein einzelnes Dateifreigabekonto konfigurieren, das für mehrere Abonnements verwendet wird. Das dateifreigabekonto wird konfiguriert, der [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Konfigurations-Manager im einheitlichen Modus **ein dateifreigabekonto angeben**. Klicken Sie auf der abonnementkonfigurationsseite wählen Benutzer dann **dateifreigabekonto verwenden**.<br /><br /> Sie können einzelne Abonnements mit spezifischen Anmeldeinformationen für die Zieldateifreigabe konfigurieren.<br /><br /> Sie können beide Ansätze auch kombinieren, sodass einige Dateifreigabeabonnements das zentrale Dateifreigabekonto verwenden, während andere Abonnements bestimmte Anmeldeinformationen nutzen.|Einheitlicher Modus|

### <a name="sql-server-data-tools-ssdt"></a>SQL Server Data Tools (SSDT)

Die neue Version von SSDT enthält die Projektvorlagen für [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]: Berichtsserverprojekt-Assistent und Berichtsserverprojekt. Informationen zum Herunterladen von SSDT finden Sie unter [SQL Server Data Tools für Visual Studio 2015](https://go.microsoft.com/fwlink/?LinkId=827542).  

### <a name="report-builder-improvements"></a>Verbesserungen am Berichts-Generator

**Neue Benutzeroberfläche für den Berichts-Generator** : Die [!INCLUDE[ssRBnoversion](../includes/ssrbnoversion.md)] -Hauptbenutzeroberfläche weist jetzt ein modernes Layout mit optimierten UI-Elementen auf.  

|||  
|-|-|  
|eine neue|Previous|  
|![ssrs_rbfacelift_new](../reporting-services/media/ssrs-rbfacelift-new.png "ssrs_rbfacelift_new")|![ssrs_rbfacelift_old](../reporting-services/media/ssrs-rbfacelift-old.png "ssrs_rbfacelift_old")|  

**Benutzerdefinierter Parameterbereich** : Sie können jetzt den Parameterbereich anpassen. Mithilfe der Entwurfsoberfläche im Berichts-Generator, können Sie einen Parameter zu einer bestimmten Spalte und Zeile im Parameterbereich ziehen. Sie können Spalten hinzufügen und entfernen, um das Layouts des Bereichs zu ändern. Weitere Informationen finden Sie unter [Benutzerdefiniertes Anpassen des Parameterbereichs in einem Bericht &#40;Berichts-Generator&#41;](../reporting-services/report-design/customize-the-parameters-pane-in-a-report-report-builder.md)erstellen.  

![Parameterliste im Berichtsdaten- und Parameterbereich](../reporting-services/media/ssrs-customizeparameter-parameterlist-reportdatapane.png "Parameter list in Report Data pane and in parameters pane")  

**Unterstützung hoher DPI-Werte:** [!INCLUDE[ssRBnoversion](../includes/ssrbnoversion.md)] unterstützt die Skalierung sowie Geräte mit hohen DPI-Werten (Punkte pro Zoll).  Weitere Informationen zu hohen DPI-Werten finden Sie in folgenden Themen:  

- [Windows 8.1 DPI Scaling Enhancements (Erweiterungen für Windows 8.1 DPI-Skalierung)](https://blogs.windows.com/windowsexperience/2013/07/15/windows-8-1-dpi-scaling-enhancements/)  

- [Hohe DPI-Werte und Windows 8.1](https://technet.microsoft.com/library/dn528848.aspx)  

## <a name="next-steps"></a>Nächste Schritte

[Neuigkeiten in Analysis Services](https://msdn.microsoft.com/aa69c299-b8f4-4969-86d8-b3292fe13f08)  
[Abwärtskompatibilität](reporting-services-backward-compatibility.md)  
[Von den SQL Server-Editionen unterstützte Reporting Services-Features](../reporting-services/reporting-services-features-supported-by-the-editions-of-sql-server-2016.md)  
[Aktualisieren und Migrieren von Reporting Services](../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)  
[Reporting Services](../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md)  

Haben Sie dazu Fragen? [Stellen Sie eine Frage im Reporting Services-Forum](https://go.microsoft.com/fwlink/?LinkId=620231)
