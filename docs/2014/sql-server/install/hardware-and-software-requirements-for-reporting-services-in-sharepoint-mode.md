---
title: Hardware-und Software Anforderungen für Reporting Services im SharePoint-Modus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ed91877d-4f74-4266-a932-b824b4810c99
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 56ddfce4fc1812e99870c22eeb0e15be64c5decb
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/19/2019
ms.locfileid: "75245627"
---
# <a name="hardware-and-software-requirements-for-reporting-services-in-sharepoint-mode"></a>Hardware- und Softwareanforderungen für Reporting Services im SharePoint-Modus

  In diesem Thema werden die Voraussetzungen, Hardwareanforderungen und über [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Legungen zur Installation für die Ausführung im SharePoint-Modus beschrieben. Da der SharePoint-Modus von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] einen SharePoint-Server erfordert, liegt den meisten Anforderungen die SharePoint-Umgebung zugrunde. Für Berichtsserver im einheitlichen Modus muss die vorhandene Hardware die Mindestanforderungen an die Hardware und Software zum Ausführen von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]erfüllen. Weitere Informationen finden Sie unter [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   [Voraussetzungen](#bkmk_prereq)  
  
-   [Anforderungen für die Berichtsserver-Datenbank](#bkmk_report_server_database)  
  
-   [Power View-Anforderungen](#bkmk_powerview)  
  
-   [Weitere Informationen](#bkmk_more_information)  
  
##  <a name="bkmk_prereq"></a>Voraussetzung  
  
-   Bei lokalen Installationen muss das Konto, das sich während der Installation von SharePoint und [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] angemeldet hat, Mitglied der Administratorgruppe im lokalen Betriebssystem sein. Das Setupkonto muss kein Mitglied der Administratorgruppe für die SharePoint-Farm sein.  
  
     Weitere Informationen finden Sie unter [Account permissions and security settings in SharePoint 2013](https://technet.microsoft.com/library/cc678863.aspx).  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]das Ausführen von im SharePoint-Modus erfordert SharePoint Server. Weitere Informationen zu SharePoint-Anforderungen und -Konfigurationen finden Sie unter:  
  
    -   [Hardware-und Softwareanforderungen (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=256365) (https://go.microsoft.com/fwlink/p/?LinkId=256365)  
  
    -   [Kapazitätsmanagement und Größenanpassung für SharePoint Server 2013](https://technet.microsoft.com/library/cc261700.aspx)  
  
    -   [Softwareanforderungen für Business Intelligence (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=256367)  
  
    -   [Hardware- und Softwareanforderungen (SharePoint Server 2010).](https://technet.microsoft.com/library/cc262485\(v=office.14\))  
  
    -   [Kapazitätsmanagement und Größenanpassung für SharePoint Server 2010](https://technet.microsoft.com/library/cc261700.aspx\(v=office.14\))  
  
-   Wenn Sie die vorhandene [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint-Installation mit [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]aktualisieren möchten (Upgrade oder Update), informieren Sie sich unter [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md)erfüllen.  
  
-   Überprüfen Sie, ob der **SharePoint 2013-Administration** -Dienst im Windows Server-Manager gestartet wurde.  
  
###  <a name="bkmk_report_server_database"></a>Anforderungen an die Berichts Server-Datenbank  
  
-   Sowohl [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] als auch SharePoint-Produkte und -Technologien verwenden relationale SQL Server-Datenbanken zum Speichern von Anwendungsdaten.  
  
-   [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]erfordert eine Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] einer kompatiblen SQL Server Edition. Weitere Informationen zu Hardware- und Softwareanforderungen finden Sie unter [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   SharePoint-Produkte können eine vorhandene Datenbankinstanz verwenden. Falls keine Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] installiert ist, installiert das Setupprogramm für SharePoint-Produkte die SQL Server Express-Edition für die SharePoint-Anwendungsdatenbanken.  
  
-   Die SQL Server Express-Edition kann nicht für die Datenbank der Berichtsserverinstanz verwendet werden. Die mit dem SharePoint-Produkt installierte Instanz der SQL Server Express Edition kann jedoch parallel mit anderen Datenbank-Engine-Editionen ausgeführt werden.  
  
##  <a name="bkmk_powerview"></a>[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] Anforderungen

 Lesen Sie die aktuelle [Power View-Dokumentation](https://office.microsoft.com/excel-help/power-view-explore-visualize-and-present-your-data-HA102835634.aspx) auf Office.Microsoft.com. [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]ist eine Funktion von Microsoft Excel 2013 und ist Teil des [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Reporting Services-Add-Ins für Microsoft SharePoint Server 2010 und 2013 Enterprise Editions.  
  
##  <a name="bkmk_more_information"></a>Weitere Informationen

 Weitere Informationen zu SharePoint-Änderungen finden [Sie unter Änderungen von SharePoint 2010 zu SharePoint 2013](https://technet.microsoft.com/library/ff607742\(office.15\).aspx) (https://technet.microsoft.com/library/ff607742(office.15).aspx).  
  
 [Anmerkungen zu dieser Version von SQL Server 2014](https://go.microsoft.com/fwlink/?LinkID=296445).  
  
