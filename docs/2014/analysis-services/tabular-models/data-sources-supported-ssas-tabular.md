---
title: Unterstützten Datenquellen (SSAS – tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d6c2b1b3-91fc-4175-af25-509946dc7f24
caps.latest.revision: 17
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1b8aac369dd82f75f251df1195ac29c8ccf3b983
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37185297"
---
# <a name="data-sources-supported-ssas-tabular"></a>Data Sources Supported (SSAS Tabular)
  In diesem Thema werden die Datenquellentypen beschrieben, die mit tabellarischen Modellen verwendet werden können.  
  
 Dieser Artikel enthält folgende Abschnitte:  
  
-   [Unterstützte Datenquellen](#bkmk_supported_ds)  
  
-   [Nicht unterstützte Quellen](#bkmk_unsupported_ds)  
  
-   [Tipps zum Auswählen von Datenquellen](#bkmk_tips)  
  
##  <a name="bkmk_supported_ds"></a> Unterstützte Datenquellen  
 Sie können Daten aus den Datenquellen in der folgenden Tabelle importieren. Bei der Installation von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]werden die für die einzelnen Datenquellen aufgelisteten Anbieter nicht von Setup installiert. Einige Anbieter wurden möglicherweise bereits mit anderen Anwendungen auf dem Computer installiert. In anderen Fällen müssen Sie den Anbieter herunterladen und installieren.  
  
|||||  
|-|-|-|-|  
|Quelle|Versionen|Dateityp|Anbieter <sup>1</sup>|  
|Access-Datenbanken|Microsoft Access 2003, 2007, 2010.|.accdb oder .mdb|ACE 14 OLE DB-Anbieter|  
|Relationale SQL Server-Datenbanken|Microsoft SQL Server 2005, 2008, 2008 R2; SQLServer 2012, Microsoft SQL Azure-Datenbank <sup>2</sup>|(–)|OLE DB-Anbieter für SQL Server<br /><br /> SQL Server Native Client OLE DB-Anbieter<br /><br /> OLE DB-Anbieter für SQL Server Native 10.0 Client<br /><br /> .NET Framework-Datenanbieter für SQL Client|  
|SQL Server Parallel Datawarehouse (PDW) <sup>3</sup>|2008 R2|(–)|OLE DB-Anbieter für SQL Server PDW|  
|Relationale Oracle-Datenbanken|Oracle 9i, 10g, 11g|(–)|OLE DB-Anbieter für Oracle<br /><br /> .NET Framework-Datenanbieter für Oracle Client<br /><br /> .NET Framework-Datenanbieter für SQL Server<br /><br /> OraOLEDB<br /><br /> MSDASQL|  
|Relationale Teradata-Datenbanken|Teradata V2R6, V12|(–)|OLE DB-Anbieter für TDOLEDB<br /><br /> .NET-Datenanbieter für Teradata|  
|Relationale Informix-Datenbanken||(–)|OLE DB-Anbieter für Informix|  
|Relationale IBM DB2-Datenbanken|8.1|(–)|DB2OLEDB|  
|Relationale Datenbanken von Sybase Adaptive Server Enterprise (ASE)|15.0.2|(–)|OLE DB-Anbieter für Sybase|  
|Andere relationale Datenbanken|(–)|(–)|OLE DB-Anbieter oder ODBC-Treiber|  
|Textdateien|(–)|.txt, .tab, .csv|ACE 14 OLE DB-Anbieter für Microsoft Access|  
|Microsoft Excel-Dateien|Excel 97-2003, 2007, 2010|.xlsx, xlsm, .xlsb, .xltx, .xltm|ACE 14 OLE DB-Anbieter|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Arbeitsmappe|Microsoft SQL Server 2008 R2 Analysis Services|XLSX, XLSM, XLSB, XLTX, XLTM|ASOLEDB 10.5<br /><br /> (wird nur für [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Arbeitsmappen verwendet, die in SharePoint-Farmen veröffentlicht werden, in denen [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] installiert ist)|  
|Analysis Services-Cube|Microsoft SQL Server 2005, 2008, 2008 R2 Analysis Services|(–)|ASOLEDB 10|  
|Datenfeeds<br /><br /> (wird verwendet, um Daten aus Reporting Services-Berichten, Atom-Dienstdokumenten, Microsoft Azure Marketplace DataMarket und einem einzelnen Datenfeed zu importieren)|Atom 1.0-Format<br /><br /> Sämtliche Datenbanken oder Dokumente, die als Windows Communication Foundation (WCF) Data Service (früher ADO.NET Data Services) verfügbar gemacht werden.|".atomsvc" für ein Dienstdokument, das einen oder mehrere Feeds definiert<br /><br /> ".atom" für ein Atom-Webfeeddokument|Microsoft-Datenfeedanbieter für [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]<br /><br /> .NET Framework-Datenfeedanbieter für [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]|  
|Office Database Connection-Dateien||ODC||  
  
 <sup>1</sup> Sie können auch den OLE DB-Anbieter für ODBC verwenden.  
  
 <sup>2</sup> finden Sie weitere Informationen zu SQL Azure, die Website [SQL Azure](http://go.microsoft.com/fwlink/?LinkID=157856).  
  
 <sup>3</sup> Weitere Informationen zu SQL Server PDW finden Sie unter der Website [SQL Server 2008 R2 Parallel Data Warehouse](http://go.microsoft.com/fwlink/?LinkId=150895).  
  
 <sup>4</sup> in einigen Fällen die Verwendung des MSDAORA-OLE DB-Anbieters kann zu Verbindungsfehlern, insbesondere bei neueren Versionen von Oracle. Treten Fehler auf, empfiehlt es sich, einen der anderen für Oracle aufgeführten Anbieter zu verwenden.  
  
##  <a name="bkmk_unsupported_ds"></a> Nicht unterstützte Quellen  
 Die folgende Datenquelle wird derzeit nicht unterstützt:  
  
-   Serverdokumente, wie bereits in SharePoint veröffentlichte Access-Datenbanken, können nicht importiert werden.  
  
##  <a name="bkmk_tips"></a> Tipps zum Auswählen von Datenquellen  
  
1.  Durch das Importieren von Tabellen aus relationalen Datenbanken ersparen Sie sich Schritte, da beim Import *Fremdschlüssel* beziehungen verwendet werden, um Beziehungen zwischen den Tabellen im Modell-Designer zu erstellen.  
  
2.  Sie können auch Zeit sparen, indem Sie mehrere Tabellen importieren und dann die Tabellen löschen, die Sie nicht benötigen. Wenn Sie Tabellen einzeln importieren, müssen Sie die Beziehungen zwischen den Tabellen ggf. manuell erstellen.  
  
3.  Spalten, die ähnliche Daten in anderen Datenquellen enthalten, bilden die Basis bei der Erstellung von Beziehungen innerhalb des Modell-Designers. Wenn Sie heterogene Datenquellen verwenden, wählen Sie Tabellen mit Spalten aus, die Tabellen in anderen Datenquellen zugeordnet werden können, die identische oder ähnliche Daten enthalten.  
  
4.  OLE DB-Anbieter können in einigen Fällen bessere Leistung für große Datenmengen anbieten. Bei der Auswahl zwischen unterschiedlichen Anbietern für die gleiche Datenquelle sollten Sie zuerst den OLE DB-Anbieter wählen.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenquellen &#40;SSAS – tabellarisch&#41;](../data-sources-ssas-tabular.md)   
 [Importieren von Daten &#40;SSAS – tabellarisch&#41;](../import-data-ssas-tabular.md)  
  
  
