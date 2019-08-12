---
title: Herunterladen von SQL Server Data Tools (SSDT) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/05/2019
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssdt
ms.topic: conceptual
keywords:
- SSDT installieren, SSDT herunterladen, aktuelle SSDT-Version
ms.assetid: b0fc4987-d260-4d0a-9dd1-98099835b361
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||=azuresqldb-mi-current'
ms.openlocfilehash: 06b2d138ce3d12fdf2a115343d922368accbeda7
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68892426"
---
# <a name="download-and-install-sql-server-data-tools-ssdt-for-visual-studio"></a>Herunterladen und Installieren von SQL Server Data Tools (SSDT) für Visual Studio
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md.md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]


**SQL Server Data Tools** ist ein modernes und kostenloses herunterladbares Entwicklungstool für relationale SQL Server-Datenbanken, Azure SQL-Datenbanken, IS-Pakete (Integration Services), AS-Datenmodelle (Analysis Services) und RS-Berichte (Reporting Services). Mit SSDT lassen sich Datenbanken und andere Inhaltstypen für SQL Server entwerfen und bereitstellen – und zwar ebenso einfach wie eine Anwendung in Visual Studio.


## <a name="changes-in-ssdt-for-visual-studio-2019"></a>Änderungen in SSDT für Visual Studio 2019 ##

In Visual Studio 2019 wurde die erforderliche Funktionalität zur Unterstützung von Analysis Services-, Integration Services- und Reporting Services-Projekten in die jeweiligen Visual Studio-Erweiterungen verlagert. Die SSDT-Kernfunktionen zum Erstellen von Datenbankprojekten sind weiterhin Bestandteil von Visual Studio. (Sie müssen während der Installation die Datenspeicher- und Verarbeitungsworkload auswählen.)  Es ist keine eigenständige SSDT-Installation mehr erforderlich. 

Wenn Sie bereits über eine Lizenz für Visual Studio 2019 verfügen:
- Installieren Sie für Projekte von SQL-Datenbank die Datenspeicher- und Verarbeitungsworkload für Visual Studio.
- Installieren Sie für Analysis Services-, Integration Services- oder Reporting Services-Projekte die geeigneten Erweiterungen aus dem Marketplace.

Wenn Sie noch keine Lizenz für Visual Studio 2019 besitzen:
- Installieren Sie [Visual Studio 2019 Community](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_content=sqlssdt). 
- Installieren Sie nach Bedarf die Erweiterung Analysis Services, Integration Services oder Reporting Services.

## <a name="changes-in-ssdt-for-visual-studio-2017"></a>Änderungen in SSDT für Visual Studio 2017 ##

Ab Visual Studio 2017 wurde die Funktionalität zum Erstellen von Datenbankprojekten in die Visual Studio-Installation integriert. Es ist nicht erforderlich, den eigenständigen SSDT-Installer zu installieren, um die Kernoberfläche von SSDT zu nutzen. Zum Erstellen von Integration Services-/Analysis Services-/Reporting Services-Projekten benötigen Sie jedoch weiterhin den eigenständigen SSDT-Installer. 

- Installieren Sie für Datenbankprojekte die Datenspeicher- und Verarbeitungsworkload für Visual Studio.
- Für Analysis Services-, Integration Services- oder Reporting Services-Projekte müssen Sie die [SQL Server Data Tools](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-2017) herunterladen und installieren.




## <a name="install-ssdt-with-visual-studio-2017"></a>Installieren von SSDT mit Visual Studio 2017

Wählen Sie für die Installation von SSDT während der [Visual Studio-Installation](https://docs.microsoft.com/visualstudio/install/install-visual-studio) die Workload **Datenspeicherung und -verarbeitung** und anschließend **SQL Server Data Tools** aus. Wenn Visual Studio bereits installiert ist, können Sie [die Liste der Workloads bearbeiten](https://docs.microsoft.com/visualstudio/install/modify-visual-studio), um SSDT einzuschließen: ![Workload zur Datenspeicherung und Verarbeitung](../ssdt/media/download-sql-server-data-tools-ssdt/data-workload.png).

## <a name="install-analysis-services-integration-services-and-reporting-services-tools"></a>Installieren der Tools Analysis Services, Integration Services und Reporting Services

Führen Sie für die Installation der Unterstützung für AS-, IS- und RS-Projekte den [eigenständigen SSDT-Installer](#ssdt-for-vs-2017-standalone-installer) aus. 

Der Installer listet verfügbare Visual Studio-Instanzen auf, auf denen die SSDT-Tools hinzugefügt werden können. Wenn Visual Studio nicht installiert ist, wird durch Auswahl der Option **Neue SQL Server Data Tools-Instanz installieren** SSDT mit einer Mindestversion von Visual Studio installiert. Zur Erzielung optimaler Ergebnisse wird jedoch empfohlen, SSDT mit der [aktuellen Version von Visual Studio](https://www.visualstudio.com/downloads) zu verwenden. 

![Auswählen von AS, IS, RS](../ssdt/media/download-sql-server-data-tools-ssdt/select-services.png)



## <a name="ssdt-for-vs-2017-standalone-installer"></a>SSDT für VS 2017 (eigenständiger Installer)

[![Download](../ssdt/media/download.png) SSDT für Visual Studio 2017 (15.9.2) herunterladen](https://go.microsoft.com/fwlink/?linkid=2095463) 

> [!IMPORTANT]
> - Deinstallieren Sie vor der Installation von SSDT für Visual Studio 2017 (15.9.2) die Erweiterungen *Analysis Services-Projekte* und *Reporting Services-Projekte*, wenn diese bereits installiert wurden, und schließen Sie alle VS-Instanzen.
> - Verwenden Sie SSDT für Visual Studio 2017 (15.8.0) oder die vorherigen Versionen zum Erstellen von SSIS-Paketen, die Teradata als Quelle oder Ziel verwenden. Mit SSDT für Visual Studio 2017 nach 15.8.0 können keine SSIS-Paketen entworfen werden, die Attunity Teradata Source/Destination enthalten.


**Versionsinformationen**  
  
Releasenummer: 15.9.2  
Buildnummer: 14.0.16194.0  
Releasedatum: 17. Juli 2019  

Eine vollständige Liste der Änderungen finden Sie in den [Versionsanmerkungen für SQL Server Data Tools (SSDT)](release-notes-ssdt.md).

SSDT für Visual Studio 2017 hat die gleichen [Systemanforderungen](https://docs.microsoft.com/visualstudio/productinfo/vs2017-system-requirements-vs) wie Visual Studio.  

### <a name="available-languages---ssdt-for-vs-2017"></a>Verfügbare Sprachen: SSDT für Visual Studio 2017

Diese Version von **SSDT für Visual Studio 2017** kann in folgenden Sprachen installiert werden:

- [Chinesisch (vereinfacht)]( https://go.microsoft.com/fwlink/?linkid=2095463&clcid=0x804)
- [Chinesisch (traditionell)]( https://go.microsoft.com/fwlink/?linkid=2095463&clcid=0x404)
- [Englisch (USA)]( https://go.microsoft.com/fwlink/?linkid=2095463&clcid=0x409)
- [Französisch]( https://go.microsoft.com/fwlink/?linkid=2095463&clcid=0x40c)
- [Deutsch]( https://go.microsoft.com/fwlink/?linkid=2095463&clcid=0x407)
- [Italienisch]( https://go.microsoft.com/fwlink/?linkid=2095463&clcid=0x410)
- [Japanisch]( https://go.microsoft.com/fwlink/?linkid=2095463&clcid=0x411)
- [Koreanisch]( https://go.microsoft.com/fwlink/?linkid=2095463&clcid=0x412)
- [Portugiesisch (Brasilien)]( https://go.microsoft.com/fwlink/?linkid=2095463&clcid=0x416)
- [Russisch]( https://go.microsoft.com/fwlink/?linkid=2095463&clcid=0x419)
- [Spanisch]( https://go.microsoft.com/fwlink/?linkid=2095463&clcid=0x40a)

## <a name="offline-install"></a>Offlineinstallation

Befolgen Sie die Anweisungen in diesem Abschnitt, um SSDT zu installieren, wenn Sie nicht mit dem Internet verbunden sind. Weitere Informationen finden Sie unter [Erstellen einer Netzwerkinstallation von Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/create-a-network-installation-of-visual-studio).

Führen Sie zunächst die folgenden Schritte aus, während Sie online sind:

1. [Installieren Sie den eigenständigen SSDT-Installer](#ssdt-for-vs-2017-standalone-installer).
2. [Laden Sie „vs_sql.exe“ herunter](https://aka.ms/vs/15/release/vs_sql.exe).
3. Führen Sie, während Sie online sind, einen der folgenden Befehle aus, um alle Dateien herunterzuladen, die für die Offlineinstallation erforderlich sind. Dabei ist die Verwendung der Option `--layout` wichtig. Mit ihr werden die tatsächlichen Dateien für die Offlineinstallation heruntergeladen. Ersetzen Sie `<filepath>` durch den tatsächlichen Layoutpfad, um die Dateien zu speichern.

   
   A.   Übergeben Sie das folgende Gebietsschema für eine bestimmte Sprache: `vs_sql.exe --layout c:\<filepath> --lang en-us` (eine einzelne Sprache hat eine Größe von etwa 1 GB)  
   B. Geben Sie für alle Sprachen das `--lang`-Argument an: `vs_sql.exe --layout c:\<filepath>` (alle Sprachen haben eine Größe von etwa 3,9 GB)

4. Führen Sie `SSDT-Setup-ENU.exe /layout c:\<filepath>` aus, um die SSDT-Nutzlast in den gleichen `<filepath>`-Speicherort zu extrahieren, an dem die heruntergeladenen VS2017-Dateien gespeichert sind. Damit stellen Sie sicher, dass alle Dateien der beiden Ordner in einem einzelnen Layoutordner zusammengeführt werden.

Nach Abschluss der vorherigen Schritte sind folgende Schritte offline möglich:

1. Führen Sie `vs_setup.exe --NoWeb` aus, um die Visual Studio 2017-Shell sowie das SQL Server-Datenprojekt zu installieren.
2. Führen Sie `SSDT-Setup-ENU.exe /install` aus dem Layoutordner aus, und wählen Sie SSIS/SSRS/SSAS aus.

   - Führen Sie alternativ für eine unbeaufsichtigte Installation `SSDT-Setup-ENU.exe /INSTALLALL[:vsinstances] /passive` aus.  

Führen Sie für verfügbare Optionen `SSDT-Setup-ENU.exe /help` aus.

> [!NOTE]
> Wenn Sie eine Vollversion von Visual Studio 2017 verwenden, erstellen Sie offline einen Ordner nur für SSDT, und führen Sie über diesen `SSDT-Setup-ENU.exe` aus. (Fügen Sie SSDT nicht zu einem anderen Offlinelayout für Visual Studio 2017 hinzu.) Wenn Sie das SSDT-Layout zu einem bereits vorhandenen Offlinelayout für Visual Studio hinzufügen, werden nicht die benötigten Laufzeitkomponenten (EXE-Dateien) erstellt.

## <a name="supported-sql-versions"></a>Unterstützte SQL-Versionen
  
|Projektvorlagen|Unterstützte SQL-Plattformen|  
|-------------------|--------------------|  
|Relationale Datenbanken|  SQL Server 2005\* – SQL Server 2017<br> (Verwenden Sie SSDT 17.x oder SSDT für Visual Studio 2017, um eine Verbindung mit [SQL Server für Linux](../linux/sql-server-linux-overview.md) herzustellen)<br /><br />Azure SQL-Datenbank<br /><br />Azure SQL Data Warehouse (unterstützt nur Abfragen, Datenbankprojekte werden noch nicht unterstützt)<br /><br /> \* SQL Server 2005 wird nicht mehr unterstützt,<br /><br /> wechseln Sie bitte zu einer offiziell unterstützten SQL-Version|
|Analysis Services-Modelle<br /><br />Reporting Services-Berichte | SQL Server 2008 – SQL Server 2017|
|Integration Services-Pakete| SQL Server 2012 – SQL Server 2019 |
  
## <a name="dacfx"></a>DacFX

Sowohl SSDT für Visual Studio 2015 als auch SSDT für Visual Studio 2017 verwenden DacFx 17.4.1: [Download Data-Tier Application Framework (DacFx) 17.4.1 (Herunterladen von Data-Tier Application Framework (DacFx) 17.4.1)](https://www.microsoft.com/download/details.aspx?id=56508).

## <a name="previous-versions"></a>Vorgängerversionen

In den [vorherigen Releases von SQL Server Data Tools (SSDT und SSDT-BI)](previous-releases-of-sql-server-data-tools-ssdt-and-ssdt-bi.md) können Sie SSDT für Visual Studio 2015 oder eine frühere Version von SSDT herunterladen und installieren.

## <a name="next-steps"></a>Nächste Schritte

Gehen Sie nach der Installation von SSDT die folgenden Tutorials durch, um zu erfahren, wie Sie mithilfe von SSDT Datenbanken, Pakete, Datenmodelle und Berichte erstellen:  

- [Projektorientierte Offlinedatenbankentwicklung](project-oriented-offline-database-development.md)  
- [SSIS-Tutorial: Erstellen eines einfachen ETL-Pakets](../integration-services/ssis-how-to-create-an-etl-package.md)  
- [Analysis Services-Tutorials](https://docs.microsoft.com/analysis-services/analysis-services-tutorials-ssas)  
- [Erstellen eines einfachen Tabellenberichts (SSRS-Lernprogramm)](../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)  

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

## <a name="see-also"></a>Weitere Informationen

[SSDT MSDN-Forum](https://social.msdn.microsoft.com/Forums/sqlserver/home?forum=ssdt)  
[SSDT-Team-Blog](https://blogs.msdn.com/b/ssdt/)  
[DACFx-API-Referenz](https://msdn.microsoft.com/library/dn645454.aspx)  
[Herunterladen von SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)  
