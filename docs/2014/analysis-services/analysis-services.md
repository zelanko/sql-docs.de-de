---
title: SQL Server 2014 Analysis Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/25/2019
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
ms.openlocfilehash: bceabba9b490be6bc2c51b4fdcce9b6b131eb0ce
ms.sourcegitcommit: 7183735e38dd94aa3b9bab2b73ccab54c916ff86
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683478"
---
# <a name="sql-server-2014-analysis-services"></a>SQL Server 2014 Analysis Services

  SQL Server 2014 Analysis Services ist eine analytische Daten-Engine, die in Lösungen für Decision Support und Business Intelligence (BI) verwendet wird und die analytischen Daten für Geschäftsberichte und Client Anwendungen wie Excel, Reporting Services Berichte und andere bereitstellt. BI-Tools von Drittanbietern. 

## <a name="about-sql-server-analysis-services-documentation"></a>Informationen zu SQL Server Analysis Services-Dokumentation

Die Dokumentation ist durch eine Version getrennt. Sie befinden sich zurzeit in SQL Server 2014 Analysis Services-Dokumentation.

- Weitere Informationen zu SQL Server 2012 und früher finden Sie in [SQL Server Dokumentation zu früheren Versionen](https://docs.microsoft.com/previous-versions/sql/).
- Weitere Informationen zu SQL Server 2014 finden Sie in der [Online Dokumentation für SQL Server 2014](../2014-toc/index.yml) .
- Weitere Informationen zu SQL Server 2016 und höher finden Sie in der [Microsoft SQL-Dokumentation](https://docs.microsoft.com/sql/).
- Weitere Informationen zu Azure Analysis Services finden Sie unter [Azure Analysis Services Dokumentation](https://docs.microsoft.com/azure/analysis-services/).

## <a name="analysis-services-workflow"></a>Workflow Analysis Services

Ein typischer Workflow umfasst das Entwickeln eines OLAP-oder tabellarischen Datenmodells, die Bereitstellung des Modells als Datenbank in einer Serverinstanz, die Verarbeitung der Datenbank, um Sie mit Daten zu laden, und das Zuweisen von Berechtigungen zum Zulassen des Datenzugriffs. Wenn dieser abgeschlossen ist, kann jede Anwendung, die [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] als Datenquelle unterstützt, auf dieses Mehrzweckdatenmodell zugreifen.  
  
 Verwenden Sie zum Erstellen eines Modells SQL Server Data Tools (siehe [Tools und Anwendungen, die in Analysis Services verwendet werden](tools-and-applications-used-in-analysis-services.md)), und wählen Sie entweder eine tabellarische oder eine mehrdimensionale und Data Mining-Projektvorlage aus. Die Projektvorlage enthält Ordner für alle in einem Modell erforderlichen Objekte. Sie können Assistenten verwenden, um alle grundlegenden Elemente, wie z. B. Datenquellen, Datenquellensichten, Dimensionen, Cubes und Rollen, zu erstellen.  
  
 Die Modelle werden mit Daten aus externen Datensystemen gefüllt. Dies sind normalerweise Data Warehouses, die von einer relationalen SQL Server- oder Oracle-Datenbank-Engine gehostet werden. (Tabellarische Modelle unterstützen zusätzliche Datenquellentypen.) Modelle geben Abfrageobjekte wie z. B. Cubes an, aber auch Dimensionen, die in mehreren Cubes verwendet werden können, Berechnungen und KPIs, die Geschäftslogik kapseln, sowie Interaktionen wie Navigations- und Drillthroughverhalten.  
  
 Um ein Modell zu verwenden, wird es auf einer Serverinstanz bereitgestellt, die Datenbanken in einem bestimmten Server Modus ausführt und die Daten autorisierten Benutzern zur Verfügung stellt, die eine Verbindung über Excel oder andere Anwendungen herstellen.  
  
 Sie können eine Instanz in einem von drei Server Modi installieren:  
  
-   Als tabellarische Instanz, die tabellarische Modelle ausführt.  
  
-   Als mehrdimensionale und Data Mining-Instanz, die OLAP-Cubes und Data Mining-Modelle ausführt (Standardeinstellung).  
  
-   Im Modus PowerPivot für SharePoint, in dem PowerPivot- und Excel-Datenmodelle in SharePoint ausgeführt werden. (PowerPivot für SharePoint ist eine Daten-Engine der mittleren Ebene, die Datenmodelle lädt, abfragt und aktualisiert, die in SharePoint gehostet werden.)  
  
 Die gleiche Daten-Engine und drei verschiedene Möglichkeiten, sie zu verwenden. Beachten Sie, dass die Servermodi während der Installation festgelegt und später nicht mehr geändert werden können. Sie müssen eine neue Instanz installieren, wenn Sie einen anderen Modus benötigen.  
  
 Die Grunddokumentation für Analysis Services ist in Abschnitten organisiert, die dem Typ des Projekts entsprechen, die Sie erstellen. Wählen Sie in den folgenden Links, um mehr über jeden Modus oder die einzelnen Funktionsbereiche zu erfahren.  
  
 **Inhalt nach Bereich Durchsuchen**  
 ![Kleines Datei Ordnersymbol](../../2014/integration-services/media/filefolder-small.gif "Kleines Dateiordnersymbol") [Vergleichen von tabellarischen und mehrdimensionalen Lösungen &#40;SSAS&#41;](comparing-tabular-and-multidimensional-solutions-ssas.md)  
  
 ![Kleines Datei Ordnersymbol](../../2014/integration-services/media/filefolder-small.gif "Kleines Dateiordnersymbol") [Analysis Services Instanzverwaltung](instances/analysis-services-instance-management.md)  
  
 ![Kleines Datei Ordnersymbol](../../2014/integration-services/media/filefolder-small.gif "Kleines Dateiordnersymbol") [tabellarische Modellierung &#40;tabellarischen SSAS-&#41;](tabular-models/tabular-models-ssas.md)  
  
 ![Kleines Datei Ordnersymbol](../../2014/integration-services/media/filefolder-small.gif "Kleines Dateiordnersymbol") mehr [dimensionale Modellierung &#40;SSAS&#41;](multidimensional-models/multidimensional-models-ssas.md)  
  
 ![Kleines Datei Ordnersymbol](../../2014/integration-services/media/filefolder-small.gif "Kleines Dateiordnersymbol") [Data Mining &#40;SSAS&#41;](data-mining/data-mining-ssas.md)  
  
 ![Kleines Datei Ordnersymbol](../../2014/integration-services/media/filefolder-small.gif "Kleines Dateiordnersymbol") [PowerPivot für SharePoint &#40;SSAS&#41;](power-pivot-sharepoint/power-pivot-for-sharepoint-ssas.md)  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]die Funktionen variieren je nach Edition. Mehrdimensionale und Data Mining-Modelle sind in der Standard Edition verfügbar, bieten aber weniger Funktionen als in den höheren Editionen. Tabellarische Modelle und PowerPivot für SharePoint sind Premium-Funktionen, die in der Standard Edition-Lizenz nicht verfügbar sind. Weitere Informationen finden Sie unter [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Analysis Services Tutorials &#40;SSAS&#41;](analysis-services-tutorials-ssas.md)   
 [Installation für SQL Server 2014](../database-engine/install-windows/installation-for-sql-server.md)   
 [Entwicklerhandbuch &#40;Analysis Services&#41;](analysis-services-developer-documentation.md)   
 [SQL Server-Ressourcen Center](https://go.microsoft.com/fwlink/?linkID=219676)   
 [SQLCat.com](https://go.microsoft.com/fwlink/?linkID=220963)  
  
  
