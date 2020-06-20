---
title: Spezifikationen der maximalen Kapazität für SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- objects [SQL Server]
- number capacity specifications [SQL Server]
- size [SQL Server], capacity specifications
- number of objects
- capacity specifications [SQL Server]
- maximum capacity specifications [SQL Server]
- size [SQL Server]
- replication capacity specifications [SQL Server]
- objects [SQL Server], capacity specifications
- Database Engine [SQL Server], capacity specifications
ms.assetid: 13e95046-0e76-4604-b561-d1a74dd824d7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 59b45d3ab221e02b89abf328eac5f189f0f84728
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85044592"
---
# <a name="maximum-capacity-specifications-for-sql-server"></a>Spezifikationen der maximalen Kapazität für SQL Server
  Die folgende Tabelle gibt die maximale Größe und Anzahl verschiedener in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Komponenten definierter Objekte an. Um zur Tabelle für eine [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Technologie zu navigieren, klicken Sie auf den zugehörigen Link:  
  
 [SQL Server-Datenbank-Engine-Objekte](#Engine)  
  
 [SQL Server-Hilfsprogrammobjekte](#Utility)  
  
 [SQL Server-Datenebenenanwendungs-Objekte](#DAC)  
  
 [SQL Server-Replikationsobjekte](#Replication)  
  
##  <a name="ssde-objects"></a><a name="Engine"></a>[!INCLUDE[ssDE](../includes/ssde-md.md)]Objekte  
 Die folgende Tabelle gibt die maximale Größe und Anzahl verschiedener in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Datenbanken definierter oder in [!INCLUDE[tsql](../includes/tsql-md.md)]-Anweisungen referenzierter Objekte an.  
  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)]-Objekte|Maximale Größe/Anzahl [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (32 Bit)|Maximale Größe/Anzahl – [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (64 Bit)|  
|---------------------------------------------------------|------------------------------------------------------------------|------------------------------------------------------------------|  
|Batchgröße<br /><br /> Hinweis: die Netzwerk Paketgröße entspricht der Größe der TDS-Pakete (Tabular Data Stream), die für die Kommunikation zwischen Anwendungen und dem relationalen verwendet werden [!INCLUDE[ssDE](../includes/ssde-md.md)] . Die Standardpaketgröße beträgt 4 KB und wird durch die Konfigurationsoption Netzwerkpaketgröße gesteuert.|65.536 * Netzwerkpaketgröße|65.536 * Netzwerkpaketgröße|  
|Bytes pro Spalte mit kurzen Zeichenfolgen|8\.000|8\.000|  
|Bytes pro GROUP BY, ORDER BY|8\.060|8\.060|  
|Bytes pro Indexschlüssel<br /><br /> Hinweis: die maximale Anzahl von Bytes in einem beliebigen Index Schlüssel darf in 900 nicht überschreiten [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Sie können einen Schlüssel mithilfe von Spalten variabler Länge definieren, deren maximale Größen zusammen mehr als 900 Bytes betragen, wenn niemals eine Zeile eingefügt wird, die in diesen Spalten mehr als 900 Bytes an Daten enthält. In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] können Sie Nichtschlüsselspalten in den nicht gruppierten Index aufnehmen, um die maximale Indexschlüsselgröße von 900 Bytes zu vermeiden.|900|900|  
|Bytes pro Fremdschlüssel|900|900|  
|Bytes pro Primärschlüssel|900|900|  
|Bytes pro Zeile<br /><br /> Hinweis:<br />        [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] unterstützt die Zeilenüberlaufspeicherung, sodass Spalten variabler Länge aus der Zeile verschoben werden können. Für Spalten variabler Länge, die aus der Zeile verschoben wurden, wird im Hauptdatensatz nur ein 24-Byte-Stamm gespeichert. Aus diesem Grund ist das tatsächlich gültige Zeilenlimit höher als in früheren Versionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Weitere Informationen finden Sie unter "Zeilenüberlauf bei Daten über 8 KB" in der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Onlinedokumentation.|8\.060|8\.060|  
|Bytes pro Zeile in speicheroptimierten Tabellen<br /><br /> Hinweis:<br />        [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Die Zeilenüberlaufspeicherung wird von In-Memory OLTP nicht unterstützt. Spalten variabler Länge werden nicht aus der Zeile verschoben. Dadurch wird die maximale Breite von Spalten variabler Länge, die Sie in einer speicheroptimierten Tabelle angeben können, auf die maximale Zeilengröße beschränkt. Weitere Informationen finden Sie unter [Tabellen- und Zeilengröße in speicheroptimierten Tabellen](../relational-databases/in-memory-oltp/table-and-row-size-in-memory-optimized-tables.md).|Nicht unterstützt|8\.060|  
|Bytes im Quelltext einer gespeicherten Prozedur|Kleiner als Batchgröße oder 250 MB|Kleiner als Batchgröße oder 250 MB|  
|Bytes pro `varchar(max)`-, `varbinary(max)`-, `xml`-, `text`- oder `image`-Spalte.|2^31-1|2^31-1|  
|Zeichen pro `ntext`- oder `nvarchar(max)`-Spalte|2^30-1|2^30-1|  
|Gruppierte Indizes pro Tabelle|1|1|  
|Spalten in GROUP BY, ORDER BY|Begrenzung nur durch die Anzahl von Bytes|Begrenzung nur durch die Anzahl von Bytes|  
|Spalten oder Ausdrücke in einer GROUP BY WITH CUBE- oder WITH ROLLUP-Anweisung|10|10|  
|Spalten pro Indexschlüssel<br /><br /> Hinweis: Wenn die Tabelle einen oder mehrere XML-Indizes enthält, ist der Clustering-Schlüssel der Benutzertabelle auf 15 Spalten beschränkt, da die XML-Spalte dem gruppierschlüssel des primären XML-Indexes hinzugefügt wird. In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] können Sie Nichtschlüsselspalten in den nicht gruppierten Index aufnehmen, um die Beschränkung auf maximal 16 Schlüsselspalten zu vermeiden. Weitere Informationen finden Sie unter [Create Indexes with Included Columns](../relational-databases/indexes/create-indexes-with-included-columns.md).|16|16|  
|Spalten pro Fremdschlüssel|16|16|  
|Spalten pro Primärschlüssel|16|16|  
|Spalten pro Tabelle (keine breite Tabelle)|1\.024|1\.024|  
|Spalten pro breiter Tabelle|30.000|30.000|  
|Spalten pro SELECT-Anweisung|4\.096|4\.096|  
|Spalten pro INSERT-Anweisung|4096|4096|  
|Verbindungen pro Client|Höchstwert konfigurierter Verbindungen|Höchstwert konfigurierter Verbindungen|  
|Datenbankgröße|524.272 Terabytes|524.272 Terabytes|  
|Datenbanken pro Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|32.767|32.767|  
|Dateigruppen pro Datenbank|32.767|32.767|  
|Dateigruppen pro Datenbank für speicheroptimierte Daten|Nicht unterstützt|1|  
|Dateien pro Datenbank|32.767|32.767|  
|Dateigröße (Daten)|16 Terabytes|16 Terabytes|  
|Dateigröße (Protokoll)|2 Terabytes|2 Terabytes|  
|Datendateien für speicheroptimierte Daten pro Datenbank|Nicht unterstützt|4.096|  
|Änderungsdatei pro Datendatei für speicheroptimierte Daten|Nicht unterstützt|1|  
|Verweise auf Fremdschlüsseltabellen pro Tabelle<br /><br /> Hinweis: Obwohl eine Tabelle eine unbegrenzte Anzahl von Foreign Key-Einschränkungen enthalten kann, ist der empfohlene Höchstwert 253. In Abhängigkeit von der Hardwarekonfiguration, die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] hostet, kann das Angeben weiterer FOREIGN KEY-Einschränkungen den Abfrageoptimierer bei der Verarbeitung stark beanspruchen.|253|253|  
|Bezeichnerlänge (in Zeichen)|128|128|  
|Instanzen pro Computer|50 Instanzen auf einem eigenständigen Server für alle [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Editionen.<br /><br /> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]unterstützt 25 Instanzen auf einem Failovercluster bei Verwendung eines freigegebenen Cluster Datenträgers als gespeicherte Option für die Cluster Installation [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] unterstützt 50-Instanzen auf einem Failovercluster, wenn Sie SMB-Dateifreigaben als Speicher Option für Ihre Cluster Installation auswählen. Weitere Informationen finden Sie unter [Hardware-und Software Anforderungen für die Installation SQL Server 2014](install/hardware-and-software-requirements-for-installing-sql-server.md).|50 Instanzen auf einem eigenständigen Server.<br /><br /> 25 Instanzen auf einem Failovercluster, wenn Sie für die Clusterinstallation einen freigegebenen Clusterdatenträger als Speicheroption verwenden. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] unterstützt 50 Instanzen auf einem Failovercluster, wenn Sie für die Clusterinstallation SMB-Dateifreigaben als Speicheroption verwenden.|  
|Indizes pro speicheroptimierter Tabelle|Nicht unterstützt|8|  
|Länge einer Zeichenfolge, die SQL-Anweisungen enthält (Batchgröße)<br /><br /> Hinweis: die Netzwerk Paketgröße entspricht der Größe der TDS-Pakete (Tabular Data Stream), die für die Kommunikation zwischen Anwendungen und dem relationalen verwendet werden [!INCLUDE[ssDE](../includes/ssde-md.md)] . Die Standardpaketgröße beträgt 4 KB und wird durch die Konfigurationsoption Netzwerkpaketgröße gesteuert.|65.536 * Netzwerkpaketgröße|65.536 * Netzwerkpaketgröße|  
|Sperren pro Verbindung|Maximale Anzahl Sperren pro Server|Maximale Anzahl Sperren pro Server|  
|Sperren pro Instanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]<br /><br /> Hinweis: dieser Wert ist für die statische Sperr Zuordnung. Dynamische Sperren sind nur durch den Arbeitsspeicher beschränkt.|Bis zu 2.147.483.647|Begrenzung nur durch Arbeitsspeicher|  
|Schachtelungsebenen gespeicherter Prozeduren<br /><br /> Hinweis: Wenn eine gespeicherte Prozedur auf mehr als 64 Datenbanken zugreift oder sich mehr als 2 Datenbanken in der überlappte befinden, erhalten Sie eine Fehlermeldung.|32|32|  
|Geschachtelte Unterabfragen|32|32|  
|Schachtelungsebenen für Trigger|32|32|  
|Nicht gruppierte Indizes pro Tabelle|999|999|  
|Anzahl der unterschiedlichen Ausdrücke in der GROUP BY-Klausel bei Vorhandensein eines der folgenden Ausdrücke: CUBE, ROLLUP, GROUPING SETS, WITH CUBE, WITH ROLLUP|32|32|  
|Anzahl der Gruppierungssätze, die von Operatoren in der GROUP BY-Klausel generiert wurden|4\.096|4\.096|  
|Parameter pro gespeicherter Prozedur|2\.100|2\.100|  
|Parameter pro benutzerdefinierter Funktion|2\.100|2\.100|  
|REFERENCES pro Tabelle|253|253|  
|Zeilen pro Tabelle|Begrenzung durch verfügbaren Speicherplatz|Begrenzung durch verfügbaren Speicherplatz|  
|Tabellen pro Datenbank<br /><br /> Hinweis: Datenbankobjekte enthalten Objekte wie Tabellen, Sichten, gespeicherte Prozeduren, benutzerdefinierte Funktionen, Trigger, Regeln, Standardwerte und Einschränkungen. Die Summe aller Objekte in einer Datenbank kann 2.147.483.647 nicht übersteigen.|Begrenzung durch die Anzahl der Objekte in einer Datenbank|Begrenzung durch die Anzahl der Objekte in einer Datenbank|  
|Partitionen pro partitionierter Tabelle oder partitioniertem Index|1\.000<br /><br /> Wichtig das Erstellen einer Tabelle oder eines Indexes mit mehr als 1.000 Partitionen ist in einem 32-Bit-System möglich, wird jedoch nicht unterstützt. ** \* \* \* \* **|15.000|  
|Statistiken für nicht indizierte Spalten|30.000|30.000|  
|Tabellen pro SELECT-Anweisung|Begrenzung nur durch verfügbare Ressourcen|Begrenzung nur durch verfügbare Ressourcen|  
|Trigger pro Tabelle<br /><br /> Hinweis: Datenbankobjekte enthalten Objekte wie Tabellen, Sichten, gespeicherte Prozeduren, benutzerdefinierte Funktionen, Trigger, Regeln, Standardwerte und Einschränkungen. Die Summe aller Objekte in einer Datenbank kann 2.147.483.647 nicht übersteigen.|Begrenzung durch die Anzahl der Objekte in einer Datenbank|Begrenzung durch die Anzahl der Objekte in einer Datenbank|  
|Spalten pro UPDATE-Anweisung (breite Tabellen)|4096|4096|  
|Benutzerverbindungen|32.767|32.767|  
|XML-Indizes|249|249|  
  
##  <a name="ssnoversion-utility-objects"></a><a name="Utility"></a>[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Hilfsprogrammobjekte  
 Die folgende Tabelle gibt die maximale Größe und Anzahl verschiedener, im [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Hilfsprogramm getesteter Objekte an.  
  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Hilfsprogrammobjekt|Maximale Größe/Anzahl [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (32 Bit)|Maximale Größe/Anzahl – [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (64 Bit)|  
|----------------------------------------------|------------------------------------------------------------------|------------------------------------------------------------------|  
|Computer (physische Computer oder virtuelle Computer) pro [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Hilfsprogramm|100|100|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanzen pro Computer|5|5|  
|Gesamtzahl von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Instanzen pro [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Hilfsprogramm|200*|200*|  
|Benutzerdatenbanken pro [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanz, einschließlich Datenebenenanwendungen|50|50|  
|Gesamtzahl von Benutzerdatenbanken pro [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Hilfsprogramm|1\.000|1\.000|  
|Dateigruppen pro Datenbank|1|1|  
|Datendateien pro Dateigruppe|1|1|  
|Protokolldateien pro Datenbank|1|1|  
|Volumes pro Computer|3|3|  
  
 * Die maximale Anzahl verwalteter Instanzen von, die [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] vom-Hilfsprogramm unterstützt werden, kann abhängig von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] der Hardwarekonfiguration des Servers variieren. Informationen zu ersten Schritten finden Sie unter [Funktionen und Tasks im SQL Server-Hilfsprogramm](../relational-databases/manage/sql-server-utility-features-and-tasks.md). Ein [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Steuerungspunkt für das Hilfsprogramm ist nicht in jeder Edition von [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] verfügbar. Eine Liste der Funktionen, die von den Editionen von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]unterstützt werden, finden Sie unter [Features Supported by the Editions of SQL Server 2014](../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
##  <a name="ssnoversion-data-tier-application-objects"></a><a name="DAC"></a>[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Datenebenenanwendungsobjekte  
 In der folgenden Tabelle wird die maximale Größe und Anzahl verschiedener in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Datenebenenanwendungen (DAC) getesteter Objekte angegeben.  
  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] DAC-Objekt|Maximale Größe/Anzahl [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (32 Bit)|Maximale Größe/Anzahl – [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (64 Bit)|  
|------------------------------------------|------------------------------------------------------------------|------------------------------------------------------------------|  
|Datenbanken pro DAC|1|1|  
|Objekte pro DAC*|Durch die Anzahl der Objekte in einer Datenbank oder durch den verfügbaren Speicher beschränkt.|Durch die Anzahl der Objekte in einer Datenbank oder durch den verfügbaren Speicher beschränkt.|  
  
 * Die maximalen Werte gelten für folgende Objekttypen: Benutzer, Tabellen, Sichten, gespeicherte Prozeduren, benutzerdefinierte Funktionen, Datentypen und Tabellentypen sowie Datenbankrollen und Schemas.  
  
##  <a name="replication-objects"></a><a name="Replication"></a>Replikations Objekte  
 Die folgende Tabelle gibt die maximale Größe und Anzahl verschiedener in der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Replikation definierter Objekte an.  
  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Replikationsobjekt|Maximale Größe/Anzahl SQL Server (32-Bit)|Maximale Größe/Anzahl SQL Server (64-Bit)|  
|--------------------------------------------------|---------------------------------------------------|---------------------------------------------------|  
|Artikel (Mergeveröffentlichung)|256|256|  
|Artikel (Momentaufnahmen- oder Transaktionsveröffentlichung)|32.767|32.767|  
|Spalten in einer Tabelle* (Mergeveröffentlichung)|246|246|  
|Spalten in einer Tabelle** ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Momentaufnahmen- oder -Transaktionsveröffentlichung)|1\.000|1\.000|  
|Spalten in einer Tabelle** (Oracle-Momentaufnahmen- oder -Transaktionsveröffentlichung)|995|995|  
|Bytes für eine in einem Zeilenfilter verwendete Spalte (Mergeveröffentlichung)|1\.024|1\.024|  
|Bytes für eine in einem Zeilenfilter verwendete Spalte (Momentaufnahmen- oder Transaktionsveröffentlichung)|8\.000|8\.000|  
  
 * Falls die Zeilennachverfolgung zur Konflikterkennung verwendet wird (Standardeinstellung), kann die Basistabelle maximal 1.024 Spalten enthalten. Die Spalten müssen jedoch im Artikel gefiltert werden, sodass maximal 246 Spalten veröffentlicht werden. Wenn Spaltennachverfolgung verwendet wird, kann die Basistabelle maximal 246 Spalten enthalten.  
  
 ** Die Basistabelle kann die maximal zulässige Anzahl von Spalten in der Veröffentlichungsdatenbank (1.024 für [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]) enthalten. Die Spalten müssen aber aus dem Artikel herausgefiltert werden, wenn sie das für den Veröffentlichungstyp angegebene Maximum überschreiten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hardware-und Software Anforderungen für die Installation von SQL Server 2014](install/hardware-and-software-requirements-for-installing-sql-server.md)   
 [Überprüfen der Parameter für die Systemkonfigurations Prüfung](../database-engine/install-windows/check-parameters-for-the-system-configuration-checker.md)   
 [SQL Server-Hilfsprogramm von Features und Aufgaben](../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
  
