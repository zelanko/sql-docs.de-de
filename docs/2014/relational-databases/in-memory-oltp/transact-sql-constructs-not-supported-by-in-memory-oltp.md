---
title: Von In-Memory OLTP nicht unterstützte Transact-SQL-Konstrukte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: e3f8009c-319d-4d7b-8993-828e55ccde11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dda74f247f9899b9e0a23d43143a5031574d8c13
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52541234"
---
# <a name="transact-sql-constructs-not-supported-by-in-memory-oltp"></a>Von In-Memory OLTP nicht unterstützte Transact-SQL-Konstrukte
  Speicheroptimierte Tabellen und systemintern kompilierte gespeicherte Prozeduren unterstützen nicht die vollständige [!INCLUDE[tsql](../../includes/tsql-md.md)]-Oberfläche, die von datenträgerbasierten Tabellen und interpretierten gespeicherten [!INCLUDE[tsql](../../includes/tsql-md.md)]-Prozeduren unterstützt wird. Wird versucht, eine der nicht unterstützten Funktionen zu verwenden, gibt der Server einen Fehler zurück.  
  
 Im Text der Fehlermeldung werden der Typ der [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisung (z. B. Funktion, Vorgang, Option) sowie der Name der Funktion oder des [!INCLUDE[tsql](../../includes/tsql-md.md)] -Schlüsselworts angegeben. Die meisten nicht unterstützten Funktionen geben den Fehler 10794 zurück, wobei der Fehlermeldungstext die nicht unterstützte Funktion angibt. In den folgenden Tabellen werden die möglichen [!INCLUDE[tsql](../../includes/tsql-md.md)] -Funktionen und -Schlüsselwörter im Meldungstext des Fehlers sowie die Korrekturmaßnahmen zum Beheben des Fehlers aufgelistet.  
  
 Weitere Informationen zu unterstützten Funktionen für speicheroptimierte Tabellen und systemintern kompilierte gespeicherte Prozeduren finden Sie unter:  
  
-   [Migrationsprobleme bei nativ kompilierten gespeicherten Prozeduren](migration-issues-for-natively-compiled-stored-procedures.md)  
  
-   [Transact-SQL-Unterstützung für In-Memory-OLTP](transact-sql-support-for-in-memory-oltp.md)  
  
-   [Unterstützte SQL Server-Features](unsupported-sql-server-features-for-in-memory-oltp.md)  
  
-   [Nativ kompilierte gespeicherte Prozeduren](../in-memory-oltp/natively-compiled-stored-procedures.md)  
  
## <a name="databases-that-use-in-memory-oltp"></a>Datenbanken, die In-Memory OLTP verwenden  
 In der folgenden Tabelle werden die [!INCLUDE[tsql](../../includes/tsql-md.md)]-Funktionen und -Schlüsselwörter aufgelistet, die im Meldungstext eines Fehlers angezeigt werden können, der eine In-Memory OLTP-Datenbank betrifft.  
  
|Typ|Name|Lösung|  
|----------|----------|----------------|  
|Option|AUTO_CLOSE|Die Datenbankoption AUTO_CLOSE=ON wird für Datenbanken, die eine MEMORY_OPTIMIZED_DATA-Dateigruppe enthalten, nicht unterstützt.|  
|Option|ATTACH_REBUILD_LOG|Die CREATE-Datenbankoption ATTACH_REBUILD_LOG wird für Datenbanken, die eine MEMORY_OPTIMIZED_DATA-Dateigruppe enthalten, nicht unterstützt.|  
|Funktion|DATABASE SNAPSHOT|Das Erstellen von Datenbankmomentaufnahmen wird für Datenbanken, die eine MEMORY_OPTIMIZED_DATA-Dateigruppe enthalten, nicht unterstützt.|  
|Funktion|Replikation mithilfe der sync_method "database snapshot" oder "database snapshot character"|Replikation mithilfe der sync_method "database snapshot" oder "database snapshot character" wird für Datenbanken, die eine MEMORY_OPTIMIZED_DATA-Dateigruppe enthalten, nicht unterstützt.|  
|Funktion|DBCC CHECKDB<br /><br /> DBCC CHECKTABLE|DBCC CHECKDB lässt die speicheroptimierten Tabellen in der Datenbank aus.<br /><br /> DBCC CHECKTABLE schlägt für speicheroptimierte Tabellen fehl.|  
  
## <a name="memory-optimized-tables"></a>Speicheroptimierte Tabellen  
 In der folgenden Tabelle werden die möglichen [!INCLUDE[tsql](../../includes/tsql-md.md)]-Funktionen und -Schlüsselwörter im Meldungstext eines Fehlers mit einer speicheroptimierten Tabelle sowie die Korrekturmaßnahmen zum Beheben des Fehlers aufgelistet.  
  
|Typ|Name|Lösung|  
|----------|----------|----------------|  
|Funktion|ON|Speicheroptimierte Tabellen können nicht in einer Dateigruppe oder einem Partitionsschema platziert werden. Entfernen Sie die ON-Klausel aus der `CREATE TABLE`-Anweisung.|  
|Datentyp|*Datentypname*|Der angegebene Datentyp wird nicht unterstützt. Ersetzen Sie den Typ durch einen der unterstützten Datentypen. Weitere Informationen finden Sie unter [Supported Data Types](supported-data-types-for-in-memory-oltp.md).|  
|Funktion|Berechnete Spalten|Berechnete Spalten werden für speicheroptimierte Tabellen nicht unterstützt. Entfernen Sie die berechneten Spalten aus der `CREATE TABLE`-Anweisung.|  
|Funktion|Replikation|Replikation wird für speicheroptimierte Tabellen nicht unterstützt.|  
|Funktion|FILESTREAM|Die FILESTREAM-Speicherung wird für Spalten von speicheroptimierten Tabellen nicht unterstützt. Entfernen Sie das `FILESTREAM`-Schlüsselwort aus der Spaltendefinition.|  
|Funktion|SPARSE|Spalten aus speicheroptimierten Tabellen können nicht als SPARSE definiert werden. Entfernen Sie das `SPARSE`-Schlüsselwort aus der Spaltendefinition.|  
|Funktion|ROWGUIDCOL|Die ROWGUIDCOL-Option wird für Spalten von speicheroptimierten Tabellen nicht unterstützt. Entfernen Sie das `ROWGUIDCOL`-Schlüsselwort aus der Spaltendefinition.|  
|Funktion|FOREIGN KEY|FOREIGN KEY-Einschränkungen werden für speicheroptimierte Tabellen nicht unterstützt. Entfernen Sie die Einschränkung aus der Tabellendefinition.<br /><br /> Informationen dazu, wie die fehlende Unterstützung für Einschränkungen gemindert werden kann, finden Sie unter [überprüfen Sie die Migration und Foreign Key-Einschränkungen](../../database-engine/migrating-check-and-foreign-key-constraints.md).|  
|Funktion|CHECK|CHECK-Einschränkungen werden für speicheroptimierte Tabellen nicht unterstützt. Entfernen Sie die Einschränkung aus der Tabellendefinition.<br /><br /> Informationen dazu, wie die fehlende Unterstützung für Einschränkungen gemindert werden kann, finden Sie unter [überprüfen Sie die Migration und Foreign Key-Einschränkungen](../../database-engine/migrating-check-and-foreign-key-constraints.md).|  
|Funktion|UNIQUE|UNIQUE-Einschränkungen werden für speicheroptimierte Tabellen nicht unterstützt. Entfernen Sie die Einschränkung aus der Tabellendefinition.<br /><br /> Informationen dazu, wie die fehlende Unterstützung für Einschränkungen gemindert werden kann, finden Sie unter [überprüfen Sie die Migration und Foreign Key-Einschränkungen](../../database-engine/migrating-check-and-foreign-key-constraints.md).|  
|Funktion|COLUMNSTORE|COLUMNSTORE-Indizes werden nicht mit speicheroptimierten Tabellen unterstützt. Geben Sie stattdessen einen NONCLUSTERED-Index oder NONCLUSTERED HASH-Index an.|  
|Funktion|Gruppierter Index|Geben Sie einen nicht gruppierten Index an. Bei einem Primärschlüsselindex müssen Sie `PRIMARY KEY NONCLUSTERED [HASH]` angeben.|  
|Funktion|Nicht-1252-Codepage|Spalten in speicheroptimierten Tabellen mit den Datentypen `char` und `varchar` müssen Codepage 1252 verwenden. Verwenden Sie n(var)char anstelle von (var)char, oder verwenden Sie eine Sortierung mit Codepage 1252 (z. B. Latin1_General_BIN2). Weitere Informationen finden Sie unter [Collations and Code Pages](../../database-engine/collations-and-code-pages.md).|  
|Funktion|DDL innerhalb von Transaktionen|Speicheroptimierte Tabellen und systemintern kompilierte gespeicherte Prozeduren können nicht im Rahmen einer Benutzertransaktion erstellt oder gelöscht werden. Starten Sie keine Transaktion, und vergewissern Sie sich, dass die Sitzungseinstellung IMPLICIT_TRANSACTIONS auf OFF festgelegt ist, bevor Sie die CREATE-Anweisung oder die DROP-Anweisung ausführen.|  
|Funktion|DDL-Trigger|Speicheroptimierte Tabellen und systemintern kompilierte gespeicherte Prozeduren können nicht erstellt oder gelöscht werden, wenn ein Server- oder Datenbanktrigger für den betreffenden DDL-Vorgang vorhanden ist. Entfernen Sie die Server- und Datenbanktrigger für CREATE/DROP TABLE und CREATE/DROP PROCEDURE.|  
|Funktion|EVENT NOTIFICATION|Speicheroptimierte Tabellen und systemintern kompilierte gespeicherte Prozeduren können nicht erstellt oder gelöscht werden, wenn eine Server- oder Datenbank-Ereignisbenachrichtigung für den betreffenden DDL-Vorgang vorhanden ist. Entfernen Sie die Server- und Datenbankereignisbenachrichtigungen in CREATE TABLE bzw. DROP TABLE und CREATE PROCEDURE bzw. DROP PROCEDURE.|  
|Funktion|FileTable|Speicheroptimierte Tabellen können nicht als File-Tabellen erstellt werden. Entfernen Sie das Argument `AS FileTable` aus der `CREATE TABLE`-Anweisung.|  
|Vorgang|Update der Primärschlüsselspalten|Primärschlüsselspalten in speicheroptimierten Tabellen und Tabellentypen können nicht aktualisiert werden. Wenn der Primärschlüssel aktualisiert werden muss, löschen Sie die alte Zeile, und fügen Sie die neue Zeile mit dem aktualisierten Primärschlüssel ein.|  
|Vorgang|CREATE INDEX|Indizes in speicheroptimierten Tabellen müssen inline mit der `CREATE TABLE`-Anweisung angegeben werden. Um einer speicheroptimierten Tabelle einen Index hinzuzufügen, löschen Sie die Tabelle, und erstellen Sie sie einschließlich der neuen Indexspezifikation neu.|  
|Vorgang|ALTER TABLE|Das Ändern von speicheroptimierten Tabellen wird nicht unterstützt. Löschen Sie die Tabelle, und erstellen Sie sie mit der aktualisierten Tabellendefinition neu.|  
|Vorgang|CREATE FULLTEXT INDEX|Volltextindizes werden für speicheroptimierte Tabellen nicht unterstützt.|  
|Vorgang|Schemaänderung|Speicheroptimierte Tabellen und systemintern kompilierte gespeicherte Prozeduren unterstützen keine Schemaänderungen wie `sp_rename`.<br /><br /> Durch den Versuch, Schemaänderungen wie das Umbenennen einer Tabelle vorzunehmen, wird der Fehler 12320 generiert. Vorgänge, für die eine Änderung an der Schemaversion wie z. B. Umbenennen erforderlich sind, werden für speicheroptimierte Tabellen nicht unterstützt.<br /><br /> Löschen Sie zum Ändern des Schemas die Tabelle oder Prozedur, und erstellten Sie sie mit einer aktualisierten Definition neu.|  
|Vorgang|CREATE TRIGGER|Trigger für speicheroptimierte Tabellen werden nicht unterstützt.|  
|Vorgang|TRUNCATE TABLE|Der TRUNCATE-Vorgang wird für speicheroptimierte Tabellen nicht unterstützt. Um alle Zeilen aus einer Tabelle zu entfernen, löschen Sie alle Zeilen mit `DELETE FROM` *Tabelle* oder löschen und erneut erstellt.|  
|Vorgang|ALTER AUTHORIZATION|Das Ändern des Besitzers einer vorhandenen speicheroptimierten Tabelle oder systemintern kompilierten gespeicherten Prozedur wird nicht unterstützt. Löschen Sie die Tabelle oder die Prozedur, und erstellen Sie sie neu, um den Besitzer zu ändern.|  
|Vorgang|ALTER SCHEMA|Das Ändern des Schemas einer vorhandenen speicheroptimierten Tabelle oder systemintern kompilierten gespeicherten Prozedur wird nicht unterstützt. Löschen Sie die Tabelle oder die Prozedur, und erstellen Sie sie neu, um das Schema zu ändern.|  
|Vorgang|DBCC CHECKTABLE|DBCC CHECKTABLE wird für speicheroptimierte Tabellen nicht unterstützt.|  
|Funktion|ANSI_PADDING OFF|Die `ANSI_PADDING`-Sitzungsoption muss beim Erstellen von speicheroptimierten Tabellen oder systemintern kompilierten gespeicherten Prozeduren auf ON festgelegt sein. Führen Sie `SET ANSI_PADDING ON` aus, bevor Sie die CREATE-Anweisung ausführen.|  
|Option|DATA_COMPRESSION|Die Datenkomprimierung wird für speicheroptimierte Tabellen nicht unterstützt. Entfernen Sie die Option aus der Tabellendefinition.|  
|Funktion|DTC|Auf speicheroptimierte Tabellen und systemintern kompilierte gespeicherte Prozeduren kann nicht aus verteilten Transaktionen zugegriffen werden. Verwenden Sie stattdessen SQL-Transaktionen.|  
|Funktion|Multiple Active Result Sets (MARS)|Multiple Active Result Sets (MARS) werden für speicheroptimierte Tabellen nicht unterstützt. Dieser Fehler kann auch auf die Verwendung eines Verbindungsservers hinweisen. Ein Verbindungsserver kann MARS verwenden. Verbindungsserver werden für speicheroptimierte Tabellen nicht unterstützt. Stattdessen müssen Sie eine direkte Verbindung mit dem Server und der Datenbank herstellen, die die speicheroptimierten Tabellen hostet.|  
|Vorgang|Speicheroptimierte Tabellen als Ziel von MERGE|Speicheroptimierte Tabellen können nicht das Ziel eines `MERGE`-Vorgangs sein. Verwenden Sie stattdessen die Anweisungen `INSERT`, `UPDATE` und `DELETE`.|  
  
## <a name="indexes-on-memory-optimized-tables"></a>Indizes für speicheroptimierte Tabellen  
 In der folgenden Tabelle werden die möglichen [!INCLUDE[tsql](../../includes/tsql-md.md)] -Funktionen und -Schlüsselwörter im Meldungstext eines Fehlers mit dem Index einer speicheroptimierten Tabelle sowie die Korrekturmaßnahmen zum Beheben des Fehlers aufgelistet.  
  
|Typ|Name|Lösung|  
|----------|----------|----------------|  
|Funktion|Gefilterter Index|Gefilterte Indizes werden nicht mit speicheroptimierten Tabellen unterstützt. Lassen Sie die `WHERE`-Klausel in der Indexspezifikation aus.|  
|Funktion|UNIQUE|Eindeutige Indizes werden für speicheroptimierte Tabellen nicht unterstützt. Entfernen Sie das Argument `UNIQUE` aus der Indexspezifikation.|  
|Funktion|Spalten, die NULL zulassen|Alle Spalten im Schlüssel eines Indexes für eine speicheroptimierte Tabelle müssen als `NOT NULL` angegeben werden. Schließen Sie die `NOT NULL`-Einschränkung für alle Spalten in die Indexschlüssel ein.|  
|Funktion|Nicht-BIN2-Sortierung|Alle Zeichenspalten im Schlüssel eines speicheroptimierten Indexes müssen mit einer BIN2-Sortierung deklariert werden. Legen Sie die Sortierung in der Spaltendefinition mit der `COLLATE`-Klausel fest. Weitere Informationen finden Sie unter [Collations and Code Pages](../../database-engine/collations-and-code-pages.md).|  
|Funktion|Eingeschlossene Spalten|Bei speicheroptimierten Tabellen müssen keine eingeschlossenen Spalten angegeben werden. Alle Spalten der speicheroptimierten Tabelle werden implizit in jeden speicheroptimierten Index eingeschlossen.|  
|Vorgang|ALTER INDEX|Das Ändern von Indizes für speicheroptimierte Tabellen wird nicht unterstützt. Löschen Sie stattdessen die Tabelle, und erstellen Sie sie mit der aktualisierten Indexspezifikation neu.|  
|Vorgang|DROP INDEX|Das Löschen von Indizes für speicheroptimierte Tabellen wird nicht unterstützt. Löschen Sie stattdessen die Tabelle, und erstellen Sie sie mit den gewünschten Indizes neu.|  
|Indexoption|*Indexoption*|Die angegebene Indexoption wird nicht für Indizes von speicheroptimierten Tabellen unterstützt. Entfernen Sie die Option aus der Indexspezifikation.|  
  
## <a name="nonclustered-hash-indexes"></a>Nicht gruppierte Hashindizes  
 In der folgenden Tabelle werden die möglichen [!INCLUDE[tsql](../../includes/tsql-md.md)] -Funktionen und -Schlüsselwörter im Meldungstext eines Fehlers mit einem nicht gruppierten Hashindex sowie die Korrekturmaßnahmen zum Beheben des Fehlers aufgelistet.  
  
|Typ|Name|Lösung|  
|----------|----------|----------------|  
|Option|ASC/DESC|Nicht gruppierte Hashindizes werden nicht sortiert. Entfernen Sie die Schlüsselwörter `ASC` und `DESC` aus der Indexschlüsselspezifikation.|  
  
## <a name="natively-compiled-stored-procedures"></a>Systemintern kompilierte gespeicherte Prozeduren  
 In der folgenden Tabelle werden die möglichen [!INCLUDE[tsql](../../includes/tsql-md.md)]-Funktionen und -Schlüsselwörter im Meldungstext eines Fehlers mit systemintern kompilierten gespeicherten Prozeduren sowie die Korrekturmaßnahmen zum Beheben des Fehlers aufgelistet.  
  
|Typ|Funktion|Lösung|  
|----------|-------------|----------------|  
|Funktion|Inline-Tabellenvariablen|Tabellentypen können nicht inline mit Variablendeklarationen deklariert werden. Tabellentypen müssen explizit mit einer `CREATE TYPE`-Anweisung deklariert werden.|  
|Funktion|Cursor|Cursor werden nicht von oder in systemintern kompilierten gespeicherten Prozeduren unterstützt.<br /><br /> – Wenn die Prozedur auf dem Client ausführen möchten, verwenden Sie RPC anstelle der Cursor-API. Vermeiden Sie bei ODBC die [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisung `EXECUTE`, und geben Sie stattdessen den Namen der Prozedur direkt an.<br /><br /> – Wenn die Prozedur aus einem [!INCLUDE[tsql](../../includes/tsql-md.md)] Batch oder einer anderen gespeicherten Prozedur, einen Cursor mit der systemintern kompilierten gespeicherten Prozedur verwenden.<br /><br /> – Wenn Sie eine systemintern kompilierte gespeicherte Prozedur erstellen, anstatt einen Cursor, verwenden Sie setbasierte Logik oder eine `WHILE` Schleife.|  
|Funktion|Nicht konstante Parameterstandardwerte|Beim Angeben von Standardwerten für Parameter für systemintern kompilierte gespeicherte Prozeduren müssen die Werte Konstanten sein. Entfernen Sie alle Platzhalter aus den Parameterdeklarationen.|  
|Funktion|EXTERNAL|CLR-gespeicherte Prozeduren können nicht systemintern kompiliert werden. Entfernen Sie entweder die Klausel AS EXTERNAL oder die Option NATIVE_COMPILATIONS aus der Anweisung CREATE PROCEDURE.|  
|Funktion|numbered_stored_procedures|Systemintern kompilierte gespeicherte Prozeduren dürfen nicht nummeriert sein. Entfernen Sie die `;` *Anzahl* aus der `CREATE PROCEDURE` Anweisung.|  
|Funktion|Mehrzeilige INSERT ... VALUES-Anweisungen|Das Einfügen mehrerer Zeilen mit derselben `INSERT`-Anweisung in einer systemintern kompilierten gespeicherten Prozedur ist nicht möglich. Erstellen Sie `INSERT`-Anweisungen für jede Zeile.|  
|Funktion|Allgemeine Tabellenausdrücke (CTEs)|Allgemeine Tabellenausdrücke (Common Table Expressions, CTE) werden in systemintern kompilierten gespeicherten Prozeduren nicht unterstützt. Schreiben Sie die Abfrage um.|  
|Funktion|Unterabfrage|Unterabfragen (geschachtelte Abfragen innerhalb einer anderen Abfrage) werden nicht unterstützt. Schreiben Sie die Abfrage um.|  
|Funktion|COMPUTE|Die `COMPUTE`-Klausel wird nicht unterstützt. Entfernen Sie sie aus der Abfrage.|  
|Funktion|SELECT INTO|Die `INTO`-Klausel wird mit der `SELECT`-Anweisung nicht unterstützt. Schreiben Sie die Abfrage als `INSERT INTO` *Tabelle*`SELECT`.|  
|Funktion|OUTPUT|Die `OUTPUT`-Klausel wird nicht unterstützt. Entfernen Sie sie aus der Abfrage.|  
|Funktion|Unvollständige Einfügespaltenliste|In `INSERT`-Anweisungen müssen Werte für alle Spalten in der Tabelle angegeben werden.|  
|Funktion|*Funktion*|Die integrierte Funktion wird in systemintern kompilierten gespeicherten Prozeduren nicht unterstützt. Entfernen Sie die Funktion aus der gespeicherten Prozedur. Weitere Informationen zu unterstützten integrierten Funktionen finden Sie unter [Natively Compiled Stored Procedures](../in-memory-oltp/natively-compiled-stored-procedures.md).|  
|Funktion|CASE|Die `CASE`-Anweisung wird nicht in Abfragen innerhalb von systemintern kompilierten gespeicherten Prozeduren unterstützt. Erstellen Sie Abfragen für jeden einzelnen Fall. Weitere Informationen finden Sie unter [Implementieren einer CASE-Anweisung](implementing-a-case-expression-in-a-natively-compiled-stored-procedure.md).|  
|Funktion|benutzerdefinierte Funktionen|Benutzerdefinierte Funktionen können nicht in systemintern kompilierten gespeicherten Prozeduren verwendet werden. Entfernen Sie den Verweis auf die Funktion aus der Prozedurdefinition.|  
|Funktion|Benutzerdefinierte Aggregate|Benutzerdefinierte Aggregatfunktionen können nicht in systemintern kompilierten gespeicherten Prozeduren verwendet werden. Entfernen Sie den Verweis auf die Funktion aus der Prozedur.|  
|Funktion|Metadaten des Durchsuchenmodus|Systemintern kompilierte gespeicherte Prozeduren unterstützen keine Metadaten des Durchsuchenmodus. Stellen Sie sicher, dass die `NO_BROWSETABLE`-Sitzungsoption auf OFF festgelegt ist.|  
|Funktion|DELETE mit FROM-Klausel|Die `FROM`-Klausel wird für `DELETE`-Anweisungen mit einer Tabellenquelle in systemintern kompilierten gespeicherten Prozeduren nicht unterstützt.<br /><br /> `DELETE` wird mit der `FROM`-Klausel unterstützt, wenn der Vorgang die Tabelle angibt, aus der Daten gelöscht werden sollen.|  
|Funktion|UPDATE mit FROM-Klausel|Die `FROM`-Klausel wird nicht für `UPDATE`-Anweisungen in systemintern kompilierten gespeicherten Prozeduren unterstützt.|  
|Funktion|Temporäre Prozeduren|Temporäre gespeicherte Prozeduren können nicht systemintern kompiliert werden. Erstellen Sie entweder eine dauerhafte systemintern kompilierte gespeicherte Prozedur oder eine als temporär interpretierte gespeicherte [!INCLUDE[tsql](../../includes/tsql-md.md)] -Prozedur.|  
|Isolationsstufe|READ UNCOMMITTED|Die Isolationsstufe READ UNCOMMITTED wird für systemintern kompilierte gespeicherte Prozeduren nicht unterstützt. Verwenden Sie eine unterstützte Isolationsstufe, beispielsweise SNAPSHOT.|  
|Isolationsstufe|READ COMMITTED|Die Isolationsstufe READ UNCOMMITTED wird für systemintern kompilierte gespeicherte Prozeduren nicht unterstützt. Verwenden Sie eine unterstützte Isolationsstufe, beispielsweise SNAPSHOT.|  
|Funktion|Temporäre Tabellen|Tabellen in tempdb können nicht in systemintern kompilierten gespeicherten Prozeduren verwendet werden. Verwenden Sie stattdessen eine Tabellenvariable oder eine speicheroptimierte Tabelle mit DURABILITY=SCHEMA_ONLY.|  
|Funktion|MARS|Multiple Active Result Sets (MARS) wird für systemintern kompilierte gespeicherte Prozeduren nicht unterstützt. Dieser Fehler kann auch auf die Verwendung eines Verbindungsservers hinweisen. Ein Verbindungsserver kann MARS verwenden. Verbindungsserver werden bei systemintern kompilierten gespeicherten Prozeduren nicht unterstützt. Stattdessen müssen Sie eine direkte Verbindung mit dem Server und der Datenbank herstellen, die die systemintern kompilierten gespeicherten Prozeduren hostet.|  
|Funktion|DTC|Auf speicheroptimierte Tabellen und systemintern kompilierte gespeicherte Prozeduren kann nicht aus verteilten Transaktionen zugegriffen werden. Verwenden Sie stattdessen SQL-Transaktionen.|  
|Funktion|Nicht-BIN2-Sortierung|Vergleichen, Sortieren und andere Vorgänge für Zeichenfolgen in systemintern kompilierten gespeicherten Prozeduren erfordern eine BIN2-Sortierung. Geben Sie die COLLATE-Klausel an, oder verwenden Sie Spalten und Variablen mit einer entsprechenden Sortierung. Weitere Informationen finden Sie unter [Collations and Code Pages](../../database-engine/collations-and-code-pages.md).|  
|Funktion|Abschneiden von Zeichenfolgen mit SC-Sortierung.|Zeichenfolgen mit einer `_SC`-Sortierung verwenden die UTF-16-Codierung. Die Konvertierung eines n(var)char-Werts in einen n(var)char-Wert mit einer gekürzten Länge involviert das Abschneiden. Dies wird für UTF-16-Werte in systemintern kompilierten gespeicherten Prozeduren nicht unterstützt. Vermeiden Sie das Abschneiden von UTF-16-Zeichenfolgen.|  
|Funktion|EXECUTE WITH RECOMPILE|Die `WITH RECOMPILE`-Option wird für systemintern kompilierte gespeicherte Prozeduren nicht unterstützt.|  
|Funktion|LEN und SUBSTRING mit einem Argument in einer SC-Sortierung|Zeichenfolgen mit einer _SC-Sortierung verwenden die UTF-16-Codierung. Wenn die integrierten Funktionen LEN und SUBSTRING innerhalb von systemintern kompilierten gespeicherten Prozeduren verwendet werden, wird die UTF-16-Codierung nicht unterstützt. Verwenden Sie eine andere Sortierung oder vermeiden Sie die Verwendung dieser Funktionen.|  
|Funktion|Ausführung von der dedizierten Administratorverbindung.|Systemintern kompilierte gespeicherte Prozeduren können nicht aus der dedizierten Administratorverbindung (DAC) ausgeführt werden. Verwenden Sie stattdessen eine reguläre Verbindung.|  
|Vorgang|ALTER PROCEDURE|Systemintern kompilierte gespeicherte Prozeduren können nicht geändert werden. Löschen Sie zum Ändern der Prozedurdefinition die gespeicherte Prozedur, und erstellen Sie sie neu.|  
|Vorgang|Sicherungspunkt|Systemintern kompilierte gespeicherte Prozeduren können nicht aus Transaktionen aufgerufen werden, die über einen aktiven Sicherungspunkt verfügen. Entfernen Sie den Sicherungspunkt aus der Transaktion.|  
|Vorgang|ALTER AUTHORIZATION|Das Ändern des Besitzers einer vorhandenen speicheroptimierten Tabelle oder systemintern kompilierten gespeicherten Prozedur wird nicht unterstützt. Löschen Sie die Tabelle oder die Prozedur, und erstellen Sie sie neu, um den Besitzer zu ändern.|  
|Operator|OPENROWSET|Dieser Operator wird nicht unterstützt. Entfernen Sie `OPENROWSET` aus der systemintern kompilierten gespeicherten Prozedur.|  
|Operator|OPENQUERY|Dieser Operator wird nicht unterstützt. Entfernen Sie `OPENQUERY` aus der systemintern kompilierten gespeicherten Prozedur.|  
|Operator|OPENDATASOURCE|Dieser Operator wird nicht unterstützt. Entfernen Sie `OPENDATASOURCE` aus der systemintern kompilierten gespeicherten Prozedur.|  
|Operator|OPENXML|Dieser Operator wird nicht unterstützt. Entfernen Sie `OPENXML` aus der systemintern kompilierten gespeicherten Prozedur.|  
|Operator|CONTAINSTABLE|Dieser Operator wird nicht unterstützt. Entfernen Sie `CONTAINSTABLE` aus der systemintern kompilierten gespeicherten Prozedur.|  
|Operator|FREETEXTTABLE|Dieser Operator wird nicht unterstützt. Entfernen Sie `FREETEXTTABLE` aus der systemintern kompilierten gespeicherten Prozedur.|  
|Funktion|Tabellenwertfunktionen|Auf Tabellenwertfunktionen kann nicht aus systemintern kompilierten gespeicherten Prozeduren verwiesen werden. Eine mögliche Lösung für diese Einschränkung besteht darin, die Logik in den Tabellenwertfunktionen dem Prozedurtext hinzuzufügen.|  
|Operator|CHANGETABLE|Dieser Operator wird nicht unterstützt. Entfernen Sie `CHANGETABLE` aus der systemintern kompilierten gespeicherten Prozedur.|  
|Operator|GOTO|Dieser Operator wird nicht unterstützt. Verwenden Sie andere prozedurale Konstrukte wie WHILE.|  
|Operator|EXECUTE, INSERT EXEC|Das Schachteln von systemintern kompilierten gespeicherten Prozeduren wird nicht unterstützt. Die erforderlichen Operationen können inline als Teil der Definition der gespeicherten Prozedur angegeben werden.|  
|Operator|OFFSET|Dieser Operator wird nicht unterstützt. Entfernen Sie `OFFSET` aus der systemintern kompilierten gespeicherten Prozedur.|  
|Operator|UNION|Dieser Operator wird nicht unterstützt. Entfernen Sie `UNION` aus der systemintern kompilierten gespeicherten Prozedur. Mehrere Resultsets können mithilfe einer Tabellenvariablen in einem einzigen Resultset kombiniert werden.|  
|Operator|INTERSECT|Dieser Operator wird nicht unterstützt. Entfernen Sie `INTERSECT` aus der systemintern kompilierten gespeicherten Prozedur. In einigen Fällen kann ein INNER JOIN verwendet werden, um dasselbe Ergebnis zu erhalten.|  
|Operator|EXCEPT|Dieser Operator wird nicht unterstützt. Entfernen Sie `EXCEPT` aus der systemintern kompilierten gespeicherten Prozedur.|  
|Operator|OUTER JOIN|Dieser Operator wird nicht unterstützt. Entfernen Sie `OUTER JOIN` aus der systemintern kompilierten gespeicherten Prozedur. Weitere Informationen finden Sie unter [Implementieren eines äußeren Join](implementing-an-outer-join.md).|  
|Operator|APPLY|Dieser Operator wird nicht unterstützt. Entfernen Sie `APPLY` aus der systemintern kompilierten gespeicherten Prozedur.|  
|Operator|PIVOT|Dieser Operator wird nicht unterstützt. Entfernen Sie `PIVOT` aus der systemintern kompilierten gespeicherten Prozedur.|  
|Operator|UNPIVOT|Dieser Operator wird nicht unterstützt. Entfernen Sie `UNPIVOT` aus der systemintern kompilierten gespeicherten Prozedur.|  
|Operator|OR, IN|Disjunktion (OR, IN) wird in der WHERE-Klausel von Abfragen in systemintern kompilierten gespeicherten Prozeduren nicht unterstützt. Erstellen Sie Abfragen für jeden der Fälle.|  
|Operator|CONTAINS|Dieser Operator wird nicht unterstützt. Entfernen Sie `CONTAINS` aus der systemintern kompilierten gespeicherten Prozedur.|  
|Operator|FREETEXT|Dieser Operator wird nicht unterstützt. Entfernen Sie `FREETEXT` aus der systemintern kompilierten gespeicherten Prozedur.|  
|Operator|NICHT|Dieser Operator wird nicht unterstützt. Entfernen Sie `NOT` aus der systemintern kompilierten gespeicherten Prozedur. In einigen Fällen kann `NOT` durch einen Ungleichheitsoperator ersetzt werden. Beispielsweise kann `NOT a=b` durch `a!=b`ersetzt werden.|  
|Operator|TSEQUAL|Dieser Operator wird nicht unterstützt. Entfernen Sie `TSEQUAL` aus der systemintern kompilierten gespeicherten Prozedur.|  
|Operator|LIKE|Dieser Operator wird nicht unterstützt. Entfernen Sie `LIKE` aus der systemintern kompilierten gespeicherten Prozedur.|  
|Operator|NEXT VALUE FOR|In systemintern kompilierten gespeicherten Prozeduren kann nicht auf Sequenzen verwiesen werden. Rufen Sie den Wert mit interpretiertem [!INCLUDE[tsql](../../includes/tsql-md.md)]ab, und übergeben Sie ihn dann an die systemintern kompilierte gespeicherte Prozedur. Weitere Informationen finden Sie unter [Implementieren von IDENTITY in einer speicheroptimierten Tabelle](implementing-identity-in-a-memory-optimized-table.md).|  
|SET-Option|*Option*|SET-Optionen können in systemintern kompilierten gespeicherten Prozeduren nicht geändert werden. Bestimmte Optionen können mit der BEGIN ATOMIC-Anweisung festgelegt werden. Weitere Informationen finden Sie im Abschnitt zu ATOMIC-Blöcken in [Systemintern kompilierte gespeicherte Prozeduren](../in-memory-oltp/natively-compiled-stored-procedures.md).|  
|Operand|TABLESAMPLE|Dieser Operator wird nicht unterstützt. Entfernen Sie `TABLESAMPLE` aus der systemintern kompilierten gespeicherten Prozedur.|  
|Option|RECOMPILE|Systemintern kompilierte gespeicherte Prozeduren werden bei der Erstellungszeit kompiliert. Zum erneuten Kompilieren einer systemintern kompilierten gespeicherten Prozedur löschen Sie sie, und erstellen Sie sie neu. Entfernen Sie `RECOMPILE` aus der Prozedurdefinition.|  
|Option|ENCRYPTION|Diese Option wird nicht unterstützt. Entfernen Sie `ENCRYPTION` aus der Prozedurdefinition.|  
|Option|FOR REPLICATION|Systemintern kompilierte gespeicherte Prozeduren können nicht für die Replikation erstellt werden. Entfernen Sie `FOR REPLICATION` aus der Prozedurdefinition.|  
|Option|FOR XML|Diese Option wird nicht unterstützt. Entfernen Sie `FOR XML` aus der systemintern kompilierten gespeicherten Prozedur.|  
|Option|FOR BROWSE|Diese Option wird nicht unterstützt. Entfernen Sie `FOR BROWSE` aus der systemintern kompilierten gespeicherten Prozedur.|  
|Jointipp|HASH, MERGE|Systemintern kompilierte Prozeduren unterstützen nur den Nested Loops-Joins. Hash- und Zusammenführungsjoins werden nicht unterstützt. Entfernen Sie den Jointipp.|  
|Abfragetipp|*Abfragetipp*|Dieser Abfragetipp befindet sich nicht in systemintern kompilierten gespeicherten Prozeduren. Unterstützte Abfragetipps finden Sie unter [Abfragehinweise &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-query).|  
|Option|DISTINCT|Diese Option wird nicht unterstützt. Entfernen Sie `DISTINCT` aus der Abfrage in der systemintern kompilierten gespeicherten Prozedur.|  
|Option|PERCENT|Diese Option wird nicht für `TOP`-Klauseln unterstützt. Entfernen Sie `PERCENT` aus der Abfrage in der systemintern kompilierten gespeicherten Prozedur.|  
|Option|WITH TIES|Diese Option wird nicht für `TOP`-Klauseln unterstützt. Entfernen Sie `WITH TIES` aus der Abfrage in der systemintern kompilierten gespeicherten Prozedur.|  
|Aggregate-Funktion|*Aggregatfunktion*|Diese Klausel wird nicht unterstützt. Weitere Informationen zu Aggregate-Funktionen in systemintern kompilierten gespeicherten Prozeduren finden Sie unter [Systemintern kompilierte gespeicherte Prozeduren](../in-memory-oltp/natively-compiled-stored-procedures.md).|  
|Rangfolgefunktion|*Rangfolgefunktion*|Rangfolgefunktionen werden nicht in systemintern kompilierten gespeicherten Prozeduren unterstützt. Entfernen Sie sie aus der Prozedurdefinition.|  
|Funktion|*Funktion*|Diese Funktion wird nicht unterstützt. Entfernen Sie sie aus der systemintern kompilierten gespeicherten Prozedur.|  
|-Anweisung.|*Anweisung*|Diese Anweisung wird nicht unterstützt. Entfernen Sie sie aus der systemintern kompilierten gespeicherten Prozedur.|  
|Funktion|MIN und MAX verwendet mit Binär- und Zeichenfolgen|Die Aggregatfunktionen `MIN` und `MAX` können nicht für Zeichenwerte oder binäre Zeichenfolgenwerte in systemintern kompilierten gespeicherten Prozeduren verwendet werden.|  
|Funktion|GROUP BY ohne Aggregatfunktion|Wenn in systemintern kompilierten gespeicherten Prozeduren eine Abfrage eine `GROUP BY`-Klausel aufweist, muss sie auch eine Aggregatfunktion in der SELECT- oder HAVING-Klausel verwenden. Fügen Sie der Abfrage eine Aggregatfunktion hinzu.|  
|Funktion|GROUP BY ALL|ALL kann nicht mit GROUP BY-Klauseln in systemintern kompilierten gespeicherten Prozeduren verwendet werden. Entfernen Sie ALL aus der GROUP BY-Klausel.|  
|Funktion|GROUP BY ()|Gruppierung nach einer leeren Liste wird nicht unterstützt. Entfernen Sie entweder die GROUP BY-Klausel, oder schließen Sie Spalten in der Gruppierungsliste ein.|  
|Funktion|ROLLUP|`ROLLUP` kann nicht mit `GROUP BY`-Klauseln in systemintern kompilierten gespeicherten Prozeduren verwendet werden. Entfernen Sie `ROLLUP` aus der Prozedurdefinition.|  
|Funktion|CUBE|`CUBE` kann nicht mit `GROUP BY`-Klauseln in systemintern kompilierten gespeicherten Prozeduren verwendet werden. Entfernen Sie `CUBE` aus der Prozedurdefinition.|  
|Funktion|GROUPING SETS|`GROUPING SETS` kann nicht mit `GROUP BY`-Klauseln in systemintern kompilierten gespeicherten Prozeduren verwendet werden. Entfernen Sie `GROUPING SETS` aus der Prozedurdefinition.|  
|Funktion|BEGIN TRANSACTION, COMMIT TRANSACTION und ROLLBACK TRANSACTION|Verwenden Sie ATOMIC-Blöcke, um Transaktionen und Fehlerbehandlung zu steuern. Weitere Informationen finden Sie unter [ATOMIC-Blöcke](atomic-blocks-in-native-procedures.md).|  
|Funktion|Deklarationen von Inlinetabellenvariablen.|Tabellenvariablen müssen auf explizit definierte speicheroptimierte Tabellentypen verweisen. Sie sollten einen speicheroptimierten Tabellentyp erstellen und diesen Typ für die Variablendeklaration verwenden, statt den Typ inline anzugeben.|  
|Funktion|sp_recompile|Das erneute Kompilieren von systemintern kompilierten gespeicherten Prozeduren wird nicht unterstützt. Löschen Sie die Prozedur und erstellen Sie sie neu.|  
|Funktion|EXECUTE AS CALLER|Die `EXECUTE AS`-Klausel ist erforderlich. `EXECUTE AS CALLER` wird jedoch nicht unterstützt. Verwendung `EXECUTE AS OWNER`, `EXECUTE AS` *Benutzer*, oder `EXECUTE AS SELF`.|  
|Funktion|Datenträgerbasierte Tabellen|Auf datenträgerbasierte Tabellen kann nicht von systemintern kompilierten gespeicherten Prozeduren zugegriffen werden. Entfernen Sie Verweise auf datenträgerbasierte Tabellen aus den systemintern kompilierten gespeicherten Prozeduren. Sie können auch datenträgerbasierte Tabellen zu speicheroptimierten Tabellen migrieren.|  
|Funktion|Ansichten|Auf Sichten kann nicht von systemintern kompilierten gespeicherten Prozeduren zugegriffen werden. Verweisen Sie nicht auf Sichten, sondern auf die zugrunde liegenden Basistabellen.|  
|Funktion|Tabellenwertfunktionen|Auf Tabellenwertfunktionen kann nicht von systemintern kompilierten gespeicherten Prozeduren aus zugegriffen werden. Entfernen Sie Verweise auf Tabellenwertfunktionen aus der systemintern kompilierten gespeicherten Prozedur.|  
  
## <a name="transactions-that-access-memory-optimized-tables"></a>Transaktionen, die auf speicheroptimierte Tabellen zugreifen  
 In der folgenden Tabelle werden die möglichen [!INCLUDE[tsql](../../includes/tsql-md.md)] -Funktionen und -Schlüsselwörter im Meldungstext eines Fehlers mit Transaktionen, die auf speicheroptimierte Tabellen zugreifen sowie die Korrekturmaßnahmen zum Beheben des Fehlers aufgelistet.  
  
|Typ|Name|Lösung|  
|----------|----------|----------------|  
|Funktion|Sicherungspunkt|Das Erstellen von expliziten Sicherungspunkten in Transaktionen, die auf speicheroptimierte Tabellen zugreifen, wird nicht unterstützt.|  
|Funktion|Gebundene Transaktion|Gebundene Sitzungen können nicht an Transaktionen teilnehmen, die auf speicheroptimierte Tabellen zugreifen. Binden Sie die Sitzung nicht, bevor Sie die Prozedur ausführen.|  
|Funktion|DTC|Transaktionen, die auf speicheroptimierte Tabellen zugreifen, können keine verteilten Transaktionen sein.|  
  
## <a name="see-also"></a>Siehe auch  
 [Migrieren zu In-Memory OLTP](migrating-to-in-memory-oltp.md)  
  
  
