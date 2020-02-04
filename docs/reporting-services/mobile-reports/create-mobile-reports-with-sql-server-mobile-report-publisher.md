---
title: Erstellen und Veröffentlichen von mobilen Berichten mit dem Publisher für mobile Berichte von SQL Server | Microsoft-Dokumentation
description: Erfahren Sie mehr über mobile Reporting Services-Berichte für mobile Geräte, die mit lokalen Daten verbunden sind und über eine Sammlung von Datenvisualisierungen verfügen.
ms.date: 12/06/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: mobile-reports
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: a5a8dbf6-4c3a-435d-8188-d6656c32f229
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 51708fc41bb154fcf67ac3a21bd6680c69e2f2c2
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "63200536"
---
# <a name="create-mobile-reports-with-sql-server-mobile-report-publisher"></a>Erstellen und Veröffentlichen von mobilen Berichten mit dem Publisher für mobile Berichte von SQL Server
Erfahren Sie mehr über mobile [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] -Berichte, die für mobile Geräte optimiert sind, mit lokalen Daten verbunden sind und über eine Sammlung von Datenvisualisierungen verfügen. 

>[!NOTE]
>  Müssen Sie Datazen-Serverinhalte wie Dashboards und KPIs zu einem SQL Server [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)]-Server migrieren? Versuchen Sie es mit dem [SQL Server Migration Assistant für Datazen](https://www.microsoft.com/download/details.aspx?id=53128). 
 
![SS_MRP_LayoutTabSm](../../reporting-services/media/ss-mrp-layouttabsm.png)  

Mit [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-long.md)]können Sie schnell mobile [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] -Berichte erstellen, die für mobile Geräte und eine Vielzahl anderer Formfaktoren optimiert sind. Mobile Berichte stellen eine Reihe von Visualisierungen zur Verfügung, von Zeit-, Kategorie- und Vergleichsdiagrammen über Treemap-Diagramme bis hin zu benutzerdefinierten Karten. 

* Verbinden Sie Ihre mobilen Berichte mit einer Reihe von Datenquellen, einschließlich lokalen SQL Server- und Analysis Services-Daten. 
* Gestalten Sie Ihre mobilen Berichte auf einer Entwurfsoberfläche mit anpassbaren Rasterzeilen und -spalten und flexiblen Elementen für mobile Berichte, die sich gut auf jede Bildschirmgröße skalieren lassen. 
* Speichern Sie diese mobilen Berichte anschließend auf einem Reporting Services-Server, und verwenden Sie zum Anzeigen bzw. Interagieren mit diesen einen Browser oder die mobile Power BI-App auf iPads, iPhones, Android-Telefonen und -Tablets und Windows 10-Geräten.
  
## <a name="create-includessrsnoversion_mdincludesssrsnoversion-mdmd--mobile-reports"></a>Erstellen von mobilen [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)]  -Berichten  
  
Diese Artikel helfen Ihnen beim Einstieg.
-  Download des [Publishers für mobile Berichte von SQL Server](https://go.microsoft.com/fwlink/?LinkID=733527)  
-  [Create a Reporting Services mobile report (Erstellen eines mobilen Berichts in Reporting Services)](../../reporting-services/mobile-reports/create-a-reporting-services-mobile-report.md)  
-  [End-to-end walkthrough: Create mobile reports and KPIs in SQL Server 2016 Reporting Services](https://christopherfinlan.com/2015/12/21/how-to-create-mobile-reports-and-kpis-in-sql-server-reporting-services-2016-an-end-to-end-walkthrough/) (Durchgängige exemplarische Vorgehensweise: Erstellen mobiler Berichte und KPIs in SQL Server Reporting Services) (Blog von Christopher Finlan)  
- [„Erst Entwurf“ oder „Erst Daten“](../../reporting-services/mobile-reports/design-first-or-data-first-when-creating-in-reporting-services-mobile-reports.md): Entscheiden Sie, ob Sie den Bericht zuerst mit simulierten Daten entwerfen oder mit Ihren eigenen Daten beginnen.  
- [Daten für mobile Reporting Services-Berichte](../../reporting-services/mobile-reports/data-for-reporting-services-mobile-reports.md): Verwenden Sie Daten aus freigegebenen Datasets, oder bereiten Sie Daten aus Excel-Arbeitsmappen auf das Verwenden in Ihren mobilen Berichten vor.
- [How data refresh works in mobile reports and KPIs in Reporting Services (Funktionsweise der Aktualisierung der Daten in mobilen Berichte und KPIs in Reporting Services)](https://christopherfinlan.com/2016/02/10/so-refreshinghow-data-refresh-works-with-mobile-reports-and-kpis-in-reporting-services/) (Christopher Finlans Blog): Erfahren Sie mehr über das Einrichten der Zwischenspeicherung für freigegebene Datasets, um zu steuern, wie oft Daten aktualisiert werden, und um die Berichterstellung zu beschleunigen.
- [Visualisierungen in mobilen Berichten](../../reporting-services/mobile-reports/add-visualizations-to-reporting-services-mobile-reports.md)
- [Messgeräte in mobilen Berichten](../../reporting-services/mobile-reports/add-gauges-to-mobile-reports-reporting-services.md)
- [Karten in mobilen Berichten](../../reporting-services/mobile-reports/maps-in-reporting-services-mobile-reports.md)
- [Branding Ihres Webportals und mobiler Berichte](../../reporting-services/branding-the-web-portal.md) mit den Farben und dem Logo Ihres Unternehmens
  
## <a name="ssrs-mobile-reports-in-the-power-bi-mobile-apps"></a>Mobile SSRS-Berichte in den mobilen Power BI-Apps

-  Weitere Informationen finden Sie unter [Anzeigen lokaler Berichte und KPIs eines Berichtsservers in den mobilen Power BI-Apps](https://powerbi.microsoft.com/documentation/powerbi-mobile-iphone-kpis-mobile-reports) für iOS- und Android-Geräte
-  Weitere Informationen finden Sie unter [Anzeigen von mobilen SSRS-Berichten (Reporting Services) und -KPIs in der mobilen Power BI-App für Windows 10](https://powerbi.microsoft.com/documentation/powerbi-mobile-win10-kpis-mobile-reports/)   

## <a name="see-also"></a>Weitere Informationen  
  
-   [Erstellen, Ändern und Löschen von freigegebenen Datenquellen (SSRS)](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md)  
-   [Verwalten von freigegebenen Datasets](../../reporting-services/report-data/manage-shared-datasets.md)  
-  [Working with KPIs in Reporting Services (Arbeiten mit KPIs in Reporting Services)](../../reporting-services/working-with-kpis-in-reporting-services.md)  
- [Aktivieren eines Berichtsservers für einen Zugang zu Power BI von Mobilgeräten](../../reporting-services/report-server/enable-a-report-server-for-power-bi-mobile-access.md)  

  
  

