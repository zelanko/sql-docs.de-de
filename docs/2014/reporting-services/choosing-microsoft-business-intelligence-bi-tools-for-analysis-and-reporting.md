---
title: Analyse und Berichterstellung mit Microsoft Business Intelligence-Tools (BI)
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.prod: sql-server-2014
ms.technology: reporting-services
ms.prod_service: reporting-services-native, reporting-services-sharepoint
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: 7c76ec1a74032b5f35bc42ab4a901d95574e0900
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "75688216"
---
# <a name="analysis-and-reporting-with-microsoft-business-intelligence-bi-tools"></a>Analyse und Berichterstellung mit Microsoft Business Intelligence-Tools (BI)

  In der folgenden Tabelle werden die verschiedenen Arbeitsauslastungen für Datenanalyse und Berichterstellung den Microsoft BI-Tools zugeordnet, die für diese Arbeitsauslastungen am besten geeignet sind.  
  
 So können Sie anhand der Tabelle das Tool wählen, das Ihre Anforderungen am besten erfüllt. Um weitere Informationen zu einem Produkt zu erhalten, klicken Sie auf den Produktlink in der Tabelle.  
  
 Wenn Sie für die Suche nach den richtigen Tools eine kurze Übersicht benötigen, informieren Sie sich unter [Einführung in Microsoft Business Intelligence (BI)-Tools](https://www.digitalvidya.com/blog/introduction-to-microsoft-power-bi/).  
  
|Workloads|Benutzer|||BI-Tools|||  
|---------------|----------|-|-|--------------|-|-|  
|||**Excel**|**SharePoint**|**SharePoint Online**|**Power BI**|**SQL Server**|  
|**Self-Service-BI**|Analyst/Endbenutzer||||||  
|Einfache Suche und einfacher Zugriff auf öffentliche und Unternehmensdaten||[Power Query](https://go.microsoft.com/fwlink/p/?LinkId=391845)||[Azure Data Catalog](https://azure.microsoft.com/services/data-catalog/)<br /><br />||  
|Erstellen leistungsstarker Datenmodelle||[Power Pivot](https://support.office.com/article/power-pivot-overview-and-learning-f9001958-7901-4caa-ad80-028a6d2432ed?ui=en-US&rs=en-US&ad=US)|||[Power BI Desktop](https://powerbi.microsoft.com/documentation/powerbi-desktop-get-the-desktop/)||  
|Ausführen von Self-Service-Vorhersageanalysen||||||[Data Mining-Add-Ins für Excel](../analysis-services/data-mining-client-for-excel-sql-server-data-mining-add-ins.md)|  
|Visualisieren und Untersuchen von Daten||[Power View](https://go.microsoft.com/fwlink/p/?LinkId=391847)<br /><br /> [3D-Karten](https://support.office.com/article/visualize-your-data-in-3d-maps-ce6b1d5c-4602-4dae-b487-91ec0268e75d)|||||  
|Fragen mithilfe von Abfragen in natürlicher Sprache|||||[Q & A](https://docs.microsoft.com/power-bi/consumer/end-user-q-and-a)||  
|Zugreifen auf Berichte über mobile Geräte||||[HTML 5 (unterstützt die Anzeige <10-MB-Dateien)](https://go.microsoft.com/fwlink/p/?LinkId=391853)|[HTML 5 (unterstützt die Anzeige <250 MB)](https://go.microsoft.com/fwlink/p/?LinkId=391854)<br /><br /> [Power BI Mobile App auf IOS-Geräten](https://docs.microsoft.com/power-bi/consumer/mobile/mobile-iphone-app-get-started)<br /><br /> [Power BI Mobile App auf Android-Geräten](https://docs.microsoft.com/power-bi/consumer/mobile/mobile-android-app-get-started) <br /><br />[Power BI Mobile App für Windows 10](https://docs.microsoft.com/power-bi/consumer/mobile/mobile-windows-10-phone-app-get-started)||  
|Zusammenarbeit und gemeinsame Nutzung|||[SharePoint-Sites](https://go.microsoft.com/fwlink/p/?LinkId=391849)|[SharePoint-Team Websites](https://go.microsoft.com/fwlink/p/?LinkId=391850)|[Power BI Websites](https://docs.microsoft.com/power-bi/service-how-to-collaborate-distribute-dashboards-reports)||  
|**Unternehmens-BI**|IT-Profi||||||  
|Erstellen mehrdimensionaler/tabellarischer Unternehmensmodelle||||||[Analysis Services](https://docs.microsoft.com/analysis-services/analysis-services-overview)|  
|Erstellen von Ad-hoc-Datenvisualisierungen|||[Power View für SharePoint](https://go.microsoft.com/fwlink/p/?LinkId=391858)||||  
|Erstellen von Dashboards|||[SharePoint-Dashboards](https://go.microsoft.com/fwlink/p/?LinkId=391859)<br /><br /> [PerformancePoint-Dienste](https://technet.microsoft.com/library/ee424392.aspx)||||  
|Erstellen von Betriebsberichten||||||<sup>1</sup> [Reporting Services](create-deploy-and-manage-mobile-and-paginated-reports.md)|  
|Erstellen benutzerdefinierter und eingebetteter Berichte||||||<sup>1</sup> [Reporting Services](create-deploy-and-manage-mobile-and-paginated-reports.md)|  
|**Erweiterte Analyse**|Data Scientist||||||  
|Ausführen von Self-Service-Vorhersageanalysen||||||[Data Mining-Add-Ins für Excel](https://msdn.microsoft.com/library/dn282385\(v=sql.120\).aspx)|  
|Verwenden von Data Mining-Algorithmen||||||[Data Mining in Analysis Services](https://technet.microsoft.com/library/bb510516\(v=sql.120\).aspx)|  
  
 <sup>1</sup> Reporting Services verfügt über eine Reihe von Funktionen, die die Bereitstellung von Betriebs Berichten und benutzerdefinierten Berichten wie Abonnements und Daten Warnungen unterstützen.