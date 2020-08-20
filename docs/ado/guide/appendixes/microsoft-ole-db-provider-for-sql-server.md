---
description: Übersicht über den Microsoft OLE DB-Anbieter für SQL Server
title: Microsoft OLE DB-Anbieter für SQL Server | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: a39166406be321d01ab6d0dc2acd2488d7b64da5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88454042"
---
# <a name="microsoft-ole-db-provider-for-sql-server-overview"></a>Übersicht über den Microsoft OLE DB-Anbieter für SQL Server
Der Microsoft OLE DB-Anbieter für SQL Server SQLOLEDB ermöglicht ADO den Zugriff auf Microsoft SQL Server.

> [!IMPORTANT]
> Der Microsoft OLE DB-Anbieter für SQL Server (SQLOLEDB) ist weiterhin veraltet, und es wird nicht empfohlen, ihn für neue Entwicklungsarbeiten zu verwenden. Verwenden Sie stattdessen den neuen [Microsoft OLE DB-Treiber für SQL Server](../../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL), der mit den aktuellsten Serverfeatures aktualisiert wird.

## <a name="connection-string-parameters"></a>Parameter der Verbindungszeichenfolge
 Legen Sie das *Provider* -Argument auf die [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) -Eigenschaft fest, um eine Verbindung mit diesem Anbieter herzustellen:

```vb
SQLOLEDB
```

 Dieser Wert kann auch mit der [Provider](../../../ado/reference/ado-api/provider-property-ado.md) -Eigenschaft festgelegt oder gelesen werden.

## <a name="typical-connection-string"></a>Typische Verbindungs Zeichenfolge
 Eine typische Verbindungs Zeichenfolge für diesen Anbieter lautet:

```vb
"Provider=SQLOLEDB;Data Source=serverName;"
Initial Catalog=databaseName;
User ID=MyUserID;Password=MyPassword;"
```

 Die Zeichenfolge besteht aus folgenden Schlüsselwörtern:

|Schlüsselwort|Beschreibung|
|-------------|-----------------|
|**Anbieter**|Gibt den OLE DB Anbieter für SQL Server an.|
|**Datenquelle** oder **Server**|Gibt den Namen eines Servers an.|
|**Anfangs Katalog** oder **Datenbank**|Gibt den Namen einer Datenbank auf dem Server an.|
|**Benutzer-ID** oder **UID**|Gibt den Benutzernamen an (für SQL Server-Authentifizierung).|
|**Kennwort** oder **pwd**|Gibt das Benutzer Kennwort an (für SQL Server-Authentifizierung).|

> [!NOTE]
>  Wenn Sie eine Verbindung mit einem Datenquellen Anbieter herstellen, der die Windows-Authentifizierung unterstützt, sollten Sie in der Verbindungs Zeichenfolge **Trusted_Connection = yes** oder **Integrated Security = SSPI** anstelle von Benutzer-ID und Kennwort angeben.

## <a name="provider-specific-connection-parameters"></a>Anbieterspezifische Verbindungsparameter
 Der Anbieter unterstützt mehrere Anbieterspezifische Verbindungsparameter zusätzlich zu den von ADO definierten Verbindungsparametern. Wie bei den ADO-Verbindungs Eigenschaften können diese anbieterspezifischen Eigenschaften über die [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) -Auflistung einer [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) festgelegt werden oder als Teil von " **ConnectionString**" festgelegt werden.

|Parameter|Beschreibung|
|---------------|-----------------|
|Trusted_Connection|Gibt den Benutzer Authentifizierungsmodus an. Dieser Wert kann auf **Ja** oder **Nein**festgelegt werden. Der Standardwert ist **Nein**. Wenn diese Eigenschaft auf " **Ja**" festgelegt ist, verwendet SQLOLEDB den Microsoft Windows NT-Authentifizierungsmodus, um den Benutzer Zugriff auf die SQL Server Datenbank zu autorisieren, die durch die Eigenschaften Werte **Location** und [DataSource](../../../ado/reference/ado-api/datasource-property-ado.md) angegeben wird. Wenn diese Eigenschaft auf **No**festgelegt ist, verwendet SQLOLEDB den gemischten Modus, um den Benutzer Zugriff auf die SQL Server Datenbank zu autorisieren. Die SQL Server-Anmeldung und das Kennwort werden in den Eigenschaften **Benutzer-ID** und **Kennwort** angegeben.|
|Aktuelle Sprache|Gibt einen SQL Server Sprachen Namen an. Identifiziert die für die Auswahl und Formatierung von Systemnachrichten verwendete Sprache. Die Sprache muss auf der SQL Server installiert sein, andernfalls tritt beim Öffnen der Verbindung ein Fehler auf.|
|Netzwerkadresse|Gibt die Netzwerkadresse des SQL Server an, der von der **Location** -Eigenschaft angegeben wird.|
|Network Library|Gibt den Namen der Netzwerk Bibliothek (dll) an, die für die Kommunikation mit dem SQL Server verwendet wird. Der Name sollte weder den Pfad noch die DLL-Dateinamenerweiterung enthalten. Der Standardwert wird von der SQL Server Client Konfiguration bereitgestellt.|
|Verfahren für Vorbereitung verwenden|Bestimmt, ob SQL Server temporär gespeicherte Prozeduren erstellt, wenn Befehle vorbereitet werden (von der **vorbereiteten** Eigenschaft).|
|Automatisches Übersetzen|Gibt an, ob OEM/ANSI-Zeichen konvertiert werden. Diese Eigenschaft kann auf " **true** " oder " **false**" festgelegt werden. Der Standardwert ist **True**. Wenn diese Eigenschaft auf **true**festgelegt ist, führt SQLOLEDB eine OEM/ANSI-Zeichen Konvertierung aus, wenn Multibyte-Zeichen folgen von der SQL Server abgerufen oder an diese gesendet werden. Wenn diese Eigenschaft auf **false**festgelegt ist, führt SQLOLEDB keine OEM/ANSI-Zeichen Konvertierung für Multibyte-Zeichen folgen Daten aus.|
|Packet Size|Gibt eine Netzwerk Paketgröße in Bytes an. Der Eigenschafts Wert für die Paketgröße muss zwischen 512 und 32767 liegen. Die standardmäßige SQLOLEDB-Netzwerk Paketgröße ist 4096.|
|Anwendungsname|Gibt den Namen der Client Anwendung an.|
|Workstation ID|Eine Zeichenfolge, die die Arbeitsstation identifiziert.|

## <a name="command-object-usage"></a>Verwendung von Befehls Objekten
 SQLOLEDB akzeptiert ein Amalgam von ODBC, ANSI und SQL Server spezifischer Transact-SQL als gültige Syntax. Die folgende SQL-Anweisung beispielsweise verwendet eine ODBC SQL-Escapesequenz, um die LCASE-Zeichenfolgenfunktion anzugeben:

```sql
SELECT customerid={fn LCASE(CustomerID)} FROM Customers

```

 LCASE gibt eine Zeichenfolge zurück und konvertiert alle Großbuchstaben in ihre kleingeschriebenen Entsprechungen. Die ANSI SQL-Zeichen folgen Funktion Lower führt den gleichen Vorgang aus, sodass die folgende SQL-Anweisung eine ANSI-Entsprechung der zuvor dargestellten ODBC-Anweisung ist:

```sql
SELECT customerid=LOWER(CustomerID) FROM Customers

```

 SQLOLEDB verarbeitet beide Formen der Anweisung erfolgreich, wenn Sie als Text für einen Befehl angegeben wird.

## <a name="stored-procedures"></a>Gespeicherte Prozeduren
 Wenn Sie eine gespeicherte Prozedur SQL Server mit einem SQLOLEDB-Befehl ausführen, verwenden Sie die ODBC-Prozedur Rückruf-Escapesequenz im Befehls Text. SQLOLEDB verwendet dann den Remote Prozedur aufrufsmechanismus von SQL Server, um die Befehls Verarbeitung zu optimieren. Beispielsweise ist die folgende ODBC SQL-Anweisung der bevorzugte Befehls Text über das Transact-SQL-Formular:

## <a name="odbc-sql"></a>ODBC SQL

```vb
{call SalesByCategory('Produce', '1995')}

```

## <a name="transact-sql"></a>Transact-SQL

```sql
EXECUTE SalesByCategory 'Produce', '1995'

```

## <a name="sql-server-features"></a>SQL Server Features
 Mit SQL Server kann ADO XML für **Befehls** Eingaben verwenden und Ergebnisse im XML-Datenstrom Format anstelle von **Recordset** -Objekten abrufen. Weitere Informationen finden Sie unter [Verwenden von Streams für Befehlseingaben](../../../ado/guide/data/command-streams.md) und [Abrufen von Resultsets in Streams](../../../ado/guide/data/retrieving-resultsets-into-streams.md).

### <a name="accessing-sql_variant-data-using-mdac-27-mdac-28-or-windows-dac-60"></a>Zugreifen auf sql_variant Daten mithilfe von MDAC 2,7, MDAC 2,8 oder Windows DAC 6,0
 Microsoft SQL Server hat einen Datentyp namens **sql_variant**. Ähnlich wie bei der **DBTYPE_VARIANT**von OLE DB können mit dem **sql_variant** -Datentyp Daten verschiedener Typen gespeichert werden. Es gibt jedoch einige wichtige Unterschiede zwischen **DBTYPE_VARIANT** und **sql_variant**. ADO verarbeitet auch als **sql_variant** Wert gespeicherte Daten anders als bei der Verarbeitung anderer Datentypen. In der folgenden Liste werden Probleme beschrieben, die beim Zugriff auf SQL Server in Spalten vom Typ **sql_variant**gespeicherten Daten zu beachten sind.

-   In MDAC 2,7, MDAC 2,8 und Windows Data Access Components (Windows DAC) 6,0 unterstützt der OLE DB Anbieter für SQL Server den **sql_variant** Typ. Der OLE DB Anbieter für ODBC nicht.

-   Der **sql_variant** -Typ stimmt nicht genau mit dem Datentyp **DBTYPE_VARIANT** überein.  Der **sql_variant** -Typ unterstützt einige neue Untertypen, die von DBTYPE_VARIANT nicht unterstützt **werden,** einschließlich **GUID**, **ANSI** (Non-Unicode)-Zeichen folgen und **bigint**. Die Verwendung von anderen als den zuvor aufgeführten Untertypen funktioniert ordnungsgemäß.

-   Der **sql_variant** - **Untertyp ist nicht mit** der Größe des **DBTYPE_DECIMAL** identisch.

-   Mehrere Datentyp Umwandlungen führen zu Typen, die nicht mit Stimmen. Das Umwandeln einer **sql_variant** mit einem Untertyp von **GUID** in eine **DBTYPE_VARIANT** führt beispielsweise zu einem Untertyp von **SAFEARRAY**(Bytes). Wenn Sie diesen Typ wieder in einen **sql_variant** zurückkehren, führt dies zu einem neuen Untertyp von **Array**(Bytes).

-   **Recordsetfelder** , die **sql_variant** Daten enthalten, können Remote (gemarshallt) oder nur persistent gespeichert werden, wenn die **sql_variant** bestimmte Untertypen enthält. Der Versuch, Daten mit den folgenden nicht unterstützten Untertypen zu Remote oder beizubehalten, führt zu einem Laufzeitfehler (nicht unterstützte Konvertierung) vom Microsoft-Persistenzanbieter (MSPersist): **VT_VARIANT**, **VT_RECORD**, **VT_ILLEGAL**, **VT_UNKNOWN**, **VT_BSTR**und **VT_DISPATCH.**

-   Der OLE DB Anbieter für SQL Server in MDAC 2,7, MDAC 2,8 und Windows DAC 6,0 verfügt über eine dynamische Eigenschaft namens **native Varianten zulassen** , die es Entwicklern ermöglicht, im Gegensatz zu einer **DBTYPE_VARIANT**auf die **sql_variant** in der nativen Form zuzugreifen. Wenn diese Eigenschaft festgelegt ist und ein **Recordset** mit der Client Cursor-Engine (**adUseClient**) geöffnet wird, schlägt der **Recordset. Open** -Befehl fehl. Wenn diese Eigenschaft festgelegt ist und ein **Recordset** mit Server Cursorn (**adsereserver**) geöffnet wird, wird der **Recordset. Open** -Befehl erfolgreich ausgeführt, aber der Zugriff auf Spalten vom Typ **sql_variant** führt zu einem Fehler.

-   In Client Anwendungen, die MDAC 2,5 verwenden, können **sql_variant** Daten mit Abfragen für Microsoft SQL Server verwendet werden. Die Werte der **sql_variant** Daten werden jedoch als Zeichen folgen behandelt. Solche Client Anwendungen sollten auf MDAC 2,7, MDAC 2,8 oder Windows DAC 6,0 aktualisiert werden.

## <a name="recordset-behavior"></a>Recordsetverhalten
 SQLOLEDB kann SQL Server Cursor nicht verwenden, um das von vielen Befehlen generierte mehrfache Ergebnis zu unterstützen. Wenn ein Consumer ein Recordset anfordert, das SQL Server Cursor Unterstützung erfordert, tritt ein Fehler auf, wenn der verwendete Befehls Text mehr als ein einzelnes Recordset als Ergebnis generiert.

 Scrollfähige SQLOLEDB-Recordsets werden von SQL Server Cursorn unterstützt. SQL Server auferlegt Einschränkungen bei Cursorn, die von anderen Benutzern der Datenbank vorgenommenen Änderungen unterschieden werden. Insbesondere können die Zeilen in einigen Cursorn nicht sortiert werden, und der Versuch, ein Recordset mit einem Befehl zu erstellen, der eine SQL ORDER BY-Klausel enthält, kann fehlschlagen.

## <a name="dynamic-properties"></a>Dynamische Eigenschaften
 Der Microsoft OLE DB-Anbieter für SQL Server fügt verschiedene dynamische Eigenschaften in die **Properties** -Sammlung der nicht geöffneten [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md)-, [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)-und [Command](../../../ado/reference/ado-api/command-object-ado.md) -Objekte ein.

 Die folgenden Tabellen sind ein Index übergreifender Index der ADO-und OLE DB Namen für jede dynamische Eigenschaft. Die OLE DB Programmierer-Referenz verweist auf einen ADO-Eigenschaftsnamen mit dem Begriff "Beschreibung". Weitere Informationen zu diesen Eigenschaften finden Sie in der OLE DB Programmierer-Referenz. Suchen Sie im Index nach dem Namen der OLE DB Eigenschaft, oder siehe [Anhang C: OLE DB Eigenschaften](https://msdn.microsoft.com/deded3ff-f508-4e1b-b2b1-fd9afd3bd292).

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
|Verbindungstimeout|DBPROP_INIT_TIMEOUT|
|Aktueller Katalog|DBPROP_CURRENTCATALOG|
|Data source|DBPROP_INIT_DATASOURCE|
|Datenquellenname|DBPROP_DATASOURCENAME|
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
|Maximale Index Größe|DBPROP_MAXINDEXSIZE|
|Maximale Zeilengröße|DBPROP_MAXROWSIZE|
|Maximale Zeilengröße schließt BLOB ein|DBPROP_MAXROWSIZEINCLUDESBLOB|
|Maximale Anzahl von Tabellen in SELECT|DBPROP_MAXTABLESINSELECT|
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
|Sicherheitsinformationen permanent speichern|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|
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
|Blockieren von Speicher Objekten|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Lese Zeichentyp|DBPROP_BOOKMARKTYPE|
|Fragmentteils|DBPROP_IROWSETLOCATE|
|Eingefügte Zeilen ändern|DBPROP_CHANGEINSERTEDROWS|
|Spalten Privilegien|DBPROP_COLUMNRESTRICT|
|Benachrichtigung über Spalten Satz|DBPROP_NOTIFYCOLUMNSET|
|Befehls Timeout|DBPROP_COMMANDTIMEOUT|
|Spalte zurückstellen|DBPROP_DEFERRED|
|Speicher Objekt Aktualisierungen verzögern|DBPROP_DELAYSTORAGEOBJECTS|
|Rückwärts abrufen|DBPROP_CANFETCHBACKWARDS|
|Halten von Zeilen|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|Immobile-Zeilen|DBPROP_IMMOBILEROWS|
|IRowset|DBPROP_IRowset|
|IRowsetChange|DBPROP_IRowsetChange|
|Irowdie tidentity|DBPROP_IRowsetIdentity|
|IRowsetInfo|DBPROP_IRowsetInfo|
|IRowsetLocate|DBPROP_IRowsestLocate|
|IRowsetResynch||
|IRowsetScroll|DBPROP_IRowsetScroll|
|IRowsetUpdate|DBPROP_IRowsetUpdate|
|ISequentialStream|DBPROP_ISequentialStream|
|ISupportErrorInfo|DBPROP_ISupportErrorInfo|
|Literale Lesezeichen|DBPROP_LITERALBOOKMARKS|
|Literale Zeilen Identität|DBPROP_LITERALIDENTITY|
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
|Benachrichtigung zum Abrufen von Rowset-Abruf Änderungen|DBPROP_NOTIFYROWSETFETCHPOSISIONCHANGE|
|Rowset-Freigabe Benachrichtigung|DBPROP_NOTIFYROWSETRELEASE|
|Bildlauf rückwärts|DBPROP_CANSCROLLBACKWARDS|
|Server Cursor|DBPROP_SERVERCURSOR|
|Löschen gelöschter Lesezeichen|DBPROP_BOOKMARKSKIPPED|
|Starke Zeilen Identität|DBPROP_STRONGITDENTITY|
|Eindeutige Zeilen|DBPROP_UNIQUEROWS|
|Aktualisierbarkeit|DBPROP_UPDATABILITY|
|Verwenden von Lesezeichen|DBPROP_BOOKMARKS|

## <a name="command-dynamic-properties"></a>Dynamische Eigenschaften des Befehls
 Die folgenden Eigenschaften werden der **Properties** -Auflistung des **Command** -Objekts hinzugefügt.

|ADO-Eigenschafts Name|Eigenschaften Name OLE DB|
|-----------------------|--------------------------|
|Zugriffs Reihenfolge|DBPROP_ACCESSORDER|
|Basispfad|SSPROP_STREAM_BASEPATH|
|Blockieren von Speicher Objekten|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Lese Zeichentyp|DBPROP_BOOKMARKTYPE|
|Fragmentteils|DBPROP_IROWSETLOCATE|
|Eingefügte Zeilen ändern|DBPROP_CHANGEINSERTEDROWS|
|Spalten Privilegien|DBPROP_COLUMNRESTRICT|
|Benachrichtigung über Spalten Satz|DBPROP_NOTIFYCOLUMNSET|
|Inhaltstyp|SSPROP_STREAM_CONTENTTYPE|
|Automatisches Abrufen von Cursor|SSPROP_CURSORAUTOFETCH|
|Spalte zurückstellen|DBPROP_DEFERRED|
|Vorbereitung zurückstellen|SSPROP_DEFERPREPARE|
|Speicher Objekt Aktualisierungen verzögern|DBPROP_DELAYSTORAGEOBJECTS|
|Rückwärts abrufen|DBPROP_CANFETCHBACKWARDS|
|Halten von Zeilen|DBPROP_CANHOLDROWS|
|IAccessor|DBPROP_IAccessor|
|IColumnsInfo|DBPROP_IColumnsInfo|
|IColumnsRowset|DBPROP_IColumnsRowset|
|IConnectionPointContainer|DBPROP_IConnectionPointContainer|
|IConvertType|DBPROP_IConvertType|
|Immobile-Zeilen|DBPROP_IMMOBILEROWS|
|IRowset|DBPROP_IRowset|
|IRowsetChange|DBPROP_IRowsetChange|
|Irowdie tidentity|DBPROP_IRowsetIdentity|
|IRowsetInfo|DBPROP_IRowsetInfo|
|IRowsetLocate|DBPROP_IRowsetLocate|
|IRowsetResynch|DBPROP_IRowsetResynch|
|IRowsetScroll|DBPROP_IRowsetScroll|
|IRowsetUpdate|DBPROP_IRowsetUpdate|
|ISequentialStream|DBPROP_ISequentialStream|
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
|Ausgabe Codierungs Eigenschaft|DBPROP_OUTPUTENCODING|
|Ausgabedatenstrom Eigenschaft|DBPROP_OUTPUTSTREAM|
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
|Server Cursor|DBPROP_SERVERCURSOR|
|Server Daten beim Einfügen|DBPROP_SERVERDATAONINSERT|
|Löschen gelöschter Lesezeichen|DBPROP_BOOKMARKSKIP|
|Starke Zeilen Identität|DBPROP_STRONGIDENTITY|
|Aktualisierbarkeit|DBPROP_UPDATABILITY|
|Verwenden von Lesezeichen|DBPROP_BOOKMARKS|
|XML-Stamm|SSPROP_STREAM_XMLROOT|
|XSL|SSPROP_STREAM_XSL|

 Spezifische Implementierungsdetails und Funktions Informationen zum Microsoft SQL Server OLE DB-Anbieters finden Sie unter [SQL Server-Anbieter](https://msdn.microsoft.com/adf1d6c4-5930-444a-9248-ff1979729635).

## <a name="see-also"></a>Siehe auch
 [ConnectionString-Eigenschaft (](../../../ado/reference/ado-api/connectionstring-property-ado.md) [ADO)-](../../../ado/reference/ado-api/provider-property-ado.md) Objekt (ADO)- [Recordset-Objekt (](../../../ado/reference/ado-api/recordset-object-ado.md) ADO)
