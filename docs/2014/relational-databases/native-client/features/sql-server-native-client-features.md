---
title: SQL Server Native Client-Funktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MDAC [SQL Server]
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- SQLNCLI, about SQL Server Native Client
- data access [SQL Server Native Client], features
ms.assetid: 7bb32865-5afb-41ab-98b4-3fa545ee8953
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 093d40734b88cc370e0c08a8f9a8b86312409e6b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63225565"
---
# <a name="sql-server-native-client-features"></a>SQL Server Native Client-Funktionen
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client macht nicht nur Funktionen der Windows (früher Microsoft) Data Access Components (WDAC) verfügbar, sondern implementiert zudem viele weitere Funktionen, um die Funktionalität von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] verfügbar zu machen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Verhaltensänderungen des ODBC-Treibers bei der Behandlung von Zeichenkonvertierungen](odbc-driver-behavior-change-when-handling-character-conversions.md)  
 Erläutert das geänderte Verhalten ab [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012 Native Client.  
  
 [Verwenden der Datenbankspiegelung](using-database-mirroring.md)  
 Erläutert, wie [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client unterstützt die Verwendung von gespiegelten Datenbanken, die Möglichkeit, eine Kopie, oder auch Spiegelbild, der beibehalten wird eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Datenbank auf einem Standbyserver.  
  
 [Ausführen asynchroner Vorgänge](performing-asynchronous-operations.md)  
 Erläutert, auf welche Weise [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client asynchrone Vorgänge unterstützt. Das ist die Fähigkeit, Rückgaben unverzüglich zu übermitteln, ohne den aufrufenden Thread zu blockieren.  
  
 [Verwenden von Multiple Active Result Sets &#40;MARS&#41;](using-multiple-active-result-sets-mars.md)  
 Erläutert, auf welche Weise [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client Multiple Active Result Sets (MARS) unterstützt. MARS ermöglichen es Ihnen, mehrere Resultsets mithilfe einer einzigen Datenbankverbindung auszuführen und zu empfangen.  
  
 [Verwenden von XML-Datentypen](using-xml-data-types.md)  
 Erläutert, auf welche Weise [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client den XML-Datentyp unterstützt. Dieser XML-basierte Datentyp kann als Spaltentyp, Variablentyp, Parametertyp oder Funktionsrückgabetyp verwendet werden.  
  
 [Verwenden von benutzerdefinierten Typen](using-user-defined-types.md)  
 Erläutert, wie [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client unterstützt benutzerdefinierte Typen (UDT), die die SQL-Typsystem erweitert, sodass Sie zum Speichern von Objekten und benutzerdefinierte Datenstrukturen in einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Datenbank.  
  
 [Verwenden von Datentypen mit umfangreichen Werten](using-large-value-types.md)  
 Erläutert, auf welche Weise [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client Datentypen mit großen Werten unterstützt, bei denen es sich um LOB-Datentypen handelt.  
  
 [Programmgesteuertes Ändern von Kennwörtern](changing-passwords-programmatically.md)  
 Erläutert, auf welche Weise [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client die Handhabung abgelaufener Kennwörter unterstützt und es ermöglicht, dass Kennwörter jetzt auf dem Client ohne Eingreifen eines Administrators geändert werden können.  
  
 [Arbeiten mit der Momentaufnahmeisolation](working-with-snapshot-isolation.md)  
 Erläutert, auf welche Weise [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client die Verbesserung der Zeilenversionsverwaltung unterstützt. Sie erhöht die Datenbankleistung, indem Leser-/Schreiberblockierungsszenarien vermieden werden.  
  
 [Arbeiten mit Abfragebenachrichtigungen](working-with-query-notifications.md)  
 Erläutert, auf welche Weise [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client die Benachrichtigung von Consumern bei Rowsetänderungen unterstützt.  
  
 [Durchführen von Massenkopiervorgängen](performing-bulk-copy-operations.md)  
 Erläutert, wie [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client unterstützt Massenkopiervorgänge, die ermöglichen, die Übertragung großer Datenmengen in oder aus einem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Tabelle oder Sicht.  
  
 [Verwenden von Verschlüsselung ohne Überprüfung](using-encryption-without-validation.md)  
 Erläutert, wie [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client zur Verschlüsselung an den Server gesendeter Daten ohne Prüfung des Zertifikats verwendet wird.  
  
 [Tabellenwertparameter &#40;SQL Server Native Client&#41;](table-valued-parameters-sql-server-native-client.md)  
 Erläutert, auf welche Weise [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client die Tabellenwertparameter unterstützt.  
  
 [Große benutzerdefinierte CLR-Typen](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
 Erläutert die Unterstützung für große CLR-benutzerdefinierte Typen (Common Language Runtime).  
  
 [FILESTREAM-Unterstützung](filestream-support.md)  
 Erläutert [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-Unterstützung für die verbesserte Funktion FILESTREAM.  
  
 [Unterstützung von Dienstprinzipalnamen &#40;SPN&#41; in Clientverbindungen](service-principal-name-spn-support-in-client-connections.md)  
 Erläutert, auf welche Weise die Unterstützung für Dienstprinzipalnamen (Service Principal Names, SPN) erweitert wurde, damit die gegenseitige Authentifizierung über alle Protokolle hinweg möglich ist.  
  
 [Unterstützung für Spalten mit geringer Dichte in SQL Server Native Client](sparse-columns-support-in-sql-server-native-client.md)  
 Erläutert, auf welche Weise [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client Sparsespalten unterstützt.  
  
 [Verbesserungen bei Datum und Zeit](date-and-time-improvements.md)  
 Erläutert die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client hinzugefügte Unterstützung für die Datums- und Uhrzeitdatentypen.  
  
 [Metadatenermittlung](metadata-discovery.md)  
 Erläutert Verbesserungen der Metadatenermittlung in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].  
  
 [Unterstützung für UTF-16 in SQL Server Native Client 11.0](utf-16-support-in-sql-server-native-client-11-0.md)  
 Erläutert eine mit [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] eingeführte Verhaltensänderung. Ab [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client wird dem Puffer kein hoher Ersatzzeichencodepunkt hinzugefügt, wenn Sie beim Binden eines Spaltenergebnisses oder Ausgabeparameters einen Puffer fester Länge übergeben und das vor dem abschließenden Zeichen in den Puffer geschriebene `wchar`-Zeichen ein hoher Ersatzzeichencodepunkt eines Ersatzzeichenpaars und das nächste `wchar`-Zeichen ein niedriger Ersatzzeichencodepunkt ist.  
  
 [SQL Server Native Client-Unterstützung für hohe Verfügbarkeit, Notfallwiederherstellung](sql-server-native-client-support-for-high-availability-disaster-recovery.md)  
 Erläutert, wie die Anwendung konfiguriert werden kann, um von den Funktionen für Hochverfügbarkeit und Notfallwiederherstellung zu profitieren, die in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] hinzugefügt wurden.  
  
 [Zugreifen auf Diagnoseinformationen im Protokoll der erweiterten Ereignisse](accessing-diagnostic-information-in-the-extended-events-log.md)  
 Erläutert Erweiterungen zu [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client und -Datenablaufverfolgung, die Ihnen Zugriff auf Diagnoseinformationen im Ringpuffer und XEvents-Protokoll geben.  
  
 [SQL Server Native Client-Unterstützung für LocalDB](sql-server-native-client-support-for-localdb.md)  
 Erläutert, auf welche Weise [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client die verbesserte LocalDB-Funktion unterstützt.  
  
## <a name="see-also"></a>Siehe auch  
 [Programmierung für SQL Server Native Client](../sql-server-native-client-programming.md)   
 [Vorgehensweisen zu ODBC](../../native-client-odbc-how-to/odbc-how-to-topics.md)   
 [Vorgehensweisen für OLE DB](../../native-client-ole-db-how-to/ole-db-how-to-topics.md)   
 [Installieren von SQL Server Native Client](../applications/installing-sql-server-native-client.md)  
  
  
