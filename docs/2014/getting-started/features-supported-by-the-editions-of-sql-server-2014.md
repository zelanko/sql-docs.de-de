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
ms.sourcegitcommit: 3b1f873f02af8f4e89facc7b25f8993f535061c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2019
ms.locfileid: "70176123"
---
# <a name="features-supported-by-the-editions-of-sql-server-2014"></a>Von den Editionen von SQLServer 2014 unterstützte Funktionen


  Dieses Thema bietet detaillierte Informationen zu den von verschiedenen [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]-Versionen unterstützten Funktionen. 

 > **Hinweis:** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ist in einer Evaluierungsversion für einen Testzeitraum von 180 Tagen verfügbar. Weitere Informationen finden Sie auf der Website zur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]- [Test Software](https://go.microsoft.com/fwlink/?LinkId=190955).  
> 
> **Hinweis:** Informationen zu Funktionen, die von Evaluation und Developer Edition unterstützt werden, finden Sie unter [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise Feature Set  
  
 Um zur Tabelle für eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Technologie zu navigieren, klicken Sie auf den zugehörigen Link:  
  
 [Feld übergreifende Skalierungs Grenzwerte](#CrossBoxScale)  
  
 [High Availability (Hohe Verfügbarkeit)](#High_availability)  
  
 [Skalierbarkeit und Leistung](#Scalability)  
  
 [Sicherheit](#Enterprise_security)  
  
 [Replikation](#Replication)  
  
 [Verwaltungs Tools](#Mgmt_Tools)  
  
 [RDBMS-Verwaltbarkeit](#RDBMS_mgmt)  
  
 [Entwicklungstools](#Dev_tools)  
  
 [Programmierbarkeit](#Programmability)  
  
 [Integration Services](#SSIS)  
  
 [Integration Services erweiterte Adapter](#SSIS_AA)  
  
 [Erweiterte Transformationen Integration Services](#SSIS_AT)  
  
 [Master Data Services](#MDS)  
  
 [Data Warehouse](#Data_warehouse)  
  
 [Analysis Services](#SSAS)  
  
 [BI-Semantik Modell (mehrdimensional)](#BISemModel_multi)  
  
 [BI-Semantikmodell (tabellarisch)](#BISemModel_tabular)  
  
 [PowerPivot für SharePoint](#PowerPivot)  
  
 [Data Mining](#DataMining)  
  
 [Reporting Services](#Reporting)  
  
 [Business Intelligence-Clients](#BIClients)  
  
 [Räumliche Dienste und Standortdienste](#Spatial)  
  
 [Zusätzliche Datenbankdienste](#Add_DBServices)  
  
 [Andere Komponenten](#Other_Components)  
  
##  <a name="CrossBoxScale"></a> Feldübergreifende Skalagrenzen  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Maximale von einer einzelnen Instanz verwendete Rechenkapazität ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Datenbank-Engine)<sup>1</sup>|Maximum des Betriebssystems|Beschränkt auf weniger als 4 Sockets oder 16 Kerne|Beschränkt auf weniger als 4 Sockets oder 16 Kerne|Beschränkt auf weniger als 4 Sockets oder 16 Kerne|Beschränkt auf weniger als 1 Socket oder 4 Kerne|Beschränkt auf weniger als 1 Socket oder 4 Kerne|Beschränkt auf weniger als 1 Socket oder 4 Kerne|  
|Maximale von einer einzelnen Instanz verwendete Rechenkapazität (Analysis Services Reporting Services) <sup>1</sup>|Maximum des Betriebssystems|Maximum des Betriebssystems|Beschränkt auf weniger als 4 Sockets oder 16 Kerne|Beschränkt auf weniger als 4 Sockets oder 16 Kerne|Beschränkt auf weniger als 1 Socket oder 4 Kerne|Beschränkt auf weniger als 1 Socket oder 4 Kerne|Beschränkt auf weniger als 1 Socket oder 4 Kerne|  
|Maximaler genutzter Arbeitsspeicher (pro Instanz der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Datenbank-Engine)|Maximum des Betriebssystems|128 GB|128 GB|64 GB|1 GB|1 GB|1 GB|  
|Maximaler genutzter Arbeitsspeicher (pro Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)])|Maximum des Betriebssystems|Maximum des Betriebssystems|64 GB|–|–|–|–|  
|Maximaler genutzter Arbeitsspeicher (pro Instanz von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)])|Maximum des Betriebssystems|Maximum des Betriebssystems|64 GB|64 GB|4 GB|–|–|  
|Maximale relationale Datenbankgröße|524 PB|524 PB|524 PB|524 PB|10 GB|10 GB|10 GB|  
  
 <sup>1</sup> die Enterprise Edition mit einer Lizenzierung auf Grundlage von Server Lizenz + Client Zugriffslizenz (CAL) (für neue Verträge nicht verfügbar) ist auf maximal 20 Kerne pro [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanz beschränkt. Für das core-basierte Serverlizenzierungsmodell gelten keine Beschränkungen. Weitere Informationen finden Sie unter [Compute Capacity Limits by Edition of SQL Server](../sql-server/compute-capacity-limits-by-edition-of-sql-server.md).  
  
##  <a name="High_availability"></a> Hochverfügbarkeit  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Server Core-Unterstützung<sup>1</sup>|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|Protokollversand|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung||||  
|Datenbankspiegelung|Benutzerkontensteuerung|Ja (nur SAFETY FULL)|Ja (nur SAFETY FULL)|Nur WITNESS|Nur WITNESS|Nur WITNESS|Nur WITNESS|  
|Sicherungskomprimierung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Datenbankmomentaufnahme|Benutzerkontensteuerung|||||||  
|AlwaysOn-Failoverclusterinstanzen|Ja (Knotenunterstützung: Maximum des Betriebssystems)|Ja (Knotenunterstützung: 2)|Ja (Knotenunterstützung: 2)|||||  
|AlwaysOn-Verfügbarkeitsgruppen|Ja (bis zu 8 sekundäre Replikate, einschließlich 2 synchronen sekundären Replikaten)|||||||  
|Connection Director|Benutzerkontensteuerung|||||||  
|Onlineseiten- und Onlinedateiwiederherstellung|Benutzerkontensteuerung|||||||  
|Online-Indizierung|Benutzerkontensteuerung|||||||  
|Onlineschemaänderung|Benutzerkontensteuerung|||||||  
|Schnelle Wiederherstellung|Benutzerkontensteuerung|||||||  
|Gespiegelte Sicherungen|Benutzerkontensteuerung|||||||  
|Arbeitsspeicher<sup>und CPU-</sup> Auslastung (Hot)|Benutzerkontensteuerung|||||||  
|Datenbankwiederherstellungsberater|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|Verschlüsselte Sicherung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Intelligente Sicherung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Nein||||  
  
 <sup>1</sup> Weitere Informationen zum Installieren von [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] auf Server Core finden Sie unter [Installieren von SQL Server 2014 unter Server Core](../database-engine/install-windows/install-sql-server-on-server-core.md).  
  
 <sup>2</sup> Diese Funktion ist nur für 64-Bit-[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]verfügbar.  
  
##  <a name="Scalability"></a>Skalierbarkeit und Leistung  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Unterstützung mehrerer Instanzen|50|50|50|50|50|50|50|  
|Tabellen- und Indexpartitionierung|Benutzerkontensteuerung|||||||  
|Datenkomprimierung|Benutzerkontensteuerung|||||||  
|Ressourcenkontrolle|Benutzerkontensteuerung|||||||  
|Partitionstabellenparallelität|Benutzerkontensteuerung|||||||  
|Mehrere FILESTREAM-Container|Benutzerkontensteuerung|||||||  
|NUMA-basierter Arbeitsspeicher für umfangreiche Seiten und Zuordnung von Pufferarrays|Benutzerkontensteuerung|||||||  
|Puffer Pool Erweiterung <sup>1</sup>|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Ressourcenkontrolle für E/A-Vorgänge|Benutzerkontensteuerung|||||||  
|In-Memory-OLTP <sup>1</sup>|Benutzerkontensteuerung|||||||  
|Verzögerte Dauerhaftigkeit|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
  
 <sup>1</sup> diese Funktion ist nur für 64-Bit-[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]verfügbar.  
  
##  <a name="Enterprise_security"></a> Security  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Allgemeine Überwachung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|Differenzierte Überwachung|Benutzerkontensteuerung|||||||  
|Transparente Datenbankverschlüsselung|Benutzerkontensteuerung|||||||  
|Erweiterbare Schlüsselverwaltung|Benutzerkontensteuerung|||||||  
|Benutzerdefinierte Rollen|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|Contained Databases|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|Verschlüsselung von Sicherungen|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
  
##  <a name="Replication"></a> Replikation  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Änderungsnachverfolgung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|Mergereplikation|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Ja (Nur Abonnent)|Ja (Nur Abonnent)|Ja (Nur Abonnent)|Ja (Nur Abonnent)|  
|Transaktionsreplikation|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Ja (Nur Abonnent)|Ja (Nur Abonnent)|Ja (Nur Abonnent)|Ja (Nur Abonnent)|  
|Momentaufnahmereplikation|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Ja (Nur Abonnent)|Ja (Nur Abonnent)|Ja (Nur Abonnent)|Ja (Nur Abonnent)|  
|Heterogene Abonnenten|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Veröffentlichungen mit Oracle|Benutzerkontensteuerung|||||||  
|Peer-zu-Peer-Transaktionsreplikation|Benutzerkontensteuerung|||||||  
  
##  <a name="Mgmt_Tools"></a> Verwaltungstools  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|SQL Management Objects (SMO)|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|SQL-Konfigurations-Manager|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|SQL CMD (Command Prompt Tool – Eingabeaufforderungstool)|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Management Studio|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung||  
|Distributed Replay: Administratortool|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung||  
|Distributed Replay - Client|Benutzerkontensteuerung|Nein|Benutzerkontensteuerung|Benutzerkontensteuerung||||  
|Distributed Replay - Controller|Ja (Enterprise unterstützt bis zu 16 Clients, Developer unterstützt nur 1 Client)|Nein|Ja (nur 1 Client unterstützt)|Ja (nur 1 Client unterstützt)||||  
|SQL Profiler|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Nein<sup>2</sup>|Nein<sup>2</sup>|Nein<sup>2</sup>|Nein<sup>2</sup>|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Agent|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung||||  
|Microsoft System Center Operations Manager Management Pack|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung||||  
|Datenbankoptimierungsratgeber (DTA)|Benutzerkontensteuerung|Benutzerkontensteuerung|Ja <sup>3</sup>|Ja <sup>3</sup>||||  
|Bereitstellen einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Datenbank für einen Azure-VM-Assistenten|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] von Datendateien in Azure|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
  
 <sup>2</sup> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Web-, [!INCLUDE[ssExpress](../includes/ssexpress-md.md)]-, [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Tools-und [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services können mit [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Standard und [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise Edition profiliert werden.  
  
 <sup>3</sup> Optimierung ist nur in Funktionen der Standard Edition aktiviert.  
  
##  <a name="RDBMS_mgmt"></a> RDBMS Manageability  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Benutzerinstanzen|||||Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|LocalDB|||||Benutzerkontensteuerung|Benutzerkontensteuerung||  
|Dedizierte Administratorverbindung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Ja (unter Ablaufverfolgungsflag)|Ja (unter Ablaufverfolgungsflag)|Ja (unter Ablaufverfolgungsflag)|  
|PowerShell-Skriptunterstützung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|Sy-p-Unterstützung<sup>1</sup>|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|Unterstützung für Komponenten Vorgänge der Datenebenenanwendung-extrahieren, bereitstellen, aktualisieren, löschen|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|Richtlinienautomatisierung (Überprüfung nach Zeitplan und Änderungen)|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung||||  
|Sammler von Leistungsdaten|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung||||  
|Fähigkeit zur Registrierung als verwaltete Instanz in einer Mehrfachinstanzverwaltung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung||||  
|Standardleistungsberichte|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung||||  
|Planhinweislisten und Planeinfrierung für Planhinweislisten|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung||||  
|Direkte Abfrage von indizierten Sichten (mittels NOEXPAND-Hinweis)|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung||||  
|Automatische Wartung für indizierte Sichten|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung||||  
|Verteilte partitionierte Sichten|Benutzerkontensteuerung|Teilweise. Verteilte partitionierte Sichten sind nicht aktualisierbar|Teilweise. Verteilte partitionierte Sichten sind nicht aktualisierbar|Teilweise. Verteilte partitionierte Sichten sind nicht aktualisierbar|Teilweise. Verteilte partitionierte Sichten sind nicht aktualisierbar|Teilweise. Verteilte partitionierte Sichten sind nicht aktualisierbar|Teilweise. Verteilte partitionierte Sichten sind nicht aktualisierbar|  
|Parallele Indexvorgänge|Benutzerkontensteuerung|||||||  
|Automatische Verwendung indizierter Sichten mittels Abfrageoptimierer|Benutzerkontensteuerung|||||||  
|Parallele Konsistenzprüfung|Benutzerkontensteuerung|||||||  
|Steuerungspunkt für das [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Hilfsprogramm|Benutzerkontensteuerung|||||||  
|Contained Databases|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|Puffer Pool Erweiterung<sup>2</sup>|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
  
 <sup>1</sup> Weitere Informationen finden Sie unter [Überlegungen zur Installation von SQL Server mit SysPrep](../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md).  
  
 <sup>2</sup> diese Funktion ist nur für 64-Bit-[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]verfügbar.  
  
##  <a name="Dev_tools"></a> Development Tools  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Integration in [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|IntelliSense ([!INCLUDE[tsql](../includes/tsql-md.md)] und MDX)|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||  
|SQL-Abfrage Bearbeitungs-und-Entwurfs Tools<sup>1</sup>|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Versions kontrollunterstützung<sup>1</sup>|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|MDX-Bearbeitungs-, Debug-und Entwurfs Tools<sup>1</sup>|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
  
 <sup>1</sup> diese Funktion ist für die 64-Bit-Version der Standard Edition nicht verfügbar.  
  
##  <a name="Programmability"></a> Programmierbarkeit  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Common Language Runtime (CLR)-Integration|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|Systemeigene XML-Unterstützung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|XML-Indizierung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|Merge & Upsert-Funktionen|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|FILESTREAM-Unterstützung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|FileTable|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|Datums- und Uhrzeitdatentypen|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|Internationalisierungsunterstützung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|Volltextsuche und semantische Suche|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||  
|Angabe der Sprache in einer Abfrage|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||  
|Service Broker (Messaging)|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Nein (nur Client)|Nein (nur Client)|Nein (nur Client)|Nein (nur Client)|  
|[!INCLUDE[tsql](../includes/tsql-md.md)]-Endpunkte|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung||||  
  
##  <a name="SSIS"></a> Integration Services  
  
|Funktion|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|-------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Import/Export-Assistent|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|Integrierte Datenquellenkonnektoren|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|SSIS-Designer und Laufzeit|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Grundlegende Transformationen|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Grundlegende Datenprofilerstellungs-Tools|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Change Data Capture Service für Oracle von Attunity|Benutzerkontensteuerung|||||||  
|Change Data Capture Designer für Oracle von Attunity|Benutzerkontensteuerung|||||||  
  
###  <a name="SSIS_AA"></a> Integration Services – Erweiterte Adapter  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|High-Performance-Oracle-Ziel|Benutzerkontensteuerung|||||||  
|High-Performance-Teradata-Ziel|Benutzerkontensteuerung|||||||  
|SAP BW-Quelle und -Ziel|Benutzerkontensteuerung|||||||  
|Zieladapter des Data Mining-Modelltrainings|Benutzerkontensteuerung|||||||  
|Zieladapter für Dimensionsverarbeitung|Benutzerkontensteuerung|||||||  
|Zieladapter für Partitionsverarbeitung|Benutzerkontensteuerung|||||||  
|Change Data Capture-Komponenten von Attunity|Benutzerkontensteuerung|||||||  
|Konnektor für Open Database Connectivity (ODBC) von Attunity|Benutzerkontensteuerung|||||||  
  
###  <a name="SSIS_AT"></a> Integration Services – Erweiterte Transformationen  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Persistente Suchen (hohe Leistungsfähigkeit)|Benutzerkontensteuerung|||||||  
|Transformation für Data Mining-Abfragen|Benutzerkontensteuerung|||||||  
|Transformationen für Fuzzygruppierung und -suche|Benutzerkontensteuerung|||||||  
|Transformationen für Ausdrucksextrahierung und -suche|Benutzerkontensteuerung|||||||  
  
##  <a name="MDS"></a> Master Data Services  
  
> [!NOTE]  
>  -   [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] ist nur in den 64-Bit-Editionen von Business Intelligence and Enterprise verfügbar.  
  
|Funktion|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|-------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] -Datenbank|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]-Webanwendung|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
  
##  <a name="Data_warehouse"></a> Data Warehouse  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Erstellen von Cubes ohne Datenbank|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Automatisches Generieren von Staging- und Data Warehouse-Schemas|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Change Data Capture|Benutzerkontensteuerung|||||||  
|Optimierung von Sternjoin-Abfragen|Benutzerkontensteuerung|||||||  
|Skalierbare schreibgeschützte Analysis Services-Konfiguration|Benutzerkontensteuerung|||||||  
|Parallele Abfrageverarbeitung bei partitionierten Tabellen und Indizes|Benutzerkontensteuerung|||||||  
|Speicheroptimierte xVelocity-columnstore-Indizes|Benutzerkontensteuerung|||||||  
|Globale Batchaggregation|Benutzerkontensteuerung|||||||  
  
##  <a name="SSAS"></a> Analysis Services  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Skalierbare freigegebene Datenbanken (Anfügen/Trennen, schreibgeschützte Datenbanken)|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|Sichern/Wiederherstellen, Anfügen/Trennen von Datenbanken|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Synchronisieren von Datenbanken|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|Hohe Verfügbarkeit|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Programmierbarkeit (AMO, ADOMD.NET, OLEDB, XML/A, ASSL)|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
  
###  <a name="BISemModel_multi"></a>BI-Semantik Modell (mehrdimensional)  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Semiadditive Measures|Benutzerkontensteuerung|Benutzerkontensteuerung|Nein<sup>1</sup>|||||  
|Hierarchien|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|KPIs|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Perspektiven|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|Aktionen|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Kontointelligenz|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Zeitintelligenz|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Benutzerdefinierte Rollups|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Cube-Rückschreiben|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Rückschreiben von Dimensionen|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|Rückschreibezellen|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Drillthroughberichte|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Erweiterte Hierarchietypen (über- und untergeordnet, unregelmäßige Hierarchien)|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Erweiterte Dimensionen (Bezugsdimensionen, m:n-Dimensionen)|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Verknüpfte Measures und Dimensionen|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|Translations|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Aggregationen|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Mehrere Partitionen|Benutzerkontensteuerung|Benutzerkontensteuerung|Ja, bis zu 3|||||  
|Proaktives Zwischenspeichern|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|Benutzerdefinierte Assemblys (gespeicherte Prozeduren)|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|MDX-Abfragen und Skripts|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|DAX-Abfragen|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|Rollenbasiertes Sicherheitsmodell|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Sicherheit auf Dimensions- und Zellenebene|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Skalierbarer Zeichenfolgenspeicher|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|MOLAP-, ROLAP-, HOLAP-Speichermodi|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Binärer und komprimierter XML-Transport|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Pushmodus-Verarbeitung|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|Direktes Rückschreiben|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|Measureausdrücke|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
  
 <sup>1</sup> Das semiadditive LastChild-Measure wird in der Standard Edition unterstützt, aber andere semiadditive Measures, wie z. b. None, firstChild, FirstNonEmpty, LastNonEmpty, AverageOfChildren und ByAccount, sind nicht. Additive Measures, z. B. Sum, Count, Min, Max und nicht additive Measures (DistinctCount) werden in allen Editionen unterstützt.  
  
###  <a name="BISemModel_tabular"></a> BI Semantic Model (Tabular)  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Hierarchien|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|KPIs|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|Perspektiven|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|Translations|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|DAX-Berechnungen, DAX-Abfragen, MDX-Abfragen|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|Sicherheit auf Zeilenebene|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|Partitionen|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|Arbeitsspeicherinterne und DirectQuery-Speichermodi (nur tabellarisch)|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
  
###  <a name="PowerPivot"></a>PowerPivot für SharePoint  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|SharePoint-Farmintegration auf Grundlage der Shared Services-Architektur|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|Verwendungsberichte|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|Systemüberwachungsregeln|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|PowerPivot-Katalog|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|PowerPivot-Datenaktualisierung|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|PowerPivot-Datenfeeds|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
  
###  <a name="DataMining"></a> Data Mining  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Standardalgorithmen|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Data Mining-Tools (Assistenten, Editoren, Abfrage-Generatoren)|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Übergreifende Überprüfung|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|Modelle für gefilterte Teilmengen von Daten der Miningstruktur|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|Zeitreihen: benutzerdefinierte Kombination von ARTXP- und ARIMA-Methoden|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|Zeitreihen: Vorhersage mit neuen Daten|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|Unbegrenzte gleichzeitige Data Mining-Abfragen|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|Erweiterte Konfigurations & Optimierungs Optionen für Data Mining-Algorithmen|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|Unterstützung für Plug-In-Algorithmen|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|Parallele Modellverarbeitung|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|Zeitreihen: reihenübergreifende Vorhersage|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|Unbegrenzte Attribute für Zuordnungsregeln|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|Sequenzvorhersage|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|Mehrere Vorhersageziele für Naïve BaJa, neuronale Netzwerke und logistische Regression|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
  
##  <a name="Reporting"></a> Reporting Services  
  
###  <a name="Reporting_features"></a>Reporting Services Features  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Unterstützte [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Edition für Katalogdatenbanken|Standard oder höher|Standard oder höher|Standard oder höher|Web|Express|||  
|Unterstützte [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Edition für Datenquellen|Alle   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Editionen|Alle [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Editionen|Alle [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Editionen|Web|Express|||  
|Berichtsserver|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||  
|Berichts-Designer|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||  
|Berichts-Manager|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||  
|Rollenbasierte Sicherheit|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||  
|Word-Export und Rich-Text-Unterstützung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||  
|Verbesserte Messgeräte und Diagramme|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||  
|Export in Excel, PDF und Bilder|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||  
|Benutzerdefinierte Authentifizierung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||  
|Berichte als Datenfeeds|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||  
|Modellunterstützung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung||||  
|Erstellen von benutzerdefinierten Rollen für rollenbasierte Sicherheit|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Modellelementsicherheit|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Uneingeschränktes Durchklicken|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Bibliothek freigegebener Komponenten|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Abonnements und Zeitplanung für E-Mail und Dateifreigabe|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Berichtsverlauf, Ausführungs-Momentaufnahmen und Zwischenspeichern|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|SharePoint-Integration|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Unterstützung von Remotedatenquellen und Nicht-SQL-Datenquellen<sup>1</sup>|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|RDCE-Erweiterbarkeit von Datenquellen, Übermittlung und Rendering|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Datengesteuerte Berichtsabonnements|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|Bereitstellung für horizontales Skalieren (Webfarmen)|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|Warnungen<sup>2</sup>|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|[!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] <sup>2</sup>|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
  
 <sup>1</sup> Weitere Informationen zu den unterstützten Datenquellen in [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]finden Sie unter [von Reporting Services &#40;SSRS&#41;unterstützte Datenquellen](../reporting-services/create-deploy-and-manage-mobile-and-paginated-reports.md).  
  
 <sup>2</sup> Erfordert [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] im SharePoint-Modus. Weitere Informationen finden Sie unter [Reporting Services SharePoint-Modus &#40;-Installation SharePoint 2010 und Share&#41;Point 2013](../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md).  
  
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
  
##  <a name="BIClients"></a> Business Intelligence Clients  
 Die folgenden Softwareclientanwendungen sind im Microsoft Downloads Center verfügbar und bieten Unterstützung beim Erstellen von Business Intelligence-Dokumenten, die in einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanz ausgeführt werden. Wenn Sie diese Dokumente in einer Serverumgebung hosten, verwenden Sie eine Edition von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , die für diesen Dokumenttyp unterstützt wird. In der folgenden Tabelle wird dargestellt, welche [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Editionen die Serverfunktionen zum Hosten der in den Clientanwendungen erstellten Dokumente besitzen.  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[ssRBnoversion](../includes/ssrbnoversion.md)]|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|Data Mining-Add-Ins für Excel und Visio 2010|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|||||  
|[!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] 2010|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
  
> [!NOTE]
>  1.  [!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] ist ein Excel-Add-in und hängt nicht von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ab. [!INCLUDE[ssGeminiShort](../includes/ssgeminishort-md.md)] ist jedoch für die Freigabe und das Zusammenarbeiten mit [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] -Arbeitsmappen in SharePoint erforderlich, und diese Funktion ist als Teil von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Enterprise und Business Intelligence-Editionen verfügbar.  
> 2.  In der oben aufgeführten Tabelle sind die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Editionen angegeben, die zur Aktivierung dieser Clienttools erforderlich sind. Über diese Funktionen kann jedoch auf Daten zugegriffen werden, die von beliebigen [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Editionen gehostet werden.  
  
##  <a name="Spatial"></a> Spatial and Location Services  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Räumlichkeitsindizes|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|Planarer und geodätischer Datentyp|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|Erweiterte räumliche Bibliotheken|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|Importieren/Exportieren räumlicher Industriestandard-Datenformate|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
  
##  <a name="Add_DBServices"></a> Additional Database Services  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Migration Assistant|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|Datenbank-E-Mail|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung||||  
  
##  <a name="Other_Components"></a> Andere Komponenten  
  
|Funktionsname|Enterprise|Business Intelligence|Standard|Web|Express mit Advanced Services|Express mit Tools|Express|  
|------------------|----------------|---------------------------|--------------|---------|------------------------------------|------------------------|-------------|  
|Data Quality Services|Benutzerkontensteuerung|Benutzerkontensteuerung||||||  
|StreamInsight|StreamInsight Premium-Edition|StreamInsight Standard-Edition|StreamInsight Standard-Edition|StreamInsight Standard-Edition||||  
|StreamInsight HA|StreamInsight Premium-Edition|||||||  
  
## <a name="see-also"></a>Siehe auch  
 [Produktspezifikationen für SQL Server 2014](../../2014/getting-started/sql-server-2014-product-specifications.md)   
 [Installation für SQL Server 2014](../database-engine/install-windows/installation-for-sql-server.md)   
 [Schnellstart-Installation von SQL Server 2014](../../2014/getting-started/quick-start-installation-of-sql-server-2014.md)  
  
  
