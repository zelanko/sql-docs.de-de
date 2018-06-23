---
title: Vergleichen von Business Intelligence-Funktionen In verschiedenen Microsoft-Umgebungen | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1fb759ee-8172-4c4c-9f7d-49af2c731006
caps.latest.revision: 18
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: ae54486aa141880189a012d897251604a292aefe
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36159956"
---
# <a name="compare-business-intelligence-capabilities-in-different-microsoft-environments"></a>Vergleichen von Business Intelligence-Funktionen in verschiedenen Microsoft-Umgebungen
  Microsoft [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Business Intelligence kann in einer Reihe von verschiedenen Umgebungen einschließlich eingesetzt werden [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] mit SharePoint-Server, SharePoint Online und Power BI für Office 365. In diesem Thema werden die Komponenten und Funktionen, die in jeder Umgebung unterstützt werden, verglichen.  
  
 Weitere Informationen zum Vergleich von SharePoint Server und SharePoint Online finden Sie unter [Vergleichen von SharePoint-Plänen und -Optionen](http://products.office.com/SharePoint/compare-sharepoint-plans).  
  
## <a name="author-and-manage-bi-reports-and-dashboards"></a>Erstellen und Verwalten von BI-Berichten und Dashboards  
  
||SQL Server 2014 und SharePoint Server 2013|SharePoint Online-Plan 2|Power BI für Office 365|  
|-|----------------------------------------------|------------------------------|-----------------------------|  
|BI-Websites|[!INCLUDE[ssGemini](../includes/ssgemini-md.md)] Galerie|nein|Power BI-Website|  
|Data Stewardship und Abfragefreigabe und -verwaltung|nein|nein|Ja  **<sup>1</sup>**|  
|Integration in Master Data Services (MDS) und Data Quality Services (DQS)|ja|nein|nein|  
|Planmäßige Datenaktualisierung|Ja, aber unterstützt keine Arbeitsmappen, die Power Query-Daten enthalten|nein|ja|  
|Abfrage in natürlicher Sprache (Fragen und Antworten)|nein|nein|Ja  **<sup>2</sup>**|  
|Prädiktive Prognose|nein|nein|Ja  **<sup>3</sup>**|  
|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]-Integration|ja|nein|nein|  
|[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Integration (mehrdimensional und tabellarisch)|ja|nein|nein|  
|Exportieren interaktiver Power View-Dashboards in PowerPoint-Präsentationen|ja|nein|nein|  
|Erstellen von Dashboards im Browser|ja|nein|nein|  
|Überwachung der Verwendung|ja|nein|ja|  
|Nutzen zeilenbasierter Sicherheit von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Cubes|ja|nein|nein|  
  
 **<sup>1</sup>**[Grundlegendes zur Rolle von Data Stewards in der Datenverwaltung](https://support.office.com/Article/Understanding-the-Role-of-Data-Stewards-in-Data-Management-ae3352f3-4389-45e8-a682-7fd6edb92524?ui=en-US&rs=en-US&ad=US) und [Video: Power BI-Informationsverwaltung und Data Stewardship](https://www.youtube.com/watch?v=8dHOj68ts7c).    
  
 **<sup>2</sup>**[Power BI Q & A: Optimieren der Power BI-Arbeitsmappe (cloudmodellierung)](https://support.office.com/article/Power-BI-Q-A-Optimize-a-Power-BI-workbook-cloud-modeling--96dc5941-d0f1-44e2-9d9d-c038a3a55849?ui=en-US&rs=en-US&ad=US).    
  
 **<sup>3</sup>**[Einführung in neuer Prognosefunktionen in Power View für Office 365](http://blogs.msdn.com/b/powerbi/archive/2014/05/08/introducing-new-forecasting-capabilities-in-power-view-for-office-365.aspx).    
  
## <a name="view-and-browse-bi-data-reports-and-dashboards"></a>Anzeigen und Durchsuchen von BI-Daten, Berichten und Dashboards  
  
||SQL Server 2014 und SharePoint Server 2013|SharePoint Online-Plan 2|Power BI für Office 365|  
|-|----------------------------------------------|------------------------------|-----------------------------|  
|Anzeigen von Microsoft Excel-Arbeitsmappen in einem Browser|Ja, wenn die Arbeitsmappe weniger als 2 GB groß ist|Ja, wenn die Arbeitsmappe weniger als 10 GB groß ist|Ja, wenn die Arbeitsmappe weniger als 250 GB groß ist|  
|Durchsuchen von Daten im Browser in HTML5|nein|nein|ja|  
|Mobil-BI-App für den Remotezugriff auf Berichte und Dashboards|nein|nein|Ja  **<sup>1</sup>**|  
|Excel-Arbeitsmappe mit [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] als Datenquelle  **<sup>2</sup>**|ja|nein|nein|  
|Features in verschiedenen Browsern und Versionen verwenden|Ja, für nicht - Power View-Visualisierungen  **<sup>3</sup>**|Ja, für die Arbeitsmappe mit Dateigrößen von weniger als 10 MB  **<sup>3</sup>**|Ja  **<sup>3</sup>**|  
  
 **<sup>1</sup>**[Microsoft Power BI](http://apps.microsoft.com/windows/app/microsoft-power-bi/b7e7c94d-2ea3-4fa6-a277-9d19a1f697ba).    
  
 **<sup>2</sup>**[PowerPivot-Arbeitsmappen als Datenquelle  ](http://blogs.technet.com/b/excel_services__powerpivot_for_sharepoint_support_blog/archive/2013/02/15/powerpivot-workbook-as-a-data-source.aspx)  
  
 **<sup>3</sup>**[mobilunterstützung von Business Intelligence (BI)-Tools](http://msdn.microsoft.com/library/dn151146\(v=sql.110\).aspx) und [Planung für Reporting Services und Power View-Browserunterstützung (Reporting Services 2014)](http://msdn.microsoft.com/library/ms156511.aspx).    
  
## <a name="more-information"></a>Weitere Informationen  
  
-   [Business Intelligence-Funktionen in Excel, SharePoint Online und Power BI für Office 365](https://technet.microsoft.com/en-us/library/dn198235.aspx).  
  
-   Informationen zu den Voraussetzungen zum Verwenden von Synonymen finden Sie unter [Synonyme zu einem Power Pivot-Excel-Datenmodell hinzufügen](https://support.office.com/Article/Add-synonyms-to-a-Power-Pivot-Excel-data-model-345f4f5b-5ec2-4998-bc46-a26bdc0810b6?ui=en-US&rs=en-US&ad=US).  
  
-   [Office Online, wählen Sie Ihr soziales Unternehmensnetzwerk: Yammer oder Newsfeed? ](https://support.office.com/article/Pick-your-enterprise-social-network-Yammer-or-Newsfeed-21954c85-4384-47d4-96c2-dfa1c9d56e66?ui=en-US&rs=en-US&ad=US).  
  
-   [Power BI für Office 365](http://www.microsoft.com/powerbi/default.aspx).  
  
-   [Power BI-Preise](http://www.microsoft.com/powerBI/pricing.aspx).  
  
-   [Vergleich einer BI Center-Website mit Power BI für Office 365-Websites](http://technet.microsoft.com/library/dn394343\(v=office.15\).aspx).  
  
-   [Einführung in Microsoft BI-Berichterstellungs- und Analysetools](http://go.microsoft.com/fwlink/p/?LinkId=617093)  
  
## <a name="community-content"></a>Community-Inhalt  
 [Microsoft Self-Service-BI: lokal versus Cloud](http://businessintelligist.com/2014/02/07/microsoft-self-service-bi-on-premise-vs-could/).  
  
  