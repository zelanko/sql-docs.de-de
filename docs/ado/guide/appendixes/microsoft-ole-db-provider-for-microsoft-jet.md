---
title: Microsoft OLE DB-Anbieter für Microsoft Jet | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Jet provider for OLE DB [ADO]
- providers [ADO], OLE DB provider for Microsoft Jet
- OLE DB provider for Microsoft Jet [ADO]
ms.assetid: fd956da1-5203-40af-aa7e-fc13a6c6581f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 986c1bf7f604f531180a14a4456325ce01702b94
ms.sourcegitcommit: 96b2355d54dfad259826e88bdff91cc9344e16f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51350594"
---
# <a name="microsoft-ole-db-provider-for-microsoft-jet-overview"></a>Microsoft OLE DB-Anbieter für Microsoft Jet-Übersicht
Der OLE DB-Anbieter für Microsoft Jet können ADO auf Microsoft Jet-Datenbanken zugreifen.

## <a name="connection-string-parameters"></a>Parameter für Verbindungszeichenfolgen
 Legen Sie zum Verbinden mit diesem Anbieter die *Anbieter* Argument der ["ConnectionString"](../../../ado/reference/ado-api/connectionstring-property-ado.md) -Eigenschaft auf Folgendes:

```vb
Microsoft.Jet.OLEDB.4.0
```

 Lesen der [Anbieter](../../../ado/reference/ado-api/provider-property-ado.md) Eigenschaft auch dieser Zeichenfolge zurück.

## <a name="typical-connection-string"></a>Typische Verbindungszeichenfolge
 Eine typische Verbindungszeichenfolge für diesen Anbieter ist:

```vb
"Provider=Microsoft.Jet.OLEDB.4.0;Data Source=databaseName;User ID=MyUserID;Password=MyPassword;"
```

 Die Zeichenfolge, die dieser Schlüsselwörter besteht aus:

|Schlüsselwort|Description|
|-------------|-----------------|
|**Anbieter**|Gibt an, für Microsoft Jet OLE DB-Anbieter.|
|**Data Source**|Gibt den Datenbanknamen Pfad und Dateinamen an (z. B. `c:\Northwind.mdb`).|
|**Benutzer-ID**|Gibt den Benutzernamen an. Wenn dieses Schlüsselwort nicht angegeben wird, die Zeichenfolge "`admin`", wird standardmäßig verwendet.|
|**Kennwort**|Gibt das Kennwort des Benutzers an. Wenn dieses Schlüsselwort nicht angegeben wird, die leere Zeichenfolge (""), wird standardmäßig verwendet.|

> [!NOTE]
>  Wenn Sie für einen Datenanbieter der Datenquelle, der Windows-Authentifizierung unterstützt herstellen, sollten Sie angeben **Trusted_Connection = Yes** oder **Integrated Security = SSPI** anstelle von Benutzer-ID und Kennwort die Informationen in der Verbindungszeichenfolge.

## <a name="provider-specific-connection-parameters"></a>Anbieterspezifische-Verbindungsparameter
 Der OLE DB-Anbieter für Microsoft Jet unterstützt verschiedene Anbieter-spezifischen Eigenschaften zusätzlich zu den, die vom ADO definiert werden. Wie bei allen anderen **Verbindung** Parameter können festgelegt werden mithilfe der **Eigenschaften** Auflistung von der **Verbindung** Objekt oder als Teil der Verbindungszeichenfolge angegeben.

 In der folgende Tabelle werden diese Eigenschaften zusammen mit den entsprechenden OLE DB-Eigenschaftsnamen in Klammern aufgeführt.

|Parameter|Description|
|---------------|-----------------|
|Jet OLEDB:Compact freigegebenen Speicherplatz Betrag (DBPROP_JETOLEDB_COMPACTFREESPACESIZE)|Gibt an, eine Schätzung der die Menge des Speicherplatzes in Bytes, die durch die Komprimierung der Datenbank verfügbar gemacht werden können. Dieser Wert ist nur gültig, nachdem eine datenbankverbindung hergestellt wurde.|
|Jet OLEDB:Connection-Steuerelement (DBPROP_JETOLEDB_CONNECTIONCONTROL)|Gibt an, ob Benutzer eine Verbindung mit der Datenbank herstellen können.|
|Jet OLEDB: Systemdatenbank (DBPROP_JETOLEDB_CREATESYSTEMDATABASE) erstellen|Gibt an, ob eine Systemdatenbank erstellt werden soll, wenn Sie eine neue Datenquelle zu erstellen.|
|Jet OLEDB: Database-Sperrmodus (DBPROP_JETOLEDB_DATABASELOCKMODE)|Gibt das Sperrverhalten für diese Datenbank an. Der erste Benutzer beim Öffnen der Datenbank bestimmt den Modus verwendet, während die Datenbank geöffnet ist.|
|Jet OLEDB: Database Password (DBPROP_JETOLEDB_DATABASEPASSWORD)|Gibt das Datenbankkennwort.|
|Jet OLEDB: Kopieren Sie keine Gebietsschemas auf Compact (DBPROP_JETOLEDB_COMPACT_DONTCOPYLOCALE)|Gibt an, ob Jet Gebietsschemainformationen beim Komprimieren einer Datenbank kopieren soll.|
|Jet OLEDB: Database (DBPROP_JETOLEDB_ENCRYPTDATABASE) verschlüsseln|Gibt an, ob es sich bei eine komprimierte Datenbank verschlüsselt werden soll. Wenn diese Eigenschaft nicht festgelegt ist, wird die komprimierte Datenbank verschlüsselt werden, wenn die ursprüngliche Datenbank auch verschlüsselt wurde.|
|Jet OLEDB:Engine Typ (DBPROP_JETOLEDB_ENGINE)|Gibt an, die Speicher-Engine, die für den Zugriff auf den Datenspeicher des aktuellen.|
|Jet Exclusive Async Verzögerung (DBPROP_JETOLEDB_EXCLUSIVEASYNCDELAY)|Gibt die maximale Zeitspanne in Millisekunden, die asynchrone Schreibvorgänge auf Datenträger, wenn die Datenbank exklusiv genutzt wird Jet verzögert werden kann.<br /><br /> Diese Eigenschaft wird ignoriert, es sei denn, **Jet OLEDB: Flush Transaktionstimeout** auf 0 festgelegt ist.|
|Jet OLEDB: Flush Transaktionstimeouts abgelaufen (DBPROP_JETOLEDB_FLUSHTRANSACTIONTIMEOUT)|Gibt die Menge an, wie lange gewartet, bevor Daten in einen Cache zum asynchronen schreiben tatsächlich geschrieben werden auf dem Datenträger. Diese Einstellung überschreibt die Werte für **Jet OLEDB: Shared Async Delay** und **Jet Exclusive Async Verzögerung**.|
|Jet OLEDB: globale Massentransaktionen (DBPROP_JETOLEDB_GLOBALBULKNOTRANSACTIONS)|Gibt an, ob SQL Massentransaktionen durchgeführt werden.|
|Jet OLEDB: globale teilweise Bulk Operations (DBPROP_JETOLEDB_GLOBALBULKPARTIAL)|Gibt das Kennwort beim Öffnen der Datenbank verwendet.|
|Jet OLEDB: ausdrückliches Commit-Sync (DBPROP_JETOLEDB_IMPLICITCOMMITSYNC)|Gibt an, ob im internen implizite Transaktionen vorgenommenen Änderungen im synchronen oder asynchronen Modus geschrieben werden.|
|Jet OLEDB:Lock Verzögerung (DBPROP_JETOLEDB_LOCKDELAY)|Gibt die Anzahl der Millisekunden vor dem Versuch, eine Sperre abzurufen, nachdem ein vorheriger Versuch fehlgeschlagen ist.|
|Jet OLEDB:Lock Wiederholung (DBPROP_JETOLEDB_LOCKRETRY)|Gibt an, wie oft ein Zugriffsversuch auf einen gesperrten Seiten wiederholt wird.|
|Jet OLEDB:Max-Puffergröße (DBPROP_JETOLEDB_MAXBUFFERSIZE)|Gibt die maximale Menge an Arbeitsspeicher in Kilobyte, Jet können vor dem Beginn wegschreiben von Änderungen auf dem Datenträger.|
|Jet OLEDB:Max Sperren pro Datei (DBPROP_JETOLEDB_MAXLOCKSPERFILE)|Gibt die maximale Anzahl von Sperren, die Jet in einer Datenbank platzieren kann. Der Standardwert ist 9500.|
|Jet OLEDB: neue Datenbankkennwort (DBPROP_JETOLEDB_NEWDATABASEPASSWORD)|Gibt das neue Kennwort für diese Datenbank festgelegt werden. Das alte Kennwort befindet sich in **Jet OLEDB: Database Password**.|
|Jet OLEDB: ODBC-Befehlstimeout (DBPROP_JETOLEDB_ODBCCOMMANDTIMEOUT)|Gibt an, dass die Anzahl der Millisekunden, bevor Sie eine ODBC-Remoteabfrage von Jet einen Timeout beendet wird.|
|Jet OLEDB:Page Sperren zu Tabellensperre (DBPROP_JETOLEDB_PAGELOCKSTOTABLELOCK)|Gibt an, wie viele Seiten in einer Transaktion gesperrt werden müssen, bevor Jet versucht wird, um die Sperre zu einer Tabellensperre höher zu stufen. Wenn dieser Wert 0 ist, wird die Sperre niemals höher gestuft.|
|Jet OLEDB:Page Timeout (DBPROP_JETOLEDB_PAGETIMEOUT)|Gibt die Anzahl der Millisekunden lang sich die Jet gewartet wird, bevor geprüft wird, ob der Cache ist veraltet. mit der Datenbankdatei ist.|
|Jet OLEDB:Recycle Long-Wert-Seiten (DBPROP_JETOLEDB_RECYCLELONGVALUEPAGES)|Gibt an, ob Jet aggressiv versuchen sollten, um BLOB-Seiten freizugeben, wenn sie freigegeben werden.|
|Jet OLEDB:Registry Pfad (DBPROP_JETOLEDB_REGPATH)|Gibt an, der Windows-Registrierungsschlüssel, der Werte für das Jet-Datenbankmodul enthält.|
|Jet OLEDB:Reset ISAM-Statistiken (DBPROP_JETOLEDB_RESETISAMSTATS)|Gibt an, ob das Schema **Recordset** DBSCHEMA_JETOLEDB_ISAMSTATS sollten die Leistungsindikatoren zurücksetzen, nach seiner Rückgabe von Informationen zur Anwendungsleistung.|
|Jet OLEDB: freigegebene Async Verzögerung (DBPROP_JETOLEDB_SHAREDASYNCDELAY)|Gibt den maximalen an der Zeit in Millisekunden, kann die Jet verzögern, asynchrone Schreibvorgänge auf Datenträger, wenn die Datenbank im Mehrbenutzermodus geöffnet wird.|
|Jet OLEDB: Database (DBPROP_JETOLEDB_SYSDBPATH)|Gibt den Pfad und Dateiname für Arbeitsgruppen-Informationsdatei (Systemdatenbank) an.|
|Jet OLEDB:Transaction Commit-Modus (DBPROP_JETOLEDB_TXNCOMMITMODE)|Gibt an, ob Jet Daten synchron auf den Datenträger schreibt, oder asynchron, wenn eine Transaktion ein Commit ausgeführt wird.|
|Jet OLEDB:User Commit-Sync (DBPROP_JETOLEDB_USERCOMMITSYNC)|Gibt an, ob Transaktionen vorgenommenen Änderungen im synchronen oder asynchronen Modus geschrieben werden.|

## <a name="provider-specific-recordset-and-command-properties"></a>Anbieterspezifische Recordset und Befehlseigenschaften
 Der Jet-Anbieter unterstützt auch mehrere anbieterspezifische **Recordset** und **Befehl** Eigenschaften. Diese Eigenschaften werden abgerufen, und legen Sie über die **Eigenschaften** Auflistung von der **Recordset** oder **Befehl** Objekt. Die Tabelle enthält die Namen der ADO-Eigenschaft und dem entsprechenden Namen der OLE DB-Eigenschaft in Klammern angegeben.

|Eigenschaftsname|Description|
|-------------------|-----------------|
|Jet OLEDB:Bulk-Transaktionen (DBPROP_JETOLEDB_BULKNOTRANSACTIONS)|Gibt an, ob die SQL-Massenvorgänge durchgeführt werden. Umfangreichen Massenvorgängen können fehlschlagen, wenn transaktiven aufgrund von Verzögerungen bei der Ressource.|
|Jet OLEDB: Enable Fat Cursor (DBPROP_JETOLEDB_ENABLEFATCURSOR)|Gibt an, ob mehrere Zeilen beim Auffüllen eines Recordsets für remote Zeilenquellen Jet zwischengespeichert werden soll.|
|Jet OLEDB:Fat Cursor-Cachegröße (DBPROP_JETOLEDB_FATCURSORMAXROWS)|Gibt die Anzahl der Zeilen in Cache an, wenn remote Zwischenspeichern verwenden. Dieser Wert wird ignoriert, es sei denn, **Jet OLEDB: Enable Fat Cursor** ist "true".|
|Jet OLEDB: inkonsistente (DBPROP_JETOLEDB_INCONSISTENT)|Gibt an, ob Abfrageergebnisse inkonsistente Updates zulassen.|
|Jet OLEDB: (DBPROP_JETOLEDB_LOCKGRANULARITY)-Granularität der Sperren|Gibt an, ob eine Tabelle mit der Sperren auf Zeilenebene geöffnet wird.|
|Jet OLEDB: ODBC-Pass-Through-Anweisung (DBPROP_JETOLEDB_ODBCPASSTHROUGH)|Gibt an, dass Jet in den SQL-Text übergeben soll eine **Befehl** Objekt, das Back-End unverändert.|
|Jet OLEDB:Partial Bulk Operations (DBPROP_JETOLEDB_BULKPARTIAL)|Gibt die Jet-Verhalten an, wenn SQL-DML-Vorgänge fehlschlagen.|
|Jet OLEDB:Pass über Abfrage Bulk-Op (DBPROP_JETOLEDB_PASSTHROUGHBULKOP)|Gibt an, ob Abfragen, die nicht zurückgeben einer **Recordset** werden mit der Datenquelle unverändert übergeben.|
|Jet OLEDB:Pass durch Abfrage der Verbindungszeichenfolge (DBPROP_JETOLEDB_ODBCPASSTHROUGHCONNECTSTRING)|Gibt an, verwendet der Jet-Verbindungszeichenfolge zur Verbindung mit eines remote-Datenspeicher. Dieser Wert wird ignoriert, es sei denn, **Jet OLEDB: ODBC-Pass-Through-Anweisung** ist "true".|
|Jet OLEDB: gespeicherte Abfrage (DBPROP_JETOLEDB_STOREDQUERY)|Gibt an, ob der Befehlstext als gespeicherte Abfrage anstelle einer SQL-Befehl interpretiert werden sollen.|
|Jet OLEDB: Überprüfen Sie die Regeln für die Gruppe (DBPROP_JETOLEDB_VALIDATEONSET)|Gibt an, ob die Jet-Validierungsregeln ausgewertet werden, wenn Spaltendaten festgelegt ist, oder wenn die Änderungen an die Datenbank übergeben werden.|

 Standardmäßig wird von der OLE DB-Anbieter für Microsoft Jet Microsoft Jet-Datenbanken im Lese-/Schreibmodus geöffnet. Um eine Datenbank im schreibgeschützten Modus geöffnet wird, legen Sie die [Modus](../../../ado/reference/ado-api/mode-property-ado.md) Eigenschaft für das ADO **Verbindung** -Objekt **AdModeRead**.

## <a name="command-object-usage"></a>Befehlsobjekt-Nutzung
 Befehlstext in die [Befehl](../../../ado/reference/ado-api/command-object-ado.md) Objekt wird den Microsoft Jet-SQL-Dialekt verwendet. Sie können Abfragen Zeilen zurückgeben, Aktionsabfragen und Tabellennamen im Befehlstext angeben. Allerdings werden die gespeicherte Prozeduren werden nicht unterstützt und sollte nicht angegeben werden.

## <a name="recordset-behavior"></a>Recordset-Verhalten
 Die Microsoft Jet-Datenbank-Engine unterstützt keine dynamische Cursor. Aus diesem Grund der OLE DB-Anbieter für Microsoft Jet unterstützt nicht die **AdLockDynamic** Cursortyp. Wenn ein dynamischer Cursor angefordert wird, der Anbieter einen Keyset-Cursor zurück und Zurücksetzen der [CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md) Eigenschaft an, dass der Typ des [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) zurückgegeben. Wenn Sie einen aktualisierbaren darüber hinaus **Recordset** angefordert wird (**LockType** ist **AdLockOptimistic**, **AdLockBatchOptimistic**, oder **AdLockPessimistic**) der Anbieter auch einen Keyset-Cursor zurück und Zurücksetzen der **CursorType** Eigenschaft.

## <a name="dynamic-properties"></a>Dynamische Eigenschaften
 Der OLE DB-Anbieter für Microsoft Jet fügt verschiedene Eigenschaften in der **Eigenschaften** Auflistung von nicht geöffneten [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md), [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), und [Befehl](../../../ado/reference/ado-api/command-object-ado.md) Objekte.

 Die folgenden Tabellen sind ein Cross-Index der ADO und OLE DB-Namen für jede dynamische Eigenschaft. Der OLE DB Programmer's Reference bezieht sich auf den Namen einer ADO-Eigenschaft, wird der Begriff "Description". Weitere Informationen zu diesen Eigenschaften finden Sie in der OLE DB Programmer's Reference.

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
|Aktuellen Katalog|DBPROP_CURRENTCATALOG|
|Datenquelle|DBPROP_INIT_DATASOURCE|
|Datenquellenname|RÜCKGABEWERT|
|Datenquellenobjekt Threading-Modell|DBPROP_DSOTHREADMODEL|
|Der DBMS-Name|DBPROP_DBMSNAME|
|DBMS-Version|DBPROP_DBMSVER|
|GROUP BY-Unterstützung|DBPROP_GROUPBY|
|Heterogene Tabellenunterstützung|DBPROP_HETEROGENEOUSTABLES|
|Bezeichner Groß-/Kleinschreibung|DBPROP_IDENTIFIERCASE|
|Isolationsstufen|DBPROP_SUPPORTEDTXNISOLEVELS|
|Isolationszurückbehaltung|DBPROP_SUPPORTEDTXNISORETAIN|
|Locale Identifier|DBPROP_INIT_LCID|
|Maximale Indexgröße|DBPROP_MAXINDEXSIZE|
|Maximale Zeilengröße|DBPROP_MAXROWSIZE|
|Maximale Zeilengröße schließt BLOB ein|DBPROP_MAXROWSIZEINCLUDESBLOB|
|Maximale Anzahl von Tabellen in SELECT|DBPROP_MAXTABLESINSELECT|
|Mode|DBPROP_INIT_MODE|
|Mehrere Parametersätze|DBPROP_MULTIPLEPARAMSETS|
|Mehrere Ergebnisse|DBPROP_MULTIPLERESULTS|
|Mehrere Speicherobjekte|DBPROP_MULTIPLESTORAGEOBJECTS|
|Aktualisierung mehrerer Tabellen|DBPROP_MULTITABLEUPDATE|
|NULL-Zusammenstellungsreihenfolge|DBPROP_NULLCOLLATION|
|NULL-Verkettungsverhalten|DBPROP_CONCATNULLBEHAVIOR|
|OLE DB-Version|DBPROP_PROVIDEROLEDBVER|
|OLE-Objektunterstützung|DBPROP_OLEOBJECTS|
|Öffnen Sie die Schemarowset-Unterstützung|DBPROP_OPENROWSETSUPPORT|
|ORDER BY-Spalten in Auswahlliste|DBPROP_ORDERBYCOLUMNSINSELECT|
|Verfügbarkeit der Ausgabeparameter|DBPROP_OUTPUTPARAMETERAVAILABILITY|
|Übergabe durch Verweiszugriffe|DBPROP_BYREFACCESSORS|
|Kennwort|DBPROP_AUTH_PASSWORD|
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
|Nur-Anhängen-Rowset|DBPROP_APPENDONLY|
|Speicherobjekte blockieren|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Lesezeichentyp|DBPROP_BOOKMARKTYPE|
|Jeden|DBPROP_IROWSETLOCATE|
|Angeforderte Lesezeichen|DBPROP_ORDEREDBOOKMARKS|
|Zwischenspeichern von verzögerten Spalten|DBPROP_CACHEDEFERRED|
|Eingefügte Zeilen ändern|DBPROP_CHANGEINSERTEDROWS|
|Spaltenprivilegien|DBPROP_COLUMNRESTRICT|
|Spaltenmengenbenachrichtigung|DBPROP_NOTIFYCOLUMNSET|
|Spalte, die beschreibbaren|DBPROP_MAYWRITECOLUMN|
|Verzögern der Spalte|DBPROP_DEFERRED|
|Speicherobjektaktualisierungen verzögern|DBPROP_DELAYSTORAGEOBJECTS|
|Rückwärts fetchen|DBPROP_CANFETCHBACKWARDS|
|Zeilen halten|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|ILockBytes|DBPROP_ILockBytes|
|Nicht Mobile Zeilen|DBPROP_IMMOBILEROWS|
|IRowset|DBPROP_IRowset|
|IRowsetChange|DBPROP_IRowsetChange|
|IRowsetIdentity|DBPROP_IRowsetIdentity|
|IRowsetIndex|DBPROP_IRowsetIndex|
|IRowsetInfo|DBPROP_IRowsetInfo|
|IRowsetLocate|DBPROP_IRowsestLocate|
|IRowsetResynch||
|IRowsetScroll|DBPROP_IRowsetScroll|
|IRowsetUpdate|DBPROP_IRowsetUpdate|
|ISequentialStream|DBPROP_ISequentialStream|
|IStorage|DBPROP_IStorage|
|IStream|DBPROP_IStream|
|ISupportErrorInfo|DBPROP_ISupportErrorInfo|
|Literale Lesezeichen|DBPROP_LITERALBOOKMARKS|
|Literale Zeilen-ID|DBPROP_LITERALIDENTITY|
|Maximale Anzahl geöffneter Zeilen|DBPROP_MAXOPENROWS|
|Maximale Anzahl ausstehender Zeilen|DBPROP_MAXPENDINGROWS|
|Maximale Zeilenanzahl|DBPROP_MAXROWS|
|Speicherauslastung|DBPROP_MEMORYUSAGE|
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
|Gelöschte Lesezeichen überspringen|DBPROP_BOOKMARKSKIPPED|
|Starke Zeilenidentität|DBPROP_STRONGITDENTITY|
|Aktualisierbarkeit|DBPROP_UPDATABILITY|
|Verwenden von Lesezeichen|DBPROP_BOOKMARKS|

## <a name="command-dynamic-properties"></a>Dynamische Eigenschaften-Befehl
 Die folgenden Eigenschaften werden hinzugefügt, um die **Eigenschaften** Auflistung von der **Befehl** Objekt.

|ADO-Eigenschaftenname|OLE DB-Eigenschaftenname|
|-----------------------|--------------------------|
|Zugriffsreihenfolge|DBPROP_ACCESSORDER|
|Nur-Anhängen-Rowset|DBPROP_APPENDONLY|
|Speicherobjekte blockieren|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Lesezeichentyp|DBPROP_BOOKMARKTYPE|
|Jeden|DBPROP_IROWSETLOCATE|
|Eingefügte Zeilen ändern|DBPROP_CHANGEINSERTEDROWS|
|Spaltenprivilegien|DBPROP_COLUMNRESTRICT|
|Spaltenmengenbenachrichtigung|DBPROP_NOTIFYCOLUMNSET|
|Verzögern der Spalte|DBPROP_DEFERRED|
|Speicherobjektaktualisierungen verzögern|DBPROP_DELAYSTORAGEOBJECTS|
|Rückwärts fetchen|DBPROP_CANFETCHBACKWARDS|
|Zeilen halten|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|ILockBytes|DBPROP_ILockBytes|
|Nicht Mobile Zeilen|DBPROP_IMMOBILEROWS|
|IRowset|DBPROP_IRowset|
|IRowsetChange|DBPROP_IRowsetChange|
|IRowsetIdentity|DBPROP_IRowsetIdentity|
|IRowsetIndex|DBPROP_IRowsetIndex|
|IRowsetInfo|DBPROP_IRowsetInfo|
|IRowsetLocate|DBPROP_IRowsetLocate|
|IRowsetResynch||
|IRowsetScroll|DBPROP_IRowsetScroll|
|IRowsetUpdate|DBPROP_IRowsetUpdate|
|ISequentialStream|DBPROP_ISequentialStream|
|IStorage|DBPROP_IStorage|
|IStream|DBPROP_IStream|
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
|Serverdaten beim Einfügen|DBPROP_SERVERDATAONINSERT|
|Gelöschte Lesezeichen überspringen|DBPROP_BOOKMARKSKIP|
|Starke Zeilenidentität|DBPROP_STRONGIDENTITY|
|Aktualisierbarkeit|DBPROP_UPDATABILITY|
|Verwenden von Lesezeichen|DBPROP_BOOKMARKS|

 Bestimmte Implementierungsdetails und funktionalen Informationen zu OLE DB-Anbieter für Microsoft Jet, finden Sie unter [Jet-Anbieters](https://msdn.microsoft.com/library/windows/desktop/ms722791.aspx) in der OLE DB-Dokumentation.
