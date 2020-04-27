---
title: Unterstützte Datenquellen (SSAS Multidimensional) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Analysis Services, data sources
- data sources [Analysis Services], about data sources
- Analysis Services, data sources
- connections [Analysis Services]
- SSAS, data sources
ms.assetid: c97e0f8d-7ddd-4941-8b51-e7832f30fbbe
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5a8cdeb912d1ead21571f1ec7f86e15b0d009514
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66072861"
---
# <a name="data-sources-supported-ssas-multidimensional"></a>Unterstützte Datenquellen (SSAS Multidimensional)
  In diesem Thema werden die Datenquellentypen beschrieben, die Sie in einem tabellarischen Modell verwenden können.  
  
##  <a name="supported-data-sources"></a><a name="bkmk_supported_ds"></a>Unterstützte Datenquellen  
 Sie können Daten aus den Datenquellen in der folgenden Tabelle abrufen. Bei der Installation von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]werden die für die einzelnen Datenquellen aufgelisteten Anbieter nicht von Setup installiert. Einige Anbieter wurden möglicherweise bereits mit anderen Anwendungen auf dem Computer installiert. In anderen Fällen müssen Sie den Anbieter herunterladen und installieren.  
  
> [!NOTE]  
>  Drittanbieterprodukte, wie z.&#160;B. der Oracle OLE DB-Anbieter, können ebenfalls verwendet werden, um eine Verbindung mit Drittanbieterdatenbanken herzustellen, wobei der Support vom entsprechenden Drittanbieter bereitgestellt wird.  
  
|||||  
|-|-|-|-|  
|`Source`|Versionen|Dateityp|Anbieter <sup>1</sup>|  
|Access-Datenbanken|Microsoft Access 2007, 2010, 2013|.accdb oder .mdb|Microsoft Jet 4.0 OLE DB-Anbieter|  
|SQL Server relationale Datenbanken <sup>5</sup>|Microsoft SQL Server 2005, 2008, 2008 R2, 2012, 2014 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] <sup>2</sup>, SQL Server parallel Data Warehouse (PDW) <sup>3</sup>|(–)|OLE DB-Anbieter für SQL Server<br /><br /> SQL Server Native Client OLE DB-Anbieter<br /><br /> OLE DB-Anbieter für SQL Server Native 11.0 Client<br /><br /> .NET Framework-Datenanbieter für SQL Client|  
|Relationale Oracle-Datenbanken|Oracle 9i, 10g, 11g|(–)|OLE DB-Anbieter für Oracle<br /><br /> .NET Framework-Datenanbieter für Oracle Client<br /><br /> .NET Framework-Datenanbieter für SQL Server<br /><br /> Msdaora OLE DB Anbieter <sup>4</sup><br /><br /> OraOLEDB<br /><br /> MSDASQL|  
|Relationale Teradata-Datenbanken|Teradata V2R6, V12|(–)|OLE DB-Anbieter für TDOLEDB<br /><br /> .NET-Datenanbieter für Teradata|  
|Relationale Informix-Datenbanken|V11.10|(–)|OLE DB-Anbieter für Informix|  
|Relationale IBM DB2-Datenbanken|8.1|(–)|DB2OLEDB|  
|Relationale Datenbanken von Sybase Adaptive Server Enterprise (ASE)|15.0.2|(–)|OLE DB-Anbieter für Sybase|  
|Andere relationale Datenbanken|(–)|(–)|Einen OLE DB-Anbieter.|  
  
 <sup>1</sup> ODBC-Datenquellen werden für mehrdimensionale Lösungen nicht unterstützt. Zwar wird die Verbindung von Analysis Services selbst behandelt, doch können die in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] zum Erstellen von Lösungen verwendeten Designer keine Verbindung mit einer ODBC-Datenquelle auch dann nicht herstellen, wenn der MSDASQL-Treiber verwendet wird. Wenn die Geschäftsanforderungen eine ODBC-Datenquelle umfassen, erwägen Sie, stattdessen eine tabellarische Lösung zu erstellen.  
  
 <sup>2</sup> Weitere Informationen finden [!INCLUDE[ssSDS](../../includes/sssds-md.md)]Sie unter auf [Azure.Microsoft.com](https://go.microsoft.com/fwlink/?LinkID=157856).  
  
 <sup>3</sup> Weitere Informationen zu [!INCLUDE[ssSDS](../../includes/sssds-md.md)] PDW finden Sie unter [SQL Server parallel Data Warehouse](https://go.microsoft.com/fwlink/?LinkId=150895).  
  
 <sup>4</sup> in einigen Fällen kann die Verwendung des MSDAORA-OLE DB Anbieters zu Verbindungsfehlern führen, insbesondere bei neueren Versionen von Oracle. Treten Fehler auf, empfiehlt es sich, einen der anderen für Oracle aufgeführten Anbieter zu verwenden.  
  
 <sup>5</sup> einige Features erfordern eine SQL Server relationale Datenbank, die lokal ausgeführt wird. Insbesondere für Rückschreibevorgänge und ROLAP-Speicher muss die zugrunde liegende Datenquelle eine relationale SQL Server-Datenbank sein.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Unterstützte Datenquellen &#40;tabellarischen SSAS-&#41;](../tabular-models/data-sources-supported-ssas-tabular.md)   
 [Datenquellen in mehrdimensionalen Modellen](data-sources-in-multidimensional-models.md)   
 [Datenquellsichten in mehrdimensionalen Modellen](data-source-views-in-multidimensional-models.md)  
  
  
