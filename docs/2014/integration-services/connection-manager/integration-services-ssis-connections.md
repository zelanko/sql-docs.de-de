---
title: Integration Services-Verbindungen (SSIS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, connections
- SSIS packages, connections
- sources [Integration Services], connections
- packages [Integration Services], connections
- destinations [Integration Services], connections
- tasks [Integration Services], connections
- connections [Integration Services], about connections
- connections [Integration Services]
- SQL Server Integration Services packages, connections
ms.assetid: 72f5afa3-d636-410b-9e81-2ffa27772a8c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 18575c95602f73baa959d35b176cf16220fc8e64
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "79112167"
---
# <a name="integration-services-ssis-connections"></a>Integration Services-Verbindungen (SSIS)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Pakete verwenden Verbindungen zum Ausführen verschiedener Tasks und zum Implementieren von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Features:  
  
-   Herstellen einer Verbindung mit Quell- und Zieldatenspeichern, z. B. Text, XML, Excel-Arbeitsmappen und relationale Datenbanken, zum Extrahieren und Laden von Daten.  
  
-   Herstellen einer Verbindung mit relationalen Datenbanken, die Verweisdaten zum Ausführen von genauen oder Fuzzysuchvorgängen beinhalten.  
  
-   Herstellen einer Verbindung mit relationalen Datenbanken zum Ausführen von SQL-Anweisungen, z. B. der Befehle SELECT-, DELETE- und INSERT, sowie zum Ausführen gespeicherter Prozeduren.  
  
-   Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zum Durchführen von Wartungs- und Übertragungstasks, z. B. dem Sichern von Datenbanken und Übertragen von Anmeldungen.  
  
-   Schreiben von Protokolleinträgen in Text- und XML-Dateien und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabellen sowie Paketkonfigurationen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Tabellen.  
  
-   Herstellen einer Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zum Erstellen temporärer Arbeitstabellen, die von einigen Transformationen benötigt werden.  
  
-   Herstellen einer Verbindung mit [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Projekten und -Datenbanken für den Zugriff auf Data Mining-Modelle, zum Verarbeiten von Cubes und Dimensionen und zum Ausführen von DDL-Code.  
  
-   Angeben vorhandener Dateien und Ordner bzw. Erstellen neuer Dateien und Ordner für die Verwendung mit Foreach-Schleifenenumeratoren und Tasks.  
  
-   Herstellen einer Verbindung mit Meldungswarteschlangen sowie mit der Windows-Verwaltungsinstrumentation (WMI, Windows Management Instrumentation), mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO), dem Web und mit Mailservern.  
  
 Um diese Verbindungen herzustellen, verwendet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Verbindungs-Manager. Dies wird im nächsten Abschnitt beschrieben.  
  
## <a name="connection-managers"></a>Verbindungs-Manager  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] verwendet den Verbindungs-Manager als logische Darstellung einer Verbindung. Zur Entwurfszeit legen Sie die Eigenschaften eines Verbindungs-Managers fest, um die physische Verbindung zu beschreiben, die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] beim Ausführen des Pakets erstellt. Beispielsweise enthält ein Verbindungs-Manager die `ConnectionString`-Eigenschaft, die Sie zur Entwurfszeit festlegen. Zur Laufzeit wird mithilfe des Werts in der ConnectionString-Eigenschaft eine physische Verbindung erstellt.  
  
 Ein Paket kann mehrere Instanzen eines Verbindungs-Manager-Typs verwenden, und Sie können die Eigenschaften für jede Instanz festlegen. Zur Laufzeit erstellt jede Instanz eines Verbindungs-Manager-Typs eine Verbindung mit verschiedenen Attributen.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] stellt verschiedene Typen von Verbindungs-Managern bereit, mit denen Pakete eine Verbindung mit einer Reihe von Datenquellen und Servern herstellen können:  
  
-   Einige integrierte Verbindungs-Manager werden bei der Installation von [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]installiert.  
  
-   Andere Verbindungs-Manager stehen auf der [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Website zum Herunterladen zur Verfügung.  
  
-   Sie können einen eigenen benutzerdefinierten Verbindungs-Manager erstellen, wenn die vorhandenen Verbindungs-Manager Ihren Anforderungen nicht entsprechen.  
  
### <a name="built-in-connection-managers"></a>Integrierte Verbindungs-Manager  
 In der folgenden Tabelle sind die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] bereitgestellten Verbindungs-Manager-Typen aufgeführt.  
  
|type|BESCHREIBUNG|Thema|  
|----------|-----------------|-----------|  
|ADO|Stellt eine Verbindung mit ADO-Objekten (ActiveX Data Objects) her.|[ADO-Verbindungs-Manager](ado-connection-manager.md)|  
|ADO.NET|Stellt eine Verbindung mit einer Datenquelle mithilfe eines .NET-Anbieters her.|[ADO.NET-Verbindungs-Manager](ado-net-connection-manager.md)|  
|CACHE|Liest Daten aus dem Datenfluss oder einer Cachedatei (.caw) und kann Daten in der Cachedatei speichern.|[Cacheverbindungs-Manager](cache-connection-manager.md)|  
|DQS|Stellt eine Verbindung mit einem Data Quality Services-Server und einer Data Quality Services-Datenbank auf dem Server her.|[Verbindungs-Manager für DQS-Bereinigung](dqs-cleansing-connection-manager.md)|  
|EXCEL|Stellt eine Verbindung mit einer Excel-Arbeitsmappendatei her.|[Excel-Verbindungs-Manager](excel-connection-manager.md)|  
|FILE|Stellt eine Verbindung mit einer Datei oder einem Ordner her.|[Dateiverbindungs-Manager](file-connection-manager.md)|  
|FLATFILE|Stellt eine Verbindung mit Daten in einer einzelnen Flatfile her.|[Verbindungs-Manager für Flatfiles](flat-file-connection-manager.md)|  
|FTP|Stellt eine Verbindung mit einem FTP-Server her.|[FTP-Verbindungs-Manager](ftp-connection-manager.md)|  
|HTTP|Stellt eine Verbindung mit einem Webserver her.|[HTTP-Verbindungs-Manager](http-connection-manager.md)|  
|MSMQ|Stellt eine Verbindung mit einer Nachrichtenwarteschlange her.|[MSMQ-Verbindungs-Manager](msmq-connection-manager.md)|  
|MSOLAP100|Stellt eine Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Instanz von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] oder einem-Projekt her.|[Analysis Services-Verbindungs-Manager](analysis-services-connection-manager.md)|  
|MULTIFILE|Stellt eine Verbindung mit mehreren Dateien und Ordnern her.|[Verbindungs-Manager für mehrere Dateien](multiple-files-connection-manager.md)|  
|MULTIFLATFILE|Stellt eine Verbindung mit mehreren Datendateien und Ordnern her.|[Verbindungs-Manager für mehrere Flatfiles](multiple-flat-files-connection-manager.md)|  
|OLEDB|Stellt eine Verbindung mit einer Datenquelle mithilfe eines OLE DB-Anbieters her.|[OLE DB-Verbindungs-Manager](ole-db-connection-manager.md)|  
|ODBC|Stellt eine Verbindung mit einer Datenquelle mithilfe von ODBC her.|[ODBC-Verbindungs-Manager](odbc-connection-manager.md)|  
|SMOServer|Stellt eine Verbindung mit einem SMO-Server ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects) her.|[SMO-Verbindungs-Manager](smo-connection-manager.md)|  
|SMTP|Stellt eine Verbindung mit einem SMTP-Mailserver her.|[SMTP-Verbindungs-Manager](smtp-connection-manager.md)|  
|SQLMOBILE|Stellt eine Verbindung mit einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact-Datenbank her.|[SQL Server Compact Edition-Verbindungs-Manager](sql-server-compact-edition-connection-manager.md)|  
|WMI|Stellt eine Verbindung mit einem Server her und gibt den Bereich der WMI-Verwaltung (Windows Management Instrumentation, Windows-Verwaltungsinstrumentation) auf dem Server an.|[WMI-Verbindungs-Manager](wmi-connection-manager.md)|  
  
### <a name="connection-managers-available-for-download"></a>Zum Herunterladen verfügbare Verbindungs-Manager  
 In der folgenden Tabelle sind weitere Typen von Verbindungs-Managern aufgeführt, die von der [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Website heruntergeladen werden können.  
  
> [!IMPORTANT]  
>  Die in der folgenden Tabelle aufgelisteten Verbindungs-Manager funktionieren nur mit [!INCLUDE[ssEnterpriseEd11](../../includes/ssenterpriseed11-md.md)] und [!INCLUDE[ssDeveloperEd11](../../includes/ssdevelopered11-md.md)].  
  
|type|BESCHREIBUNG|Thema|  
|----------|-----------------|-----------|  
|ORACLE|Stellt eine Verbindung mit \<einer Oracle-Versions Info> Server her.|Der Oracle-Verbindungs-Manager ist die Verbindungs-Manager-Komponente des [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Connectors für Oracle von Attunity. Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Connector für Oracle von Attunity enthält auch eine Quelle und ein Ziel. Weitere Informationen finden Sie auf der Downloadseite [Microsoft Connectors for Oracle and Teradata by Attunity](https://go.microsoft.com/fwlink/?LinkId=251526).|  
|SAPBI|Stellt eine Verbindung mit einem System mit SAP NetWeaver BI, Version 7 her.|Der SAP BI-Verbindungs-Manager ist die Verbindungs-Manager-Komponente des [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Connectors für SAP BI. Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Connector für SAP BI enthält auch eine Quelle und ein Ziel. Weitere Informationen finden Sie auf der Downloadseite [Microsoft SQL Server 2008 Feature Pack](https://www.microsoft.com/download/details.aspx?id=30440).|  
|TERADATA|Stellt eine Verbindung mit einer Teradata \<-Versions Info> Server her.|Der Teradata-Verbindungs-Manager ist die Verbindungs-Manager-Komponente des [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Connectors für Teradata von Attunity. Der [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Connector für Teradata von Attunity enthält auch eine Quelle und ein Ziel. Weitere Informationen finden Sie auf der Downloadseite [Microsoft Connectors for Oracle and Teradata by Attunity](https://go.microsoft.com/fwlink/?LinkId=251526).|  
  
### <a name="custom-connection-managers"></a>Benutzerdefinierte Verbindungs-Manager  
 Sie können auch benutzerdefinierte Verbindungs-Manager schreiben. Weitere Informationen finden Sie unter [Developing a Custom Connection Manager](../extending-packages-custom-objects/connection-manager/developing-a-custom-connection-manager.md).  
  
## <a name="related-tasks"></a>Related Tasks  
 Ausführliche Informationen zum Hinzufügen oder Löschen eines Verbindungs-Managers in einem Paket finden Sie unter [Hinzufügen, Löschen oder Freigeben eines Verbindungs-Managers in einem Paket](../add-delete-or-share-a-connection-manager-in-a-package.md).  
  
 Details zum Festlegen der Eigenschaften eines Verbindungs-Managers in einem Paket finden Sie unter [Festlegen der Eigenschaften eines Verbindungs-Managers](../set-the-properties-of-a-connection-manager.md).  
  
## <a name="related-content"></a>Verwandte Inhalte  
  
-   Video, [Nutzen der Vorteile von Microsoft Attunity Connector für Oracle zur Erweiterung der Paketleistung](https://technet.microsoft.com/sqlserver/gg598963.aspx), auf technet.microsoft.com  
  
-   Wiki-Artikel, [SSIS-Konnektivität](https://social.technet.microsoft.com/wiki/contents/articles/sql-server-integration-services-ssis.aspx#Connectivity), auf social.technet.microsoft.com  
  
-   Blogeintrag [Verbinden mit MySQL von SSIS](https://go.microsoft.com/fwlink/?LinkId=217669)auf blogs.msdn.com.  
  
-   Technischer Artikel zum [Extrahieren und Laden von SharePoint-Daten in SQL Server Integration Services](https://go.microsoft.com/fwlink/?LinkId=247826)auf msdn.microsoft.com.  
  
-   Technischer Artikel [You get "DTS_E_CANNOTACQUIRECONNECTIONFROMCONNECTIONMANAGER" error message when using Oracle connection manager in SSIS (Sie erhalten die Fehlermeldung "DTS_E_CANNOTACQUIRECONNECTIONFROMCONNECTIONMANAGER" bei der Verwendung eines Oracle-Verbindungs-Managers in SSIS)](https://go.microsoft.com/fwlink/?LinkId=233696)auf support.microsoft.com.  
  
  
