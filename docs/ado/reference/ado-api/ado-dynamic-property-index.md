---
title: Dynamischer ADO-Eigenschafts Index | Microsoft-Dokumentation
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
ms.openlocfilehash: 9eb88905f56abf9c1c702f5fd73cbe61a1bcde3d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67921081"
---
# <a name="ado-dynamic-property-index"></a>ADO – Index für dynamische Eigenschaften
Datenanbieter, Dienstanbieter und Dienst Komponenten können den **Eigenschaften** Auflistungen der nicht geöffneten [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) -und [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekte dynamische Eigenschaften hinzufügen. Ein bestimmter Anbieter kann auch zusätzliche Eigenschaften einfügen, wenn diese Objekte geöffnet werden. Einige dieser Eigenschaften werden im Abschnitt " [Eigenschaften](../../../ado/reference/ado-api/ado-dynamic-properties.md) von ADO.net" aufgeführt. Weitere Informationen finden Sie unter den jeweiligen Anbietern im Abschnitt [Anhang A: Anbieter](../../../ado/guide/appendixes/appendix-a-providers.md) .  
  
 Die folgenden Tabellen sind Index übergreifende Indizes der ADO-und OLE DB Namen für jede dynamische Eigenschaft des Standard OLE DB Anbieters. Ihre Anbieter können weitere Eigenschaften hinzufügen, als hier aufgeführt sind. Informationen zu den spezifischen Informationen zu anbieterspezifischen dynamischen Eigenschaften finden Sie in der Dokumentation des Anbieters.  
  
 Die OLE DB Programmierer-Referenz verweist auf einen ADO-Eigenschaftsnamen mit dem Begriff "Beschreibung". Weitere Informationen zu diesen Standardeigenschaften erhalten Sie, indem Sie den Index in der [OLE DB-Dokumentation](https://msdn.microsoft.com/library/windows/desktop/ms722784.aspx)für die OLE DB-Eigenschaft nach Namen suchen oder durchsuchen.  
  
## <a name="connection-dynamic-properties"></a>Dynamische Eigenschaften der Verbindung  
  
|ADO-Eigenschafts Name|Eigenschaften Name OLE DB|  
|-----------------------|--------------------------|  
|Aktive Sitzungen|DBPROP_ACTIVESESSIONS|  
|Asynchroner Abbruch|DBPROP_ASYNCTXNABORT|  
|Asynchroner Commit|DBPROP_ASYNCTNXCOMMIT|  
|Autocommit-Isolations Stufen|DBPROP_SESS_AUTOCOMMITISOLEVELS|  
|Katalog Speicherort|DBPROP_CATALOGLOCATION|  
|Katalog Begriff|DBPROP_CATALOGTERM|  
|Spalten Definition|DBPROP_COLUMNDEFINITION|  
|Verbindungstimeout|DBPROP_INIT_TIMEOUT|  
|Aktueller Katalog|DBPROP_CURRENTCATALOG|  
|Data source|DBPROP_INIT_DATASOURCE|  
|Name der Datenquelle|DBPROP_DATASOURCENAME|  
|Datenquellen Objekt-Threading Modell|DBPROP_DSOTHREADMODEL|  
|DBMS-Name|DBPROP_DBMSNAME|  
|DBMS-Version|DBPROP_DBMSVER|  
|Extended Properties|DBPROP_INIT_PROVIDERSTRING|  
|Group by-Unterstützung|DBPROP_GROUPBY|  
|Unterstützung heterogener Tabellen|DBPROP_HETEROGENEOUSTABLES|  
|Sensitivität bei Bezeichnern|DBPROP_IDENTIFIERCASE|  
|Anfangskatalog|DBPROP_INIT_CATALOG|  
|Isolationsstufen|DBPROP_SUPPORTEDTXNISOLEVELS|  
|Isolations Beibehaltung|DBPROP_SUPPORTEDTXNISORETAIN|  
|Locale Identifier|DBPROP_INIT_LCID|  
|Location|DBPROP_INIT_LOCATION|  
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
|OLE DB Dienste|DBPROP_INIT_OLEDBSERVICES|  
|OLE DB Version|DBPROP_PROVIDEROLEDBVER|  
|OLE-Objekt Unterstützung|DBPROP_OLEOBJECTS|  
|Open Rowset-Unterstützung|DBPROP_OPENROWSETSUPPORT|  
|Order by-Spalten in Auswahlliste|DBPROP_ORDERBYCOLUMNSINSELECT|  
|Verfügbarkeit der Ausgabe Parameter|DBPROP_OUTPUTPARAMETERAVAILABILITY|  
|Pass-by-Verweis-Accessoren|DBPROP_BYREFACCESSORS|  
|Kennwort|DBPROP_AUTH_PASSWORD|  
|Sicherheitsinformationen permanent speichern|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|  
|Persistente ID-Typ|DBPROP_PERSISTENTIDTYPE|  
|Abbruch Verhalten vorbereiten|DBPROP_PREPAREABORTBEHAVIOR|  
|Commit-Verhalten vorbereiten|DBPROP_PREPARECOMMITBEHAVIOR|  
|Prozedur Begriff|DBPROP_PROCEDURETERM|  
|Auffordern|DBPROP_INIT_PROMPT|  
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
|Fenster handle|DBPROP_INIT_HWND|  
  
## <a name="recordset-dynamic-properties"></a>Dynamische Recordset-Eigenschaften  
 Beachten Sie, dass die **dynamischen Eigenschaften** des **Recordset** -Objekts den Gültigkeitsbereich verlassen (nicht verfügbar), wenn das **Recordset** geschlossen wird.  
  
|ADO-Eigenschafts Name|Eigenschaften Name OLE DB|  
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
|Iparser-Rowset||  
|IRowsetChange|DBPROP_IROWSETCHANGE|  
|Irowantexactscroll||  
|IRowsetFind|DBPROP_IROWSETFIND|  
|Irowdie tidentity|DBPROP_IROWSETIDENTITY|  
|IRowsetInfo|DBPROP_IROWSETINFO|  
|IRowsetLocate|DBPROP_IROWSETLOCATE|  
|Irowsee trefresh|DBPROP_IROWSETREFRESH|  
|IRowsetResynch||  
|IRowsetScroll|DBPROP_IROWSETSCROLL|  
|IRowsetUpdate|DBPROP_IROWSETUPDATE|  
|Irowsetview|DBPROP_IROWSETVIEW|  
|IRowsetIndex|DBPROP_IROWSETINDEX|  
|ISequentialStream|DBPROP_ISEQUENTIALSTREAM|  
|IStorage|DBPROP_ISTORAGE|  
|IStream|DBPROP_ISTREAM|  
|ISupportErrorInfo|DBPROP_ISUPPORTERRORINFO|  
|Zugriffs Reihenfolge|DBPROP_ACCESSORDER|  
|Nur Append-Rowset|DBPROP_APPENDONLY|  
|Asynchrone Rowsetverarbeitung|DBPROP_ROWSET_ASYNCH|  
|Automatisch neu berechnen|DBPROP_ADC_AUTORECALC|  
|Hintergrundfetch-Größe|DBPROP_ASYNCHFETCHSIZE|  
|Background Thread Priority|DBPROP_ASYNCHTHREADPRIORITY|  
|Batchgröße|DBPROP_ADC_BATCHSIZE|  
|Blockieren von Speicher Objekten|DBPROP_BLOCKINGSTORAGEOBJECTS|  
|Lese Zeichentyp|DBPROP_BOOKMARKTYPE|  
|Fragmentteils|DBPROP_IROWSETLOCATE|  
|Geordnete Lesezeichen|DBPROP_ORDEREDBOOKMARKS|  
|Untergeordnete Zeilen Zwischenspeichern|DBPROP_ADC_CACHECHILDROWS|  
|Verzögerte Spalten Zwischenspeichern|DBPROP_CACHEDEFERRED|  
|Eingefügte Zeilen ändern|DBPROP_CHANGEINSERTEDROWS|  
|Spalten Privilegien|DBPROP_COLUMNRESTRICT|  
|Benachrichtigung über Spalten Satz|DBPROP_NOTIFYCOLUMNSET|  
|Spalten beschreibbar|DBPROP_MAYWRITECOLUMN|  
|Befehls Timeout|DBPROP_COMMANDTIMEOUT|  
|Cursor-Engine-Version|DBPROP_ADC_CEVER|  
|Spalte zurückstellen|DBPROP_DEFERRED|  
|Speicher Objekt Aktualisierungen verzögern|DBPROP_DELAYSTORAGEOBJECTS|  
|Rückwärts abrufen|DBPROP_CANFETCHBACKWARDS|  
|Filter Vorgänge|DBPROP_FILTERCOMPAREOPS|  
|Suchen von Vorgängen|DBPROP_FINDCOMPAREOPS|  
|Ausgeblendete Spalten (Anzahl)|DBPROP_HIDDENCOLUMNS|  
|Halten von Zeilen|DBPROP_CANHOLDROWS|  
|Immobile-Zeilen|DBPROP_IMMOBILEROWS|  
|Anfängliche Abruf Größe|DBPROP_ASYNCHPREFETCHSIZE|  
|Literale Lesezeichen|DBPROP_LITERALBOOKMARKS|  
|Literale Zeilen Identität|DBPROP_LITERALIDENTITY|  
|Beibehalten des Änderungs Status|DBPROP_ADC_MAINTAINCHANGESTATUS|  
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
|Private1||  
|Schneller Neustart|DBPROP_QUICKRESTART|  
|Reentrante Ereignisse|DBPROP_REENTRANTEVENTS|  
|Gelöschte Zeilen entfernen|DBPROP_REMOVEDELETED|  
|Mehrere Änderungen melden|DBPROP_REPORTMULTIPLECHANGES|  
|Name der erneuten Form|DBPROP_ADC_RESHAPENAME|  
|Befehl zum erneuten Synchronisieren|DBPROP_ADC_CUSTOMRESYNCH|  
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
|Server Cursor|DBPROP_SERVERCURSOR|  
|Löschen gelöschter Lesezeichen|DBPROP_BOOKMARKSKIPPED|  
|Starke Zeilen Identität|DBPROP_STRONGIDENTITY|  
|Eindeutiger Katalog|DBPROP_ADC_UNIQUECATALOG|  
|Eindeutige Zeilen|DBPROP_UNIQUEROWS|  
|Eindeutiges Schema|DBPROP_ADC_UNIQUESCHEMA|  
|Eindeutige Tabelle|DBPROP_ADC_UNIQUETABLE|  
|Aktualisierbarkeit|DBPROP_UPDATABILITY|  
|Update Kriterien|DBPROP_ADC_UPDATECRITERIA|  
|Neusynchronisierung aktualisieren|DBPROP_ADC_UPDATERESYNC|  
|Verwenden von Lesezeichen|DBPROP_BOOKMARKS|
