---
title: Parallele Data Warehouse Komponenten
description: In diesem Artikel werden die Geräte Software und die nicht Appliance-Softwarekomponenten von Analytics Platform System erläutert.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 5e609585e464cb52b996f45c7d8c57aaffcd79fe
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74400931"
---
# <a name="parallel-data-warehouse-components---analytics-platform-system"></a>Parallele Data Warehouse Komponenten-Analytics Platform System
In diesem Artikel werden die Geräte Software und die nicht Appliance-Softwarekomponenten von Analytics Platform System erläutert.  
  
<!-- MISSING LINKS

To learn more about Analytics Platform System, see:  
  
-   [Analytics Platform System architecture](architecture-overview.md)  
  
-   [Distributed and Replicated Tables &#40;SQL Server PDW&#41;](../sqlpdw/distributed-and-replicated-tables-sql-server-pdw.md)  
  
-   [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md)  
  
-   [Clustered Columnstore Indexes &#40;SQL Server PDW&#41;](../sqlpdw/clustered-columnstore-indexes-sql-server-pdw.md)  
  
-   [Query Process &#40;SQL Server PDW&#41;](../sqlpdw/query-process-sql-server-pdw.md)  
  
-   [Minimum and Maximum Values &#40;SQL Server PDW&#41;](../sqlpdw/minimum-and-maximum-values-sql-server-pdw.md)  

-->
   
  
![Parallele Data Warehouse Software](media/parallel-data-warehouse-software.png "Parallele Data Warehouse Software")  
  
## <a name="sec1"></a>Geräte Software-Abfrage Verarbeitung und Speicherung von Benutzerdaten  
  
### <a name="control-node"></a>Steuerknoten  
MPP-Engine  
Die MPP-Engine ist das Hirn des MPP-Systems (massive Parallel Processing). Die Option bewirkt Folgendes:  
  
-   Erstellt parallele Abfrage Pläne und koordiniert die parallele Ausführung von Abfragen auf den Computeknoten.  
  
-   Speichert und koordiniert Metadaten und Konfigurationsdaten für alle Datenbanken.  
  
-   Verwaltet SQL Server PDW Daten Bank Authentifizierung und-Autorisierung.  
  
-   Verfolgt den Hardware-und Software Status.  
  
### <a name="data-movement-service-dms"></a>Daten Verschiebungs Dienst (DMS)  
Der Daten Verschiebungs Dienst (Data Movement Service, DMS) ist Teil der "geheimen Soße" von PDW. Die Option bewirkt Folgendes:  
  
-   Überträgt Daten an und von den SQL Server PDW Knoten.  
  
-   Verarbeitet Abfrage Vorgänge, die das Übertragen von Daten zwischen den Knoten erfordern.  
  
-   Durch Optimieren der Datenübertragungsgeschwindigkeit wird die Abfrageleistung verbessert.  
  
### <a name="admin-console"></a>Verwaltungskonsole  
Die Verwaltungskonsole ist eine Webanwendung, in der die Gerätestatus-, Integritäts-und Leistungsinformationen dargestellt werden.  
  
### <a name="configuration-manager"></a>Konfigurations-Manager  
Der Configuration Manager (dwconfig. exe) ist das Tool, das von Anwendungs Administratoren zum Konfigurieren von Analytics Platform System verwendet wird.  
  
### <a name="control-node-databases"></a>Steuern von Knoten Datenbanken  
SQL Server verwaltet alle Datenbanken auf dem Steuer Knoten.  
  
-   Die Shelldatenbank verwaltet die Metadaten für alle verteilten Benutzer Datenbanken.  
  
-   Tempdb enthält die Metadaten für alle temporären Benutzer Tabellen in der gesamten Anwendung.  
  
-   Master ist die Master Tabelle für SQL Server auf dem Steuer Knoten.  
  
### <a name="compute-node"></a>Computeknoten  
Die Computeknoten sind parallele Datenverarbeitungs-und Speichereinheiten. Sie verfügen über einen direkt angeschlossenen Speicher und verwenden SQL Server zum Verwalten von Benutzerdaten.  
  
### <a name="data-movement-service-dms"></a>Daten Verschiebungs Dienst (DMS)  
Der Daten Verschiebungs Dienst (DMS) wird auf jedem Computeknoten ausgeführt, um folgende Aufgaben durchzuführen:  
  
-   Im Rahmen der Verarbeitung paralleler Abfragen überträgt DMS Daten an und von anderen Computer Knoten und dem Steuerungs Knoten.  
  
-   DMS, die auf jedem Computeknoten ausgeführt werden, empfängt Daten Ladevorgänge parallel. Daten werden parallel direkt vom Lade Server auf die Computeknoten geladen.  
  
-   DMS überträgt Daten von jedem Computeknoten direkt auf den Sicherungs Server.  
  
-   Bei Verwendung von polybase überträgt DMS Daten an einen oder aus einem externen Hadoop-Cluster oder Azure Storage BLOB.  
  
### <a name="compute-node-databases"></a>Compute-Knoten Datenbanken 
Jeder Computeknoten führt eine Instanz von SQL Server aus, um Abfragen zu verarbeiten und Benutzerdaten zu verwalten.  
  
## <a name="appliance-fabric"></a>Appliance-Fabric  
Das Appliance-Fabric stellt das Betriebssystem, Dienste und die Netzwerkinfrastruktur für das Gerät bereit.  
  
### <a name="domain-controller"></a>Domänencontroller  
Active Directory (AD) Domain Services (DS)  
Analytics Platform System führt die Authentifizierung zwischen den Analytics-Plattformsystem Knoten durch und verwaltet die Authentifizierung von SQL Server PDW Windows-Authentifizierungs Anmeldungen.  
  
DNS-Dienst  
Mit Windows Domain Name Service (DNS) werden Domänen Namen in IP-Adressen für die Analytics Platform System-Appliance aufgelöst.  
  
### <a name="windows-deployment-service"></a>Windows-Bereitstellungs Dienst  
Der Windows-Bereitstellungs Dienst (WDS) stellt das Windows Server-Betriebssystem auf dem Gerät bereit. Sie wird auf allen Hosts und virtuellen Computern auf der gesamten Appliance bereitgestellt.  
  
Der DHCP-Dienst erstellt IP-Adressen, sodass die Hosts innerhalb der Geräte Domäne dem Geräte Netzwerk beitreten können, ohne dass eine vorkonfigurierte IP-Adresse vorhanden ist.  
  
### <a name="virtual-machine-manager"></a>Virtual Machine Manager  
Analytics Platform System verwendet die Virtualisierung, um Hochverfügbarkeit zu erzielen. Der Virtual Machine Manager hostet System Center, um das Betriebs System auf den physischen Hosts bereitzustellen.  
  
Windows Server Update Services (WSUS) zum Anwenden oder Entfernen von Windows-Updates auf allen Hosts und virtuellen Maschinen.  
  
### <a name="windows-server"></a>Windows Server  
Auf allen Hosts und virtuellen Maschinen in der Appliance wird das Windows Server-Betriebssystem ausgeführt.  
  
### <a name="failover-clustering"></a>Failoverclustering  
Windows-Failoverclustering bietet die Möglichkeit, Prozesse auf einem passiven Host neu zu starten, wenn ein Host ausfällt.  
  
### <a name="storage-spaces"></a>Speicherplätze  
Windows-Speicherplätze verwalten Benutzerdaten als Speicherpool für eine kleine Gruppe von Computeknoten. Wenn ein Computeknoten ausfällt, kann auf die Daten immer noch über einen anderen Computeknoten in der Gruppe zugegriffen werden.  
  
### <a name="hyper-v"></a>Hyper-V  
Microsoft Hyper-V Server bietet eine einfache und zuverlässige Virtualisierungslösung. Analytics Platform System verwendet Virtualisierungen, um CPU-Ressourcen auszugleichen und Hochverfügbarkeit für die PDW-Knoten und Appliance Fabric-Komponenten bereitzustellen.  
  
## <a name="sec2"></a>Nicht relationale Daten
Die polybase-Technologie integriert SQL Server PDW Daten mit externen Hadoop-Daten. Die Hadoop-Daten können auf allen folgenden Hadoop-Datenquellen gespeichert werden:  
  
-   Hortonworks Hadoop-Verteilung  
  
-   Cloudera-Verteilung von Hadoop  
  
-   Hdinsight-Daten, die auf Azure Storage BLOB gespeichert sind  
  
## <a name="query-tools"></a>Abfragetools   
  
Abfragen werden mit Transact\--SQL geschrieben, das an die MPP-Natur der Abfragen angepasst ist. Alle Abfragen werden an den Steuerungs Knoten übermittelt, von dem ein paralleler Abfrageplan generiert wird, um die Abfrage über die Computeknoten hinweg auszuführen.  
  
### <a name="sql-server-data-tools-ssdt"></a>SQL Server Data Tools (SSDT)  
SQL Server Data Tools wird innerhalb von Visual Studio ausgeführt und ist unser empfohlenes GUI-Tool zum Senden von Abfragen an SQL Server PDW. Sie ähnelt SQL Server Management Studio, indem Sie durch einen Objekt-Explorer navigieren können.  
  
Wenn Sie noch nicht über Visual Studio verfügen, können Sie die Tools herunterladen, die Sie kostenlos benötigen. 
<!-- MISSING LINKS
For more information, see [Install SQL Server database tooling  for Visual Studio &#40;SQL Server PDW&#41;](../sqlpdw/install-sql-server-database-tooling-for-visual-studio-sql-server-pdw.md).  
-->
  
### <a name="sqlcmd-command-line-query-tool"></a>SQLCMD-Befehlszeilen Abfrage-Tool  
sqlcmd ist das SQL Server Befehlszeilen Tool zum Ausführen von Transact\--SQL-Anweisungen und System Befehlen. Es funktioniert mit SQL Server PDW und ist unser empfohlenes Befehlszeilen Tool für die Abfrage SQL Server PDW. Mit sqlcmd können Sie Transact\--SQL-Anweisungen interaktiv von der Befehlszeile, als Batchdatei oder über Windows PowerShell ausführen.  
  
<!-- MISSING LINKS

If you don't have SQL Server, you can download this as a standalone package. For more information, see [Install sqlcmd Command-Line Client &#40;SQL Server PDW&#41;](../sqlpdw/install-sqlcmd-command-line-client-sql-server-pdw.md) 
--> 
  
### <a name="integration-services"></a>Integration Services  
Sie können Integration Services verwenden, um SQL Server PDW abzufragen. 

<!-- MISSING LINKS
For more information, see [Connect With SQL Server Integration Services for Querying &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-integration-services-for-querying-sql-server-pdw.md). 

--> 
  
### <a name="linked-server"></a>Verknüpfter Server  
Mithilfe einer SQL Server Verbindungs Server Verbindung können Sie SQL Server verwenden, um Transact\--SQL-Anweisungen an SQL Server PDW zu übermitteln. 
<!-- MISSING LINKS
For more information, see [Connect With SQL Server Linked Server &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-linked-server-sql-server-pdw.md). 
--> 
  
## <a name="business-intelligence-tools"></a>Business Intelligence-Tools
  
### <a name="analysis-services"></a>Analysis Services  
SQL Server PDW ist eine gültige Datenquelle für Analysis Services Datenbanken und Excel Power Pivot-Modelle. Mithilfe des OLE DB Anbieters können Sie einen Analysis Services Cube für die Verwendung von MOLAP (Multidimensional Online Analytical Processing) oder ROLAP-Speicher (Relational Online Analytical Processing) konfigurieren.  
  
<!-- MISSING LINKS
For more information, see [Connect With SQL Server Analysis Services &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-analysis-services-sql-server-pdw.md).  

-->
  
### <a name="report-builder"></a>Berichts-Generator  
Sie können SQL Server PDW als SQL Server Datenquelle für Berichte verwenden, die Sie mit SQL Server Berichts-Generator für Reporting Services entwickeln. Sie können auch SQL Server PDW als SQL Server Quelle für Berichts Modelle verwenden. Mithilfe von Berichts-Manager oder der Berichts Server-API können Sie ein Modell aus einer SQL Server PDW Datenbank generieren.  
  
<!-- MISSING LINKS

For more information, see [Connect With SQL Server Report Builder &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-report-builder-sql-server-pdw.md) and [Connect With SQL Server Reporting Services &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-sql-server-reporting-services-sql-server-pdw.md). 

--> 
  
### <a name="power-pivot-for-excel"></a>Power Pivot für Excel  
Mit Power Pivot für Excel können Sie eine Verbindung mit SQL Server PDW herstellen. ein kostenloser Download, der die Datenanalyse Funktionen von Excel erheblich erweitert.  
  
<!-- MISSING LINKS

For more information, see [Connect With PowerPivot for Excel &#40;SQL Server PDW&#41;](../sqlpdw/connect-with-powerpivot-for-excel-sql-server-pdw.md).  

-->
  
## <a name="loading-tools"></a>Laden von Tools 
  
### <a name="integration-services"></a>Integration Services  
Installieren Sie PDW-spezifische Ziel Adapter, die die Verwendung von SQL Server Integration Services zum Laden von Daten in SQL Server PDW ermöglichen.  

<!-- MISSING LINKS
For more information, see [Install Integration Services Destination Adapters &#40;SQL Server PDW&#41;](../sqlpdw/install-integration-services-destination-adapters-sql-server-pdw.md). 
--> 
  
### <a name="dwloader-command-line-loader"></a>"dwloader-Befehlszeilen Lade Modul  
"dwloader ist ein Befehlszeilen-Lade Tool, das Daten parallel von Ihrem Lade Server auf die SQL Server PDW Computeknoten lädt. 

<!-- MISSING LINKS
For more information, see [Install dwloader Command-Line Loader &#40;SQL Server PDW&#41;](../sqlpdw/install-dwloader-command-line-loader-sql-server-pdw.md)  
-->
  
### <a name="polybase-for-hadoop-integration"></a>Polybase für Hadoop-Integration  
Mit der polybase-Technologie können Sie nicht relationale Daten aus einem Hadoop-Cluster in eine relationale Tabelle in SQL Server PDW laden. Die Hadoop-Daten können sich in einem externen Hadoop-Cluster oder in einem Azure Storage BLOB befinden.  

<!-- MISSING LINKS
For more information, see [PolyBase &#40;SQL Server PDW&#41;](../sqlpdw/polybase-sql-server-pdw.md).
-->  
  
## <a name="database-backup-and-restore"></a>Datenbanksicherung und-Wiederherstellung  
SQL Server PDW verwendet Befehle zum Sichern und Wiederherstellen von Transact-SQL-Datenbanken, um Benutzer Datenbanken parallel zu und von einem Sicherungs Server zu sichern und wiederherzustellen. SQL Server PDW schreibt die Sicherung in ein Verzeichnis in einer Windows-Dateifreigabe und stellt dann gleichzeitig Daten aus einer Windows-Dateifreigabe wieder her.  
  
Weitere Informationen finden Sie unter [Planen der Sicherung und Laden von Hardware](backup-and-loading-hardware.md) und [Sichern und Wiederherstellen (Übersicht](backup-and-restore-overview.md) ).  
  
## <a name="remote-table-copy"></a>Remote Tabellen Kopie  
Mit dem Feature "Remote Tabellen Kopie" können Sie Tabellen aus SQL Server PDW-Datenbanken in Remote-SMP-SQL Server Datenbanken (nicht-Appliance) kopieren. Dies ermöglicht Hub-und sprach Szenarios für SQL Server PDW.  
  
<!-- MISSING LINKS

For more information, see [Remote Table Copy &#40;SQL Server PDW&#41;](../sqlpdw/remote-table-copy-sql-server-pdw.md).  

-->
  
## <a name="monitoring"></a>Überwachung  
Analytics Platform System bietet mehrere Möglichkeiten zum Überwachen der Geräte Aktivität  
  
### <a name="admin-console"></a>Verwaltungskonsole  
Mithilfe der Verwaltungskonsole können Sie den aktuellen Status der Geräte Integrität anzeigen. Diese wird als Webanwendung auf dem Steuer Knoten ausgeführt und kann über HTTPS aufgerufen werden.  
  
Weitere Informationen finden Sie unter [Überwachen der Appliance mithilfe der Verwaltungskonsole &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  

### <a name="system-views"></a>Systemsichten  
Die-Verwaltungskonsole basiert auf Systemsicht Abfragen. Sie können die System Sichten einzeln Abfragen, um die benötigten Informationen zu erhalten.  

Weitere Informationen finden Sie unter [Überwachen der Appliance mithilfe von System Sichten &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-views.md) 
  
### <a name="system-center-operations-manager"></a>System Center Operations Manager  
Es gibt System Center Operations Manager Management Packs (SCOM) für SQL Server PDW. 

Informationen zum Konfigurieren des Geräts für SCOM finden Sie unter [Überwachen der Appliance mithilfe System Center Operations Manager &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
  
