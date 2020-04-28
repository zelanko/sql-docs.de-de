---
title: Vergleichen Sie Business Intelligence-Funktionen in verschiedenen Microsoft-Umgebungen | Microsoft-Dokumentation
ms.prod: sql-server-2014
ms.technology: reporting-services-native
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 12/15/2019
ms.openlocfilehash: a5f9e9b52186a2d4569ac30a591ae95acfa36101
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "75656587"
---
# <a name="compare-business-intelligence-capabilities-in-different-microsoft-environments"></a>Vergleichen von Business Intelligence-Funktionen in verschiedenen Microsoft-Umgebungen

Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Business Intelligence kann in verschiedenen Umgebungen eingesetzt werden, einschließlich [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] SharePoint Server, SharePoint Online und Power BI für Office 365. In diesem Thema werden die Komponenten und Funktionen, die in jeder Umgebung unterstützt werden, verglichen.  
  
Weitere Informationen zum Vergleich von SharePoint Server und SharePoint Online finden Sie unter [Vergleichen von SharePoint-Plänen und -Optionen](https://products.office.com/SharePoint/compare-sharepoint-plans).  
  
## <a name="author-and-manage-bi-reports-and-dashboards"></a>Erstellen und Verwalten von BI-Berichten und Dashboards  
  
||SQL Server 2014 & SharePoint Server 2013|SharePoint Online-Plan 2|Power BI für Office 365|  
|-|----------------------------------------------|------------------------------|-----------------------------|  
|BI-Websites|[!INCLUDE[ssGemini](../includes/ssgemini-md.md)] Galerie|Nein|Power BI-Website|  
|Data Stewardship und Abfragefreigabe und -verwaltung|Nein|Nein|Ja ** <sup>1</sup>**|  
|Integration in Master Data Services (MDS) und Data Quality Services (DQS)|Ja|Nein|Nein|  
|Planmäßige Datenaktualisierung|Ja, aber unterstützt keine Arbeitsmappen, die Power Query-Daten enthalten|Nein |Ja|  
|Abfragen in natürlicher Sprache (Q&A)|Nein|Nein|Ja ** <sup>2</sup>**|  
|Prädiktive Prognose|Nein|Nein|Ja ** <sup>3</sup>**|  
|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Integration|Ja|Nein|Nein|  
|[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Integration (mehrdimensional und tabellarisch)|Ja|Nein|Nein|  
|Exportieren interaktiver Power View-Dashboards in PowerPoint-Präsentationen|Ja|Nein|Nein|  
|Erstellen von Dashboards im Browser|Ja|Nein|Nein|  
|Überwachung der Verwendung|Ja|Nein |Ja|  
|Nutzen zeilenbasierter Sicherheit von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] -Cubes|Ja|Nein|Nein|  
|||||

 **<sup>1</sup>**  [Grundlegendes zur Rolle von Data Stewards in der Datenverwaltung](https://support.office.com/Article/Understanding-the-Role-of-Data-Stewards-in-Data-Management-ae3352f3-4389-45e8-a682-7fd6edb92524?ui=en-US&rs=en-US&ad=US) und [Video: Power BI-Informationsverwaltung und Data Stewardship](https://www.youtube.com/watch?v=8dHOj68ts7c).  
  
 **<sup>2</sup>**  [Power BI Q&a: Optimieren einer Power BI Arbeitsmappe (cloudmodellierung)](https://powerbi.microsoft.com/nl-nl/blog/new-in-power-bi-cloud-modeling-for-q-and-a/).  
  
 **<sup>3</sup>**  [Einführung in neuer Prognosefunktionen in Power View für Office 365](https://blogs.msdn.com/b/powerbi/archive/2014/05/08/introducing-new-forecasting-capabilities-in-power-view-for-office-365.aspx).  
  
## <a name="view-and-browse-bi-data-reports-and-dashboards"></a>Anzeigen und Durchsuchen von BI-Daten, Berichten und Dashboards  
  
||SQL Server 2014 & SharePoint Server 2013|SharePoint Online-Plan 2|Power BI für Office 365|  
|-|----------------------------------------------|------------------------------|-----------------------------|  
|Anzeigen von Microsoft Excel-Arbeitsmappen in einem Browser|Ja, wenn die Arbeitsmappe weniger als 2 GB groß ist|Ja, wenn die Arbeitsmappe weniger als 10 GB groß ist|Ja, wenn die Arbeitsmappe weniger als 250 GB groß ist|  
|Durchsuchen von Daten im Browser in HTML5|Nein|Nein |Ja|  
|Mobil-BI-App für den Remotezugriff auf Berichte und Dashboards|Nein|Nein|Ja ** <sup>1</sup>**|  
|Excel-Arbeitsmappe mit [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] als Datenquelle **<sup>2</sup>**|Ja|Nein|Nein|  
|Features in verschiedenen Browsern und Versionen verwenden|Ja, für Nicht-Power View-Visualisierungen **<sup>3</sup>**|Ja, für Arbeitsmappen mit Dateigrößen von weniger als 10 MB **<sup>3</sup>**|Ja ** <sup>3</sup>**|  
|||||

 **<sup>1</sup>**  [Microsoft Power BI](https://apps.microsoft.com/windows/app/microsoft-power-bi/b7e7c94d-2ea3-4fa6-a277-9d19a1f697ba).  
  
 **<sup>2</sup>**  [PowerPivot-Arbeitsmappen als Datenquelle](https://support.office.com/article/Power-Pivot-Powerful-data-analysis-and-data-modeling-in-Excel-A9C2C6E2-CC49-4976-A7D7-40896795D045)  
  
 **<sup>3</sup>**  [Mobilunterstützung von Business Intelligence (BI)-Tools](https://msdn.microsoft.com/library/dn151146\(v=sql.110\).aspx) and [Planung für Reporting Services und Power View-Browserunterstützung (Reporting Services 2014)](https://msdn.microsoft.com/library/ms156511.aspx).  
  
## <a name="more-information"></a>Weitere Informationen  
  
- [BI-Funktionen in Excel und Office 365](https://support.office.com/article/BI-capabilities-in-Excel-and-Office-365-26c0548e-124c-4fd3-aab3-5f64568cb743).  
  
- Informationen zu den Anforderungen zum Verwenden von Synonymen finden Sie unter [Optimieren von Power BI Q-&A mit Synonymen & formulieren](https://blog.pragmaticworks.com/optimizing-power-bi-qa-with-synonyms-phrasing-using-cloud-modeling) unter pragmaticworks.com.  
  
- [Office Online, wählen Sie Ihr soziales Unternehmensnetzwerk: Yammer oder Newsfeed?](https://support.office.com/article/Pick-your-enterprise-social-network-Yammer-or-Newsfeed-21954c85-4384-47d4-96c2-dfa1c9d56e66?ui=en-US&rs=en-US&ad=US)aus.  
  
- [Power BI für Office 365](https://www.microsoft.com/powerbi/default.aspx).  
  
- [Power BI Preise](https://www.microsoft.com/powerBI/pricing.aspx).  
  
- [Analyse und Berichterstellung mit Microsoft Business Intelligence-Tools (BI)](../reporting-services/choosing-microsoft-business-intelligence-bi-tools-for-analysis-and-reporting.md)  
  
## <a name="community-content"></a>Community-Inhalt

