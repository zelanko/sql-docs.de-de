---
title: Von den-Editionen unterstützte Funktionen SQL Server 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 5da61ff5-12b9-48e6-b3c8-0dacca1751c4
author: mightypen
ms.author: genemi
manager: craigg
ms.openlocfilehash: caae4212e2182ae6afde29b0fed1aaee4f05645a
ms.sourcegitcommit: ff1bd69a8335ad656b220e78acb37dbef86bc78a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2020
ms.locfileid: "78339292"
---
# <a name="features-supported-by-the-editions-of-sql-server-2014"></a>Von den SQL Server 2014-Editionen unterstützte Funktionen


  Dieses Thema bietet detaillierte Informationen zu den von verschiedenen [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]-Versionen unterstützten Funktionen. 

 > **Hinweis:** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ist in einer Evaluierungsversion für einen Testzeitraum von 180 Tagen verfügbar. Weitere Informationen finden Sie auf der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [von](https://go.microsoft.com/fwlink/?LinkId=190955).  
> 
> **Hinweis:** Informationen zu Funktionen, die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] von Evaluation und Developer Edition unterstützt werden, finden Sie unter Enterprise Feature  
  
 Um zur Tabelle für eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Technologie zu navigieren, klicken Sie auf den zugehörigen Link:  
  
 [Feld übergreifende Skalierungs Grenzwerte](#CrossBoxScale)  
  
 [Hochverfügbarkeit](#High_availability)  
  
 [Skalierbarkeit und Leistung](#Scalability)  
  
 [Security](#Enterprise_security)  
  
 [Replikation](#Replication)  
  
 [Verwaltungstools](#Mgmt_Tools)  
  
 [RDBMS-Verwaltbarkeit](#RDBMS_mgmt)  
  
 [Entwicklungs Tools](#Dev_tools)  
  
 [Programmierbarkeit](#Programmability)  
  
 [Integration Services](#SSIS)  
  
 [Integration Services – Erweiterte Adapter](#SSIS_AA)  
  
 [Integration Services – Erweiterte Transformationen](#SSIS_AT)  
  
 [Master Data Services](#MDS)  
  
 [Data Warehouse](#Data_warehouse)  
  
 [Analysis Services](#SSAS)  
  
 [BI-Semantikmodell (mehrdimensional)](#BISemModel_multi)  
  
 [BI-Semantik Modell (tabellarisch)](#BISemModel_tabular)  
  
 [PowerPivot für SharePoint](#PowerPivot)  
  
 [Data Mining](#DataMining)  
  
 [Reporting Services](#Reporting)  
  
 [Business Intelligence-Clients](#BIClients)  
  
 [Räumliche Dienste und Standortdienste](#Spatial)  
  
 [Zusätzliche Datenbankdienste](#Add_DBServices)  
  
 [Andere Komponenten](#Other_Components)  
  
##  <a name="CrossBoxScale"></a>Feld übergreifende Skalierungs Grenzwerte  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Maximale von einer einzelnen Instanz verwendete Rechenkapazität ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Datenbank-Engine)<sup>1</sup>|Maximum des Betriebssystems|Beschränkt auf weniger als 4 Sockets oder 16 Kerne|Beschränkt auf weniger als 4 Sockets oder 16 Kerne|Beschränkt auf weniger als 4 Sockets oder 16 Kerne|Beschränkt auf weniger als 1 Socket oder 4 Kerne|Beschränkt auf weniger als 1 Socket oder 4 Kerne|Beschränkt auf weniger als 1 Socket oder 4 Kerne|  
|Maximale von einer einzelnen Instanz verwendete Rechenkapazität (Analysis Services Reporting Services) <sup>1</sup>|Maximum des Betriebssystems|Maximum des Betriebssystems|Beschränkt auf weniger als 4 Sockets oder 16 Kerne|Beschränkt auf weniger als 4 Sockets oder 16 Kerne|Beschränkt auf weniger als 1 Socket oder 4 Kerne|Beschränkt auf weniger als 1 Socket oder 4 Kerne|Beschränkt auf weniger als 1 Socket oder 4 Kerne|  
|Maximaler genutzter Arbeitsspeicher (pro Instanz der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenbank-Engine)|Maximum des Betriebssystems|128 GB|128 GB|64 GB|1 GB|1 GB|1 GB|  
|Maximaler genutzter Arbeitsspeicher (pro Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)])|Maximum des Betriebssystems|Maximum des Betriebssystems|64 GB|–|–|–|–|  
|Maximaler genutzter Arbeitsspeicher (pro Instanz von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)])|Maximum des Betriebssystems|Maximum des Betriebssystems|64 GB|64 GB|4 GB|–|–|  
|Maximale relationale Datenbankgröße|524 PB|524 PB|524 PB|524 PB|10 GB|10 GB|10 GB|  
  
 <sup>1</sup> die Enterprise Edition mit einer Lizenzierung auf Grundlage von Server + Client Zugriffslizenz (CAL) (für neue Verträge nicht verfügbar) ist auf maximal 20 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Kerne pro-Instanz beschränkt. Für das auf Prozessorkernen basierende Serverlizenzierungsmodell gelten keine Beschränkungen. Weitere Informationen finden Sie unter [Compute Capacity Limits by Edition of SQL Server](../sql-server/compute-capacity-limits-by-edition-of-sql-server.md).  
  
##  <a name="High_availability"></a>Hohe Verfügbarkeit  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Server Core-Unterstützung<sup>1</sup>|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|Protokollversand|Ja|Ja|Ja|Ja||||  
|Datenbankspiegelung|Ja|Ja (nur SAFETY FULL)|Ja (nur SAFETY FULL)|Nur WITNESS|Nur WITNESS|Nur WITNESS|Nur WITNESS|  
|Sicherungskomprimierung|Ja|Ja|Ja|||||  
|Datenbankmomentaufnahme|Ja|||||||  
|AlwaysOn-Failoverclusterinstanzen|Ja (Knotenunterstützung: Maximum des Betriebssystems)|Ja (Knotenunterstützung: 2)|Ja (Knotenunterstützung: 2)|||||  
|AlwaysOn-Verfügbarkeitsgruppen|Ja (bis zu 8 sekundäre Replikate, einschließlich 2 synchronen sekundären Replikaten)|||||||  
|Connection Director|Ja|||||||  
|Onlineseiten- und Onlinedateiwiederherstellung|Ja|||||||  
|Online-Indizierung|Ja|||||||  
|Onlineschemaänderung|Ja|||||||  
|Schnelle Wiederherstellung|Ja|||||||  
|Gespiegelte Sicherungen|Ja|||||||  
|Arbeitsspeicher<sup>und CPU-</sup> Auslastung (Hot)|Ja|||||||  
|Datenbankwiederherstellungsberater|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|Verschlüsselte Sicherung|Ja|Ja|Ja|||||  
|Intelligente Sicherung|Ja|Ja|Ja|Nein||||  
  
 <sup>1</sup> Weitere Informationen zum Installieren [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] von auf Server Core finden Sie unter Installieren von [SQL Server 2014 auf Server Core](../database-engine/install-windows/install-sql-server-on-server-core.md).  
  
 <sup>2</sup> Diese Funktion ist nur für 64-Bit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]verfügbar.  
  
##  <a name="Scalability"></a>Skalierbarkeit und Leistung  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Unterstützung mehrerer Instanzen|50|50|50|50|50|50|50|  
|Tabellen- und Indexpartitionierung|Ja|||||||  
|Datenkomprimierung|Ja|||||||  
|Resource Governor|Ja|||||||  
|Partitionstabellenparallelität|Ja|||||||  
|Mehrere FILESTREAM-Container|Ja|||||||  
|NUMA-basierter Arbeitsspeicher für umfangreiche Seiten und Zuordnung von Pufferarrays|Ja|||||||  
|Puffer Pool Erweiterung <sup>1</sup>|Ja|Ja|Ja|||||  
|Ressourcenkontrolle für E/A-Vorgänge|Ja|||||||  
|In-Memory-OLTP <sup>1</sup>|Ja|||||||  
|Verzögerte Dauerhaftigkeit|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
  
 <sup>1</sup> diese Funktion ist nur für 64-Bit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]verfügbar.  
  
##  <a name="Enterprise_security"></a> Sicherheit  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Allgemeine Überwachung|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|Differenzierte Überwachung|Ja|||||||  
|Transparente Datenbankverschlüsselung|Ja|||||||  
|Erweiterbare Schlüsselverwaltung|Ja|||||||  
|Benutzerdefinierte Rollen|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|Eigenständige Datenbanken|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|Verschlüsselung von Sicherungen|Ja|Ja|Ja|||||  
  
##  <a name="Replication"></a> Replikation  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Änderungs Nachverfolgung|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|Mergereplikation|Ja|Ja|Ja|Ja (Nur Abonnent)|Ja (Nur Abonnent)|Ja (Nur Abonnent)|Ja (Nur Abonnent)|  
|Transaktionsreplikation|Ja|Ja|Ja|Ja (Nur Abonnent)|Ja (Nur Abonnent)|Ja (Nur Abonnent)|Ja (Nur Abonnent)|  
|Momentaufnahmereplikation|Ja|Ja|Ja|Ja (Nur Abonnent)|Ja (Nur Abonnent)|Ja (Nur Abonnent)|Ja (Nur Abonnent)|  
|Heterogene Abonnenten|Ja|Ja|Ja|||||  
|Veröffentlichungen mit Oracle|Ja|||||||  
|Peer-zu-Peer-Transaktionsreplikation|Ja|||||||  
  
##  <a name="Mgmt_Tools"></a>Verwaltungs Tools  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|SQL Management Objects (SMO)|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|SQL-Konfigurations-Manager|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|SQL CMD (Command Prompt Tool – Eingabeaufforderungstool)|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Management Studio|Ja|Ja|Ja|Ja|Ja|Ja||  
|Distributed Replay: Administratortool|Ja|Ja|Ja|Ja|Ja|Ja||  
|Distributed Replay - Client|Ja|Nein|Ja|Ja||||  
|Distributed Replay - Controller|Ja (Enterprise unterstützt bis zu 16 Clients, Developer unterstützt nur 1 Client)|Nein|Ja (nur 1 Client unterstützt)|Ja (nur 1 Client unterstützt)||||  
|SQL Profiler|Ja|Ja|Ja|Nein<sup>2</sup>|Nein<sup>2</sup>|Nein<sup>2</sup>|Nein<sup>2</sup>|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent|Ja|Ja|Ja|Ja||||  
|Microsoft System Center Operations Manager Management Pack|Ja|Ja|Ja|Ja||||  
|Datenbankoptimierungsratgeber (DTA)|Ja|Ja|Ja<sup>3</sup>|Ja<sup>3</sup>||||  
|Assistent zum [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Bereitstellen einer Datenbank in einer Azure-VM|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Datendateien in Azure|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
  
 <sup>2</sup> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Web, [!INCLUDE[ssExpress](../includes/ssexpress-md.md)], [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Tools und [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services können mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] der Standard Edition und [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] der Enterprise Edition profiliert werden.  
  
 <sup>3</sup> Optimierung ist nur in Funktionen der Standard Edition aktiviert.  
  
##  <a name="RDBMS_mgmt"></a>RDBMS-Verwaltbarkeit  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Benutzerinstanzen|||||Ja|Ja|Ja|  
|LocalDB|||||Ja|Ja||  
|Dedizierte Administratorverbindung|Ja|Ja|Ja|Ja|Ja (unter Ablaufverfolgungsflag)|Ja (unter Ablaufverfolgungsflag)|Ja (unter Ablaufverfolgungsflag)|  
|PowerShell-Skriptunterstützung|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|Sy-p-Unterstützung<sup>1</sup>|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|Unterstützung für Komponenten Vorgänge der Datenebenenanwendung-extrahieren, bereitstellen, aktualisieren, löschen|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|Richtlinienautomatisierung (Überprüfung nach Zeitplan und Änderungen)|Ja|Ja|Ja|Ja||||  
|Sammler von Leistungsdaten|Ja|Ja|Ja|Ja||||  
|Fähigkeit zur Registrierung als verwaltete Instanz in einer Mehrfachinstanzverwaltung|Ja|Ja|Ja|Ja||||  
|Standardleistungsberichte|Ja|Ja|Ja|Ja||||  
|Planhinweislisten und Planeinfrierung für Planhinweislisten|Ja|Ja|Ja|Ja||||  
|Direkte Abfrage von indizierten Sichten (mittels NOEXPAND-Hinweis)|Ja|Ja|Ja|Ja||||  
|Automatische Wartung für indizierte Sichten|Ja|Ja|Ja|Ja||||  
|Verteilte partitionierte Sichten|Ja|Teilweise. Verteilte partitionierte Sichten sind nicht aktualisierbar|Teilweise. Verteilte partitionierte Sichten sind nicht aktualisierbar|Teilweise. Verteilte partitionierte Sichten sind nicht aktualisierbar|Teilweise. Verteilte partitionierte Sichten sind nicht aktualisierbar|Teilweise. Verteilte partitionierte Sichten sind nicht aktualisierbar|Teilweise. Verteilte partitionierte Sichten sind nicht aktualisierbar|  
|Parallele Indexvorgänge|Ja|||||||  
|Automatische Verwendung indizierter Sichten mittels Abfrageoptimierer|Ja|||||||  
|Parallele Konsistenzprüfung|Ja|||||||  
|Steuerungspunkt für das [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Hilfsprogramm|Ja|||||||  
|Eigenständige Datenbanken|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|Puffer Pool Erweiterung<sup>2</sup>|Ja|Ja|Ja|||||  
  
 <sup>1</sup> Weitere Informationen finden Sie unter [Überlegungen zum Installieren von SQL Server mithilfe der System](../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md)Vorbereitung.  
  
 <sup>2</sup> diese Funktion ist nur für 64-Bit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]verfügbar.  
  
##  <a name="Dev_tools"></a>Entwicklungs Tools  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[msCoName](../includes/msconame-md.md)]Visual Studio-Integration|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|IntelliSense ([!INCLUDE[tsql](../includes/tsql-md.md)] und MDX)|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]|Ja|Ja|Ja|Ja|Ja|||  
|SQL-Abfrage Bearbeitungs-und-Entwurfs Tools<sup>1</sup>|Ja|Ja|Ja|||||  
|Versions kontrollunterstützung<sup>1</sup>|Ja|Ja|Ja|||||  
|MDX-Bearbeitungs-, Debug-und Entwurfs Tools<sup>1</sup>|Ja|Ja|Ja|||||  
  
 <sup>1</sup> diese Funktion ist für die 64-Bit-Version der Standard Edition nicht verfügbar.  
  
##  <a name="Programmability"></a> Programmability  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Common Language Runtime (CLR)-Integration|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|Systemeigene XML-Unterstützung|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|XML-Indizierung|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|Merge & Upsert-Funktionen|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|FILESTREAM-Unterstützung|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|FileTable|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|Datums- und Uhrzeitdatentypen|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|Internationalisierungsunterstützung|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|Volltextsuche und semantische Suche|Ja|Ja|Ja|Ja|Ja|||  
|Angabe der Sprache in einer Abfrage|Ja|Ja|Ja|Ja|Ja|||  
|Service Broker (Messaging)|Ja|Ja|Ja|Nein (nur Client)|Nein (nur Client)|Nein (nur Client)|Nein (nur Client)|  
|[!INCLUDE[tsql](../includes/tsql-md.md)]Endpunkte|Ja|Ja|Ja|Ja||||  
  
##  <a name="SSIS"></a> Integration Services  
  
|Funktion|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|-------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Import/Export-Assistent|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|Integrierte Datenquellenkonnektoren|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|SSIS-Designer und Laufzeit|Ja|Ja|Ja|||||  
|Grundlegende Transformationen|Ja|Ja|Ja|||||  
|Grundlegende Datenprofilerstellungs-Tools|Ja|Ja|Ja|||||  
|Change Data Capture Service für Oracle von Attunity|Ja|||||||  
|Change Data Capture Designer für Oracle von Attunity|Ja|||||||  
  
###  <a name="SSIS_AA"></a>Integration Services erweiterte Adapter  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|High-Performance-Oracle-Ziel|Ja|||||||  
|High-Performance-Teradata-Ziel|Ja|||||||  
|SAP BW-Quelle und -Ziel|Ja|||||||  
|Zieladapter des Data Mining-Modelltrainings|Ja|||||||  
|Zieladapter für Dimensionsverarbeitung|Ja|||||||  
|Zieladapter für Partitionsverarbeitung|Ja|||||||  
|Change Data Capture-Komponenten von Attunity|Ja|||||||  
|Konnektor für Open Database Connectivity (ODBC) von Attunity|Ja|||||||  
  
###  <a name="SSIS_AT"></a>Erweiterte Transformationen Integration Services  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Persistente Suchen (hohe Leistungsfähigkeit)|Ja|||||||  
|Transformation für Data Mining-Abfragen|Ja|||||||  
|Transformationen für Fuzzygruppierung und -suche|Ja|||||||  
|Transformationen für Ausdrucksextrahierung und -suche|Ja|||||||  
  
##  <a name="MDS"></a>Master Data Services  
  
> [!NOTE]  
>  -   
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] ist nur in den 64-Bit-Editionen von Business Intelligence and Enterprise verfügbar.  
  
|Funktion|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|-------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]Verbindung|Ja|Ja||||||  
|[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]Webanwendung|Ja|Ja||||||  
  
##  <a name="Data_warehouse"></a>Data Warehouse  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Erstellen von Cubes ohne Datenbank|Ja|Ja|Ja|||||  
|Automatisches Generieren von Staging- und Data Warehouse-Schemas|Ja|Ja|Ja|||||  
|Erfassung geänderter Daten|Ja|||||||  
|Optimierung von Sternjoin-Abfragen|Ja|||||||  
|Skalierbare schreibgeschützte Analysis Services-Konfiguration|Ja|||||||  
|Parallele Abfrageverarbeitung bei partitionierten Tabellen und Indizes|Ja|||||||  
|Speicheroptimierte xVelocity-columnstore-Indizes|Ja|||||||  
|Globale Batchaggregation|Ja|||||||  
  
##  <a name="SSAS"></a>Analysis Services  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Skalierbare freigegebene Datenbanken (Anfügen/Trennen, schreibgeschützte Datenbanken)|Ja|Ja||||||  
|Sichern/Wiederherstellen, Anfügen/Trennen von Datenbanken|Ja|Ja|Ja|||||  
|Synchronisieren von Datenbanken|Ja|Ja||||||  
|Hochverfügbarkeit|Ja|Ja|Ja|||||  
|Programmierbarkeit (AMO, ADOMD.NET, OLEDB, XML/A, ASSL)|Ja|Ja|Ja|||||  
  
###  <a name="BISemModel_multi"></a>BI-Semantik Modell (mehrdimensional)  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Semiadditive Measures|Ja|Ja|Nein<sup>1</sup>|||||  
|Hierarchien|Ja|Ja|Ja|||||  
|KPIs (Key Performance Indicators)|Ja|Ja|Ja|||||  
|Perspektiven|Ja|Ja||||||  
|Aktionen|Ja|Ja|Ja|||||  
|Kontointelligenz|Ja|Ja|Ja|||||  
|Zeitintelligenz|Ja|Ja|Ja|||||  
|Benutzerdefinierte Rollups|Ja|Ja|Ja|||||  
|Cube-Rückschreiben|Ja|Ja|Ja|||||  
|Rückschreiben von Dimensionen|Ja|Ja||||||  
|Rückschreibezellen|Ja|Ja|Ja|||||  
|Drillthrough ausführen|Ja|Ja|Ja|||||  
|Erweiterte Hierarchietypen (über- und untergeordnet, unregelmäßige Hierarchien)|Ja|Ja|Ja|||||  
|Erweiterte Dimensionen (Bezugsdimensionen, m:n-Dimensionen)|Ja|Ja|Ja|||||  
|Verknüpfte Measures und Dimensionen|Ja|Ja||||||  
|Translations|Ja|Ja|Ja|||||  
|Aggregationen|Ja|Ja|Ja|||||  
|Mehrere Partitionen|Ja|Ja|Ja, bis zu 3|||||  
|Proaktives Zwischenspeichern|Ja|Ja||||||  
|Benutzerdefinierte Assemblys (gespeicherte Prozeduren)|Ja|Ja|Ja|||||  
|MDX-Abfragen und Skripts|Ja|Ja|Ja|||||  
|DAX-Abfragen|Ja|Ja||||||  
|Rollenbasiertes Sicherheitsmodell|Ja|Ja|Ja|||||  
|Sicherheit auf Dimensions- und Zellenebene|Ja|Ja|Ja|||||  
|Skalierbarer Zeichenfolgenspeicher|Ja|Ja|Ja|||||  
|MOLAP-, ROLAP-, HOLAP-Speichermodi|Ja|Ja|Ja|||||  
|Binärer und komprimierter XML-Transport|Ja|Ja|Ja|||||  
|Pushmodus-Verarbeitung|Ja|Ja||||||  
|Direktes Rückschreiben|Ja|Ja||||||  
|Measureausdrücke|Ja|Ja||||||  
  
 <sup>1</sup> Das semiadditive LastChild-Measure wird in der Standard Edition unterstützt, aber andere semiadditive Measures, wie z. b. None, firstChild, FirstNonEmpty, LastNonEmpty, AverageOfChildren und ByAccount, sind nicht. Additive Measures, z. B. Sum, Count, Min, Max und nicht additive Measures (DistinctCount) werden in allen Editionen unterstützt.  
  
###  <a name="BISemModel_tabular"></a>BI-Semantik Modell (tabellarisch)  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Hierarchien|Ja|Ja||||||  
|KPIs (Key Performance Indicators)|Ja|Ja||||||  
|Perspektiven|Ja|Ja||||||  
|Translations|Ja|Ja||||||  
|DAX-Berechnungen, DAX-Abfragen, MDX-Abfragen|Ja|Ja||||||  
|Sicherheit auf Zeilenebene|Ja|Ja||||||  
|Partitionen|Ja|Ja||||||  
|Arbeitsspeicherinterne und DirectQuery-Speichermodi (nur tabellarisch)|Ja|Ja||||||  
  
###  <a name="PowerPivot"></a>PowerPivot für SharePoint  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|SharePoint-Farmintegration auf Grundlage der Shared Services-Architektur|Ja|Ja||||||  
|Nutzungsberichte|Ja|Ja||||||  
|Systemüberwachungsregeln|Ja|Ja||||||  
|PowerPivot-Katalog|Ja|Ja||||||  
|PowerPivot-Datenaktualisierung|Ja|Ja||||||  
|PowerPivot-Datenfeeds|Ja|Ja||||||  
  
###  <a name="DataMining"></a>Data Mining  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Standardalgorithmen|Ja|Ja|Ja|||||  
|Data Mining-Tools (Assistenten, Editoren, Abfrage-Generatoren)|Ja|Ja|Ja|||||  
|Kreuzvalidierung im Vergleich|Ja|Ja||||||  
|Modelle für gefilterte Teilmengen von Daten der Miningstruktur|Ja|Ja||||||  
|Zeitreihen: benutzerdefinierte Kombination von ARTXP- und ARIMA-Methoden|Ja|Ja||||||  
|Zeitreihen: Vorhersage mit neuen Daten|Ja|Ja||||||  
|Unbegrenzte gleichzeitige Data Mining-Abfragen|Ja|Ja||||||  
|Erweiterte Konfigurations & Optimierungs Optionen für Data Mining-Algorithmen|Ja|Ja||||||  
|Unterstützung für Plug-In-Algorithmen|Ja|Ja||||||  
|Parallele Modellverarbeitung|Ja|Ja||||||  
|Zeitreihen: reihenübergreifende Vorhersage|Ja|Ja||||||  
|Unbegrenzte Attribute für Zuordnungsregeln|Ja|Ja||||||  
|Sequenzvorhersage|Ja|Ja||||||  
|Mehrere Vorhersageziele für Naïve BaJa, neuronale Netzwerke und logistische Regression|Ja|Ja||||||  
  
##  <a name="Reporting"></a>Reporting Services  
  
###  <a name="Reporting_features"></a>Reporting Services Features  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Unterstützte [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Edition für Katalogdatenbanken|Standard oder höher|Standard oder höher|Standard oder höher|Web|Express|||  
|Unterstützte [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Edition für Datenquellen|Alle   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Editionen|Alle [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Editionen|Alle [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Editionen|Web|Express|||  
|Berichtsserver|Ja|Ja|Ja|Ja|Ja|||  
|Berichts-Designer|Ja|Ja|Ja|Ja|Ja|||  
|Berichts-Manager|Ja|Ja|Ja|Ja|Ja|||  
|Rollenbasierte Sicherheit|Ja|Ja|Ja|Ja|Ja|||  
|Word-Export und Rich-Text-Unterstützung|Ja|Ja|Ja|Ja|Ja|||  
|Verbesserte Messgeräte und Diagramme|Ja|Ja|Ja|Ja|Ja|||  
|Export in Excel, PDF und Bilder|Ja|Ja|Ja|Ja|Ja|||  
|Benutzerdefinierte Authentifizierung|Ja|Ja|Ja|Ja|Ja|||  
|Berichte als Datenfeeds|Ja|Ja|Ja|Ja|Ja|||  
|Modellunterstützung|Ja|Ja|Ja|Ja||||  
|Erstellen von benutzerdefinierten Rollen für rollenbasierte Sicherheit|Ja|Ja|Ja|||||  
|Modellelementsicherheit|Ja|Ja|Ja|||||  
|Uneingeschränktes Durchklicken|Ja|Ja|Ja|||||  
|Bibliothek freigegebener Komponenten|Ja|Ja|Ja|||||  
|Abonnements und Zeitplanung für E-Mail und Dateifreigabe|Ja|Ja|Ja|||||  
|Berichtsverlauf, Ausführungs-Momentaufnahmen und Zwischenspeichern|Ja|Ja|Ja|||||  
|SharePoint-Integration|Ja|Ja|Ja|||||  
|Unterstützung von Remotedatenquellen und Nicht-SQL-Datenquellen<sup>1</sup>|Ja|Ja|Ja|||||  
|RDCE-Erweiterbarkeit von Datenquellen, Übermittlung und Rendering|Ja|Ja|Ja|||||  
|Datengesteuerte Berichtsabonnements|Ja|Ja||||||  
|Bereitstellung für horizontales Skalieren (Webfarmen)|Ja|Ja||||||  
|Warnungen<sup>2</sup>|Ja|Ja||||||  
|[!INCLUDE[ssCrescent](../includes/sscrescent-md.md)]<sup>2</sup>|Ja|Ja||||||  
  
 <sup>1</sup> Weitere Informationen zu den unterstützten Datenquellen in [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]finden Sie [unter von Reporting Services &#40;SSRS&#41;unterstützte Datenquellen ](../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md).  
  
 <sup>2</sup> Erfordert [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] im SharePoint-Modus. Weitere Informationen finden Sie unter [Reporting Services Installation im SharePoint-Modus &#40;SharePoint 2010 und SharePoint 2013&#41;](../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md).  
  
### <a name="report-server-database-server-edition-requirements"></a>Anforderungen für die Berichtsserver-Datenbankserver-Edition  
 Wenn Sie eine Berichtsserver-Datenbank erstellen, können nicht alle Editionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] zum Hosten der Datenbank verwendet werden. Folgende Tabelle zeigt, welche Editionen von [!INCLUDE[ssDE](../includes/ssde-md.md)] Sie für spezielle Editionen von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]verwenden können.  
  
|Für diese Edition von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Reporting Services|Verwendung dieser Edition der Datenbank-Engine-Instanz als Host für die Datenbank|  
|----------------------------------------------------------------------|---------------------------------------------------------------------------|  
|Enterprise|Standard, Business Intelligence Enterprise (lokal oder remote)|  
|Business Intelligence|Standard, Business Intelligence Enterprise (lokal oder remote)|  
|Standard|Standard, Enterprise Editions (lokal oder remote)|  
|Web|Web Edition (nur lokal)|  
|Express mit Advanced Services|Express mit Advanced Services (nur lokal)|  
|Auswertung|Auswertung|  
  
##  <a name="BIClients"></a>Business Intelligence-Clients  
 Die folgenden Softwareclientanwendungen sind im Microsoft Downloads Center verfügbar und bieten Unterstützung beim Erstellen von Business Intelligence-Dokumenten, die in einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz ausgeführt werden. Wenn Sie diese Dokumente in einer Serverumgebung hosten, verwenden Sie eine Edition von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , die für diesen Dokumenttyp unterstützt wird. In der folgenden Tabelle wird dargestellt, welche [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Editionen die Serverfunktionen zum Hosten der in den Clientanwendungen erstellten Dokumente besitzen.  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[ssRBnoversion](../includes/ssrbnoversion.md)]|Ja|Ja|Ja|||||  
|Data Mining-Add-Ins für Excel und Visio 2010|Ja|Ja|Ja|||||  
|[!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)]2010|Ja|Ja||||||  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]|Ja|Ja||||||  
  
> [!NOTE]
>  1.  [!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)]ist ein Excel-Add-in und hängt [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]nicht von ab. 
  [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)] ist jedoch für die Freigabe und das Zusammenarbeiten mit [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] -Arbeitsmappen in SharePoint erforderlich, und diese Funktion ist als Teil von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise und Business Intelligence-Editionen verfügbar.  
> 2.  In der oben aufgeführten Tabelle sind die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Editionen angegeben, die zur Aktivierung dieser Clienttools erforderlich sind. Über diese Funktionen kann jedoch auf Daten zugegriffen werden, die von beliebigen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Editionen gehostet werden.  
  
##  <a name="Spatial"></a>Räumliche Dienste und Standortdienste  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Räumlichkeitsindizes|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|Planarer und geodätischer Datentyp|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|Erweiterte räumliche Bibliotheken|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|Importieren/Exportieren räumlicher Industriestandard-Datenformate|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
  
##  <a name="Add_DBServices"></a>Zusätzliche Datenbankdienste  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Migration Assistant|Ja|Ja|Ja|Ja|Ja|Ja|Ja|  
|Datenbank-E-Mail|Ja|Ja|Ja|Ja||||  
  
##  <a name="Other_Components"></a>Andere Komponenten  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Data Quality Services|Ja|Ja||||||  
|StreamInsight|StreamInsight Premium-Edition|StreamInsight Standard-Edition|StreamInsight Standard-Edition|StreamInsight Standard-Edition||||  
|StreamInsight HA|StreamInsight Premium-Edition|||||||  
  
## <a name="see-also"></a>Weitere Informationen  
 [Produktspezifikationen für SQL Server 2014](../../2014/getting-started/sql-server-2014-product-specifications.md)   
 [Installation für SQL Server 2014](../database-engine/install-windows/installation-for-sql-server.md)   
 [Schnellstart-Installation von SQL Server 2014](../../2014/getting-started/quick-start-installation-of-sql-server-2014.md)  
  
  
