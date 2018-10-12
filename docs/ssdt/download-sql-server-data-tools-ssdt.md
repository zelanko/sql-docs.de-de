---
title: Herunterladen von SQL Server Data Tools (SSDT) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/05/2018
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssdt
ms.reviewer: ''
ms.suite: sql
ms.technology: ssdt
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords:
- SSDT installieren, SSDT herunterladen, aktuelle SSDT-Version
ms.assetid: b0fc4987-d260-4d0a-9dd1-98099835b361
caps.latest.revision: 113
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.openlocfilehash: 907b8a7d11bbd7889f3796d3f56633caec22a529
ms.sourcegitcommit: c929887686eabd6b754cf644a45656f0a0eb0445
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/05/2018
ms.locfileid: "43743483"
---
# <a name="download-and-install-sql-server-data-tools-ssdt-for-visual-studio"></a>Herunterladen und Installieren von SQL Server Data Tools (SSDT) für Visual Studio
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md.md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
**SQL Server Data Tools** ist ein modernes und kostenloses herunterladbares Entwicklungstool für relationale SQL Server-Datenbanken, Azure SQL-Datenbanken, IS-Pakete (Integration Services), AS-Datenmodelle (Analysis Services) und RS-Berichte (Reporting Services). Mit SSDT lassen sich Datenbanken und andere Inhaltstypen für SQL Server entwerfen und bereitstellen – und zwar ebenso einfach wie eine Anwendung in Visual Studio.

*Bei den meisten Benutzern wird SQL Server Data Tools (SSDT) während der Installation von Visual Studio installiert. Durch die Installation von SSDT mit dem Visual Studio-Installer wird die SSDT-Grundfunktionalität hinzugefügt. Demnach müssen Sie für die Tools AS, IS und RS noch den [eigenständigen SSDT-Installer](#ssdt-for-vs-2017-standalone-installer) ausführen.*

## <a name="install-ssdt-with-visual-studio-2017"></a>Installieren von SSDT mit Visual Studio 2017

Wählen Sie für die Installation von SSDT während der [Visual Studio-Installation](https://docs.microsoft.com/visualstudio/install/install-visual-studio) die Workload **Datenspeicherung und -verarbeitung** und anschließend **SQL Server Data Tools** aus. Wenn Visual Studio bereits installiert ist, können Sie [die Liste der Workloads bearbeiten](https://docs.microsoft.com/visualstudio/install/modify-visual-studio), um SSDT einzuschließen: Workload ![Datenspeicherung und -verarbeitung](../ssdt/media/download-sql-server-data-tools-ssdt/data-workload.png)



## <a name="install-analysis-services-integration-services-and-reporting-services-tools"></a>Installieren der Tools Analysis Services, Integration Services und Reporting Services
Führen Sie für die Installation der Unterstützung für AS-, IS- und RS-Projekte den [eigenständigen SSDT-Installer](#ssdt-for-vs-2017-standalone-installer) aus. 

Der Installer listet verfügbare Visual Studio-Instanzen auf, auf denen die SSDT-Tools hinzugefügt werden können. Wenn Visual Studio nicht installiert ist, wird durch Auswahl der Option **Neue SQL Server Data Tools-Instanz installieren** SSDT mit einer Mindestversion von Visual Studio installiert. Zur Erzielung optimaler Ergebnisse wird jedoch empfohlen, SSDT mit der [aktuellen Version von Visual Studio](https://www.visualstudio.com/downloads) zu verwenden. 

![Auswählen von AS, IS, RS](../ssdt/media/download-sql-server-data-tools-ssdt/select-services.png)



## <a name="ssdt-for-vs-2017-standalone-installer"></a>SSDT für VS 2017 (eigenständiger Installer)

[![Download](../ssdt/media/download.png) Herunterladen von SSDT für Visual Studio 2017 (15.8) ](https://go.microsoft.com/fwlink/?linkid=2014060) 

> [!IMPORTANT]
> - Deinstallieren Sie vor der Installation von SSDT für Visual Studio 2017 (15.8) die Erweiterungen *Analysis Services-Projekte* und *Reporting Services-Projekte*, wenn diese bereits installiert wurden, und schließen Sie sämtliche VS-Instanzen.



**Versionsinformationen**  
  
Releasenummer: 15.8  
Buildnummer: 14.0.16174.0  
Veröffentlichungsdatum: 5. September 2018  

Eine vollständige Liste der Änderungen finden Sie unter [changelog (Änderungsprotokoll)](changelog-for-sql-server-data-tools-ssdt.md).

SSDT für Visual Studio 2017 hat die gleichen [Systemanforderungen](https://docs.microsoft.com/visualstudio/productinfo/vs2017-system-requirements-vs) wie Visual Studio.  

### <a name="available-languages---ssdt-for-vs-2017"></a>Verfügbare Sprachen: SSDT für Visual Studio 2017

Diese Version von **SSDT für Visual Studio 2017** kann in folgenden Sprachen installiert werden:  

[Chinesisch (vereinfacht)]( https://go.microsoft.com/fwlink/?linkid=2014060&clcid=0x804) | 
[Chinesisch (traditionell)]( https://go.microsoft.com/fwlink/?linkid=2014060&clcid=0x404) | 
[Englisch (Vereinigte Staaten)]( https://go.microsoft.com/fwlink/?linkid=2014060&clcid=0x409) | 
[Französisch]( https://go.microsoft.com/fwlink/?linkid=2014060&clcid=0x40c)  
[Deutsch]( https://go.microsoft.com/fwlink/?linkid=2014060&clcid=0x407) | 
[Italienisch]( https://go.microsoft.com/fwlink/?linkid=2014060&clcid=0x410) | 
[Japanisch]( https://go.microsoft.com/fwlink/?linkid=2014060&clcid=0x411) | 
[Koreanisch]( https://go.microsoft.com/fwlink/?linkid=2014060&clcid=0x412) | 
[Portugiesisch (Brasilien)]( https://go.microsoft.com/fwlink/?linkid=2014060&clcid=0x416) | 
[Russisch]( https://go.microsoft.com/fwlink/?linkid=2014060&clcid=0x419) | 
[Spanisch]( https://go.microsoft.com/fwlink/?linkid=2014060&clcid=0x40a)  





## <a name="supported-sql-versions"></a>Unterstützte SQL-Versionen
  
|Projektvorlagen|Unterstützte SQL-Plattformen|  
|-------------------|--------------------|  
Relationale Datenbanken|  SQL Server 2005* – SQL Server 2017<br> (Verwenden Sie SSDT 17.x oder SSDT für Visual Studio 2017, um eine Verbindung mit [SQL Server für Linux](../linux/sql-server-linux-overview.md) herzustellen)<br /><br />Azure SQL-Datenbank<br /><br />Azure SQL Data Warehouse (unterstützt nur Abfragen, Datenbankprojekte werden noch nicht unterstützt)<br /><br />  * SQL Server 2005-Support ist veraltet,<br /><br /> wechseln Sie bitte zu einer offiziell unterstützten SQL-Version|
  |Analysis Services-Modelle<br /><br />Reporting Services-Berichte | SQL Server 2008 – SQL Server 2017|
  |Integration Services-Pakete| SQL Server 2012 – SQL Server 2017    |
  
## <a name="dacfx"></a>DacFX
SSDT für Visual Studio 2015 und SSDT für Visual Studio 2017 verwenden beide DacFx 17.4.1: [Herunterladen von Data-Tier Application Framework (DacFx) 17.4.1](https://www.microsoft.com/download/details.aspx?id=56508).

## <a name="previous-versions"></a>Vorgängerversionen

In den [vorherigen Releases von SQL Server Data Tools (SSDT und SSDT-BI)](previous-releases-of-sql-server-data-tools-ssdt-and-ssdt-bi.md) können Sie SSDT für Visual Studio 2015 oder eine frühere Version von SSDT herunterladen und installieren.



## <a name="next-steps"></a>Nächste Schritte  
Gehen Sie nach der Installation von SSDT die folgenden Tutorials durch, um zu erfahren, wie Sie mithilfe von SSDT Datenbanken, Pakete, Datenmodelle und Berichte erstellen:  

- [Projektorientierte Offlinedatenbankentwicklung](project-oriented-offline-database-development.md)  
- [SSIS-Tutorial: Erstellen eines einfachen ETL-Pakets](../integration-services/ssis-how-to-create-an-etl-package.md)  
- [Analysis Services-Tutorials](../analysis-services/analysis-services-tutorials-ssas.md)  
- [Erstellen eines einfachen Tabellenberichts (SSRS-Lernprogramm)](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)  

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]


## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[SSDT MSDN-Forum](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=ssdt)  
[SSDT-Team-Blog](http://blogs.msdn.com/b/ssdt/)  
[DACFx-API-Referenz](https://msdn.microsoft.com/library/dn645454.aspx)  
[Herunterladen von SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)  
