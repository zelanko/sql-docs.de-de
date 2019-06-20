---
title: Microsoft OLE DB-Anbieter für SQLServer | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], OLE DB provider for SQL Server
- OLE DB provider for SQL Server [ADO]
- SQLOLEDB [ADO]
ms.assetid: 99bc40c4-9181-4ca1-a06f-9a1a914a0b7b
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f083f62a67a2255b59fe9ca7cffc03e5aaf5f0a1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66701182"
---
# <a name="microsoft-ole-db-provider-for-sql-server-overview"></a>Microsoft OLE DB-Anbieter für SQL Server – Übersicht
Microsoft OLE DB-Anbieter für SQL Server, SQLOLEDB, kann es sich um ADO auf Microsoft SQL Server zugreifen.

> [!IMPORTANT]
> Microsoft OLE DB-Anbieter für SQL Server (SQLOLEDB) bleibt als veraltet markierte, und es wird nicht empfohlen, für das Entwickeln neuer Anwendungen nicht verwendet. Verwenden Sie stattdessen die neuen [Microsoft OLE DB-Treiber für SQL Server](../../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL) wird die mit den neuesten Serverfunktionen aktualisiert.

## <a name="connection-string-parameters"></a>Parameter für Verbindungszeichenfolgen
 Legen Sie zum Verbinden mit diesem Anbieter die *Anbieter* Argument für die ["ConnectionString"](../../../ado/reference/ado-api/connectionstring-property-ado.md) Eigenschaft:

```vb
SQLOLEDB
```

 Dieser Wert kann auch festlegen oder Lesen Sie mithilfe der [Anbieter](../../../ado/reference/ado-api/provider-property-ado.md) Eigenschaft.

## <a name="typical-connection-string"></a>Typische Verbindungszeichenfolge
 Eine typische Verbindungszeichenfolge für diesen Anbieter ist:

```vb
"Provider=SQLOLEDB;Data Source=serverName;"
Initial Catalog=databaseName;
User ID=MyUserID;Password=MyPassword;"
```

 Die Zeichenfolge, die dieser Schlüsselwörter besteht aus:

|Schlüsselwort|Description|
|-------------|-----------------|
|**Anbieter**|Gibt an, die OLE DB-Anbieter für SqlServer.|
|**Datenquelle** oder **Server**|Gibt den Namen eines Servers.|
|**Anfangskatalog** oder **Datenbank**|Gibt den Namen einer Datenbank auf dem Server an.|
|**Benutzer-ID** oder **Uid**|Gibt den Benutzernamen (für SQL Server-Authentifizierung).|
|**Kennwort** oder **Pwd**|Gibt das Kennwort des Benutzers (für SQL Server-Authentifizierung).|

> [!NOTE]
>  Wenn Sie für einen Datenanbieter der Datenquelle, der Windows-Authentifizierung unterstützt herstellen, sollten Sie angeben **Trusted_Connection = Yes** oder **Integrated Security = SSPI** anstelle von Benutzer-ID und Kennwort die Informationen in der Verbindungszeichenfolge.

## <a name="provider-specific-connection-parameters"></a>Anbieterspezifische-Verbindungsparameter
 Der Anbieter unterstützt mehrere Anbieter-spezifischen Verbindungsdaten Parameter zusätzlich zu den von ADO definiert. Wie mit den Eigenschaften der ADO-Verbindung diese Anbieter-spezifischen Eigenschaften können, über festgelegt werden die [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Auflistung von einer [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) oder als Teil der festgelegt werden kann die **"ConnectionString"** .

|Parameter|Beschreibung|
|---------------|-----------------|
|Trusted_Connection|Gibt den Authentifizierungsmodus für den Benutzer an. Dies kann so festgelegt werden **Ja** oder **keine**. Der Standardwert ist **keine**. Wenn diese Eigenschaft, um festgelegt wird **Ja**, SQLOLEDB verwendet Microsoft Windows NT-Authentifizierungsmodus zum Autorisieren des Benutzerzugriffs mit der SQL Server-Datenbank, die gemäß der **Speicherort** und [Datasource ](../../../ado/reference/ado-api/datasource-property-ado.md) Eigenschaftswerte. Wenn diese Eigenschaft, um festgelegt wird **keine**, SQLOLEDB verwendet im gemischten Modus zum Autorisieren des Benutzerzugriffs auf SQL Server-Datenbank. Der SQL Server-Anmeldenamen und das Kennwort werden angegeben, der **Benutzer-Id** und **Kennwort** Eigenschaften.|
|Aktuelle Sprache|Gibt an, ein SQL Server-Sprachenname. Identifiziert die für die Auswahl und Formatierung von Systemnachrichten verwendete Sprache. Die Sprache auf dem SQL-Server installiert werden muss andernfalls öffnen, die die Verbindung fehl.|
|Netzwerkadresse|Gibt die Netzwerkadresse des SQL Servers gemäß der **Speicherort** Eigenschaft.|
|Netzwerkbibliothek|Gibt den Namen der Netzwerkbibliothek (DLL) zur Kommunikation mit dem SQL Server verwendet. Der Name sollte weder den Pfad noch die DLL-Dateinamenerweiterung enthalten. Der Standardwert wird durch die SQL Server-Clientkonfiguration bereitgestellt.|
|Verfahren für Vorbereitung verwenden|Bestimmt, ob SQL Server temporäre gespeicherte Prozeduren erstellt, bei der Vorbereitung der Befehle (durch die **Prepared** Eigenschaft).|
|Automatisch übersetzen|Gibt an, ob der OEM-ANSI-Zeichen konvertiert werden. Diese Eigenschaft kann festgelegt werden, um **"true"** oder **"false"** . Der Standardwert lautet **True**. Wenn diese Eigenschaft, um festgelegt wird **"true"** , SQLOLEDB OEM-/ANSI-zeichenkonvertierung ausführt, wenn Multibyte-Zeichenfolgen aus abgerufen oder an, die SQL-Server gesendet werden. Wenn diese Eigenschaft, um festgelegt wird **"false"** , SQLOLEDB führt keine OEM-ANSI-zeichenkonvertierung Multibyte-Zeichensatz-Zeichenfolgendaten.|
|Packet Size|Gibt ein Netzwerk-Paketgröße in Bytes an. Der Paketgrößen-Eigenschaftswert muss zwischen 512 und 32767 liegen. Die standardmäßige Netzwerkpaketgröße SQLOLEDB ist 4096.|
|ApplicationName|Gibt den Namen der Clientanwendung an.|
|Workstation ID|Eine Zeichenfolge, die die Arbeitsstation identifiziert.|

## <a name="command-object-usage"></a>Befehlsobjekt-Nutzung
 SQLOLEDB akzeptiert einen Zusammenschluss von ODBC, ANSI und SQL Server-spezifische Transact-SQL als gültige Syntax. Die folgende SQL-Anweisung beispielsweise verwendet eine ODBC SQL-Escapesequenz, um die LCASE-Zeichenfolgenfunktion anzugeben:

```sql
SELECT customerid={fn LCASE(CustomerID)} FROM Customers

```

 LCASE gibt eine Zeichenfolge zurück und konvertiert alle Großbuchstaben in ihre kleingeschriebenen Entsprechungen. Die ANSI SQL-Zeichenfolgenfunktion LOWER führt denselben Vorgang, daher ist die folgende SQL-Anweisung entspricht die ODBC-Anweisung, die zuvor gezeigte ANSI:

```sql
SELECT customerid=LOWER(CustomerID) FROM Customers

```

 SQLOLEDB verarbeitet beide Formen der Anweisung, wenn als Text für einen Befehl angegeben.

## <a name="stored-procedures"></a>Gespeicherte Prozeduren
 Beim Ausführen einer SQL Server gespeicherten Prozedur, die mit einem SQLOLEDB-Befehl verwenden Sie, die ODBC-Prozedur Aufruf-Escapesequenz im Befehlstext. SQLOLEDB verwendet dann den remoteprozeduraufrufsmechanismus von SQL Server, um die befehlsverarbeitung zu optimieren. Beispielsweise ist die folgende ODBC SQL-Anweisung bevorzugter Befehlstext über das Transact-SQL-Formular:

## <a name="odbc-sql"></a>ODBC SQL

```vb
{call SalesByCategory('Produce', '1995')}

```

## <a name="transact-sql"></a>Transact-SQL

```sql
EXECUTE SalesByCategory 'Produce', '1995'

```

## <a name="sql-server-features"></a>SQL Server-Funktionen
 ADO können mit SQL Server XML-Code für **Befehl** eingeben und Abrufen der Ergebnisse im XML-Stream-Format statt im **Recordset** Objekte. Weitere Informationen finden Sie unter [Using Streams für die Eingabe des Befehls](../../../ado/guide/data/command-streams.md) und [Abrufen von Resultsets in Streams](../../../ado/guide/data/retrieving-resultsets-into-streams.md).

### <a name="accessing-sqlvariant-data-using-mdac-27-mdac-28-or-windows-dac-60"></a>Zugreifen auf die Sql_variant-Daten mithilfe von MDAC 2.7, MDAC 2.8 oder Windows DAC 6.0
 Microsoft SQL Server verfügt über einen Datentyp namens **Sql_variant**. OLE DB ähnelt **DBTYPE_VARIANT**, **Sql_variant** -Datentyp kann mehrere unterschiedliche Datentypen speichern. Es gibt jedoch einige wichtige Unterschiede zwischen **DBTYPE_VARIANT** und **Sql_variant**. ADO verarbeitet auch Daten als eine **Sql_variant** Wert anders als wie andere Datentypen verarbeitet. Die folgende Liste beschreibt die Probleme zu berücksichtigen, beim Zugriff auf SQL Server-Daten in Spalten vom Typ **Sql_variant**.

-   In MDAC 2.7, MDAC 2.8 und Windows Data Access Components (Windows DAC) 6.0, OLE DB-Anbieter für SQL Server unterstützt die **Sql_variant** Typ. Der OLE DB-Anbieter für ODBC wird nicht verwendet.

-   Die **Sql_variant** Typ stimmt nicht genau überein. die **DBTYPE_VARIANT** -Datentyp.  Die **Sql_variant** unterstützt einige neue Untertypen von nicht unterstützten **DBTYPE_VARIANT,** einschließlich **GUID**, **ANSI** (nicht-UNICODE) Zeichenfolgen, und **BIGINT**. Mithilfe von Untertypen außer funktioniert den oben aufgeführten ordnungsgemäß.

-   Die **Sql_variant** Untertyp **numerischen** entspricht nicht der **DBTYPE_DECIMAL** Größe.

-   Mehrere Datentypumwandlungen führt Typen, die nicht übereinstimmen. Beispielsweise Koersion eine **Sql_variant** mit einen Untertyp des **GUID** auf eine **DBTYPE_VARIANT** führt dazu, einen Untertyp des **Safearray**(Bytes) . Konvertieren dieses Typs zurück in eine **Sql_variant** führt zu einer neuen Untertyp des **Array**(Bytes).

-   **Recordset** Felder mit **Sql_variant** Daten können Remote ausgeführt werden (gemarshallt) oder persistenten nur, wenn die **Sql_variant** bestimmte Untertypen enthält. Es wird versucht, auf den Remotecomputer oder beibehalten von Daten mit den folgenden nicht unterstützten Untertypen verursacht einen Laufzeitfehler (nicht unterstützte Konvertierung) aus der Persistenz-Provider von Microsoft (MSPersist): **VT_VARIANT**, **VT_RECORD**, **VT_ILLEGAL**, **VT_UNKNOWN**, **VT_BSTR**, und **"VT_DISPATCH".**

-   Der OLE DB-Anbieter für SQL Server in MDAC 2.7, MDAC 2.8 und Windows DAC 6.0 verfügt über eine dynamische Eigenschaft namens **können Native Varianten** , wie der Name schon sagt, wodurch Entwicklern den Zugriff auf die **Sql_variant** in Ihre ursprüngliche Form im Gegensatz zu einem **DBTYPE_VARIANT**. Wenn diese Eigenschaft festgelegt ist, und eine **Recordset** wird geöffnet, mit der Client-Cursor-Engine (**AdUseClient**), wird die **Recordset.Open** Aufruf schlägt fehl. Wenn diese Eigenschaft festgelegt ist und eine **Recordset** wird mit der Servercursor geöffnet (**AdUseServer**), wird die **Recordset.Open** Aufruf erfolgreich ausgeführt, aber den Zugriff auf Spalten des Typs **Sql_variant** erzeugt einen Fehler.

-   In Clientanwendungen, MDAC 2.5 verwenden **Sql_variant** Daten mit Abfragen für Microsoft SQL Server verwendet werden können. Allerdings die Werte der **Sql_variant** Daten werden als Zeichenfolgen behandelt. Derartige Clientanwendungen sollten auf MDAC 2.7, MDAC 2.8 oder Windows DAC 6.0 aktualisiert werden.

## <a name="recordset-behavior"></a>Recordset-Verhalten
 SQLOLEDB darf nicht SQL Server-Cursor verwenden, um die von zahlreichen Befehlen generiert mehrere-Ergebnis unterstützen zu können. Wenn ein Consumer ein Recordset, erfordern die Unterstützung für SQL Server-Cursor angefordert wird, tritt ein Fehler auf, wenn der Befehlstext zum mehr als einem einzigen Datensatz als Ergebnis generiert.

 Bildlauffähige SQLOLEDB-Recordsets werden von SQL Server-Cursor unterstützt. SQL Server erzwingt Einschränkungen für Cursor, die von anderen Benutzern der Datenbank vorgenommenen Änderungen berücksichtigt werden. Insbesondere die Zeilen in einigen Cursorn nicht verändert werden, und versuchen, erstellen ein Recordset mit einem Befehl mit einer SQL ORDER BY-Klausel kann ein Fehler auftreten.

## <a name="dynamic-properties"></a>Dynamische Eigenschaften
 Microsoft OLE DB-Anbieter für SQL Server fügt verschiedene Eigenschaften in der **Eigenschaften** Auflistung von nicht geöffneten [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md), [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), und [ Befehl](../../../ado/reference/ado-api/command-object-ado.md) Objekte.

 Die folgenden Tabellen sind ein Cross-Index der ADO und OLE DB-Namen für jede dynamische Eigenschaft. Der OLE DB Programmer's Reference bezieht sich auf den Namen einer ADO-Eigenschaft, wird der Begriff "Description". Weitere Informationen zu diesen Eigenschaften finden Sie in der OLE DB Programmer's Reference. Suchen Sie nach den Namen des OLE DB-Eigenschaft im Index oder finden Sie unter [Anhang C: Eigenschaften für OLE DB](https://msdn.microsoft.com/deded3ff-f508-4e1b-b2b1-fd9afd3bd292).

## <a name="connection-dynamic-properties"></a>Dynamische Eigenschaften der Verbindung
 Die folgenden Eigenschaften werden hinzugefügt, um die **Eigenschaften** Auflistung von der **Verbindung** Objekt.

|ADO-Eigenschaftenname|OLE DB-Eigenschaftenname|
|-----------------------|--------------------------|
|Aktive Sitzungen|DBPROP_ACTIVESESSIONS|
|Asynchroner Abbruch|DBPROP_ASYNCTXNABORT|
|Asynchroner Commit|DBPROP_ASYNCTNXCOMMIT|
|Autocommit-Isolationsgrade|DBPROP_SESS_AUTOCOMMITISOLEVELS|
|Speicherort des Katalogs|DBPROP_CATALOGLOCATION|
|Katalogbegriff|DBPROP_CATALOGTERM|
|Spaltendefinition|DBPROP_COLUMNDEFINITION|
|Verbindungstimeout|DBPROP_INIT_TIMEOUT|
|Aktuellen Katalog|DBPROP_CURRENTCATALOG|
|Datenquelle|DBPROP_INIT_DATASOURCE|
|Datenquellenname|DBPROP_DATASOURCENAME|
|Datenquellenobjekt Threading-Modell|DBPROP_DSOTHREADMODEL|
|Der DBMS-Name|DBPROP_DBMSNAME|
|DBMS Version|DBPROP_DBMSVER|
|Extended Properties|DBPROP_INIT_PROVIDERSTRING|
|GROUP BY-Unterstützung|DBPROP_GROUPBY|
|Heterogene Tabellenunterstützung|DBPROP_HETEROGENEOUSTABLES|
|Bezeichner Groß-/Kleinschreibung|DBPROP_IDENTIFIERCASE|
|Anfangskatalog|DBPROP_INIT_CATALOG|
|Isolationsstufen|DBPROP_SUPPORTEDTXNISOLEVELS|
|Isolationszurückbehaltung|DBPROP_SUPPORTEDTXNISORETAIN|
|Locale Identifier|DBPROP_INIT_LCID|
|Maximale Indexgröße|DBPROP_MAXINDEXSIZE|
|Maximale Zeilengröße|DBPROP_MAXROWSIZE|
|Maximale Zeilengröße schließt BLOB ein|DBPROP_MAXROWSIZEINCLUDESBLOB|
|Maximale Anzahl von Tabellen in SELECT|DBPROP_MAXTABLESINSELECT|
|Mehrere Parametersätze|DBPROP_MULTIPLEPARAMSETS|
|Mehrere Ergebnisse|DBPROP_MULTIPLERESULTS|
|Mehrere Speicherobjekte|DBPROP_MULTIPLESTORAGEOBJECTS|
|Aktualisierung mehrerer Tabellen|DBPROP_MULTITABLEUPDATE|
|NULL-Zusammenstellungsreihenfolge|DBPROP_NULLCOLLATION|
|NULL-Verkettungsverhalten|DBPROP_CONCATNULLBEHAVIOR|
|OLE DB Version|DBPROP_PROVIDEROLEDBVER|
|OLE-Objektunterstützung|DBPROP_OLEOBJECTS|
|Öffnen Sie die Schemarowset-Unterstützung|DBPROP_OPENROWSETSUPPORT|
|ORDER BY-Spalten in Auswahlliste|DBPROP_ORDERBYCOLUMNSINSELECT|
|Verfügbarkeit der Ausgabeparameter|DBPROP_OUTPUTPARAMETERAVAILABILITY|
|Übergabe durch Verweiszugriffe|DBPROP_BYREFACCESSORS|
|Kennwort|DBPROP_AUTH_PASSWORD|
|Sicherheitsinformationen permanent speichern|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|
|Persistenter ID-Typ|DBPROP_PERSISTENTIDTYPE|
|Abbruchverhalten vorbereiten|DBPROP_PREPAREABORTBEHAVIOR|
|Commitverhalten vorbereiten|DBPROP_PREPARECOMMITBEHAVIOR|
|Prozedurbegriff|DBPROP_PROCEDURETERM|
|Eingabeaufforderung|DBPROP_INIT_PROMPT|
|Anbietername|DBPROP_PROVIDERFRIENDLYNAME|
|Provider Name|DBPROP_PROVIDERFILENAME|
|Anbieterversion|DBPROP_PROVIDERVER|
|Nur-Lese Datenquelle|DBPROP_DATASOURCEREADONLY|
|Rowsetkonvertierung auf Befehl|DBPROP_ROWSETCONVERSIONSONCOMMAND|
|Schemabegriff|DBPROP_SCHEMATERM|
|Schemaverwendung|DBPROP_SCHEMAUSAGE|
|SQL-Unterstützung|DBPROP_SQLSUPPORT|
|Strukturierte Speicherung|DBPROP_STRUCTUREDSTORAGE|
|Unterstützung für Unterabfragen|DBPROP_SUBQUERIES|
|Tabellenbegriff|DBPROP_TABLETERM|
|Transaktions-DDL|DBPROP_SUPPORTEDTXNDDL|
|Benutzer-ID|DBPROP_AUTH_USERID|
|Benutzername|DBPROP_USERNAME|
|Das Fensterhandle|DBPROP_INIT_HWND|

## <a name="recordset-dynamic-properties"></a>Recordset Dynamic-Eigenschaften
 Die folgenden Eigenschaften werden hinzugefügt, um die **Eigenschaften** Auflistung von der **Recordset** Objekt.

|ADO-Eigenschaftenname|OLE DB-Eigenschaftenname|
|-----------------------|--------------------------|
|Zugriffsreihenfolge|DBPROP_ACCESSORDER|
|Speicherobjekte blockieren|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Lesezeichentyp|DBPROP_BOOKMARKTYPE|
|Jeden|DBPROP_IROWSETLOCATE|
|Eingefügte Zeilen ändern|DBPROP_CHANGEINSERTEDROWS|
|Spaltenprivilegien|DBPROP_COLUMNRESTRICT|
|Spaltenmengenbenachrichtigung|DBPROP_NOTIFYCOLUMNSET|
|Befehlstimeout|DBPROP_COMMANDTIMEOUT|
|Verzögern der Spalte|DBPROP_DEFERRED|
|Speicherobjektaktualisierungen verzögern|DBPROP_DELAYSTORAGEOBJECTS|
|Rückwärts fetchen|DBPROP_CANFETCHBACKWARDS|
|Zeilen halten|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|Nicht Mobile Zeilen|DBPROP_IMMOBILEROWS|
|IRowset|DBPROP_IRowset|
|IRowsetChange|DBPROP_IRowsetChange|
|IRowsetIdentity|DBPROP_IRowsetIdentity|
|IRowsetInfo|DBPROP_IRowsetInfo|
|IRowsetLocate|DBPROP_IRowsestLocate|
|IRowsetResynch||
|IRowsetScroll|DBPROP_IRowsetScroll|
|IRowsetUpdate|DBPROP_IRowsetUpdate|
|ISequentialStream|DBPROP_ISequentialStream|
|ISupportErrorInfo|DBPROP_ISupportErrorInfo|
|Literale Lesezeichen|DBPROP_LITERALBOOKMARKS|
|Literale Zeilen-ID|DBPROP_LITERALIDENTITY|
|Maximale Anzahl geöffneter Zeilen|DBPROP_MAXOPENROWS|
|Maximale Anzahl ausstehender Zeilen|DBPROP_MAXPENDINGROWS|
|Maximale Zeilenanzahl|DBPROP_MAXROWS|
|Benachrichtigungsgranularität|DBPROP_NOTIFICATIONGRANULARITY|
|Benachrichtigungsphasen|DBPROP_NOTIFICATIONPHASES|
|Von Transaktion betroffene Objekte|DBPROP_TRANSACTEDOBJECT|
|Änderungen anderer sichtbar|DBPROP_OTHERUPDATEDELETE|
|Einfügungen anderer sichtbar|DBPROP_OTHERINSERT|
|Eigene Änderungen sichtbar|DBPROP_OWNUPDATEDELETE|
|Eigene Einfügungen sichtbar|DBPROP_OWNINSERT|
|Bei Abbruch erhalten|DBPROP_ABORTPRESERVE|
|Bei Commit beibehalten|DBPROP_COMMITPRESERVE|
|Schneller Neustart|DBPROP_QUICKRESTART|
|Wiedereintretende Ereignisse|DBPROP_REENTRANTEVENTS|
|Gelöschte Zeilen entfernen|DBPROP_REMOVEDELETED|
|Mehrere Änderungen melden|DBPROP_REPORTMULTIPLECHANGES|
|Ausstehende Einfügungen zurückgeben|DBPROP_RETURNPENDINGINSERTS|
|Benachrichtigung: Spalten löschen|DBPROP_NOTIFYROWDELETE|
|Benachrichtigung: erste Zeilenänderung|DBPROP_NOTIFYROWFIRSTCHANGE|
|Benachrichtigung: Zeile einfügen|DBPROP_NOTIFYROWINSERT|
|Zeilenprivilegien|DBPROP_ROWRESTRICT|
|Benachrichtigung: Zeile bei der erneuten Synchronisierung|DBPROP_NOTIFYROWRESYNCH|
|Zeilenthreadingmodell|DBPROP_ROWTHREADMODEL|
|Benachrichtigung: Änderung rückgängig machen|DBPROP_NOTIFYROWUNDOCHANGE|
|Löschbenachrichtigung rückgängig machen|DBPROP_NOTIFYROWUNDODELETE|
|Benachrichtigung: Zeile einfügen rückgängig|DBPROP_NOTIFYROWUNDOINSERT|
|Benachrichtigung: Zeile aktualisieren|DBPROP_NOTIFYROWUPDATE|
|Benachrichtigung: Rowset-Positionsänderungsabruf|DBPROP_NOTIFYROWSETFETCHPOSISIONCHANGE|
|Rowset-Freigabe-Benachrichtigung|DBPROP_NOTIFYROWSETRELEASE|
|Bildlauf rückwärts|DBPROP_CANSCROLLBACKWARDS|
|Servercursor|DBPROP_SERVERCURSOR|
|Gelöschte Lesezeichen überspringen|DBPROP_BOOKMARKSKIPPED|
|Starke Zeilenidentität|DBPROP_STRONGITDENTITY|
|Eindeutige Zeilen|DBPROP_UNIQUEROWS|
|Aktualisierbarkeit|DBPROP_UPDATABILITY|
|Verwenden von Lesezeichen|DBPROP_BOOKMARKS|

## <a name="command-dynamic-properties"></a>Dynamische Eigenschaften-Befehl
 Die folgenden Eigenschaften werden hinzugefügt, um die **Eigenschaften** Auflistung von der **Befehl** Objekt.

|ADO-Eigenschaftenname|OLE DB-Eigenschaftenname|
|-----------------------|--------------------------|
|Zugriffsreihenfolge|DBPROP_ACCESSORDER|
|Basispfad|SSPROP_STREAM_BASEPATH|
|Speicherobjekte blockieren|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Lesezeichentyp|DBPROP_BOOKMARKTYPE|
|Jeden|DBPROP_IROWSETLOCATE|
|Eingefügte Zeilen ändern|DBPROP_CHANGEINSERTEDROWS|
|Spaltenprivilegien|DBPROP_COLUMNRESTRICT|
|Spaltenmengenbenachrichtigung|DBPROP_NOTIFYCOLUMNSET|
|Inhaltstyp|SSPROP_STREAM_CONTENTTYPE|
|Cursor-Auto-Fetch|SSPROP_CURSORAUTOFETCH|
|Verzögern der Spalte|DBPROP_DEFERRED|
|Vorbereitung zurückstellen|SSPROP_DEFERPREPARE|
|Speicherobjektaktualisierungen verzögern|DBPROP_DELAYSTORAGEOBJECTS|
|Rückwärts fetchen|DBPROP_CANFETCHBACKWARDS|
|Zeilen halten|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|Nicht Mobile Zeilen|DBPROP_IMMOBILEROWS|
|IRowset|DBPROP_IRowset|
|IRowsetChange|DBPROP_IRowsetChange|
|IRowsetIdentity|DBPROP_IRowsetIdentity|
|IRowsetInfo|DBPROP_IRowsetInfo|
|IRowsetLocate|DBPROP_IRowsetLocate|
|IRowsetResynch|DBPROP_IRowsetResynch|
|IRowsetScroll|DBPROP_IRowsetScroll|
|IRowsetUpdate|DBPROP_IRowsetUpdate|
|ISequentialStream|DBPROP_ISequentialStream|
|ISupportErrorInfo|DBPROP_ISupportErrorInfo|
|Literale Lesezeichen|DBPROP_LITERALBOOKMARKS|
|Literale Zeilen-ID|DBPROP_LITERALIDENTITY|
|Sperrmodus|DBPROP_LOCKMODE|
|Maximale Anzahl geöffneter Zeilen|DBPROP_MAXOPENROWS|
|Maximale Anzahl ausstehender Zeilen|DBPROP_MAXPENDINGROWS|
|Maximale Zeilenanzahl|DBPROP_MAXROWS|
|Benachrichtigungsgranularität|DBPROP_NOTIFICATIONGRANULARITY|
|Benachrichtigungsphasen|DBPROP_NOTIFICATIONPHASES|
|Von Transaktion betroffene Objekte|DBPROP_TRANSACTEDOBJECT|
|Änderungen anderer sichtbar|DBPROP_OTHERUPDATEDELETE|
|Einfügungen anderer sichtbar|DBPROP_OTHERINSERT|
|Ausgabe-Encoding-Eigenschaft|DBPROP_OUTPUTENCODING|
|Output Stream-Eigenschaft|DBPROP_OUTPUTSTREAM|
|Eigene Änderungen sichtbar|DBPROP_OWNUPDATEDELETE|
|Eigene Einfügungen sichtbar|DBPROP_OWNINSERT|
|Bei Abbruch erhalten|DBPROP_ABORTPRESERVE|
|Bei Commit beibehalten|DBPROP_COMMITPRESERVE|
|Schneller Neustart|DBPROP_QUICKRESTART|
|Wiedereintretende Ereignisse|DBPROP_REENTRANTEVENTS|
|Gelöschte Zeilen entfernen|DBPROP_REMOVEDELETED|
|Mehrere Änderungen melden|DBPROP_REPORTMULTIPLECHANGES|
|Ausstehende Einfügungen zurückgeben|DBPROP_RETURNPENDINGINSERTS|
|Benachrichtigung: Spalten löschen|DBPROP_NOTIFYROWDELETE|
|Benachrichtigung: erste Zeilenänderung|DBPROP_NOTIFYROWFIRSTCHANGE|
|Benachrichtigung: Zeile einfügen|DBPROP_NOTIFYROWINSERT|
|Zeilenprivilegien|DBPROP_ROWRESTRICT|
|Benachrichtigung: Zeile bei der erneuten Synchronisierung|DBPROP_NOTIFYROWRESYNCH|
|Zeilenthreadingmodell|DBPROP_ROWTHREADMODEL|
|Benachrichtigung: Änderung rückgängig machen|DBPROP_NOTIFYROWUNDOCHANGE|
|Löschbenachrichtigung rückgängig machen|DBPROP_NOTIFYROWUNDODELETE|
|Benachrichtigung: Zeile einfügen rückgängig|DBPROP_NOTIFYROWUNDOINSERT|
|Benachrichtigung: Zeile aktualisieren|DBPROP_NOTIFYROWUPDATE|
|Benachrichtigung: Rowset-Positionsänderungsabruf|DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE|
|Rowset-Freigabe-Benachrichtigung|DBPROP_NOTIFYROWSETRELEASE|
|Bildlauf rückwärts|DBPROP_CANSCROLLBACKWARDS|
|Servercursor|DBPROP_SERVERCURSOR|
|Serverdaten beim Einfügen|DBPROP_SERVERDATAONINSERT|
|Gelöschte Lesezeichen überspringen|DBPROP_BOOKMARKSKIP|
|Starke Zeilenidentität|DBPROP_STRONGIDENTITY|
|Aktualisierbarkeit|DBPROP_UPDATABILITY|
|Verwenden von Lesezeichen|DBPROP_BOOKMARKS|
|XML-Stamm|SSPROP_STREAM_XMLROOT|
|XSL|SSPROP_STREAM_XSL|

 Bestimmte Implementierungsdetails und funktionalen Informationen zu Microsoft SQL Server OLE DB-Anbieter finden Sie in der [SQL Server-Anbieter](https://msdn.microsoft.com/adf1d6c4-5930-444a-9248-ff1979729635).

## <a name="see-also"></a>Siehe auch
 [ConnectionString-Eigenschaft (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md) [Provider-Eigenschaft (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
