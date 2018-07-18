---
title: Parallel Data Warehouse-Komponenten - Analytics Platform System | Microsoft-Dokumentation
description: In diesem Artikel wird erläutert, die Softwareupdates und die nicht zur Appliance gehört Softwarekomponenten des Analytics Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 99d3317f25af947f042d43fdd64e4cad334ca51f
ms.sourcegitcommit: 974c95fdda6645b9bc77f1af2d14a6f948fe268a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37891001"
---
# <a name="parallel-data-warehouse-components---analytics-platform-system"></a>Parallel Data Warehouse-Komponenten - Analytics Platform System
Dieser Artikel beschreibt die Appliance-Software und die nicht zur Appliance gehört Softwarekomponenten des Analytics Platform System.  
  
<!-- MISSING LINKS

To learn more about Analytics Platform System, see:  
  
-   [Analytics Platform System architecture](architecture-overview.md)  
  
-   [Distributed and Replicated Tables &#40;SQL Server PDW&#41;](../sqlpdw/distributed-and-replicated-tables-sql-server-pdw.md)  
  
-   [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md)  
  
-   [Clustered Columnstore Indexes &#40;SQL Server PDW&#41;](../sqlpdw/clustered-columnstore-indexes-sql-server-pdw.md)  
  
-   [Query Process &#40;SQL Server PDW&#41;](../sqlpdw/query-process-sql-server-pdw.md)  
  
-   [Minimum and Maximum Values &#40;SQL Server PDW&#41;](../sqlpdw/minimum-and-maximum-values-sql-server-pdw.md)  

-->
   
  
![Parallel Data Warehouse-Software](media/parallel-data-warehouse-software.png "Parallel Data Warehouse-Software")  
  
## <a name="sec1"></a>Softwareupdates – Verarbeitung und Speicherung von Abfragen  
  
### <a name="control-node"></a>Steuerknoten  
MPP-Engine  
Die MPP-Engine ist die Gehirne des Systems MPP (Massively Parallel Processing). Sie führt die folgenden Aktionen aus:  
  
-   Parallele Abfragepläne erstellt und koordiniert die Ausführung paralleler Abfragen auf den Computeknoten.  
  
-   Speichert und Metadaten und Daten für alle Datenbanken koordiniert.  
  
-   Verwaltet die SQL Server-PDW-Datenbank-Authentifizierung und Autorisierung.  
  
-   Verfolgt den Status der Hardware und Software.  
  
### <a name="data-movement-service-dms"></a>Data Movement Service (DMS)  
(Data Movement Service, DMS) ist Teil von PDW die "geheimzutat". Sie führt die folgenden Aktionen aus:  
  
-   Überträgt die Daten in und aus der SQL Server-PDW-Knoten.  
  
-   Prozesse Abfragevorgängen, die erfordern, Übertragen von Daten zwischen den Knoten.  
  
-   Verbessert die abfrageleistung durch Optimieren der Geschwindigkeit der Daten übertragen.  
  
### <a name="admin-console"></a>Verwaltungskonsole  
Die Verwaltungskonsole ist eine Webanwendung, in dem die Appliance Zustand, Integrität und Leistungsinformationen dargestellt.  
  
### <a name="configuration-manager"></a>Konfigurations-Manager  
Der Konfigurations-Manager (dwconfig.exe), ist das Tool, mit denen Appliance Administratoren Analytics Platform System zu konfigurieren.  
  
### <a name="control-node-databases"></a>Control-Knoten-Datenbanken  
SQL Server, die alle Datenbanken auf dem steuerknoten verwaltet.  
  
-   Die Shell-Datenbank verwaltet die Metadaten für alle verteilten Benutzerdatenbanken.  
  
-   ' Tempdb ' enthält die Metadaten für alle Benutzer temporären Tabellen auf der gesamten Appliance an.  
  
-   Master ist die Mastertabelle für SQL Server auf dem steuerknoten.  
  
### <a name="compute-node"></a>Compute-Knoten  
Die Compute-Knoten sind die parallelverarbeitung von Daten und Speichereinheiten. Sie haben direkten angeschlossenen Speicher und SQL Server verwenden, um Benutzerdaten zu verwalten.  
  
### <a name="data-movement-service-dms"></a>Data Movement Service (DMS)  
(Data Movement Service, DMS) wird auf jedem Computeknoten für die folgenden Aufgaben ausgeführt:  
  
-   Als Teil der Verarbeitung von paralleler Abfragen Datenübertragung DMS zu und von anderen Computerknoten und den Steuerelementknoten aus.  
  
-   DMS, ausgeführt auf jedem Computeknoten empfängt Datenladevorgängen parallel. Daten werden direkt vom Server Laden auf den Computeknoten parallel geladen.  
  
-   DMS überträgt Daten von jeder Compute-Knoten, direkt an den Sicherungsserver gesendet wird.  
  
-   Bei Verwendung von PolyBase-DMS überträgt Daten in und aus einer externen Hadoop-Cluster oder Azure Storage-Blob.  
  
### <a name="compute-node-databases"></a>Compute-Knoten-Datenbanken 
Jeder Compute-Knoten ausgeführt wird, eine Instanz von SQL Server zum Verarbeiten von Abfragen und Verwalten von Benutzerdaten.  
  
## <a name="appliance-fabric"></a>Appliance-Fabric  
Das Appliance-Fabric stellt das Betriebssystem, Dienste und Netzwerkinfrastruktur für die Anwendung bereit.  
  
### <a name="domain-controller"></a>Domänencontroller  
Active Directory (AD) Domain Services (DS)  
Analytics Platform System führt die Authentifizierung zwischen den Knoten für Analytics Platform System und verwaltet die Authentifizierung der PDW-Windows-Authentifizierung für SQL Server-Anmeldungen.  
  
DNS-Dienst  
Windows Service DNS (Domain Name) löst den Domänennamen zu IP-Adressen für die Analytics Platform System Appliance.  
  
### <a name="windows-deployment-service"></a>Windows-Bereitstellungsdienste  
Windows-Verwaltungsinstrumentation (Windows Deployment Service, WDS) stellt das Betriebssystem Windows Server, auf dem Gerät bereit. Es wird auf jedem Host und die virtuellen Computer über das Gerät bereitgestellt werden.  
  
Der DHCP-Dienst erstellt die IP-Adressen, damit die Hosts innerhalb der Domäne der Anwendung des Netzwerks der Appliance verbinden können, ohne dass eine vorab konfigurierte IP-Adresse.  
  
### <a name="virtual-machine-manager"></a>Virtual Machine Manager  
Analytics Platform System verwendet Netzwerkvirtualisierung, um hochverfügbarkeit zu erzielen. Die Virtual Machine Manager hostet System Center, um das Betriebssystem auf den physischen Hosts bereitzustellen.  
  
Windows Server Update Services (WSUS), anwenden oder Entfernen von Windows-Updates auf allen Hosts und virtuellen Computern.  
  
### <a name="windows-server"></a>Windows Server  
Alle Hosts und virtuellen Computern in der Appliance führen Sie Windows Server-Betriebssystem.  
  
### <a name="failover-clustering"></a>Failoverclustering  
Windows-Failoverclustering bietet die Möglichkeit, Prozesse auf einem passiven Host neu zu starten, falls ein Host ausfällt.  
  
### <a name="storage-spaces"></a>Speicherplätze  
Windows-Speicherplätze verwaltet Benutzerdaten als Speicherpool für eine kleine Gruppe von Compute-Knoten. Wenn Compute-Knoten fehlschlägt, sind die Daten immer noch über einen anderen Computeknoten in der Gruppe zugegriffen werden kann.  
  
### <a name="hyper-v"></a>Hyper-V  
Microsoft Hyper-V Server bietet eine einfache und zuverlässige Virtualisierungslösung. Analytics Platform System verwendet Virtualisierungstechnologien aus, um die CPU-Ressourcen zu verteilen und hohe Verfügbarkeit für die PDW-Knoten und die Anwendung Fabric-Komponenten bereitgestellt.  
  
## <a name="sec2"></a>Nicht relationale Daten
PolyBase-Technologie integriert SQL Server-PDW-Daten mit externen Hadoop-Daten. Die Hadoop-Daten können auf einer dieser Quellen Hadoop-Daten gespeichert werden:  
  
-   Hortonworks Hadoop-Distribution  
  
-   Cloudera-Verteilung von Hadoop  
  
-   HDInsight-Daten auf Azure Storage-Blob  
  
## <a name="query-tools"></a>Abfragetools   
  
Abfragen werden geschrieben, mit der Transact\-SQL geändert wird, entsprechend der MPP-Arten von Abfragen. Alle Abfragen werden an den Steuerungsknoten übermittelt, die zum Ausführen der Abfrage über die Compute-Knoten hinweg einen parallelen Abfrageplan generiert.  
  
### <a name="sql-server-data-tools-ssdt"></a>SQL Server Data Tools (SSDT)  
SQL Server Data Tools in Visual Studio ausgeführt wird, und es ist unsere empfohlenen GUI-Tool zum Übermitteln von Abfragen in SQL Server PDW. Sie ähnelt damit SQL Server Management Studio, sodass Sie über einen Objekt-Explorer Navigieren zur Verfügung.  
  
Wenn Sie bereits über Visual Studio haben, können Sie die Tools herunterladen, die Sie kostenlos benötigen. 
<!-- MISSING LINKS
For more information, see [Install SQL Server database tooling  for Visual Studio &#40;SQL Server PDW&#41;](../sqlpdw/install-sql-server-database-tooling-for-visual-studio-sql-server-pdw.md).  
-->
  
### <a name="sqlcmd-command-line-query-tool"></a>Sqlcmd-Abfrage-Befehlszeilentool  
"SQLCMD" verwendet die SQL Server-Befehlszeilentool zum Ausführen von Transact\-SQL-Anweisungen und Systembefehle. Sie funktioniert mit SQL Server PDW und unsere empfohlenen Befehlszeilentool zum Abfragen von SQL Server PDW ist. Sie können mit Sqlcmd Transact ausführen\-SQL-Anweisungen interaktiv über die Befehlszeile wie eine Batchdatei oder über Windows PowerShell.  
  
<!-- MISSING LINKS

If you don’t have SQL Server, you can download this as a standalone package. For more information, see [Install sqlcmd Command-Line Client &#40;SQL Server PDW&#41;](../sqlpdw/install-sqlcmd-command-line-client-sql-server-pdw.md) 
--> 
  
### <a name="integration-services"></a>Integration Services  
Sie können die Integration Services auf SQL Server-PDW-Abfrage verwenden. 

<!-- MISSING LINKS
For more information, see [Connect With SQL Server Integration Services for Querying &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-integration-services-for-querying-sql-server-pdw.md). 

--> 
  
### <a name="linked-server"></a>Verbindungsserver  
Verwenden Sie eine verknüpften SQL Server-Server-Verbindung, können Sie SQL Server zum Senden von Transact\-SQL-Anweisungen in SQL Server PDW. 
<!-- MISSING LINKS
For more information, see [Connect With SQL Server Linked Server &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-linked-server-sql-server-pdw.md). 
--> 
  
## <a name="business-intelligence-tools"></a>Business Intelligence-Tools
  
### <a name="analysis-services"></a>Analysis Services  
SQL Server PDW ist eine gültige Datenquelle für Analysis Services-Datenbanken und Excel PowerPivot-Modelle. Verwenden den OLE DB-Anbieter, können Sie einen Analysis Services-Cube, um entweder mehrdimensionale analytische onlineverarbeitung (MOLAP) oder relationale analytische onlineverarbeitung (ROLAP)-Speicher verwenden, konfigurieren.  
  
<!-- MISSING LINKS
For more information, see [Connect With SQL Server Analysis Services &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-analysis-services-sql-server-pdw.md).  

-->
  
### <a name="report-builder"></a>Berichts-Generator  
Sie können SQL Server PDW als SQL Server-Datenquelle für Berichte verwenden, die Sie mithilfe von SQL Server-Berichts-Generator für Reporting Services zu entwickeln. Sie können auch SQL Server PDW als eine SQL Server-Datenquelle für Berichtsmodelle verwenden. Verwenden Sie Berichts-Manager oder der Report Server-API, können Sie ein Modell aus einer SQL Server-PDW-Datenbank generieren.  
  
<!-- MISSING LINKS

For more information, see [Connect With SQL Server Report Builder &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-report-builder-sql-server-pdw.md) and [Connect With SQL Server Reporting Services &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-reporting-services-sql-server-pdw.md). 

--> 
  
### <a name="power-pivot-for-excel"></a>Power Pivot für Excel  
Sie können in SQL Server PDW mit PowerPivot für Excel, als kostenloser Download verbinden, die deutlich die Datenanalysefunktionen von Excel erweitert wird.  
  
<!-- MISSING LINKS

For more information, see [Connect With PowerPivot for Excel &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-powerpivot-for-excel-sql-server-pdw.md).  

-->
  
## <a name="loading-tools"></a>Laden Tools 
  
### <a name="integration-services"></a>Integration Services  
PDW-Zieladapter, die Ihnen ermöglichen, SQL-ServerIntegration-Services verwenden, um das Laden von Daten in SQL Server PDW zu installieren.  

<!-- MISSING LINKS
For more information, see [Install Integration Services Destination Adapters &#40;SQL Server PDW&#41;](../sqlpdw/install-integration-services-destination-adapters-sql-server-pdw.md). 
--> 
  
### <a name="dwloader-command-line-loader"></a>Dwloader Command-Line-Ladeprogramm  
Dwloader ist ein Befehlszeilen-ladetool, die Daten parallel von Ihrem Server Laden auf die SQL Server PDW-Compute-Knoten geladen. 

<!-- MISSING LINKS
For more information, see [Install dwloader Command-Line Loader &#40;SQL Server PDW&#41;](../sqlpdw/install-dwloader-command-line-loader-sql-server-pdw.md)  
-->
  
### <a name="polybase-for-hadoop-integration"></a>PolyBase für Hadoop-Integration  
Mit der PolyBase-Technologie können Sie nicht relationale Daten aus einem Hadoop-Cluster in einer relationalen Tabelle in SQL Server PDW laden. Die Hadoop-Daten können in einer externen Hadoop-Cluster oder in einem Azure Storage Blob befinden.  

<!-- MISSING LINKS
For more information, see [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md).
-->  
  
## <a name="database-backup-and-restore"></a>Datenbank sichern und Wiederherstellen  
SQL Server PDW verwendet Transact-SQL-datenbanksicherung und Befehle für die Sicherung wiederherstellen und Benutzerdatenbanken, parallel in und aus einem backup-Server. SQL Server PDW schreibt die Sicherung in ein Verzeichnis in einer Windows-Dateifreigabe, und klicken Sie dann auch Daten wiederhergestellt, aus einer Windows-Dateifreigabe.  
  
Weitere Informationen finden Sie unter [für die Sicherung und Laden von Hardware planen](backup-and-loading-hardware.md) und [sichern und Wiederherstellen – Übersicht](backup-and-restore-overview.md)  
  
## <a name="remote-table-copy"></a>Remotetabellenkopie  
Die Remotetabellenkopie-Funktion ermöglicht Ihnen das Kopieren von Tabellen von SQL Server-PDW-Datenbanken auf SMP-SQL Server-Remotedatenbanken (nicht zur Appliance gehört). Hub- and -Spoke-Szenarios aktiviert für SQL Server PDW.  
  
<!-- MISSING LINKS

For more information, see [Remote Table Copy &#40;SQL Server PDW&#41;](../sqlpdw/remote-table-copy-sql-server-pdw.md).  

-->
  
## <a name="monitoring"></a>Überwachung  
Analytics Platform System verfügt über verschiedene Möglichkeiten zum Überwachen der Appliance-Aktivität  
  
### <a name="admin-console"></a>Verwaltungskonsole  
Die-Verwaltungskonsole können Sie zum aktuellen Status über die Integrität der Anwendung anzuzeigen. Dies führt zu einer Webanwendung auf dem steuerknoten und wird über Https zugegriffen werden kann.  
  
Weitere Informationen finden Sie unter [Überwachen der Appliance mithilfe der Verwaltungskonsole &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  

### <a name="system-views"></a>Systemsichten  
Die Admin-Konsole basiert auf System ansichtsabfragen. Sie können einzeln durch, um die spezifische Information zu erhalten, benötigen Sie die Sichten Abfragen.  

Weitere Informationen finden Sie unter [Überwachen der Appliance durch Verwenden von Systemansichten &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-views.md) 
  
### <a name="system-center-operations-manager"></a>System Center Operationsmanager  
Es sind System Center Operations Manager (SCOM) Management Packs für SQL Server PDW. 

Um die Einheit für SCOM konfigurieren zu können, finden Sie unter [Überwachen der Appliance, indem Sie mithilfe von System Center Operations Manager &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
  
