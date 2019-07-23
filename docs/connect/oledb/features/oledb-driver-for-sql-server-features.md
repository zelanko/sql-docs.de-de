---
title: OLE DB Treiber für SQL Server Features | Microsoft-Dokumentation
description: OLE DB-Treiber für SQL Server-Features
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- MDAC [SQL Server]
- MSOLEDBSQL, about OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], features
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 46f7de1e57686a0f54368407580d90236152d147
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989050"
---
# <a name="ole-db-driver-for-sql-server-features"></a>OLE DB-Treiber für SQL Server-Features
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Der OLE DB-Treiber für SQL Server macht nicht nur Features der Windows (früher Microsoft) Data Access Components (WDAC) verfügbar, sondern implementiert zudem viele weitere Features, um die Funktionalität von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verfügbar zu machen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt    
 [Verwenden der Datenbankspiegelung](../../oledb/features/using-database-mirroring.md)  
 Erläutert, auf welche Weise der OLE DB-Treiber für SQL Server die Verwendung von Spiegeldatenbanken unterstützt, das heißt, die Fähigkeit, eine Kopie (Spiegelung) einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank auf einem Standbyserver bereitzuhalten.  
  
 [Ausführen asynchroner Vorgänge](../../oledb/features/performing-asynchronous-operations.md)  
 Erläutert, auf welche Weise der OLE DB-Treiber für SQL Server asynchrone Vorgänge unterstützt. Das ist die Fähigkeit, Rückgaben unverzüglich zu übermitteln, ohne den aufrufenden Thread zu blockieren.  

[Verwendung von Azure Active Directory](using-azure-active-directory.md)  
Erläutert neue Authentifizierungsmethoden, die in OLE DB Treiber 18.2.1 eingeführt wurden und über sicherere Standardeinstellungen verfügen und das Herstellen einer Verbindung mit einer Instanz von Azure SQL-Datenbank mithilfe einer Verbund Identität ermöglichen.

 [Verwenden von Multiple Active Result Sets &#40;MARS&#41;](../../oledb/features/using-multiple-active-result-sets-mars.md)  
 Erläutert, wie OLE DB Treiber für SQL Server Multiple Active Result Sets (Mars) unterstützt. MARS ermöglichen es Ihnen, mehrere Resultsets mithilfe einer einzigen Datenbankverbindung auszuführen und zu empfangen.  
  
 [Verwenden von XML-Datentypen](../../oledb/features/using-xml-data-types.md)  
 Erläutert, auf welche Weise der OLE DB-Treiber für SQL Server den XML-Datentyp unterstützt. Dieser XML-basierte Datentyp kann als Spaltentyp, Variablentyp, Parametertyp oder Funktionsrückgabetyp verwendet werden.  
  
 [Verwenden von benutzerdefinierten Typen](../../oledb/features/using-user-defined-types.md)  
 Erläutert, auf welche Weise der OLE DB-Treiber für SQL Server benutzerdefinierte Typen (User-Defined Types, UDT) unterstützt. Sie erweitern das SQL-Typsystem, indem sie es ermöglichen, Objekte und benutzerdefinierte Datenstrukturen in einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank zu speichern.  
  
 [Verwenden von Datentypen mit umfangreichen Werten](../../oledb/features/using-large-value-types.md)  
 Erläutert, wie OLE DB Treiber für SQL Server Datentypen mit hohen Werten unterstützt, bei denen es sich um LOB-Datentypen (Large Object) handelt.  
  
 [Programmgesteuertes Ändern von Kennwörtern](../../oledb/features/changing-passwords-programmatically.md)  
 Erläutert, auf welche Weise der OLE DB-Treiber für SQL Server die Handhabung abgelaufener Kennwörter unterstützt und es ermöglicht, dass Kennwörter jetzt auf dem Client ohne Eingreifen eines Administrators geändert werden können.  
  
 [Arbeiten mit der Momentaufnahmeisolation](../../oledb/features/working-with-snapshot-isolation.md)  
 Erläutert, auf welche Weise der OLE DB-Treiber für SQL Server die Verbesserung der Zeilenversionsverwaltung unterstützt. Diese erhöht die Datenbankleistung, indem Leser-/Schreiberblockierungsszenarios vermieden werden.  
  
 [Arbeiten mit Abfragebenachrichtigungen](../../oledb/features/working-with-query-notifications.md)  
 Erläutert, wie OLE DB Treiber für SQL Server die Consumer-Benachrichtigung bei der Rowsetänderung unterstützt.  
  
 [Durchführen von Massenkopiervorgängen](../../oledb/features/performing-bulk-copy-operations.md)  
 Erläutert, auf welche Weise der OLE DB-Treiber für SQL Server Massenkopiervorgänge unterstützt, die das Übermitteln großer Datenmengen in eine/aus einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Tabelle oder -Sicht ermöglichen.  
  
 [Verwenden von Verschlüsselung ohne Überprüfung](../../oledb/features/using-encryption-without-validation.md)  
 Erläutert, wie OLE DB Treiber für SQL Server verwendet wird, um Daten zu verschlüsseln, die an den Server gesendet werden, ohne dass das Zertifikat überprüft wird.  
  
 [Tabellenwertparameter &#40;OLE DB-Treiber für SQL Server&#41;](../../oledb/features/table-valued-parameters-oledb-driver-for-sql-server.md)  
 Erläutert OLE DB Treiber für die SQL Server Unterstützung für Tabellenwert Parameter.  
  
 [Große benutzerdefinierte CLR-Typen](../../oledb/features/large-clr-user-defined-types.md)  
 Erläutert die Unterstützung für große CLR-benutzerdefinierte Typen (Common Language Runtime).  
  
 [FILESTREAM-Unterstützung](../../oledb/features/filestream-support.md)  
 Erläutert OLE DB Treiber für die SQL Server Unterstützung für die erweiterte FILESTREAM-Funktion.  
  
 [Unterstützung von Dienstprinzipalnamen &#40;SPN&#41; in Clientverbindungen](../../oledb/features/service-principal-name-spn-support-in-client-connections.md)  
 Erläutert, auf welche Weise die Unterstützung für Dienstprinzipalnamen (Service Principal Names, SPN) erweitert wurde, damit die gegenseitige Authentifizierung über alle Protokolle hinweg möglich ist.  
  
 [Unterstützung von Spalten mit geringer Dichte im OLE DB-Treiber für SQL Server](../../oledb/features/sparse-columns-support-in-oledb-driver-for-sql-server.md)  
 Erläutert OLE DB Treiber für die SQL Server Unterstützung für sparsespalten.  
  
 [Verbesserungen bei Datum und Zeit](../../oledb/features/date-and-time-improvements.md)  
 Erläutert die Unterstützung, die OLE DB Treiber für SQL Server für die Datums-und Uhrzeit Datentypen hinzugefügt wurde.  
  
 [Metadatenermittlung](../../oledb/features/metadata-discovery.md)  
 Erläutert Verbesserungen der Metadatenermittlung in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].  
  
 [UTF-16-Unterstützung im OLE DB-Treiber für SQL Server (OLE DB)](../../oledb/features/utf-16-support-in-oledb-driver-for-sql-server.md)  
 Erläutert eine mit [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] eingeführte Verhaltensänderung. Wenn Sie einen Puffer mit fester Länge beim Binden eines Spaltenergebnisses oder eines Ausgabeparameters angeben, wenn das Zeichen **wchar**, das vor dem abschließenden Zeichen in den Puffer geschrieben wird, ein hoher Codepunkt eines Ersatzzeichenpaars ist, und wenn das nächste Zeichen **wchar** ein niedriger Codepunkt ist, fügt der OLE DB-Treiber für SQL Server den hohen Codepunkt nicht zum Puffer hinzu.  
 
 [UTF-8-Unterstützung im OLE DB-Treiber für SQL Server](../../oledb/features/utf-8-support-in-oledb-driver-for-sql-server.md)  
 Erläutert die Unterstützung für UTF-8-Server Codierung und Konfigurations Vorkehrungen, die Benutzer bei der Arbeit mit UTF-8-codierten Daten treffen sollten.
  
 [OLE DB-Treiber für SQL Server-Unterstützung für Hochverfügbarkeit, Notfallwiederherstellung](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)  
 Erläutert, wie die Anwendung konfiguriert werden kann, um von den Funktionen für Hochverfügbarkeit und Notfallwiederherstellung zu profitieren, die in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] hinzugefügt wurden.  
  
 [Zugreifen auf Diagnoseinformationen im Protokoll der erweiterten Ereignisse](../../oledb/features/accessing-diagnostic-information-in-the-extended-events-log.md)  
 Erläutert Erweiterungen zu OLE DB-Treiber für SQL Server und Datenablaufverfolgung, die Ihnen Zugriff auf Diagnoseinformationen im Ringpuffer und XEvents-Protokoll geben.  
  
 [OLE DB-Treiber für SQL Server-Unterstützung für LocalDB](../../oledb/features/oledb-driver-for-sql-server-support-for-localdb.md)  
 Erläutert OLE DB Treiber für die SQL Server-Unterstützung der localdb-Funktion.  
  
## <a name="see-also"></a>Weitere Informationen  
 [OLE DB-Treiber für SQL Server](../../oledb/oledb-driver-for-sql-server.md)      
 [Vorgehensweisen für OLE DB](../../oledb/ole-db-how-to/ole-db-how-to-topics.md)   
 [Installation des OLE DB-Treibers für SQL Server](../../oledb/applications/installing-oledb-driver-for-sql-server.md)  
  
  
