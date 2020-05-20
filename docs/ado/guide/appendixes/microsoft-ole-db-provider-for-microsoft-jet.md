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
author: rothja
ms.author: jroth
ms.openlocfilehash: 204aca25a330dd912e1a9354adc92bbb7c58f847
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763211"
---
# <a name="microsoft-ole-db-provider-for-microsoft-jet-overview"></a>Übersicht über Microsoft OLE DB-Anbieter für Microsoft Jet
Der OLE DB Anbieter für Microsoft Jet ermöglicht ADO den Zugriff auf Microsoft Jet-Datenbanken.

## <a name="connection-string-parameters"></a>Parameter der Verbindungszeichenfolge
 Legen Sie das *Provider* -Argument der [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) -Eigenschaft auf Folgendes fest, um eine Verbindung mit diesem Anbieter herzustellen:

```vb
Microsoft.Jet.OLEDB.4.0
```

 Beim Lesen der [Provider](../../../ado/reference/ado-api/provider-property-ado.md) -Eigenschaft wird auch diese Zeichenfolge zurückgegeben.

## <a name="typical-connection-string"></a>Typische Verbindungs Zeichenfolge
 Eine typische Verbindungs Zeichenfolge für diesen Anbieter lautet:

```vb
"Provider=Microsoft.Jet.OLEDB.4.0;Data Source=databaseName;User ID=MyUserID;Password=MyPassword;"
```

 Die Zeichenfolge besteht aus folgenden Schlüsselwörtern:

|Stichwort|BESCHREIBUNG|
|-------------|-----------------|
|**Anbieter**|Gibt den OLE DB Anbieter für Microsoft Jet an.|
|**Data Source**|Gibt den Daten bankpfad und den Dateinamen an (z `c:\Northwind.mdb` . b.).|
|**Benutzer-ID**|Gibt den Benutzernamen an. Wenn dieses Schlüsselwort nicht angegeben wird, wird standardmäßig die Zeichenfolge " `admin` " verwendet.|
|**Kennwort**|Gibt das Benutzer Kennwort an. Wenn dieses Schlüsselwort nicht angegeben wird, wird standardmäßig die leere Zeichenfolge ("") verwendet.|

> [!NOTE]
>  Wenn Sie eine Verbindung mit einem Datenquellen Anbieter herstellen, der die Windows-Authentifizierung unterstützt, sollten Sie in der Verbindungs Zeichenfolge **Trusted_Connection = yes** oder **Integrated Security = SSPI** anstelle von Benutzer-ID und Kennwort angeben.

## <a name="provider-specific-connection-parameters"></a>Anbieterspezifische Verbindungsparameter
 Der OLE DB Anbieter für Microsoft Jet unterstützt neben den, die von ADO definiert werden, mehrere anbieterspezifische dynamische Eigenschaften. Wie bei allen anderen **Verbindungs** Parametern können diese mithilfe der **Properties** -Auflistung des **Connection** -Objekts oder als Teil der Verbindungs Zeichenfolge festgelegt werden.

 In der folgenden Tabelle werden diese Eigenschaften mit dem entsprechenden OLE DB Eigenschaftsnamen in Klammern aufgelistet.

|Parameter|Beschreibung|
|---------------|-----------------|
|Jet OLEDB: Compact freigegebene Speicherplatz Menge (DBPROP_JETOLEDB_COMPACTFREESPACESIZE)|Gibt eine Schätzung des Speicherplatzes in Bytes an, der durch die Komprimierung der Datenbank freigegeben werden kann. Dieser Wert ist nur gültig, wenn eine Datenbankverbindung hergestellt wurde.|
|Jet OLEDB: Verbindungs Steuerung (DBPROP_JETOLEDB_CONNECTIONCONTROL)|Gibt an, ob Benutzer eine Verbindung mit der Datenbank herstellen können.|
|Jet OLEDB: Create System Database (DBPROP_JETOLEDB_CREATESYSTEMDATABASE)|Gibt an, ob beim Erstellen einer neuen Datenquelle eine Systemdatenbank erstellt werden soll.|
|Jet OLEDB: Daten Bank Sperrmodus (DBPROP_JETOLEDB_DATABASELOCKMODE)|Gibt den Sperrmodus für diese Datenbank an. Der erste Benutzer, der die Datenbank öffnet, legt den Modus fest, der verwendet wird, während die Datenbank geöffnet ist.|
|Jet OLEDB: Daten Bank Kennwort (DBPROP_JETOLEDB_DATABASEPASSWORD)|Gibt das Daten Bank Kennwort an.|
|Jet OLEDB: Gebiets Schema nicht auf Compact kopieren (DBPROP_JETOLEDB_COMPACT_DONTCOPYLOCALE)|Gibt an, ob Jet Gebiets Schema Informationen kopieren soll, wenn eine Datenbank komprimiert wird.|
|Jet OLEDB: Datenbank verschlüsseln (DBPROP_JETOLEDB_ENCRYPTDATABASE)|Gibt an, ob eine komprimierte Datenbank verschlüsselt werden soll. Wenn diese Eigenschaft nicht festgelegt ist, wird die komprimierte Datenbank verschlüsselt, wenn die ursprüngliche Datenbank ebenfalls verschlüsselt wurde.|
|Jet OLEDB: Engine-Typ (DBPROP_JETOLEDB_ENGINE)|Gibt die Speicher-Engine an, die zum Zugreifen auf den aktuellen Datenspeicher verwendet wird.|
|Jet OLEDB: exklusive Async-Verzögerung (DBPROP_JETOLEDB_EXCLUSIVEASYNCDELAY)|Gibt die maximale Zeitdauer in Millisekunden an, die der Jet asynchrone Schreibvorgänge auf den Datenträger verzögern kann, wenn die Datenbank exklusiv geöffnet wird.<br /><br /> Diese Eigenschaft wird ignoriert, es sei denn, **Jet OLEDB: Flush Transaction Timeout** ist auf 0 festgelegt.|
|Jet OLEDB: Timeout für Transaktions Timeout (DBPROP_JETOLEDB_FLUSHTRANSACTIONTIMEOUT)|Gibt an, wie lange gewartet werden soll, bevor Daten, die in einem Cache für asynchrone Schreibvorgänge gespeichert werden, tatsächlich auf den Datenträger geschrieben werden. Diese Einstellung überschreibt die Werte für **Jet OLEDB: Shared Async Delay** und **Jet OLEDB: Exclusive Async Delay**.|
|Jet OLEDB: globale Massen Transaktionen (DBPROP_JETOLEDB_GLOBALBULKNOTRANSACTIONS)|Gibt an, ob SQL-Massen Transaktionen transaktiv sind.|
|Jet OLEDB: globale partielle Massen Massen Vorgänge (DBPROP_JETOLEDB_GLOBALBULKPARTIAL)|Gibt das Kennwort an, das zum Öffnen der Datenbank verwendet wird.|
|Jet OLEDB: implizite Commit-Synchronisierung (DBPROP_JETOLEDB_IMPLICITCOMMITSYNC)|Gibt an, ob Änderungen, die in internen impliziten Transaktionen vorgenommen wurden, im synchronen oder asynchronen Modus geschrieben werden.|
|Jet OLEDB: Sperr Verzögerung (DBPROP_JETOLEDB_LOCKDELAY)|Gibt die Anzahl der Millisekunden an, die gewartet werden soll, bevor versucht wird, eine Sperre abzurufen, nachdem ein vorheriger Versuch fehlgeschlagen ist.|
|Jet OLEDB: Wiederholungsversuch für Sperre (DBPROP_JETOLEDB_LOCKRETRY)|Gibt an, wie oft versucht wird, auf eine gesperrte Seite zuzugreifen.|
|Jet OLEDB: maximale Puffergröße (DBPROP_JETOLEDB_MAXBUFFERSIZE)|Gibt die maximale Arbeitsspeicher Menge in Kilobyte an, die Jet verwenden kann, bevor die Änderungen auf den Datenträger geleert werden.|
|Jet OLEDB: maximale Anzahl von Sperren pro Datei (DBPROP_JETOLEDB_MAXLOCKSPERFILE)|Gibt die maximale Anzahl von Sperren an, die Jet in einer Datenbank platzieren kann. Der Standardwert ist 9500.|
|Jet OLEDB: neues Daten Bank Kennwort (DBPROP_JETOLEDB_NEWDATABASEPASSWORD)|Gibt das neue Kennwort an, das für diese Datenbank festgelegt werden soll. Das alte Kennwort wird in **Jet OLEDB: Database Password**gespeichert.|
|Jet OLEDB: Timeout für ODBC-Befehl (DBPROP_JETOLEDB_ODBCCOMMANDTIMEOUT)|Gibt die Anzahl von Millisekunden an, nach der ein Timeout für eine ODBC-Remote Abfrage von Jet auftritt.|
|Jet OLEDB: Seiten sperren zu Tabellensperre (DBPROP_JETOLEDB_PAGELOCKSTOTABLELOCK)|Gibt an, wie viele Seiten innerhalb einer Transaktion gesperrt sein müssen, bevor Jet versucht, die Sperre auf eine Tabellensperre herauf zusetzen. Wenn dieser Wert 0 ist, wird die Sperre nie herauf gestuft.|
|Jet OLEDB: Seiten Timeout (DBPROP_JETOLEDB_PAGETIMEOUT)|Gibt die Anzahl der Millisekunden an, die Jet wartet, bevor überprüft wird, ob der Cache mit der Datenbankdatei veraltet ist.|
|Jet OLEDB: wieder verwenden von lang wertigen Seiten (DBPROP_JETOLEDB_RECYCLELONGVALUEPAGES)|Gibt an, ob Jet aggressiv versuchen soll, BLOB-Seiten freizugeben, wenn Sie freigegeben werden.|
|Jet OLEDB: Registrierungs Pfad (DBPROP_JETOLEDB_REGPATH)|Gibt den Windows-Registrierungsschlüssel an, der Werte für die Jet-Datenbank-Engine enthält.|
|Jet OLEDB: Zurücksetzen von ISAM-Statistiken (DBPROP_JETOLEDB_RESETISAMSTATS)|Gibt an, ob das Schema **Recordset** DBSCHEMA_JETOLEDB_ISAMSTATS seine Leistungsindikatoren zurücksetzen soll, nachdem es Leistungsinformationen zurückgegeben hat.|
|Jet OLEDB: freigegebene Async-Verzögerung (DBPROP_JETOLEDB_SHAREDASYNCDELAY)|Gibt die maximale Zeitspanne in Millisekunden an, die der Jet asynchrone Schreibvorgänge auf den Datenträger verzögern kann, wenn die Datenbank im Multibenutzermodus geöffnet wird.|
|Jet OLEDB: System Datenbank (DBPROP_JETOLEDB_SYSDBPATH)|Gibt den Pfad und den Dateinamen für die Arbeitsgruppen-Informationsdatei (Systemdatenbank) an.|
|Jet OLEDB: transaktionscommitmodus (DBPROP_JETOLEDB_TXNCOMMITMODE)|Gibt an, ob Jet Daten synchron oder asynchron auf den Datenträger schreibt, wenn für eine Transaktion ein Commit ausgeführt wird.|
|Jet OLEDB: Synchronisierung von Benutzer Commit (DBPROP_JETOLEDB_USERCOMMITSYNC)|Gibt an, ob Änderungen, die in Transaktionen vorgenommen wurden, im synchronen oder asynchronen Modus geschrieben werden.|

## <a name="provider-specific-recordset-and-command-properties"></a>Anbieterspezifische Recordset-und Befehls Eigenschaften
 Der Jet-Anbieter unterstützt auch mehrere anbieterspezifische **Recordset** -und **Befehls** Eigenschaften. Der Zugriff auf diese Eigenschaften und die Festlegung erfolgt über die **Properties** -Auflistung des **Recordsets** oder **Befehls** Objekts. In der Tabelle werden der ADO-Eigenschaftsname und der zugehörige OLE DB Eigenschaften Name in Klammern aufgelistet.

|Eigenschaftenname|Beschreibung|
|-------------------|-----------------|
|Jet OLEDB: Massen Transaktionen (DBPROP_JETOLEDB_BULKNOTRANSACTIONS)|Gibt an, ob SQL-Massen Vorgänge transaktiv sind. Bei umfangreichen Massen Vorgängen kann es bei Transaktionen aufgrund von Ressourcen Verzögerungen zu Fehlern kommen.|
|Jet OLEDB: Aktivieren von FAT-Cursorn (DBPROP_JETOLEDB_ENABLEFATCURSOR)|Gibt an, ob Jet beim Auffüllen eines Recordsets für Remote Zeilen Quellen mehrere Zeilen zwischenspeichern soll.|
|Jet OLEDB: FAT Cursor Cache Size (DBPROP_JETOLEDB_FATCURSORMAXROWS)|Gibt die Anzahl der Zeilen an, die zwischengespeichert werden sollen, wenn die Zeilen Zwischenspeicherung von Remote Daten speichern Dieser Wert wird ignoriert, es sei denn, **Jet OLEDB: enable FAT Cursors** ist true.|
|Jet OLEDB: inkonsistent (DBPROP_JETOLEDB_INCONSISTENT)|Gibt an, ob die Abfrageergebnisse inkonsistente Updates zulassen.|
|Jet OLEDB: Sperr Granularität (DBPROP_JETOLEDB_LOCKGRANULARITY)|Gibt an, ob eine Tabelle mit Sperren auf Zeilenebene geöffnet wird.|
|Jet OLEDB: ODBC-Pass-Through-Anweisung (DBPROP_JETOLEDB_ODBCPASSTHROUGH)|Gibt an, dass Jet den SQL-Text in einem **Befehls** Objekt unverändert an das Back-End übergeben soll.|
|Jet OLEDB: partielle Massen Vorgänge (DBPROP_JETOLEDB_BULKPARTIAL)|Gibt das Verhalten von Jet an, wenn SQL DML-Vorgänge fehlschlagen.|
|Jet OLEDB: Massen Vorgang durchlaufen der Abfrage (DBPROP_JETOLEDB_PASSTHROUGHBULKOP)|Gibt an, ob Abfragen, die kein **Recordset** zurückgeben, unverändert an die Datenquelle übermittelt werden.|
|Jet OLEDB: Verbindungs Zeichenfolge der Pass-Through-Abfrage (DBPROP_JETOLEDB_ODBCPASSTHROUGHCONNECTSTRING)|Gibt die Jet-Verbindungs Zeichenfolge zum Herstellen einer Verbindung mit einem Remote Datenspeicher an. Dieser Wert wird ignoriert, es sei denn, **Jet OLEDB: die ODBC-Pass-Through-Anweisung** ist true.|
|Jet OLEDB: gespeicherte Abfrage (DBPROP_JETOLEDB_STOREDQUERY)|Gibt an, ob der Befehls Text anstelle eines SQL-Befehls als gespeicherte Abfrage interpretiert werden soll.|
|Jet OLEDB: Validieren von Regeln für Set (DBPROP_JETOLEDB_VALIDATEONSET)|Gibt an, ob die Jet-Validierungsregeln ausgewertet werden, wenn Spaltendaten festgelegt werden oder wenn die Änderungen an die Datenbank übertragen werden.|

 Standardmäßig öffnet der OLE DB Anbieter für Microsoft Jet Microsoft Jet-Datenbanken im Lese-/Schreibmodus. Um eine Datenbank im schreibgeschützten Modus zu öffnen, legen Sie die [Mode](../../../ado/reference/ado-api/mode-property-ado.md) -Eigenschaft des ADO- **Verbindungs** Objekts auf **admoderead**fest.

## <a name="command-object-usage"></a>Verwendung von Befehls Objekten
 Der Befehls Text im [Command](../../../ado/reference/ado-api/command-object-ado.md) -Objekt verwendet den Microsoft Jet SQL-Dialekt. Sie können Zeilen rückgabeabfragen, Aktions Abfragen und Tabellennamen im Befehls Text angeben. gespeicherte Prozeduren werden jedoch nicht unterstützt und sollten nicht angegeben werden.

## <a name="recordset-behavior"></a>Recordsetverhalten
 Dynamic Cursors werden von der Microsoft Jet-Datenbank-Engine nicht unterstützt. Daher unterstützt der OLE DB Anbieter für Microsoft Jet den **adlockdynamic** -Cursortyp nicht. Wenn ein dynamischer Cursor angefordert wird, gibt der Anbieter einen Keyset-Cursor zurück und setzt die [CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md) -Eigenschaft zurück, um den Typ des zurückgegebenen [Recordsets](../../../ado/reference/ado-api/recordset-object-ado.md) anzugeben. Wenn ein Aktualisier bares **Recordset** angefordert wird (**LockType** ist " **adlockoptimi"**, " **adlockbatchoptimi"** oder " **adlockpessimi"**), gibt der Anbieter außerdem einen Keyset-Cursor zurück und setzt die **CursorType** -Eigenschaft zurück.

## <a name="dynamic-properties"></a>Dynamische Eigenschaften
 Der OLE DB Anbieter für Microsoft Jet fügt verschiedene dynamische Eigenschaften in die **Properties** -Sammlung der nicht geöffneten [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md)-, [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)-und [Command](../../../ado/reference/ado-api/command-object-ado.md) -Objekte ein.

 Die folgenden Tabellen sind ein Index übergreifender Index der ADO-und OLE DB Namen für jede dynamische Eigenschaft. Die OLE DB Programmierer-Referenz verweist auf einen ADO-Eigenschaftsnamen mit dem Begriff "Description". Weitere Informationen zu diesen Eigenschaften finden Sie in der OLE DB Programmierer-Referenz.

## <a name="connection-dynamic-properties"></a>Dynamische Eigenschaften der Verbindung
 Die folgenden Eigenschaften werden der **Properties** -Auflistung des **Connection** -Objekts hinzugefügt.

|ADO-Eigenschafts Name|Eigenschaften Name OLE DB|
|-----------------------|--------------------------|
|Aktive Sitzungen|DBPROP_ACTIVESESSIONS|
|Asynchroner Abbruch|DBPROP_ASYNCTXNABORT|
|Asynchroner Commit|DBPROP_ASYNCTNXCOMMIT|
|Autocommit-Isolations Stufen|DBPROP_SESS_AUTOCOMMITISOLEVELS|
|Katalog Speicherort|DBPROP_CATALOGLOCATION|
|Katalog Begriff|DBPROP_CATALOGTERM|
|Spalten Definition|DBPROP_COLUMNDEFINITION|
|Aktueller Katalog|DBPROP_CURRENTCATALOG|
|Data source|DBPROP_INIT_DATASOURCE|
|Datenquellenname|DBPROP_DATASOURCENAME|
|Datenquellen Objekt-Threading Modell|DBPROP_DSOTHREADMODEL|
|DBMS-Name|DBPROP_DBMSNAME|
|DBMS-Version|DBPROP_DBMSVER|
|Group by-Unterstützung|DBPROP_GROUPBY|
|Unterstützung heterogener Tabellen|DBPROP_HETEROGENEOUSTABLES|
|Sensitivität bei Bezeichnern|DBPROP_IDENTIFIERCASE|
|Isolationsstufen|DBPROP_SUPPORTEDTXNISOLEVELS|
|Isolations Beibehaltung|DBPROP_SUPPORTEDTXNISORETAIN|
|Locale Identifier|DBPROP_INIT_LCID|
|Maximale Index Größe|DBPROP_MAXINDEXSIZE|
|Maximale Zeilengröße|DBPROP_MAXROWSIZE|
|Maximale Zeilengröße schließt BLOB ein|DBPROP_MAXROWSIZEINCLUDESBLOB|
|Maximale Anzahl von Tabellen in SELECT|DBPROP_MAXTABLESINSELECT|
|Mode|DBPROP_INIT_MODE|
|Mehrere Parameter Sätze|DBPROP_MULTIPLEPARAMSETS|
|Mehrere Ergebnisse|DBPROP_MULTIPLERESULTS|
|Mehrere Speicher Objekte|DBPROP_MULTIPLESTORAGEOBJECTS|
|Aktualisierung von mehreren Tabellen|DBPROP_MULTITABLEUPDATE|
|NULL-Sortierreihenfolge|DBPROP_NULLCOLLATION|
|NULL-Verkettungs Verhalten|DBPROP_CONCATNULLBEHAVIOR|
|OLE DB Version|DBPROP_PROVIDEROLEDBVER|
|OLE-Objekt Unterstützung|DBPROP_OLEOBJECTS|
|Open Rowset-Unterstützung|DBPROP_OPENROWSETSUPPORT|
|Order by-Spalten in Auswahlliste|DBPROP_ORDERBYCOLUMNSINSELECT|
|Verfügbarkeit der Ausgabe Parameter|DBPROP_OUTPUTPARAMETERAVAILABILITY|
|Pass-by-Verweis-Accessoren|DBPROP_BYREFACCESSORS|
|Kennwort|DBPROP_AUTH_PASSWORD|
|Persistente ID-Typ|DBPROP_PERSISTENTIDTYPE|
|Abbruch Verhalten vorbereiten|DBPROP_PREPAREABORTBEHAVIOR|
|Commit-Verhalten vorbereiten|DBPROP_PREPARECOMMITBEHAVIOR|
|Prozedur Begriff|DBPROP_PROCEDURETERM|
|Prompt|DBPROP_INIT_PROMPT|
|Anzeige Name des Anbieters|DBPROP_PROVIDERFRIENDLYNAME|
|Anbietername|DBPROP_PROVIDERFILENAME|
|Anbieterversion|DBPROP_PROVIDERVER|
|Schreibgeschützte Datenquelle|DBPROP_DATASOURCEREADONLY|
|Rowsetkonvertierungen für Befehl|DBPROP_ROWSETCONVERSIONSONCOMMAND|
|Schema Begriff|DBPROP_SCHEMATERM|
|Schema Verwendung|DBPROP_SCHEMAUSAGE|
|SQL-Unterstützung|DBPROP_SQLSUPPORT|
|Strukturierter Speicher|DBPROP_STRUCTUREDSTORAGE|
|Unterstützung für Unterabfragen|DBPROP_SUBQUERIES|
|Tabellen Begriff|DBPROP_TABLETERM|
|Transaktions-DDL|DBPROP_SUPPORTEDTXNDDL|
|Benutzer-ID|DBPROP_AUTH_USERID|
|Benutzername|DBPROP_USERNAME|
|Fensterhandle|DBPROP_INIT_HWND|

## <a name="recordset-dynamic-properties"></a>Dynamische Recordset-Eigenschaften
 Die folgenden Eigenschaften werden der **Properties** -Auflistung des **Recordset** -Objekts hinzugefügt.

|ADO-Eigenschafts Name|Eigenschaften Name OLE DB|
|-----------------------|--------------------------|
|Zugriffs Reihenfolge|DBPROP_ACCESSORDER|
|Nur Append-Rowset|DBPROP_APPENDONLY|
|Blockieren von Speicher Objekten|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Lese Zeichentyp|DBPROP_BOOKMARKTYPE|
|Fragmentteils|DBPROP_IROWSETLOCATE|
|Geordnete Lesezeichen|DBPROP_ORDEREDBOOKMARKS|
|Verzögerte Spalten Zwischenspeichern|DBPROP_CACHEDEFERRED|
|Eingefügte Zeilen ändern|DBPROP_CHANGEINSERTEDROWS|
|Spalten Privilegien|DBPROP_COLUMNRESTRICT|
|Benachrichtigung über Spalten Satz|DBPROP_NOTIFYCOLUMNSET|
|Spalten beschreibbar|DBPROP_MAYWRITECOLUMN|
|Spalte zurückstellen|DBPROP_DEFERRED|
|Speicher Objekt Aktualisierungen verzögern|DBPROP_DELAYSTORAGEOBJECTS|
|Rückwärts abrufen|DBPROP_CANFETCHBACKWARDS|
|Halten von Zeilen|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|ILockBytes|DBPROP_ILockBytes|
|Immobile-Zeilen|DBPROP_IMMOBILEROWS|
|IRowset|DBPROP_IRowset|
|IRowsetChange|DBPROP_IRowsetChange|
|Irowdie tidentity|DBPROP_IRowsetIdentity|
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
|Literale Zeilen Identität|DBPROP_LITERALIDENTITY|
|Maximal geöffnete Zeilen|DBPROP_MAXOPENROWS|
|Maximale Anzahl ausstehender Zeilen|DBPROP_MAXPENDINGROWS|
|Maximale Zeilen Anzahl|DBPROP_MAXROWS|
|Speicherauslastung|DBPROP_MEMORYUSAGE|
|Benachrichtigungs Granularität|DBPROP_NOTIFICATIONGRANULARITY|
|Benachrichtigungs Phasen|DBPROP_NOTIFICATIONPHASES|
|Transaktive Objekte|DBPROP_TRANSACTEDOBJECT|
|Änderungen anderer Benutzer sichtbar|DBPROP_OTHERUPDATEDELETE|
|Einfügungen anderer Benutzer sichtbar|DBPROP_OTHERINSERT|
|Eigene Änderungen sichtbar|DBPROP_OWNUPDATEDELETE|
|Eigene Einfügungen sichtbar|DBPROP_OWNINSERT|
|Bei Abbruch beibehalten|DBPROP_ABORTPRESERVE|
|Bei Commit beibehalten|DBPROP_COMMITPRESERVE|
|Schneller Neustart|DBPROP_QUICKRESTART|
|Reentrante Ereignisse|DBPROP_REENTRANTEVENTS|
|Gelöschte Zeilen entfernen|DBPROP_REMOVEDELETED|
|Mehrere Änderungen melden|DBPROP_REPORTMULTIPLECHANGES|
|Ausstehende Einfügungen zurück|DBPROP_RETURNPENDINGINSERTS|
|Benachrichtigung zum Löschen von Zeilen|DBPROP_NOTIFYROWDELETE|
|Zeilen erste Änderungs Benachrichtigung|DBPROP_NOTIFYROWFIRSTCHANGE|
|Benachrichtigung über Zeilen Einfügung|DBPROP_NOTIFYROWINSERT|
|Zeilen Privilegien|DBPROP_ROWRESTRICT|
|Benachrichtigung zum erneuten Synchronisieren von Zeilen|DBPROP_NOTIFYROWRESYNCH|
|Zeilen Thread Modell|DBPROP_ROWTHREADMODEL|
|Benachrichtigung über Zeilen Rückgängigmachen|DBPROP_NOTIFYROWUNDOCHANGE|
|Benachrichtigung zum Löschen von Zeilen rückgängig|DBPROP_NOTIFYROWUNDODELETE|
|Benachrichtigung zum Einfügen von Zeilen rückgängig|DBPROP_NOTIFYROWUNDOINSERT|
|Benachrichtigung über Zeilen Aktualisierung|DBPROP_NOTIFYROWUPDATE|
|Benachrichtigung zum Abrufen von Rowset-Abruf Änderungen|DBPROP_NOTIFYROWSETFETCHPOSISIONCHANGE|
|Rowset-Freigabe Benachrichtigung|DBPROP_NOTIFYROWSETRELEASE|
|Bildlauf rückwärts|DBPROP_CANSCROLLBACKWARDS|
|Löschen gelöschter Lesezeichen|DBPROP_BOOKMARKSKIPPED|
|Starke Zeilen Identität|DBPROP_STRONGITDENTITY|
|Aktualisierbarkeit|DBPROP_UPDATABILITY|
|Verwenden von Lesezeichen|DBPROP_BOOKMARKS|

## <a name="command-dynamic-properties"></a>Dynamische Eigenschaften des Befehls
 Die folgenden Eigenschaften werden der **Properties** -Auflistung des **Command** -Objekts hinzugefügt.

|ADO-Eigenschafts Name|Eigenschaften Name OLE DB|
|-----------------------|--------------------------|
|Zugriffs Reihenfolge|DBPROP_ACCESSORDER|
|Nur Append-Rowset|DBPROP_APPENDONLY|
|Blockieren von Speicher Objekten|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Lese Zeichentyp|DBPROP_BOOKMARKTYPE|
|Fragmentteils|DBPROP_IROWSETLOCATE|
|Eingefügte Zeilen ändern|DBPROP_CHANGEINSERTEDROWS|
|Spalten Privilegien|DBPROP_COLUMNRESTRICT|
|Benachrichtigung über Spalten Satz|DBPROP_NOTIFYCOLUMNSET|
|Spalte zurückstellen|DBPROP_DEFERRED|
|Speicher Objekt Aktualisierungen verzögern|DBPROP_DELAYSTORAGEOBJECTS|
|Rückwärts abrufen|DBPROP_CANFETCHBACKWARDS|
|Halten von Zeilen|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|ILockBytes|DBPROP_ILockBytes|
|Immobile-Zeilen|DBPROP_IMMOBILEROWS|
|IRowset|DBPROP_IRowset|
|IRowsetChange|DBPROP_IRowsetChange|
|Irowdie tidentity|DBPROP_IRowsetIdentity|
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
|Literale Zeilen Identität|DBPROP_LITERALIDENTITY|
|Sperrmodus|DBPROP_LOCKMODE|
|Maximal geöffnete Zeilen|DBPROP_MAXOPENROWS|
|Maximale Anzahl ausstehender Zeilen|DBPROP_MAXPENDINGROWS|
|Maximale Zeilen Anzahl|DBPROP_MAXROWS|
|Benachrichtigungs Granularität|DBPROP_NOTIFICATIONGRANULARITY|
|Benachrichtigungs Phasen|DBPROP_NOTIFICATIONPHASES|
|Transaktive Objekte|DBPROP_TRANSACTEDOBJECT|
|Änderungen anderer Benutzer sichtbar|DBPROP_OTHERUPDATEDELETE|
|Einfügungen anderer Benutzer sichtbar|DBPROP_OTHERINSERT|
|Eigene Änderungen sichtbar|DBPROP_OWNUPDATEDELETE|
|Eigene Einfügungen sichtbar|DBPROP_OWNINSERT|
|Bei Abbruch beibehalten|DBPROP_ABORTPRESERVE|
|Bei Commit beibehalten|DBPROP_COMMITPRESERVE|
|Schneller Neustart|DBPROP_QUICKRESTART|
|Reentrante Ereignisse|DBPROP_REENTRANTEVENTS|
|Gelöschte Zeilen entfernen|DBPROP_REMOVEDELETED|
|Mehrere Änderungen melden|DBPROP_REPORTMULTIPLECHANGES|
|Ausstehende Einfügungen zurück|DBPROP_RETURNPENDINGINSERTS|
|Benachrichtigung zum Löschen von Zeilen|DBPROP_NOTIFYROWDELETE|
|Zeilen erste Änderungs Benachrichtigung|DBPROP_NOTIFYROWFIRSTCHANGE|
|Benachrichtigung über Zeilen Einfügung|DBPROP_NOTIFYROWINSERT|
|Zeilen Privilegien|DBPROP_ROWRESTRICT|
|Benachrichtigung zum erneuten Synchronisieren von Zeilen|DBPROP_NOTIFYROWRESYNCH|
|Zeilen Thread Modell|DBPROP_ROWTHREADMODEL|
|Benachrichtigung über Zeilen Rückgängigmachen|DBPROP_NOTIFYROWUNDOCHANGE|
|Benachrichtigung zum Löschen von Zeilen rückgängig|DBPROP_NOTIFYROWUNDODELETE|
|Benachrichtigung zum Einfügen von Zeilen rückgängig|DBPROP_NOTIFYROWUNDOINSERT|
|Benachrichtigung über Zeilen Aktualisierung|DBPROP_NOTIFYROWUPDATE|
|Benachrichtigung zum Abrufen von Rowset-Abruf Änderungen|DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE|
|Rowset-Freigabe Benachrichtigung|DBPROP_NOTIFYROWSETRELEASE|
|Bildlauf rückwärts|DBPROP_CANSCROLLBACKWARDS|
|Server Daten beim Einfügen|DBPROP_SERVERDATAONINSERT|
|Löschen gelöschter Lesezeichen|DBPROP_BOOKMARKSKIP|
|Starke Zeilen Identität|DBPROP_STRONGIDENTITY|
|Aktualisierbarkeit|DBPROP_UPDATABILITY|
|Verwenden von Lesezeichen|DBPROP_BOOKMARKS|

 Spezifische Implementierungsdetails und Funktions Informationen zum OLE DB Anbieter für Microsoft Jet finden Sie unter [Jet Provider](https://msdn.microsoft.com/library/windows/desktop/ms722791.aspx) in der OLE DB-Dokumentation.
