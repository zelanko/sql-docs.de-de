---
title: SQL Server 2014-Analysedienste | Microsoft Docs
ms.custom: ''
ms.date: 04/06/2020
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
ms.openlocfilehash: 986356e6ebf7697bf0b425553f6803659a0fc5cb
ms.sourcegitcommit: 8f99d15c5b23d9f3c08a77e2b8bea5772f570493
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/07/2020
ms.locfileid: "80760305"
---
# <a name="sql-server-2014-analysis-services"></a>SQL Server 2014 Analysis Services

  SQL Server 2014 Analysis Services ist eine analytische Daten-Engine, die in Entscheidungsunterstützungs- und Business Intelligence-Lösungen (Bi)-Lösungen verwendet wird und die analytischen Daten für Geschäftsberichte und Clientanwendungen wie Excel, Reporting Services-Berichte und andere BI-Tools von Drittanbietern bereitstellt. 

## <a name="about-sql-server-analysis-services-documentation"></a>Informationen zur SQL Server Analysis Services-Dokumentation

Die Dokumentation ist nach Version getrennt. Sie befinden sich derzeit in der SQL Server 2014 Analysis Services-Dokumentation.

- Weitere Informationen zu SQL Server 2012 und früheren Informationen finden Sie in der [Dokumentation zu früheren SQL Server-Versionen](https://docs.microsoft.com/previous-versions/sql/).
- Weitere Informationen zu SQL Server 2014 finden Sie unter [Bücher online für SQL Server 2014](../2014-toc/index.yml)
- Weitere Informationen zu SQL Server 2016 und höher finden Sie in der [Analysis Services-Dokumentation](https://docs.microsoft.com/analysis-services/).
- Weitere Informationen zu Azure Analysis Services finden Sie unter [Azure Analysis Services Documentation](https://docs.microsoft.com/azure/analysis-services/).

## <a name="analysis-services-workflow"></a>Analysis Services-Workflow

Ein typischer Workflow umfasst das Erstellen eines OLAP- oder Tabellarischen Datenmodells, das Bereitstellen des Modells als Datenbank auf einer Serverinstanz, das Verarbeiten des Ladens der Datenbank mit Daten und das Zuweisen von Berechtigungen zum Zulassen des Datenzugriffs. Wenn dieser abgeschlossen ist, kann jede Anwendung, die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] als Datenquelle unterstützt, auf dieses Mehrzweckdatenmodell zugreifen.  
  
 Um ein Modell zu erstellen, verwenden Sie SQL Server-Datentools (siehe Tools und Anwendungen, die [in Analysis Services verwendet werden),](tools-and-applications-used-in-analysis-services.md)und wählen Sie entweder eine tabellenförmige oder eine projektbasierte und Data Mining-Projektvorlage aus. Die Projektvorlage enthält Ordner für alle in einem Modell erforderlichen Objekte. Sie können Assistenten verwenden, um alle grundlegenden Elemente, wie z. B. Datenquellen, Datenquellensichten, Dimensionen, Cubes und Rollen, zu erstellen.  
  
 Die Modelle werden mit Daten aus externen Datensystemen gefüllt. Dies sind normalerweise Data Warehouses, die von einer relationalen SQL Server- oder Oracle-Datenbank-Engine gehostet werden. (Tabellarische Modelle unterstützen zusätzliche Datenquellentypen.) Modelle geben Abfrageobjekte wie z. B. Cubes an, aber auch Dimensionen, die in mehreren Cubes verwendet werden können, Berechnungen und KPIs, die Geschäftslogik kapseln, sowie Interaktionen wie Navigations- und Drillthroughverhalten.  
  
 Um ein Modell zu verwenden, wird es auf einer Serverinstanz bereitgestellt, die Datenbanken in einem bestimmten Servermodus ausführt und die Daten autorisierten Benutzern zur Verfügung stellt, die über Excel oder andere Anwendungen eine Verbindung herstellen.  
  
 Sie können eine Instance in einem von drei Servermodi installieren:  
  
-   Als tabellarische Instanz, die tabellarische Modelle ausführt.  
  
-   Als mehrdimensionale und Data Mining-Instanz, die OLAP-Cubes und Data Mining-Modelle ausführt (Standardeinstellung).  
  
-   Im Modus PowerPivot für SharePoint, in dem PowerPivot- und Excel-Datenmodelle in SharePoint ausgeführt werden. (PowerPivot für SharePoint ist eine Daten-Engine der mittleren Ebene, die Datenmodelle lädt, abfragt und aktualisiert, die in SharePoint gehostet werden.)  
  
 Die gleiche Daten-Engine und drei verschiedene Möglichkeiten, sie zu verwenden. Beachten Sie, dass die Servermodi während der Installation festgelegt und später nicht mehr geändert werden können. Sie müssen eine neue Instanz installieren, wenn Sie einen anderen Modus benötigen.  
  
 Die Grunddokumentation für Analysis Services ist in Abschnitten organisiert, die dem Typ des Projekts entsprechen, die Sie erstellen. Wählen Sie in den folgenden Links, um mehr über jeden Modus oder die einzelnen Funktionsbereiche zu erfahren.  
  
 **Durchsuchen von Inhalt nach Bereich**  
 ![Kleines Dateiordnersymbol](../../2014/integration-services/media/filefolder-small.gif "Kleines Dateiordnersymbol") [Vergleich von tabellarischen und mehrdimensionalen Lösungen &#40;SSAS&#41;](comparing-tabular-and-multidimensional-solutions-ssas.md)  
  
 ![Kleine Dateiordner Icon](../../2014/integration-services/media/filefolder-small.gif "Kleines Dateiordnersymbol") [Analysis Services Instanzverwaltung](instances/analysis-services-instance-management.md)  
  
 ![Kleine Dateiordner Icon](../../2014/integration-services/media/filefolder-small.gif "Kleines Dateiordnersymbol") [Tabellarische Modellierung &#40;SSAS Tabellarischen&#41;](tabular-models/tabular-models-ssas.md)  
  
 ![Kleine Dateiordner-Symbol](../../2014/integration-services/media/filefolder-small.gif "Kleines Dateiordnersymbol") [MultidimensionalE Modellierung &#40;SSAS&#41;](multidimensional-models/multidimensional-models-ssas.md)  
  
 ![Kleine Dateiordner Icon](../../2014/integration-services/media/filefolder-small.gif "Kleines Dateiordnersymbol") [Data Mining &#40;SSAS&#41;](data-mining/data-mining-ssas.md)  
  
 ![Kleines Dateiordnersymbol](../../2014/integration-services/media/filefolder-small.gif "Kleines Dateiordnersymbol") [PowerPivot für SharePoint &#40;SSAS&#41;](power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Funktionen variieren je nach Edition. Mehrdimensionale und Data Mining-Modelle sind in der Standard Edition verfügbar, bieten aber weniger Funktionen als in den höheren Editionen. Tabellarische Modelle und PowerPivot für SharePoint sind Premium-Funktionen, die in der Standard Edition-Lizenz nicht verfügbar sind. Weitere Informationen finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Analysedienste-Tutorials &#40;SSAS-&#41;](analysis-services-tutorials-ssas.md)   
 [Installation für SQL Server 2014](../database-engine/install-windows/installation-for-sql-server.md)   
 [Entwicklerhandbuch &#40;Analysis Services&#41;](analysis-services-developer-documentation.md)   
 [SQL Server-Ressourcencenter](https://go.microsoft.com/fwlink/?linkID=219676)   
 [SQLCat.com](https://go.microsoft.com/fwlink/?linkID=220963)  
  
  
