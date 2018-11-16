---
title: Editionen und unterstützte Funktionen von SQL Server 2017 ~ Linux | Microsoft-Dokumentation
ms.custom: sql-linux
ms.date: 09/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: linux
ms.topic: conceptual
helpviewer_keywords:
- Enterprise Edition [SQL Server]
- Developer Edition [SQL Server]
- default components
- installing SQL Server, components
- Setup [SQL Server], components
- SQL Server, editions
- SQL Server, components
- editions [SQL Server]
- versions [SQL Server]
- Setup [SQL Server], editions
- SQL Server Installation Wizard
- components [SQL Server]
- Standard Edition [SQL Server]
- installing SQL Server, editions
- editions [SQL Server], about edition options
- Setup [SQL Server]
ms.assetid: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 089ced09d718b0716f0c19d4553e52ff02c3d505
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51665579"
---
# <a name="editions-and-supported-features-of-sql-server-2017-on-linux"></a>Editionen und unterstützte Funktionen von SQL Server 2017 unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dieser Artikel enthält detaillierte Informationen zu Funktionen, die von den verschiedenen Editionen von SQL Server 2017 unter Linux unterstützt. Editionen und unterstützte Funktionen von SQL Server unter Windows finden Sie [SQL Server 2017 - Windows](../sql-server/editions-and-components-of-sql-server-2017.md).  
  
Die Installationsanforderungen variieren je nach den benötigten Anwendungen. Die verschiedenen Editionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] tragen den individuellen Leistungs-, Laufzeit- und Preisanforderungen von Organisationen und Einzelpersonen Rechnung. Welche [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Komponenten Sie installieren, hängt auch von den individuellen Anforderungen ab. In den folgenden Abschnitten erfahren Sie, wie Sie die bestmögliche Auswahl unter den in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]verfügbaren Editionen und Komponenten treffen.  

Die neuesten Versionsanmerkungen und Informationen zu Neuerungen finden Sie über die folgenden Links:
- [SQL Server unter Linux: Anmerkungen zu dieser Version](sql-server-linux-release-notes.md)
- [Neuerungen in SQL Server unter Linux](sql-server-linux-whats-new.md)

Eine Liste der SQL Server-Funktionen unter Linux nicht verfügbar, finden Sie unter [nicht unterstützten Funktionen und Dienste](sql-server-linux-release-notes.md#Unsupported).

### <a name="try-sql-server"></a>Testen Sie SQL Server!    
    
[SQLServer 2017 herunterladen](https://www.microsoft.com/sql-server/sql-server-2017)

## <a name="includessnoversionincludesssnoversion-mdmd-editions"></a>[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] Editionen  
 In der folgenden Tabelle werden die Editionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]beschrieben. 
  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Edition|Definition|  
|---------------------------------------|----------------|  
|Enterprise|Die Premium-Angebot [!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] Enterprise Edition bietet umfassende hochwertige datencenterfunktionen mit blitzschneller Performance hohe Servicelevel für unternehmenswichtige Workloads.|  
|Standard|[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] Standard Edition bietet grundlegenden datenverwaltung für Abteilungen und kleinere Unternehmen ihre Anwendungen ausführen und unterstützt allgemeine Entwicklungstools für lokale und Cloud, ermöglicht eine effektive datenbankverwaltung mit minimalen IT-Ressourcen.|  
|Web|Die[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] Web Edition ist eine mit geringen Anschaffungs- und Betriebskosten verbundene Option für Webhoster und Web-VAPs, die kostengünstige Skalierbarkeit und Verwaltungsfunktionen für Webpräsenzen jeder Größe bietet.|  
|Entwickler|[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] Developer Edition ermöglicht Entwicklern das Erstellen beliebiger Anwendungen auf der Basis von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Sämtliche Funktionen der Enterprise Edition stehen zur Verfügung. Die Lizenz bezieht sich jedoch auf die Verwendung als Entwicklungs- und Testsystem und nicht als Produktionsserver. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Developer ist eine ideale Option zum Erstellen und Testen von Anwendungen.|  
|Express Edition|Die Express Edition ist eine kostenlose Datenbank auf Einstiegsebene und eignet sich ideal zum Üben und zum Erstellen von datengesteuerten Anwendungen für Desktopcomputer und kleine Server. Dies ist die beste Wahl für unabhängige Softwareanbieter, Entwickler und Tüftler, die Clientanwendungen erstellen. Wenn Sie erweiterte Datenbankfunktionen benötigen, können Sie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Express nahtlos auf höhere Endversionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]aktualisieren.|  
  
## <a name="using-includessnoversionincludesssnoversion-mdmd-with-clientserver-applications"></a>Verwenden von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] mit Client-/Server-Anwendungen  

Sie können auch nur die Clientkomponenten von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf einem Computer mit Client-/Serveranwendungen installieren und so eine direkte Verbindung mit einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanz herstellen. Die Installation der Clientkomponenten ist auch dann eine gute Wahl, wenn Sie eine Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf einem Datenbankserver verwalten, oder wenn Sie [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anwendungen entwickeln möchten.  
  
## <a name="includessnoversionincludesssnoversion-mdmd-components"></a>[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Komponenten  

SQL Server 2017 unter Linux unterstützt die SQL Server-Datenbank-Engine. Die folgende Tabelle beschreibt die Funktionen in der Datenbank-Engine.   
  
|Serverkomponenten|Description|  
|-----------------------|-----------------|  
|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] enthält die [!INCLUDE[ssDE](../includes/ssde-md.md)], den Basisdienst für speichern, verarbeiten und Sichern von Daten, Replikation, Volltextsuche, Tools zum Verwalten von relationalen und XML-Daten, und klicken Sie in der Datenbank-Analytics-Integration.|  

**Developer, Enterprise Core und Evaluation-Editionen**  
Von der Developer, Enterprise Core und Evaluation-Editionen unterstützte Funktionen finden Sie unter für die SQL Server Enterprise Edition in den folgenden Tabellen aufgeführten Funktionen.

Die Developer Edition unterstützt weiterhin nur einen Client für [SQL Server Distributed Replay](../tools/distributed-replay/sql-server-distributed-replay.md). 
  
##  <a name="Cross-BoxScaleLimits"></a> Skalierungsgrenzen  
  
|Funktion|Enterprise|Standard|Web|Express| 
|-------------|----------------|--------------|---------|------------------------|
|Maximale von einer einzelnen Instanz verwendete Rechenkapazität ( [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]<sup>1</sup>|Maximum des Betriebssystems|Beschränkt auf weniger als 4 Sockets oder 24 Kerne|Beschränkt auf weniger als 4 Sockets oder 16 Kerne|Beschränkt auf weniger als 1 Socket oder 4 Kerne| 
|Maximale von einer einzelnen Instanz verwendete Rechenkapazität ( [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] oder [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)])|Maximum des Betriebssystems|Beschränkt auf weniger als 4 Sockets oder 24 Kerne|Beschränkt auf weniger als 4 Sockets oder 16 Kerne|Beschränkt auf weniger als 1 Socket oder 4 Kerne|
|Maximaler Arbeitsspeicher für den Pufferpool pro Instanz von [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]|Maximum des Betriebssystems|128 GB|64 GB|1410 MB|
|Maximaler Arbeitsspeicher für Columnstore-Segmentcache pro Instanz von [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]|Unbegrenzter Arbeitsspeicher| 32 GB| 16 GB| 352 MB|  
|Maximale speicheroptimierte Datengröße pro Datenbank in [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]|Unbegrenzter Arbeitsspeicher| 32 GB| 16 GB| 352 MB|
|Maximale relationale Datenbankgröße|524 PB|524 PB|524 PB|10 GB|  
  
<sup>1</sup> Enterprise Edition mit Server + Clientzugriffslizenz (CAL) basierte Lizenzierung (für neue Verträge nicht verfügbar) ist auf maximal 20 Kerne pro SQL Server-Instanz beschränkt. Für das auf Prozessorkernen basierende Serverlizenzierungsmodell gelten keine Beschränkungen. Weitere Informationen finden Sie unter [Rechenkapazitätsgrenzen von bestimmten Editionen von SQL Server](../sql-server/compute-capacity-limits-by-edition-of-sql-server.md).  
 
##  <a name="RDBMSHA"></a> RDBMS: Hochverfügbarkeit  
  
|Funktion|Enterprise|Standard|Web|Express|  
|-------------|----------------|--------------|---------|------------------------|  
|Protokollversand|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|  
|Sicherungskomprimierung|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|nein| 
|Datenbankmomentaufnahme|Benutzerkontensteuerung|nein|nein|nein|
|Always On-Failoverclusterinstanz<sup>1</sup>|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|nein| 
|Always On-Verfügbarkeitsgruppen<sup>2</sup>|Benutzerkontensteuerung|nein|nein|nein|
|Basis-Verfügbarkeitsgruppen <sup>3</sup>|nein|Benutzerkontensteuerung|nein|nein|
|Mindestreplikate für Commitverfügbarkeitsgruppen|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|nein|
|Verfügbarkeitsgruppe ohne Cluster|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|nein|
|Onlineseiten- und Onlinedateiwiederherstellung|Benutzerkontensteuerung|nein|nein|nein|
|Online-Indizierung|Benutzerkontensteuerung|nein|nein|nein|
|Fortsetzbare Neuerstellung von online geschalteten Indizes|Benutzerkontensteuerung|nein|nein|nein|
|Onlineschemaänderung|Benutzerkontensteuerung|nein|nein|nein|
|Schnelle Wiederherstellung|Benutzerkontensteuerung|nein|nein|nein|
|Gespiegelte Sicherungen|Benutzerkontensteuerung|nein|nein|nein|
|Hinzufügen von Speicher im laufenden Systembetrieb und CPU|Benutzerkontensteuerung|nein|nein|nein|
|Verschlüsselte Sicherung|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|nein|
|Hybridsicherung in Windows Azure (Sicherung über URL)|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|nein|
  
<sup>1</sup> für die Enterprise Edition, ist die Anzahl der Knoten dem maximum des Betriebssystems. Bei der Standard Edition werden nur zwei Knoten unterstützt. 

<sup>2</sup> auf Enterprise Edition bietet Unterstützung für bis zu 8 sekundäre Replikate – einschließlich 2 synchronen sekundären Replikaten. 

<sup>3</sup> standard Edition werden Basis-Verfügbarkeitsgruppen unterstützt. Eine Basis-Verfügbarkeitsgruppe unterstützt zwei Replikate mit einer Datenbank. Weitere Informationen über Basis-Verfügbarkeitsgruppen finden Sie unter [Basis-Verfügbarkeitsgruppen](../database-engine/availability-groups/windows/basic-availability-groups-always-on-availability-groups.md).    

##  <a name="RDBMSSP"></a> RDBMS: Skalierbarkeit und Leistung  
  
|Funktion|Enterprise|Standard|Web|Express|  
|-------------|----------------|--------------|---------|------------------------| 
|Columnstore <sup>1</sup>|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|Große Objektbinärdateien in gruppierten Columnstore-Indizes|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|Onlineneuerstellung für nicht gruppierten Columnstore-Index|Benutzerkontensteuerung|nein|nein|nein|
|In-Memory-OLTP <sup>1</sup>|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|
|Persistenter Hauptspeicher|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|
|Tabellen- und Indexpartitionierung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|Datenkomprimierung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|
|Ressourcenkontrolle|Benutzerkontensteuerung|nein|nein|nein|  
|Parallelverarbeitung für partitionierte Tabellen|Benutzerkontensteuerung|nein|nein|nein|
|NUMA-basierter und großer Arbeitsspeicher für umfangreiche Seiten und Zuordnung von Pufferarrays|Benutzerkontensteuerung|nein|nein|nein|
|Ressourcenkontrolle für E/A-Vorgänge|Benutzerkontensteuerung|nein|nein|nein|  
|Verzögerte Dauerhaftigkeit|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|
|Automatische Optimierung|Benutzerkontensteuerung|nein|nein|nein|
|Adaptive Joins im Batchmodus|Benutzerkontensteuerung|nein|nein|nein|
|Feedback zur Speicherzuweisung im Batchmodus|Benutzerkontensteuerung|nein|nein|nein|
|Verschachtelte Ausführung mit Tabellenwertfunktionen mit mehreren Anweisungen|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|
|Verbesserungen beim massenhaften Einfügen|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|


<sup>1</sup> Die Größe der In-Memory OLTP-Daten und des Columnstore-Segmentcaches sind auf die Größe des Arbeitsspeichers beschränkt, die von der Edition im Bereich Kapazitätsgrenzen festgelegt wird. Den maximale Grad an Parallelität ist beschränkt. Der Grad an prozessparallelität (DOP) für eine indexerstellung ist auf 2 DOP für die Standard Edition und auf 1 DOP für die Web und Express-Editionen beschränkt. Dies gilt für Columnstore-Indizes, die über datenträgerbasierte Tabellen und speicheroptimierte Tabellen erstellt wurden.

##  <a name="RDBMSS"></a> RDBMS: Sicherheit  
  
|Funktion|Enterprise|Standard|Web|Express|
|-------------|----------------|--------------|---------|------------------------------------| 
|Sicherheit auf Zeilenebene|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|Always Encrypted|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung| 
|Dynamische Datenmaskierung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|   
|Allgemeine Überwachung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung| 
|Feine Überwachung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung| 
|Transparente Datenbankverschlüsselung|Benutzerkontensteuerung|nein|nein|nein|   
|Benutzerdefinierte Rollen|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung| 
|Eigenständige Datenbanken|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung| 
|Verschlüsselung von Sicherungen|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|nein|  

##  <a name="RDBMSM"></a> RDBMS: Verwaltbarkeit  
  
|Funktion|Enterprise|Standard|Web|Express|   
|-------------|----------------|--------------|---------|------------------------|  
|Dedizierte Administratorverbindung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Ja, mit Ablaufverfolgungsflag|Ja, mit Ablaufverfolgungsflag|   
|PowerShell-Skriptunterstützung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung| 
|Unterstützung für Komponentenvorgänge der Datenschichtanwendung: Extrahieren, Bereitstellen, Aktualisieren, Löschen|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung| 
|Richtlinienautomatisierung (Überprüfung nach Zeitplan und Änderungen)|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|nein|   
|Sammler von Leistungsdaten|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|nein| 
|Standardleistungsberichte|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|nein| 
|Planhinweislisten und Planeinfrierung für Planhinweislisten|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|nein|   
|Direkte Abfrage von indizierten Sichten (mittels NOEXPAND-Hinweis)|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung| 
|Automatische Wartung für indizierte Sichten|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|nein| 
|Verteilte partitionierte Sichten|Benutzerkontensteuerung|nein|nein|nein| 
|Parallele Indexvorgänge|Benutzerkontensteuerung|nein|nein|nein|  
|Automatische Verwendung indizierter Sichten mittels Abfrageoptimierer|Benutzerkontensteuerung|nein|nein|nein| 
|Parallele Konsistenzprüfung|Benutzerkontensteuerung|nein|nein|nein| 
|SQL Server-Steuerungspunkt für das Hilfsprogramm|Benutzerkontensteuerung|nein|nein|nein|    

##  <a name="Programmability"></a> Programmability  
  
|Funktion|Enterprise|Standard|Web|Express 
|-------------|----------------|--------------|---------|------------------------|  
|JSON|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|   
|Abfragespeicher|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|   
|Temporal|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|   
|Systemeigene XML-Unterstützung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung| 
|XML-Indizierung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung| 
|MERGE- und UPSERT-Funktionen|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|   
|Datums- und Uhrzeitdatentypen|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  
|Internationalisierungsunterstützung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung| 
|Volltextsuche und semantische Suche|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|nein| 
|Angabe der Sprache in einer Abfrage|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|   
|Service Broker (Messaging)|Benutzerkontensteuerung|Benutzerkontensteuerung|Nein (nur Client)|Nein (nur Client)|Nein (nur Client)|   
|Transact-SQL-Endpunkte|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|nein|nein| 
|Diagramm|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|  


<sup>1</sup> Horizontale Skalierung mit mehreren Computeknoten erfordert einen Hauptknoten.

## <a name="IS"></a> Integration Services

Informationen zu den von den Editionen unterstützte Integration Services (SSIS)-Funktionen [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)], finden Sie unter [Integration Services-Funktionen, die von den Editionen von SQL Server unterstützte](../integration-services/integration-services-features-supported-by-the-editions-of-sql-server.md).

##  <a name="SLS"></a> Räumliche und ortsbezogene Dienste  
  
|Funktionsname|Enterprise|Standard|Web|Express|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|
|Räumlichkeitsindizes|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|   
|Planarer und geodätischer Datentyp|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung| 
|Erweiterte räumliche Bibliotheken|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|   
|Importieren/Exportieren räumlicher Industriestandard-Datenformate|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|   

  
## <a name="next-steps"></a>Nächste Schritte 
 [Editionen und unterstützte Funktionen für SQL Server 2017 – Windows](../sql-server/editions-and-components-of-sql-server-2017.md)  
 [Editionen und unterstützte Funktionen für SQL Server 2016 - Windows](../sql-server/editions-and-components-of-sql-server-2016.md)  
 [Editionen und unterstützte Funktionen für SQL Server 2014 - Windows](https://msdn.microsoft.com/library/cc645993(v=sql.120).aspx)  
 [Installation for SQL Server (Installation für SQLServer 2016)](../database-engine/install-windows/installation-for-sql-server-2016.md)  
 [Produktspezifikationen für SQLServer](https://msdn.microsoft.com/library/6445fd53-6844-4170-a86b-7fe76a9f64cb) 

  
  
