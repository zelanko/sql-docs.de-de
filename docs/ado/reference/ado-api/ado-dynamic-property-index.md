---
title: ADO-Index für dynamische Eigenschaften | Microsoft-Dokumentation
ms.prod: sql
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- dynamic properties [ADO], index
ms.assetid: 80d389dd-46ef-459f-b0d4-6f712fc4f32d
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8dd1263d19972124166e1e11d91c8370fc3a9ff0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66696736"
---
# <a name="ado-dynamic-property-index"></a>ADO – Index für dynamische Eigenschaften
Datenanbieter, Dienstanbietern und Dienstkomponenten können dynamische Eigenschaften zum Hinzufügen der **Eigenschaften** Auflistungen von nicht geöffneten [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) und [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekte. Ein angegebenen Anbieter kann auch weitere Eigenschaften einfügen, wenn diese Objekte geöffnet werden. Einige dieser Eigenschaften finden Sie in der [ADO – dynamische Eigenschaften](../../../ado/reference/ado-api/ado-dynamic-properties.md) Abschnitt. Mehr finden Sie unter den jeweiligen Anbietern in der [Anhang A: Anbieter](../../../ado/guide/appendixes/appendix-a-providers.md) Abschnitt.  
  
 Die folgenden Tabellen sind Cross-indexes der ADO und OLE DB-Namen für jede dynamische Eigenschaft der standard OLE DB-Anbieter. Ihr Anbieter möglicherweise mehr Eigenschaften als aufgelisteten hier hinzufügen. Spezifische Informationen zu anbieterspezifischen dynamischen Eigenschaften finden Sie unter der Dokumentation Ihres Anbieters.  
  
 Der OLE DB Programmer's Reference bezieht sich auf den Namen einer ADO-Eigenschaft, wird der Begriff "Description". Weitere Informationen zu diesen standard Eigenschaften suchen, oder Durchsuchen Sie den Index in die [OLE DB-Dokumentation](https://msdn.microsoft.com/library/windows/desktop/ms722784.aspx)für die OLE DB-Eigenschaft mit dem Namen.  
  
## <a name="connection-dynamic-properties"></a>Dynamische Eigenschaften der Verbindung  
  
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
|Speicherort|DBPROP_INIT_LOCATION|  
|Maximale Indexgröße|DBPROP_MAXINDEXSIZE|  
|Maximale Zeilengröße|DBPROP_MAXROWSIZE|  
|Maximale Zeilengröße schließt BLOB ein|DBPROP_MAXROWSIZEINCLUDESBLOB|  
|Maximale Anzahl von Tabellen in SELECT|DBPROP_MAXTABLESINSELECT|  
|Modus|DBPROP_INIT_MODE|  
|Mehrere Parametersätze|DBPROP_MULTIPLEPARAMSETS|  
|Mehrere Ergebnisse|DBPROP_MULTIPLERESULTS|  
|Mehrere Speicherobjekte|DBPROP_MULTIPLESTORAGEOBJECTS|  
|Aktualisierung mehrerer Tabellen|DBPROP_MULTITABLEUPDATE|  
|NULL-Zusammenstellungsreihenfolge|DBPROP_NULLCOLLATION|  
|NULL-Verkettungsverhalten|DBPROP_CONCATNULLBEHAVIOR|  
|OLE DB-Diensten|DBPROP_INIT_OLEDBSERVICES|  
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
 Beachten Sie, dass die **dynamische Eigenschaften** von der **Recordset** Objekt navigieren, die außerhalb des gültigen Bereichs (nicht mehr verfügbar) Wenn Sie die **Recordset** geschlossen wird.  
  
|ADO-Eigenschaftenname|OLE DB-Eigenschaftenname|  
|-----------------------|--------------------------|  
|IAccessor|DBPROP_IACCESSOR|  
|IChapteredRowset||  
|IColumnsInfo|DBPROP_ICOLUMNSINFO|  
|IColumnsRowset|DBPROP_ICOLUMNSROWSET|  
|IConnectionPointContainer|DBPROP_ICONNECTIONPOINTCONTAINER|  
|IConvertType||  
|ILockBytes|DBPROP_ILOCKBYTES|  
|IRowset|DBPROP_IROWSET|  
|IDBAsynchStatus|DBPROP_IDBASYNCHSTATUS|  
|IParentRowset||  
|IRowsetChange|DBPROP_IROWSETCHANGE|  
|IRowsetExactScroll||  
|IRowsetFind|DBPROP_IROWSETFIND|  
|IRowsetIdentity|DBPROP_IROWSETIDENTITY|  
|IRowsetInfo|DBPROP_IROWSETINFO|  
|IRowsetLocate|DBPROP_IROWSETLOCATE|  
|IRowsetRefresh|DBPROP_IROWSETREFRESH|  
|IRowsetResynch||  
|IRowsetScroll|DBPROP_IROWSETSCROLL|  
|IRowsetUpdate|DBPROP_IROWSETUPDATE|  
|IRowsetView|DBPROP_IROWSETVIEW|  
|IRowsetIndex|DBPROP_IROWSETINDEX|  
|ISequentialStream|DBPROP_ISEQUENTIALSTREAM|  
|IStorage|DBPROP_ISTORAGE|  
|IStream|DBPROP_ISTREAM|  
|ISupportErrorInfo|DBPROP_ISUPPORTERRORINFO|  
|Zugriffsreihenfolge|DBPROP_ACCESSORDER|  
|Nur-Anhängen-Rowset|DBPROP_APPENDONLY|  
|Asynchrone Rowsetverarbeitung|DBPROP_ROWSET_ASYNCH|  
|Automatische Neuberechnung|DBPROP_ADC_AUTORECALC|  
|Hintergrund Abrufgröße|DBPROP_ASYNCHFETCHSIZE|  
|Background Thread Priority|DBPROP_ASYNCHTHREADPRIORITY|  
|Batchgröße|DBPROP_ADC_BATCHSIZE|  
|Speicherobjekte blockieren|DBPROP_BLOCKINGSTORAGEOBJECTS|  
|Lesezeichentyp|DBPROP_BOOKMARKTYPE|  
|Jeden|DBPROP_IROWSETLOCATE|  
|Angeforderte Lesezeichen|DBPROP_ORDEREDBOOKMARKS|  
|Zwischenspeichern von untergeordneten Zeilen|DBPROP_ADC_CACHECHILDROWS|  
|Zwischenspeichern von verzögerten Spalten|DBPROP_CACHEDEFERRED|  
|Eingefügte Zeilen ändern|DBPROP_CHANGEINSERTEDROWS|  
|Spaltenprivilegien|DBPROP_COLUMNRESTRICT|  
|Spaltenmengenbenachrichtigung|DBPROP_NOTIFYCOLUMNSET|  
|Spalte, die beschreibbaren|DBPROP_MAYWRITECOLUMN|  
|Befehlstimeout|DBPROP_COMMANDTIMEOUT|  
|Cursor-Engine-Version|DBPROP_ADC_CEVER|  
|Verzögern der Spalte|DBPROP_DEFERRED|  
|Speicherobjektaktualisierungen verzögern|DBPROP_DELAYSTORAGEOBJECTS|  
|Rückwärts fetchen|DBPROP_CANFETCHBACKWARDS|  
|Filtervorgänge|DBPROP_FILTERCOMPAREOPS|  
|Suchvorgänge|DBPROP_FINDCOMPAREOPS|  
|Ausgeblendete Spalten (Anzahl)|DBPROP_HIDDENCOLUMNS|  
|Zeilen halten|DBPROP_CANHOLDROWS|  
|Nicht Mobile Zeilen|DBPROP_IMMOBILEROWS|  
|Anfängliche Abrufgröße|DBPROP_ASYNCHPREFETCHSIZE|  
|Literale Lesezeichen|DBPROP_LITERALBOOKMARKS|  
|Literale Zeilen-ID|DBPROP_LITERALIDENTITY|  
|Verwalten von Änderungsstatus|DBPROP_ADC_MAINTAINCHANGESTATUS|  
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
|Private1||  
|Schneller Neustart|DBPROP_QUICKRESTART|  
|Wiedereintretende Ereignisse|DBPROP_REENTRANTEVENTS|  
|Gelöschte Zeilen entfernen|DBPROP_REMOVEDELETED|  
|Mehrere Änderungen melden|DBPROP_REPORTMULTIPLECHANGES|  
|Reshape Name|DBPROP_ADC_RESHAPENAME|  
|Resync-Befehl|DBPROP_ADC_CUSTOMRESYNCH|  
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
|Gelöschte Lesezeichen überspringen|DBPROP_BOOKMARKSKIPPED|  
|Starke Zeilenidentität|DBPROP_STRONGIDENTITY|  
|Eindeutige Katalogressource|DBPROP_ADC_UNIQUECATALOG|  
|Eindeutige Zeilen|DBPROP_UNIQUEROWS|  
|Eindeutiges Schema|DBPROP_ADC_UNIQUESCHEMA|  
|Eindeutige Tabelle|DBPROP_ADC_UNIQUETABLE|  
|Aktualisierbarkeit|DBPROP_UPDATABILITY|  
|Aktualisieren von Kriterien|DBPROP_ADC_UPDATECRITERIA|  
|Aktualisieren Sie die erneute Synchronisierung|DBPROP_ADC_UPDATERESYNC|  
|Verwenden von Lesezeichen|DBPROP_BOOKMARKS|
