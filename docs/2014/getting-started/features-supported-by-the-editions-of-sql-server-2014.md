---
title: Funktionen, die von den Editionen von SQLServer 2014 unterstützte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- data-quality-services
- database-engine
- integration-services
- master-data-services
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5da61ff5-12b9-48e6-b3c8-0dacca1751c4
caps.latest.revision: 126
author: mightypen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dac6134987f8a6d3964d919d1aff7688b74da7fe
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37312310"
---
# <a name="features-supported-by-the-editions-of-sql-server-2014"></a>Von den SQL Server 2014-Editionen unterstützte Funktionen
  Dieses Thema bietet detaillierte Informationen zu den von verschiedenen [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]-Versionen unterstützten Funktionen.  
  
> **Hinweis:** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] steht in einer Evaluierungsedition für einen Testzeitraum von 180 Tagen. Weitere Informationen finden Sie unter den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Website für Testsoftware](http://go.microsoft.com/fwlink/?LinkId=190955).  
  
> **Hinweis:** von Evaluation und Developer-Editionen unterstützte Funktionen finden Sie unter den [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise-Funktionssatz.  
  
 Um zur Tabelle für eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Technologie zu navigieren, klicken Sie auf den zugehörigen Link:  
  
 [Cross Skalagrenzen](#CrossBoxScale)  
  
 [High Availability (Hohe Verfügbarkeit)](#High_availability)  
  
 [Skalierbarkeit und Leistung](#Scalability)  
  
 [Security](#Enterprise_security)  
  
 [Replikation](#Replication)  
  
 [Verwaltungstools](#Mgmt_Tools)  
  
 [RDBMS-Verwaltbarkeit](#RDBMS_mgmt)  
  
 [Entwicklungstools](#Dev_tools)  
  
 [Programmierbarkeit](#Programmability)  
  
 [Integration Services](#SSIS)  
  
 [Integration Services – erweiterte Adapter](#SSIS_AA)  
  
 [Integration Services – erweiterte Transformationen](#SSIS_AT)  
  
 [Master Data Services](#MDS)  
  
 [Data Warehouse](#Data_warehouse)  
  
 [Analysis Services](#SSAS)  
  
 [BI-Semantikmodell (mehrdimensional)](#BISemModel_multi)  
  
 [BI-Semantikmodell (tabellarisch)](#BISemModel_tabular)  
  
 [PowerPivot für SharePoint](#PowerPivot)  
  
 [Data Mining](#DataMining)  
  
 [Reporting Services](#Reporting)  
  
 [Business Intelligence-Clients](#BIClients)  
  
 [Räumliche und ortsbezogene Dienste](#Spatial)  
  
 [Weitere Datenbankdienste](#Add_DBServices)  
  
 [Andere Komponenten](#Other_Components)  
  
##  <a name="CrossBoxScale"></a> Feldübergreifende Skalagrenzen  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Maximale von einer einzelnen Instanz verwendete Rechenkapazität ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Datenbank-Engine)<sup>1</sup>|Maximum des Betriebssystems|Beschränkt auf weniger als 4 Sockets oder 16 Kerne|Beschränkt auf weniger als 4 Sockets oder 16 Kerne|Beschränkt auf weniger als 4 Sockets oder 16 Kerne|Beschränkt auf weniger als 1 Socket oder 4 Kerne|Beschränkt auf weniger als 1 Socket oder 4 Kerne|Beschränkt auf weniger als 1 Socket oder 4 Kerne|  
|Maximale Rechenkapazität, die von einer einzelnen Instanz (Analysis Services, Reporting Services) verwendet <sup>1</sup>|Maximum des Betriebssystems|Maximum des Betriebssystems|Beschränkt auf weniger als 4 Sockets oder 16 Kerne|Beschränkt auf weniger als 4 Sockets oder 16 Kerne|Beschränkt auf weniger als 1 Socket oder 4 Kerne|Beschränkt auf weniger als 1 Socket oder 4 Kerne|Beschränkt auf weniger als 1 Socket oder 4 Kerne|  
|Maximaler genutzter Arbeitsspeicher (pro Instanz der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Datenbank-Engine)|Maximum des Betriebssystems|128 GB|128 GB|64 GB|1 GB|1 GB|1 GB|  
|Maximaler genutzter Arbeitsspeicher (pro Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)])|Maximum des Betriebssystems|Maximum des Betriebssystems|64 GB|Nicht zutreffend|–|–|–|  
|Maximaler genutzter Arbeitsspeicher (pro Instanz von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)])|Maximum des Betriebssystems|Maximum des Betriebssystems|64 GB|64 GB|4 GB|–|–|  
|Maximale relationale Datenbankgröße|524 PB|524 PB|524 PB|524 PB|10 GB|10 GB|10 GB|  
  
 <sup>1</sup> Enterprise Edition mit Server + Clientzugriffslizenz (CAL) basierte Lizenzierung (für neue Verträge nicht verfügbar) ist auf maximal 20 Kerne pro beschränkt [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Instanz. Für das auf Prozessorkernen basierende Serverlizenzierungsmodell gelten keine Beschränkungen. Weitere Informationen finden Sie unter [Compute Capacity Limits by Edition of SQL Server](../sql-server/compute-capacity-limits-by-edition-of-sql-server.md).  
  
##  <a name="High_availability"></a> Hohe Verfügbarkeit  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Server Core-Unterstützung<sup>1</sup>|ja|ja|ja|ja|ja|ja|ja|  
|Protokollversand|ja|ja|ja|ja||||  
|Datenbankspiegelung|ja|Ja (nur SAFETY FULL)|Ja (nur SAFETY FULL)|Nur WITNESS|Nur WITNESS|Nur WITNESS|Nur WITNESS|  
|Sicherungskomprimierung|ja|ja|ja|||||  
|Datenbankmomentaufnahme|ja|||||||  
|AlwaysOn-Failoverclusterinstanzen|Ja (Knotenunterstützung: Maximum des Betriebssystems)|Ja (Knotenunterstützung: 2)|Ja (Knotenunterstützung: 2)|||||  
|AlwaysOn-Verfügbarkeitsgruppen|Ja (bis zu 8 sekundäre Replikate, einschließlich 2 synchronen sekundären Replikaten)|||||||  
|Connection Director|ja|||||||  
|Onlineseiten- und Onlinedateiwiederherstellung|ja|||||||  
|Online-Indizierung|ja|||||||  
|Onlineschemaänderung|ja|||||||  
|Schnelle Wiederherstellung|ja|||||||  
|Gespiegelte Sicherungen|ja|||||||  
|Speicherebenen "Hot" Hinzufügen von Speicher und CPU-<sup>2</sup>|ja|||||||  
|Datenbankwiederherstellungsberater|ja|ja|ja|ja|ja|ja|ja|  
|Verschlüsselte Sicherung|ja|ja|ja|||||  
|Intelligente Sicherung|ja|ja|ja|nein||||  
  
 <sup>1</sup>für Weitere Informationen zum Installieren von [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] unter Server Core finden Sie unter [Installieren von SQL Server 2014 unter Server Core](../database-engine/install-windows/install-sql-server-on-server-core.md).  
  
 <sup>2</sup>dieses Feature steht nur für 64-Bit- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
##  <a name="Scalability"></a> Skalierbarkeit und Leistung  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Unterstützung mehrerer Instanzen|50|50|50|50|50|50|50|  
|Tabellen- und Indexpartitionierung|ja|||||||  
|Datenkomprimierung|ja|||||||  
|Ressourcenkontrolle|ja|||||||  
|Partitionstabellenparallelität|ja|||||||  
|Mehrere FILESTREAM-Container|ja|||||||  
|NUMA-basierter Arbeitsspeicher für umfangreiche Seiten und Zuordnung von Pufferarrays|ja|||||||  
|Pufferpoolerweiterung <sup>1</sup>|ja|ja|ja|||||  
|Ressourcenkontrolle für E/A-Vorgänge|ja|||||||  
|In-Memory-OLTP <sup>1</sup>|ja|||||||  
|Verzögerte Dauerhaftigkeit|ja|ja|ja|ja|ja|ja|ja|  
  
 <sup>1</sup> dieses Feature steht nur für 64-Bit- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
##  <a name="Enterprise_security"></a> Sicherheit  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Allgemeine Überwachung|ja|ja|ja|ja|ja|ja|ja|  
|Differenzierte Überwachung|ja|||||||  
|Transparente Datenbankverschlüsselung|ja|||||||  
|Erweiterbare Schlüsselverwaltung|ja|||||||  
|Benutzerdefinierte Rollen|ja|ja|ja|ja|ja|ja|ja|  
|Eigenständige Datenbanken|ja|ja|ja|ja|ja|ja|ja|  
|Verschlüsselung von Sicherungen|ja|ja|ja|||||  
  
##  <a name="Replication"></a> Replication  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] "Änderungen nachverfolgen"|ja|ja|ja|ja|ja|ja|ja|  
|Mergereplikation|ja|ja|ja|Ja (Nur Abonnent)|Ja (Nur Abonnent)|Ja (Nur Abonnent)|Ja (Nur Abonnent)|  
|Transaktionsreplikation|ja|ja|ja|Ja (Nur Abonnent)|Ja (Nur Abonnent)|Ja (Nur Abonnent)|Ja (Nur Abonnent)|  
|Momentaufnahmereplikation|ja|ja|ja|Ja (Nur Abonnent)|Ja (Nur Abonnent)|Ja (Nur Abonnent)|Ja (Nur Abonnent)|  
|Heterogene Abonnenten|ja|ja|ja|||||  
|Veröffentlichungen mit Oracle|ja|||||||  
|Peer-zu-Peer-Transaktionsreplikation|ja|||||||  
  
##  <a name="Mgmt_Tools"></a> Management Tools  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|SQL Management Objects (SMO)|ja|ja|ja|ja|ja|ja|ja|  
|SQL-Konfigurations-Manager|ja|ja|ja|ja|ja|ja|ja|  
|SQL CMD (Command Prompt Tool – Eingabeaufforderungstool)|ja|ja|ja|ja|ja|ja|ja|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Studio|ja|ja|ja|ja|ja|ja||  
|Distributed Replay – Administratortool|ja|ja|ja|ja|ja|ja||  
|Distributed Replay - Client|ja|nein|ja|ja||||  
|Distributed Replay - Controller|Ja (Enterprise unterstützt bis zu 16 Clients, Developer unterstützt nur 1 Client)|nein|Ja (nur 1 Client unterstützt)|Ja (nur 1 Client unterstützt)||||  
|SQL Profiler|ja|ja|ja|Keine<sup>2</sup>|Keine<sup>2</sup>|Keine<sup>2</sup>|Keine<sup>2</sup>|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent|ja|ja|ja|ja||||  
|Microsoft System Center Operations Manager Management Pack|ja|ja|ja|ja||||  
|Datenbankoptimierungsratgeber (DTA)|ja|ja|Ja <sup>3</sup>|Ja <sup>3</sup>||||  
|Assistent zum Bereitstellen einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Datenbank auf einem virtuellen Computer in Windows Azure|ja|ja|ja|ja|ja|ja|ja|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datendateien in Windows Azure|ja|ja|ja|ja|ja|ja|ja|  
  
 <sup>2</sup> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Web [!INCLUDE[ssExpress](../includes/ssexpress-md.md)], [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Tools und [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] mit Advanced Services können mit profiliert werden [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Standard und [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise Edition.  
  
 <sup>3</sup> Optimierung ist nur in Funktionen der Standard Edition aktiviert.  
  
##  <a name="RDBMS_mgmt"></a> RDBMS Manageability  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Benutzerinstanzen|||||ja|ja|ja|  
|LocalDB|||||ja|ja||  
|Dedizierte Administratorverbindung|ja|ja|ja|ja|Ja (unter Ablaufverfolgungsflag)|Ja (unter Ablaufverfolgungsflag)|Ja (unter Ablaufverfolgungsflag)|  
|PowerShell-Skriptunterstützung|ja|ja|ja|ja|ja|ja|ja|  
|SysPrep-Unterstützung<sup>1</sup>|ja|ja|ja|ja|ja|ja|ja|  
|Unterstützung für Komponentenvorgänge der Datenebenenanwendung – Extrahieren, Bereitstellen, Aktualisieren, Löschen|ja|ja|ja|ja|ja|ja|ja|  
|Richtlinienautomatisierung (Überprüfung nach Zeitplan und Änderungen)|ja|ja|ja|ja||||  
|Sammler von Leistungsdaten|ja|ja|ja|ja||||  
|Fähigkeit zur Registrierung als verwaltete Instanz in einer Mehrfachinstanzverwaltung|ja|ja|ja|ja||||  
|Standardleistungsberichte|ja|ja|ja|ja||||  
|Planhinweislisten und Planeinfrierung für Planhinweislisten|ja|ja|ja|ja||||  
|Direkte Abfrage von indizierten Sichten (mittels NOEXPAND-Hinweis)|ja|ja|ja|ja||||  
|Automatische Wartung für indizierte Sichten|ja|ja|ja|ja||||  
|Verteilte partitionierte Sichten|ja|Teilweise. Verteilte partitionierte Sichten sind nicht aktualisierbar|Teilweise. Verteilte partitionierte Sichten sind nicht aktualisierbar|Teilweise. Verteilte partitionierte Sichten sind nicht aktualisierbar|Teilweise. Verteilte partitionierte Sichten sind nicht aktualisierbar|Teilweise. Verteilte partitionierte Sichten sind nicht aktualisierbar|Teilweise. Verteilte partitionierte Sichten sind nicht aktualisierbar|  
|Parallele Indexvorgänge|ja|||||||  
|Automatische Verwendung indizierter Sichten mittels Abfrageoptimierer|ja|||||||  
|Parallele Konsistenzprüfung|ja|||||||  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Steuerungspunkt|ja|||||||  
|Eigenständige Datenbanken|ja|ja|ja|ja|ja|ja|ja|  
|Pufferpoolerweiterung<sup>2</sup>|ja|ja|ja|||||  
  
 <sup>1</sup> Weitere Informationen finden Sie unter [Überlegungen zur Installation von SQL Server mit SysPrep](../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md).  
  
 <sup>2</sup> dieses Feature steht nur für 64-Bit- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
##  <a name="Dev_tools"></a> Development Tools  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Integration in [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio|ja|ja|ja|ja|ja|ja|ja|  
|IntelliSense ([!INCLUDE[tsql](../includes/tsql-md.md)] und MDX)|ja|ja|ja|ja|ja|ja|ja|  
|[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]|ja|ja|ja|ja|ja|||  
|SQL-bearbeiten und-Entwurfstools<sup>1</sup>|ja|ja|ja|||||  
|Unterstützung für Versionskontrolle<sup>1</sup>|ja|ja|ja|||||  
|MDX-bearbeitungs-, Debuggen und Entwurfstools<sup>1</sup>|ja|ja|ja|||||  
  
 <sup>1</sup> dieses Feature ist nicht für 64-Bit-Version von Standard Edition verfügbar.  
  
##  <a name="Programmability"></a> Programmability  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Common Language Runtime (CLR)-Integration|ja|ja|ja|ja|ja|ja|ja|  
|Systemeigene XML-Unterstützung|ja|ja|ja|ja|ja|ja|ja|  
|XML-Indizierung|ja|ja|ja|ja|ja|ja|ja|  
|MERGE & UPSERT-Funktionen|ja|ja|ja|ja|ja|ja|ja|  
|FILESTREAM-Unterstützung|ja|ja|ja|ja|ja|ja|ja|  
|FileTable|ja|ja|ja|ja|ja|ja|ja|  
|Datums- und Uhrzeitdatentypen|ja|ja|ja|ja|ja|ja|ja|  
|Internationalisierungsunterstützung|ja|ja|ja|ja|ja|ja|ja|  
|Volltextsuche und semantische Suche|ja|ja|ja|ja|ja|||  
|Angabe der Sprache in einer Abfrage|ja|ja|ja|ja|ja|||  
|Service Broker (Messaging)|ja|ja|ja|Nein (nur Client)|Nein (nur Client)|Nein (nur Client)|Nein (nur Client)|  
|[!INCLUDE[tsql](../includes/tsql-md.md)]-Endpunkte|ja|ja|ja|ja||||  
  
##  <a name="SSIS"></a> Integration Services  
  
|Funktion|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|-------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Import/Export-Assistent|ja|ja|ja|ja|ja|ja|ja|  
|Integrierte Datenquellenkonnektoren|ja|ja|ja|ja|ja|ja|ja|  
|SSIS-Designer und Laufzeit|ja|ja|ja|||||  
|Grundlegende Transformationen|ja|ja|ja|||||  
|Grundlegende Datenprofilerstellungs-Tools|ja|ja|ja|||||  
|Change Data Capture Service für Oracle von Attunity|ja|||||||  
|Change Data Capture Designer für Oracle von Attunity|ja|||||||  
  
###  <a name="SSIS_AA"></a> Integration Services – Erweiterte Adapter  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|High-Performance-Oracle-Ziel|ja|||||||  
|High-Performance-Teradata-Ziel|ja|||||||  
|SAP BW-Quelle und -Ziel|ja|||||||  
|Zieladapter des Data Mining-Modelltrainings|ja|||||||  
|Zieladapter für Dimensionsverarbeitung|ja|||||||  
|Zieladapter für Partitionsverarbeitung|ja|||||||  
|Change Data Capture-Komponenten von Attunity|ja|||||||  
|Konnektor für Open Database Connectivity (ODBC) von Attunity|ja|||||||  
  
###  <a name="SSIS_AT"></a> Integration Services – Erweiterte Transformationen  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Persistente Suchen (hohe Leistungsfähigkeit)|ja|||||||  
|Transformation für Data Mining-Abfragen|ja|||||||  
|Transformationen für Fuzzygruppierung und -suche|ja|||||||  
|Transformationen für Ausdrucksextrahierung und -suche|ja|||||||  
  
##  <a name="MDS"></a> Master Data Services  
  
> [!NOTE]  
>  -   [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] ist nur in den 64-Bit-Editionen von Business Intelligence und Enterprise verfügbar.  
  
|Funktion|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|-------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]-Datenbank|ja|ja||||||  
|[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]-Webanwendung|ja|ja||||||  
  
##  <a name="Data_warehouse"></a> Data Warehouse  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Erstellen von Cubes ohne Datenbank|ja|ja|ja|||||  
|Automatisches Generieren von Staging- und Data Warehouse-Schemas|ja|ja|ja|||||  
|Change Data Capture|ja|||||||  
|Optimierung von Sternjoin-Abfragen|ja|||||||  
|Skalierbare schreibgeschützte Analysis Services-Konfiguration|ja|||||||  
|Parallele Abfrageverarbeitung bei partitionierten Tabellen und Indizes|ja|||||||  
|Speicheroptimierte xVelocity-columnstore-Indizes|ja|||||||  
|Globale Batchaggregation|ja|||||||  
  
##  <a name="SSAS"></a> Analysis Services  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Skalierbare freigegebene Datenbanken (Anfügen/Trennen, schreibgeschützte Datenbanken)|ja|ja||||||  
|Sichern/Wiederherstellen, Anfügen/Trennen von Datenbanken|ja|ja|ja|||||  
|Synchronisieren von Datenbanken|ja|ja||||||  
|Hohe Verfügbarkeit|ja|ja|ja|||||  
|Programmierbarkeit (AMO, ADOMD.NET, OLEDB, XML/A, ASSL)|ja|ja|ja|||||  
  
###  <a name="BISemModel_multi"></a> BI-Semantikmodell (mehrdimensional)  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Semiadditive Measures|ja|ja|Keine<sup>1</sup>|||||  
|Hierarchien|ja|ja|ja|||||  
|KPIs (Key Performance Indicators)|ja|ja|ja|||||  
|Perspektiven|ja|ja||||||  
|Aktionen|ja|ja|ja|||||  
|Kontointelligenz|ja|ja|ja|||||  
|Zeitintelligenz|ja|ja|ja|||||  
|Benutzerdefinierte Rollups|ja|ja|ja|||||  
|Cube-Rückschreiben|ja|ja|ja|||||  
|Rückschreiben von Dimensionen|ja|ja||||||  
|Rückschreibezellen|ja|ja|ja|||||  
|Drillthrough ausführen|ja|ja|ja|||||  
|Erweiterte Hierarchietypen (über- und untergeordnet, unregelmäßige Hierarchien)|ja|ja|ja|||||  
|Erweiterte Dimensionen (Bezugsdimensionen, m:n-Dimensionen)|ja|ja|ja|||||  
|Verknüpfte Measures und Dimensionen|ja|ja||||||  
|Translations|ja|ja|ja|||||  
|Aggregations|ja|ja|ja|||||  
|Mehrere Partitionen|ja|ja|Ja, bis zu 3|||||  
|Proaktives Zwischenspeichern|ja|ja||||||  
|Benutzerdefinierte Assemblys (gespeicherte Prozeduren)|ja|ja|ja|||||  
|MDX-Abfragen und Skripts|ja|ja|ja|||||  
|DAX-Abfragen|ja|ja||||||  
|Rollenbasiertes Sicherheitsmodell|ja|ja|ja|||||  
|Sicherheit auf Dimensions- und Zellenebene|ja|ja|ja|||||  
|Skalierbarer Zeichenfolgenspeicher|ja|ja|ja|||||  
|MOLAP-, ROLAP-, HOLAP-Speichermodi|ja|ja|ja|||||  
|Binärer und komprimierter XML-Transport|ja|ja|ja|||||  
|Pushmodus-Verarbeitung|ja|ja||||||  
|Direktes Rückschreiben|ja|ja||||||  
|Measureausdrücke|ja|ja||||||  
  
 <sup>1</sup>Semiadditives der LastChild-Measure wird in der standard Edition unterstützt, aber andere semiadditive Measures, z. B. None, FirstChild, FirstNonEmpty, LastNonEmpty, AverageOfChildren und ByAccount, nicht sind. Additive Measures, z. B. Sum, Count, Min, Max und nicht additive Measures (DistinctCount) werden in allen Editionen unterstützt.  
  
###  <a name="BISemModel_tabular"></a> BI Semantic Model (Tabular)  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Hierarchien|ja|ja||||||  
|KPIs (Key Performance Indicators)|ja|ja||||||  
|Perspektiven|ja|ja||||||  
|Translations|ja|ja||||||  
|DAX-Berechnungen, DAX-Abfragen, MDX-Abfragen|ja|ja||||||  
|Sicherheit auf Zeilenebene|ja|ja||||||  
|Partitionen|ja|ja||||||  
|Arbeitsspeicherinterne und DirectQuery-Speichermodi (nur tabellarisch)|ja|ja||||||  
  
###  <a name="PowerPivot"></a> PowerPivot für SharePoint  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|SharePoint-Farmintegration auf Grundlage der Shared Services-Architektur|ja|ja||||||  
|Verwendungsberichte|ja|ja||||||  
|Systemüberwachungsregeln|ja|ja||||||  
|PowerPivot-Katalog|ja|ja||||||  
|PowerPivot-Datenaktualisierung|ja|ja||||||  
|PowerPivot-Datenfeeds|ja|ja||||||  
  
###  <a name="DataMining"></a> Data Mining  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Standardalgorithmen|ja|ja|ja|||||  
|Data Mining-Tools (Assistenten, Editoren, Abfrage-Generatoren)|ja|ja|ja|||||  
|Übergreifende Überprüfung|ja|ja||||||  
|Modelle für gefilterte Teilmengen von Daten der Miningstruktur|ja|ja||||||  
|Zeitreihen: benutzerdefinierte Kombination von ARTXP- und ARIMA-Methoden|ja|ja||||||  
|Zeitreihen: Vorhersage mit neuen Daten|ja|ja||||||  
|Unbegrenzte gleichzeitige Data Mining-Abfragen|ja|ja||||||  
|Erweiterte Konfigurations- & Optimierungsoptionen für Data Mining-Algorithmen|ja|ja||||||  
|Unterstützung für Plug-In-Algorithmen|ja|ja||||||  
|Parallele Modellverarbeitung|ja|ja||||||  
|Zeitreihen: reihenübergreifende Vorhersage|ja|ja||||||  
|Unbegrenzte Attribute für Zuordnungsregeln|ja|ja||||||  
|Sequenzvorhersage|ja|ja||||||  
|Mehrere Vorhersageziele für Naïve BaJa, neuronale Netzwerke und logistische Regression|ja|ja||||||  
  
##  <a name="Reporting"></a> Reporting Services  
  
###  <a name="Reporting_features"></a> Reporting Services-Funktionen  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Unterstützte [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Edition für Katalogdatenbanken|Standard oder höher|Standard oder höher|Standard oder höher|Web|Express|||  
|Unterstützte [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Edition für Datenquellen|Alle   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Editionen|Alle [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Editionen|Alle [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Editionen|Web|Express|||  
|Berichtsserver|ja|ja|ja|ja|ja|||  
|Berichts-Designer|ja|ja|ja|ja|ja|||  
|Berichts-Manager|ja|ja|ja|ja|ja|||  
|Rollenbasierte Sicherheit|ja|ja|ja|ja|ja|||  
|Word-Export und Rich-Text-Unterstützung|ja|ja|ja|ja|ja|||  
|Verbesserte Messgeräte und Diagramme|ja|ja|ja|ja|ja|||  
|Export in Excel, PDF und Bilder|ja|ja|ja|ja|ja|||  
|Benutzerdefinierte Authentifizierung|ja|ja|ja|ja|ja|||  
|Berichte als Datenfeeds|ja|ja|ja|ja|ja|||  
|Modellunterstützung|ja|ja|ja|ja||||  
|Erstellen von benutzerdefinierten Rollen für rollenbasierte Sicherheit|ja|ja|ja|||||  
|Modellelementsicherheit|ja|ja|ja|||||  
|Uneingeschränktes Durchklicken|ja|ja|ja|||||  
|Bibliothek freigegebener Komponenten|ja|ja|ja|||||  
|Abonnements und Zeitplanung für E-Mail und Dateifreigabe|ja|ja|ja|||||  
|Berichtsverlauf, Ausführungs-Momentaufnahmen und Zwischenspeichern|ja|ja|ja|||||  
|SharePoint-Integration|ja|ja|ja|||||  
|Unterstützung von Remotedatenquellen und Nicht-SQL-Datenquellen<sup>1</sup>|ja|ja|ja|||||  
|RDCE-Erweiterbarkeit von Datenquellen, Übermittlung und Rendering|ja|ja|ja|||||  
|Datengesteuerte Berichtsabonnements|ja|ja||||||  
|Bereitstellung für horizontales Skalieren (Webfarmen)|ja|ja||||||  
|Warnungen<sup>2</sup>|ja|ja||||||  
|[!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] <sup>2</sup>|ja|ja||||||  
  
 <sup>1</sup>für Weitere Informationen zu den unterstützten Datenquellen in [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)], finden Sie unter [von Reporting Services unterstützte Datenquellen &#40;SSRS&#41;](../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md).  
  
 <sup>2</sup>erfordert [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] im SharePoint-Modus. Weitere Informationen finden Sie unter [Reporting Services SharePoint-Modus-Installation &#40;SharePoint 2010 und SharePoint 2013&#41;](../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md).  
  
### <a name="report-server-database-server-edition-requirements"></a>Anforderungen für die Berichtsserver-Datenbankserver-Edition  
 Wenn Sie eine Berichtsserver-Datenbank erstellen, können nicht alle Editionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] zum Hosten der Datenbank verwendet werden. Folgende Tabelle zeigt, welche Editionen von [!INCLUDE[ssDE](../includes/ssde-md.md)] Sie für spezielle Editionen von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]verwenden können.  
  
|Für diese Edition von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Reporting Services|Verwendung dieser Edition der Datenbank-Engine-Instanz als Host für die Datenbank|  
|----------------------------------------------------------------------|---------------------------------------------------------------------------|  
|Enterprise|Standard, Business Intelligence Enterprise (lokal oder remote)|  
|Business Intelligence|Standard, Business Intelligence Enterprise (lokal oder remote)|  
|Standard|Standard, Enterprise Editions (lokal oder remote)|  
|Web|Web Edition (nur lokal)|  
|Express mit Advanced Services|Express mit Advanced Services (nur lokal)|  
|Evaluation|Evaluation|  
  
##  <a name="BIClients"></a> Business Intelligence-Clients  
 Die folgenden softwareclientanwendungen sind im Microsoft Downloads Center verfügbar und werden bereitgestellt, um unterstützt Sie beim Erstellen von Business Intelligence-Dokumenten, die ausgeführt werden, auf eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Instanz. Wenn Sie diese Dokumente in einer serverumgebung hosten, verwenden Sie eine Edition von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , die für diesen Dokumenttyp unterstützt wird. In der folgenden Tabelle wird dargestellt, welche [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Editionen die Serverfunktionen zum Hosten der in den Clientanwendungen erstellten Dokumente besitzen.  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[ssRBnoversion](../includes/ssrbnoversion-md.md)]|ja|ja|ja|||||  
|Data Mining-Add-Ins für Excel und Visio 2010|ja|ja|ja|||||  
|[!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] 2010|ja|ja||||||  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]|ja|ja||||||  
  
> [!NOTE]  
>  1.  [!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] ist eine Excel-Add-in und hängt nicht [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)] ist jedoch für die Freigabe und das Zusammenarbeiten mit [!INCLUDE[ssGemini](../includes/ssgemini-md.md)]-Arbeitsmappen in SharePoint erforderlich, und diese Funktion ist als Teil von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise und Business Intelligence-Editionen verfügbar.  
> 2.  Die oben aufgeführten Tabelle sind die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Editionen, die zur Aktivierung dieser Clienttools erforderlich sind, jedoch diese Features Daten, die auf eine beliebige Edition von gehosteten zugreifen können [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
##  <a name="Spatial"></a> Spatial and Location Services  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Räumlichkeitsindizes|ja|ja|ja|ja|ja|ja|ja|  
|Planarer und geodätischer Datentyp|ja|ja|ja|ja|ja|ja|ja|  
|Erweiterte räumliche Bibliotheken|ja|ja|ja|ja|ja|ja|ja|  
|Importieren/Exportieren räumlicher Industriestandard-Datenformate|ja|ja|ja|ja|ja|ja|ja|  
  
##  <a name="Add_DBServices"></a> Additional Database Services  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Migration Assistant|ja|ja|ja|ja|ja|ja|ja|  
|Datenbank-E-Mail|ja|ja|ja|ja||||  
  
##  <a name="Other_Components"></a> Andere Komponenten  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Data Quality Services|ja|ja||||||  
|StreamInsight|StreamInsight Premium-Edition|StreamInsight Standard-Edition|StreamInsight Standard-Edition|StreamInsight Standard-Edition||||  
|StreamInsight HA|StreamInsight Premium-Edition|||||||  
  
## <a name="see-also"></a>Siehe auch  
 [Produktspezifikationen für SQLServer 2014](../../2014/getting-started/sql-server-2014-product-specifications.md)   
 [Installation für SQLServer 2014](../database-engine/install-windows/installation-for-sql-server.md)   
 [Schnellstart-Installation von SQL Server 2014](../../2014/getting-started/quick-start-installation-of-sql-server-2014.md)  
  
  
