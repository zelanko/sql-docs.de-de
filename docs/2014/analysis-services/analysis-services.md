---
title: Analysis Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, about Analysis Services - Multidimensional Data
- SSAS
- Analysis Services
- SQL Server Analysis Services, about Analysis Services - Multidimensional Data
- SQL Server Analysis Services
- multidimensional data [Analysis Services]
- SSAS, about Analysis Services - Multidimensional Data
ms.assetid: 49d186f4-4b4d-4a5a-bb1a-e2699c64a731
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 241bb57ffd0ce05f1daa289cc7ae78c365a27cc9
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66062341"
---
# <a name="analysis-services"></a>Analysis Services
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ist eine analytische Online-Daten-Engine, die in Lösungen für Decision Support und Business Intelligence (BI) zur Anwendung kommt und analytische Daten für Geschäftsberichte und Clientanwendungen wie Excel, Reporting Services-Berichte und andere BI-Tools von Drittanbietern bereitstellt. Ein typischer Workflow für [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] beinhaltet die Erstellung eines OLAP- oder eines tabellarischen Datenmodells, die Bereitstellung des Modells als Datenbank in einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Instanz und die Bearbeitung der Datenbank, um Daten in diese zu laden, und dann Berechtigungen zum Datenzugriff zuzuweisen. Wenn dieser abgeschlossen ist, kann jede Anwendung, die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] als Datenquelle unterstützt, auf dieses Mehrzweckdatenmodell zugreifen.  
  
 Um ein Modell zu erstellen, verwenden Sie SQL Server Data Tools (siehe [in Analysis Services verwendete Tools und Anwendungen](tools-and-applications-used-in-analysis-services.md)), Auswählen einer tabellarischen oder mehrdimensionalen und Data Mining-Projekt-Vorlage. Die Projektvorlage enthält Ordner für alle in einem Modell erforderlichen Objekte. Sie können Assistenten verwenden, um alle grundlegenden Elemente, wie z. B. Datenquellen, Datenquellensichten, Dimensionen, Cubes und Rollen, zu erstellen.  
  
 Die Modelle werden mit Daten aus externen Datensystemen gefüllt. Dies sind normalerweise Data Warehouses, die von einer relationalen SQL Server- oder Oracle-Datenbank-Engine gehostet werden. (Tabellarische Modelle unterstützen zusätzliche Datenquellentypen.) Modelle geben Abfrageobjekte wie z. B. Cubes an, aber auch Dimensionen, die in mehreren Cubes verwendet werden können, Berechnungen und KPIs, die Geschäftslogik kapseln, sowie Interaktionen wie Navigations- und Drillthroughverhalten.  
  
 Um ein Modell zu verwenden, wird es in einer [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Instanz bereitgestellt, die Datenbanken in einem bestimmten Servermodus ausführt und die Daten autorisierten Benutzern zur Verfügung stellt, die mit Excel oder anderen Anwendungen eine Verbindung herstellen.  
  
 Sie können eine [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]-Instanz in einem von drei Servermodi installieren:  
  
-   Als tabellarische Instanz, die tabellarische Modelle ausführt.  
  
-   Als mehrdimensionale und Data Mining-Instanz, die OLAP-Cubes und Data Mining-Modelle ausführt (Standardeinstellung).  
  
-   Im Modus PowerPivot für SharePoint, in dem PowerPivot- und Excel-Datenmodelle in SharePoint ausgeführt werden. (PowerPivot für SharePoint ist eine Daten-Engine der mittleren Ebene, die Datenmodelle lädt, abfragt und aktualisiert, die in SharePoint gehostet werden.)  
  
 Die gleiche Daten-Engine und drei verschiedene Möglichkeiten, sie zu verwenden. Beachten Sie, dass die Servermodi während der Installation festgelegt und später nicht mehr geändert werden können. Sie müssen eine neue Instanz installieren, wenn Sie einen anderen Modus benötigen.  
  
 Die Grunddokumentation für Analysis Services ist in Abschnitten organisiert, die dem Typ des Projekts entsprechen, die Sie erstellen. Wählen Sie in den folgenden Links, um mehr über jeden Modus oder die einzelnen Funktionsbereiche zu erfahren.  
  
 **Durchsuchen von Inhalt nach Bereich**  
 ![Kleines Dateiordnersymbol](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Vergleichen von tabellarischen und mehrdimensionalen Lösungen &#40;SSAS&#41;](comparing-tabular-and-multidimensional-solutions-ssas.md)  
  
 ![Kleines Dateiordnersymbol](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Analysis Services-Instanzverwaltung](instances/analysis-services-instance-management.md)  
  
 ![Kleines Dateiordnersymbol](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Tabellenmodellierung &#40;SSAS – tabellarisch&#41;](tabular-models/tabular-models-ssas.md)  
  
 ![Kleines Dateiordnersymbol](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [mehrdimensionale Modellierung &#40;SSAS&#41;](multidimensional-models/multidimensional-models-ssas.md)  
  
 ![Kleines Dateiordnersymbol](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [Datamining- &#40;SSAS&#41;](data-mining/data-mining-ssas.md)  
  
 ![Kleines Dateiordnersymbol](../../2014/integration-services/media/filefolder-small.gif "Small File Folder Icon") [PowerPivot für SharePoint &#40;SSAS&#41;](power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Funktionen variieren je nach Edition. Mehrdimensionale und Data Mining-Modelle sind in der Standard Edition verfügbar, bieten aber weniger Funktionen als in den höheren Editionen. Tabellarische Modelle und PowerPivot für SharePoint sind Premium-Funktionen, die in der Standard Edition-Lizenz nicht verfügbar sind. Weitere Informationen finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services-Lernprogramme &#40;SSAS&#41;](analysis-services-tutorials-ssas.md)   
 [Installation für SQLServer 2014](../database-engine/install-windows/installation-for-sql-server.md)   
 [Entwicklerhandbuch für &#40;Analysis Services&#41;](analysis-services-developer-documentation.md)   
 [SQL Server-Ressourcencenter](https://go.microsoft.com/fwlink/?linkID=219676)   
 [SQLCat.com](https://go.microsoft.com/fwlink/?linkID=220963)  
  
  
