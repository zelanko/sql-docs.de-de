---
description: Übersicht über Microsoft OLE DB-Anbieter für ODBC
title: Microsoft OLE DB-Anbieter für ODBC | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB provider for ODBC [ADO]
- providers [ADO], OLE DB provider for ODBC
ms.assetid: 2dc0372d-e74d-4d0f-9c8c-04e5a168c148
author: rothja
ms.author: jroth
ms.openlocfilehash: 2dcd280098a5ca4075f424f12b0abdfede6b7653
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88806644"
---
# <a name="microsoft-ole-db-provider-for-odbc-overview"></a>Übersicht über Microsoft OLE DB-Anbieter für ODBC
Für einen ADO-oder RDS-Programmierer wäre eine ideale Welt eine ideale Welt, bei der jede Datenquelle eine OLE DB-Schnittstelle verfügbar macht, sodass ADO direkt in der Datenquelle aufgerufen werden kann. Obwohl immer mehr Datenbankanbieter OLE DB-Schnittstellen implementieren, sind einige Datenquellen auf diese Weise noch nicht verfügbar. Allerdings kann auf die meisten derzeit verwendeten DBMS-Systeme über ODBC zugegriffen werden.

 ODBC-Treiber sind zusätzlich zu den derzeit verwendeten DBMS verfügbar, z. b. Microsoft SQL Server, Microsoft Access (Microsoft Jet-Datenbank-Engine) und Microsoft FoxPro sowie nicht von Microsoft stammende Daten Bankprodukte wie Oracle.

 Mit dem Microsoft ODBC-Anbieter kann ADO jedoch eine Verbindung mit einer beliebigen ODBC-Datenquelle herstellen. Der Anbieter ist frei Thread-und Unicode-fähig.

 Der Anbieter unterstützt Transaktionen, auch wenn verschiedene DBMS-Engines verschiedene Arten von Transaktionsunterstützung bieten. Beispielsweise unterstützt Microsoft Access verschachtelte Transaktionen mit einer Tiefe von bis zu fünf Ebenen.

 Dies ist der Standardanbieter für ADO, und alle vom Anbieter abhängigen ADO-Eigenschaften und-Methoden werden unterstützt.

## <a name="connection-string-parameters"></a>Parameter der Verbindungszeichenfolge
 Legen Sie das **Provider =** -Argument der [ConnectionString](../../reference/ado-api/connectionstring-property-ado.md) -Eigenschaft auf fest, um eine Verbindung mit diesem Anbieter herzustellen:

```
MSDASQL
```

 Wenn Sie die [Provider](../../reference/ado-api/provider-property-ado.md) -Eigenschaft lesen, wird auch diese Zeichenfolge zurückgegeben.

## <a name="typical-connection-string"></a>Typische Verbindungs Zeichenfolge
 Eine typische Verbindungs Zeichenfolge für diesen Anbieter lautet:

```
"Provider=MSDASQL;DSN=dsnName;UID=MyUserID;PWD=MyPassword;"
```

 Die Zeichenfolge besteht aus folgenden Schlüsselwörtern:

|Schlüsselwort|Beschreibung|
|-------------|-----------------|
|**Anbieter**|Gibt den OLE DB Anbieter für ODBC an.|
|**DSN**|Gibt den Namen der Datenquelle an.|
|**UID**|Gibt den Benutzernamen an.|
|**PWD**|Gibt das Benutzer Kennwort an.|
|**URL**|Gibt die URL einer Datei oder eines Verzeichnisses an, die in einem Webordner veröffentlicht wird.|

 Da es sich hierbei um den Standardanbieter für ADO handelt, wird von ADO versucht, eine Verbindung mit diesem Anbieter herzustellen, wenn Sie den **Provider =** -Parameter aus der Verbindungs Zeichenfolge weglassen.

> [!NOTE]
>  Wenn Sie eine Verbindung mit einem Datenquellen Anbieter herstellen, der die Windows-Authentifizierung unterstützt, sollten Sie in der Verbindungs Zeichenfolge **Trusted_Connection = yes** oder **Integrated Security = SSPI** anstelle von Benutzer-ID und Kennwort angeben.

 Der Anbieter unterstützt keine bestimmten Verbindungsparameter zusätzlich zu den von ADO definierten Verbindungsparametern. Allerdings übergibt der Anbieter alle nicht-ADO-Verbindungsparameter an den ODBC-Treiber-Manager.

 Da Sie den **Provider** -Parameter weglassen können, können Sie daher eine ADO-Verbindungs Zeichenfolge erstellen, die mit einer ODBC-Verbindungs Zeichenfolge für die gleiche Datenquelle identisch ist. Verwenden Sie die gleichen Parameternamen (**Driver =**, **Database =**, **DSN =** usw.), Werte und Syntax, wie beim Erstellen einer ODBC-Verbindungs Zeichenfolge. Sie können eine Verbindung mit oder ohne vordefinierten Datenquellen Namen (DSN) oder FILEDSN herstellen.

## <a name="syntax-with-a-dsn-or-filedsn"></a>Syntax mit einem DSN oder Datei-DSN:

```
"[Provider=MSDASQL;] { DSN=name | FileDSN=filename } ;
[DATABASE=database;] UID=user; PWD=password"
```

## <a name="syntax-without-a-dsn-dsn-less-connection"></a>Syntax ohne DSN (DSN-lose Verbindung):

```
"[Provider=MSDASQL;] DRIVER=driver; SERVER=server;
DATABASE=database; UID=MyUserID; PWD=MyPassword"
```

## <a name="remarks"></a>Bemerkungen
 Wenn Sie einen **DSN** oder eine **FILEDSN**verwenden, muss er in der Windows-Systemsteuerung über den ODBC-Datenquellen-Administrator definiert werden. In Microsoft Windows 2000 befindet sich der ODBC-Administrator unter "Verwaltung". In früheren Versionen von Windows hat das ODBC-Administrator Symbol den Namen " **32-Bit-ODBC** " oder "nur **ODBC**".

 Als Alternative zum Festlegen eines **DSN**können Sie den ODBC-Treiber angeben (**Driver =**), z. b. "SQL Server;" den Servernamen (**Server =**); und den Datenbanknamen (**Database =**).

 Sie können auch einen Benutzerkonto Namen (**UID =**) und das Kennwort für das Benutzerkonto (**pwd =**) in den ODBC-spezifischen Parametern oder in den standardmäßigen ADO-definierten *Benutzer* -und Kenn *Wort* Parametern angeben.

 Obwohl eine **DSN** -Definition bereits eine Datenbank angibt, können Sie zusätzlich zu einem **DSN** *einen* *Daten Bank* Parameter angeben, um eine Verbindung mit einer anderen Datenbank herzustellen. Wenn Sie einen **DSN**verwenden, empfiehlt es sich, immer *den* *Database* -Parameter einzubeziehen. Dadurch wird sichergestellt, dass Sie eine Verbindung mit der richtigen Datenbank herstellen, wenn ein anderer Benutzer den Standarddaten Bank Parameter seit der letzten Überprüfung der **DSN** -Definition geändert hat

## <a name="provider-specific-connection-properties"></a>Anbieterspezifische Verbindungs Eigenschaften
 Der OLE DB Anbieter für ODBC fügt der [Properties](../../reference/ado-api/properties-collection-ado.md) -Sammlung des **Connection** -Objekts mehrere Eigenschaften hinzu. In der folgenden Tabelle werden diese Eigenschaften mit dem entsprechenden OLE DB-Eigenschaftsnamen in Klammern aufgelistet.

|Eigenschaftenname|Beschreibung|
|-------------------|-----------------|
|Barrierefreie Prozeduren (KAGPROP_ACCESSIBLEPROCEDURES)|Gibt an, ob der Benutzer Zugriff auf gespeicherte Prozeduren hat.|
|Barrierefreie Tabellen (KAGPROP_ACCESSIBLETABLES)|Gibt an, ob der Benutzer über die Berechtigung zum Ausführen von SELECT-Anweisungen für die Datenbanktabellen verfügt.|
|Aktive Anweisungen (KAGPROP_ACTIVESTATEMENTS)|Gibt die Anzahl der Handles an, die ein ODBC-Treiber für eine Verbindung unterstützen kann.|
|Treiber Name (KAGPROP_DRIVERNAME)|Gibt den Dateinamen des ODBC-Treibers an.|
|ODBC-Treiber Version (KAGPROP_DRIVERODBCVER)|Gibt die Version von ODBC an, die dieser Treiber unterstützt.|
|Datei Verwendung (KAGPROP_FILEUSAGE)|Gibt an, wie der Treiber eine Datei in einer Datenquelle behandelt. als Tabelle oder als Katalog.|
|Like-Escape-Klausel (KAGPROP_LIKEESCAPECLAUSE)|Gibt an, ob der Treiber die Definition und die Verwendung eines Escapezeichens für das Prozentzeichen (%) unterstützt. und unterstreichen Sie das Zeichen (_) im LIKE-Prädikat einer WHERE-Klausel.|
|Maximale Spalten Anzahl in Group by (KAGPROP_MAXCOLUMNSINGROUPBY)|Gibt die maximale Anzahl der Spalten an, die in der Group By-Klausel einer SELECT-Anweisung aufgelistet werden können.|
|Maximale Spalten Anzahl in Index (KAGPROP_MAXCOLUMNSININDEX)|Gibt die maximale Anzahl der Spalten an, die in einem Index enthalten sein können.|
|Maximale Spalten Anzahl in order by (KAGPROP_MAXCOLUMNSINORDERBY)|Gibt die maximale Anzahl der Spalten an, die in der ORDER BY-Klausel einer SELECT-Anweisung aufgelistet werden können.|
|Maximale Spalten in SELECT (KAGPROP_MAXCOLUMNSINSELECT)|Gibt die maximale Anzahl der Spalten an, die im SELECT-Teil einer SELECT-Anweisung aufgelistet werden können.|
|Maximale Spalten in Tabelle (KAGPROP_MAXCOLUMNSINTABLE)|Gibt die maximal zulässige Anzahl von Spalten in einer Tabelle an.|
|Numerische Funktionen (KAGPROP_NUMERICFUNCTIONS)|Gibt an, welche numerischen Funktionen vom ODBC-Treiber unterstützt werden. Eine Auflistung der Funktionsnamen und der zugeordneten Werte, die in dieser Bitmaske verwendet werden, finden Sie in der ODBC-Dokumentation unter [Anhang E: Skalarfunktionen](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).|
|Funktionen für äußere Joins (KAGPROP_OJCAPABILITY)|Gibt die Typen von äußeren Joins an, die vom Anbieter unterstützt werden.|
|Äußere Joins (KAGPROP_OUTERJOINS)|Gibt an, ob der Anbieter äußere Joins unterstützt.|
|Sonderzeichen (KAGPROP_SPECIALCHARACTERS)|Gibt an, welche Zeichen für den ODBC-Treiber eine besondere Bedeutung haben.|
|Gespeicherte Prozeduren (KAGPROP_PROCEDURES)|Gibt an, ob gespeicherte Prozeduren für den Einsatz mit diesem ODBC-Treiber verfügbar sind.|
|Zeichen folgen Funktionen (KAGPROP_STRINGFUNCTIONS)|Gibt an, welche Zeichen folgen Funktionen vom ODBC-Treiber unterstützt werden. Eine Auflistung der Funktionsnamen und der zugeordneten Werte, die in dieser Bitmaske verwendet werden, finden Sie in der ODBC-Dokumentation unter [Anhang E: Skalarfunktionen](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).|
|System Funktionen (KAGPROP_SYSTEMFUNCTIONS)|Gibt an, welche Systemfunktionen vom ODBC-Treiber unterstützt werden. Eine Auflistung der Funktionsnamen und der zugeordneten Werte, die in dieser Bitmaske verwendet werden, finden Sie in der ODBC-Dokumentation unter [Anhang E: Skalarfunktionen](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).|
|Datums-/Uhrzeitfunktionen (KAGPROP_TIMEDATEFUNCTIONS)|Gibt an, welche Zeit-und Datumsfunktionen vom ODBC-Treiber unterstützt werden. Eine Auflistung der Funktionsnamen und der zugeordneten Werte, die in dieser Bitmaske verwendet werden, finden Sie in der ODBC-Dokumentation unter [Anhang E: Skalarfunktionen](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).|
|SQL-Grammatik Unterstützung (KAGPROP_ODBCSQLCONFORMANCE)|Gibt die SQL-Grammatik an, die der ODBC-Treiber unterstützt.|

## <a name="provider-specific-recordset-and-command-properties"></a>Anbieterspezifische Recordset-und Befehls Eigenschaften
 Der OLE DB Anbieter für ODBC fügt der **Properties** -Auflistung der **Recordset** -und **Command** -Objekte mehrere Eigenschaften hinzu. In der folgenden Tabelle werden diese Eigenschaften mit dem entsprechenden OLE DB-Eigenschaftsnamen in Klammern aufgelistet.

|Eigenschaftenname|Beschreibung|
|-------------------|-----------------|
|Abfrage basierte Updates/Löschungen/Einfügungen (KAGPROP_QUERYBASEDUPDATES)|Gibt an, ob Aktualisierungen, Löschungen und Einfügungen mithilfe von SQL-Abfragen ausgeführt werden können.|
|ODBC-Parallelitäts Typ (KAGPROP_CONCURRENCY)|Gibt die Methode an, mit der potenzielle Probleme reduziert werden, die dazu geführt haben, dass zwei Benutzer gleichzeitig versuchen, auf dieselben Daten von der Datenquelle zuzugreifen.|
|BLOB-Barrierefreiheit bei Vorwärts Cursor (KAGPROP_BLOBSONFOCURSOR)|Gibt an, ob auf BLOB- **Felder** zugegriffen werden kann, wenn ein Vorwärts Cursor verwendet wird.|
|Einschließen von SQL_FLOAT, SQL_DOUBLE und SQL_REAL in qbu WHERE-Klauseln (KAGPROP_INCLUDENONEXACT)|Gibt an, ob die Werte SQL_FLOAT, SQL_DOUBLE und SQL_REAL in eine qbu WHERE-Klausel eingeschlossen werden können.|
|Position in der letzten Zeile nach dem Einfügen (KAGPROP_POSITIONONNEWROW)|Gibt an, dass die letzte Zeile in der Tabelle in der aktuellen Zeile angezeigt wird, nachdem ein neuer Datensatz in eine Tabelle eingefügt wurde.|
|Irowsetchangeextinfo (KAGPROP_IROWSETCHANGEEXTINFO)|Gibt an, ob die **IRowsetChange** -Schnittstelle erweiterte Informationsunterstützung bereitstellt.|
|ODBC-Cursortyp (KAGPROP_CURSOR)|Gibt den Typ des Cursors an, der vom **Recordset**verwendet wird.|
|Generieren eines Rowsets, das gemarshallt werden kann (KAGPROP_MARSHALLABLE)|Gibt an, dass der ODBC-Treiber ein Recordset generiert, das gemarshallt werden kann.|

## <a name="command-text"></a>Befehlstext
 Wie Sie das [Command](../../reference/ado-api/command-object-ado.md) -Objekt verwenden, hängt größtenteils von der Datenquelle und davon ab, welche Art von Abfrage oder Befehls Anweisung Sie akzeptieren wird.

 ODBC stellt eine bestimmte Syntax zum Aufrufen gespeicherter Prozeduren bereit. Für die [CommandText](../../reference/ado-api/commandtext-property-ado.md) -Eigenschaft eines **Befehls** Objekts, das *CommandText* -Argument für die **Execute** -Methode für ein [Verbindungs](../../reference/ado-api/connection-object-ado.md) Objekt oder das *Quell* Argument für die **Open** -Methode in einem [Recordset](../../reference/ado-api/recordset-object-ado.md) -Objekt, übergibt eine Zeichenfolge mit der folgenden Syntax:

```
"{ [ ? = ] call procedure [ ( ? [, ? [ , ... ]] ) ] }"
```

 Beides **?** verweist auf ein Objekt in der [Parameter](../../reference/ado-api/parameters-collection-ado.md) Auflistung. Der erste **?** verweist auf **Parameter**(0), die nächste **?** verweist auf **Parameter**(1) usw.

 Die Parameter Verweise sind optional und hängen von der Struktur der gespeicherten Prozedur ab. Wenn Sie eine gespeicherte Prozedur, die keine Parameter definiert, abrufen möchten, sieht die Zeichenfolge wie folgt aus:

```
"{ call procedure }"
```

 Wenn Sie über zwei Abfrage Parameter verfügen, ähnelt die Zeichenfolge folgendem:

```
"{ call procedure ( ?, ? ) }"
```

 Wenn die gespeicherte Prozedur einen Wert zurückgibt, wird der Rückgabewert als weiterer Parameter behandelt. Wenn Sie über keine Abfrage Parameter verfügen, aber einen Rückgabewert haben, sieht die Zeichenfolge wie folgt aus:

```
"{ ? = call procedure }"
```

 Wenn Sie über einen Rückgabewert und zwei Abfrage Parameter verfügen, sieht die Zeichenfolge in etwa wie folgt aus:

```
"{ ? = call procedure ( ?, ? ) }"
```

## <a name="recordset-behavior"></a>Recordsetverhalten
 In den folgenden Tabellen sind die standardmäßigen ADO-Methoden und-Eigenschaften aufgeführt, die für ein mit diesem Anbieter geöffnetes **Recordset** -Objekt

 Ausführlichere Informationen zum **recordsetverhalten** ihrer Anbieter Konfiguration erhalten Sie, wenn Sie die [unterstützte](../../reference/ado-api/supports-method.md) Methode ausführen und die **Properties** -Auflistung des **Recordsets** auflisten, um zu bestimmen, ob anbieterspezifische dynamische Eigenschaften vorhanden sind.

 Verfügbarkeit von Eigenschaften des Standard-ADO- **Recordsets** :

|Eigenschaft|Nur Weiterleitung|Dynamisch|Keyset|statischen|
|--------------|-----------------|-------------|------------|------------|
|[AbsolutePage](../../reference/ado-api/absolutepage-property-ado.md)|nicht verfügbar|nicht verfügbar|Lesen/Schreiben|Lesen/Schreiben|
|[AbsolutePosition](../../reference/ado-api/absoluteposition-property-ado.md)|nicht verfügbar|nicht verfügbar|Lesen/Schreiben|Lesen/Schreiben|
|[ActiveConnection](../../reference/ado-api/activeconnection-property-ado.md)|Lesen/Schreiben|Lesen/Schreiben|Lesen/Schreiben|Lesen/Schreiben|
|[BOF](../../reference/ado-api/bof-eof-properties-ado.md)|schreibgeschützt|schreibgeschützt|schreibgeschützt|schreibgeschützt|
|[Lesezeichen](../../reference/ado-api/bookmark-property-ado.md)|nicht verfügbar|nicht verfügbar|Lesen/Schreiben|Lesen/Schreiben|
|[CacheSize](../../reference/ado-api/cachesize-property-ado.md)|Lesen/Schreiben|Lesen/Schreiben|Lesen/Schreiben|Lesen/Schreiben|
|[CursorLocation –](../../reference/ado-api/cursorlocation-property-ado.md)|Lesen/Schreiben|Lesen/Schreiben|Lesen/Schreiben|Lesen/Schreiben|
|[CursorType](../../reference/ado-api/cursortype-property-ado.md)|Lesen/Schreiben|Lesen/Schreiben|Lesen/Schreiben|Lesen/Schreiben|
|[EditMode](../../reference/ado-api/editmode-property.md)|schreibgeschützt|schreibgeschützt|schreibgeschützt|schreibgeschützt|
|[Filter](../../reference/ado-api/filter-property.md)|Lesen/Schreiben|Lesen/Schreiben|Lesen/Schreiben|Lesen/Schreiben|
|[LockType](../../reference/ado-api/locktype-property-ado.md)|Lesen/Schreiben|Lesen/Schreiben|Lesen/Schreiben|Lesen/Schreiben|
|[MarshalOptions](../../reference/ado-api/marshaloptions-property-ado.md)|Lesen/Schreiben|Lesen/Schreiben|Lesen/Schreiben|Lesen/Schreiben|
|[MaxRecords](../../reference/ado-api/maxrecords-property-ado.md)|Lesen/Schreiben|Lesen/Schreiben|Lesen/Schreiben|Lesen/Schreiben|
|[PageCount](../../reference/ado-api/pagecount-property-ado.md)|Lesen/Schreiben|nicht verfügbar|schreibgeschützt|schreibgeschützt|
|[PageSize](../../reference/ado-api/pagesize-property-ado.md)|Lesen/Schreiben|Lesen/Schreiben|Lesen/Schreiben|Lesen/Schreiben|
|[RecordCount](../../reference/ado-api/recordcount-property-ado.md)|Lesen/Schreiben|nicht verfügbar|schreibgeschützt|schreibgeschützt|
|[Quelle](../../reference/ado-api/source-property-ado-recordset.md)|Lesen/Schreiben|Lesen/Schreiben|Lesen/Schreiben|Lesen/Schreiben|
|[State](../../reference/ado-api/state-property-ado.md)|schreibgeschützt|schreibgeschützt|schreibgeschützt|schreibgeschützt|
|[Status](../../reference/ado-api/status-property-ado-recordset.md)|schreibgeschützt|schreibgeschützt|schreibgeschützt|schreibgeschützt|

 Die Eigenschaften " [AbsolutePosition](../../reference/ado-api/absoluteposition-property-ado.md) " und " [AbsolutePage](../../reference/ado-api/absolutepage-property-ado.md) " sind schreibgeschützt, wenn ADO mit Version 1,0 des Microsoft OLE DB-Anbieters für ODBC verwendet wird.

 Verfügbarkeit der standardmäßigen ADO- **recordsetmethoden** :

|Methode|Nur Weiterleitung|Dynamisch|Keyset|statischen|
|------------|-----------------|-------------|------------|------------|
|[AddNew](../../reference/ado-api/addnew-method-ado.md)|Ja|Ja|Ja|Ja|
|[Abbrechen](../../reference/ado-api/cancel-method-ado.md)|Ja|Ja|Ja|Ja|
|[CancelBatch](../../reference/ado-api/cancelbatch-method-ado.md)|Ja|Ja|Ja|Ja|
|[CancelUpdate](../../reference/ado-api/cancelupdate-method-ado.md)|Ja|Ja|Ja|Ja|
|[Klonen](../../reference/ado-api/clone-method-ado.md)|Nein|Nein|Ja|Ja|
|[Schließen](../../reference/ado-api/close-method-ado.md)|Ja|Ja|Ja|Ja|
|[Löschen](../../reference/ado-api/delete-method-ado-recordset.md)|Ja|Ja|Ja|Ja|
|[GetRows](../../reference/ado-api/getrows-method-ado.md)|Ja|Ja|Ja|Ja|
|[Verschieben](../../reference/ado-api/move-method-ado.md)|Ja|Ja|Ja|Ja|
|[MoveFirst](../../reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Ja|Ja|Ja|Ja|
|[MoveLast](../../reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Nein|Ja|Ja|Ja|
|[MoveNext](../../reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Ja|Ja|Ja|Ja|
|[MovePrevious](../../reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Nein|Ja|Ja|Ja|
|[NextRecordset](../../reference/ado-api/nextrecordset-method-ado.md)*|Ja|Ja|Ja|Ja|
|[Öffnen](../../reference/ado-api/open-method-ado-recordset.md)|Ja|Ja|Ja|Ja|
|[Requery](../../reference/ado-api/requery-method.md)|Ja|Ja|Ja|Ja|
|[Erneut synchronisieren](../../reference/ado-api/resync-method.md)|Nein|Nein|Ja|Ja|
|[Unterstützt](../../reference/ado-api/supports-method.md)|Ja|Ja|Ja|Ja|
|[Aktualisieren](../../reference/ado-api/update-method.md)|Ja|Ja|Ja|Ja|
|[Update Batch](../../reference/ado-api/updatebatch-method.md)|Ja|Ja|Ja|Ja|

 * Wird für Microsoft Access-Datenbanken nicht unterstützt.

## <a name="dynamic-properties"></a>Dynamische Eigenschaften
 Der Microsoft OLE DB-Anbieter für ODBC fügt verschiedene dynamische Eigenschaften in die **Properties** -Sammlung der nicht geöffneten [Verbindungs](../../reference/ado-api/connection-object-ado.md)-, [Recordset](../../reference/ado-api/recordset-object-ado.md)-und [Command](../../reference/ado-api/command-object-ado.md) -Objekte ein.

 Die folgenden Tabellen sind ein Index übergreifender Index der ADO-und OLE DB Namen für jede dynamische Eigenschaft. Die OLE DB Programmierer-Referenz verweist auf einen ADO-Eigenschaftsnamen mit dem Begriff "Description". Weitere Informationen zu diesen Eigenschaften finden Sie in der OLE DB Programmierer-Referenz. Suchen Sie im Index nach dem Namen der OLE DB Eigenschaft, oder siehe [Anhang C: OLE DB Eigenschaften](/previous-versions/windows/desktop/ms723130(v=vs.85)).

## <a name="connection-dynamic-properties"></a>Dynamische Eigenschaften der Verbindung
 Die folgenden Eigenschaften werden der **Properties** -Auflistung des **Verbindungs** Objekts hinzugefügt.

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
|Standort|DBPROP_INIT_LOCATION|
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
|Kennwort|DBPROP_AUTH_PASSWORD|
|Pass-by-Verweis-Accessoren|DBPROP_BYREFACCESSORS|
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
|IRowsetResynch||
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
|Eindeutige Zeilen|DBPROP_UNIQUEROWS|
|Aktualisierbarkeit|DBPROP_UPDATABILITY|
|Verwenden von Lesezeichen|DBPROP_BOOKMARKS|

## <a name="command-dynamic-properties"></a>Dynamische Eigenschaften des Befehls
 Die folgenden Eigenschaften werden der **Properties** -Auflistung des **Command** -Objekts hinzugefügt.

|ADO-Eigenschafts Name|Eigenschaften Name OLE DB|
|-----------------------|--------------------------|
|Zugriffs Reihenfolge|DBPROP_ACCESSORDER|
|Blockieren von Speicher Objekten|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Lese Zeichentyp|DBPROP_BOOKMARKTYPE|
|Fragmentteils|DBPROP_IROWSETLOCATE|
|Eingefügte Zeilen ändern|DBPROP_CHANGEINSERTEDROWS|
|Spalten Privilegien|DBPROP_COLUMNRESTRICT|
|Benachrichtigung über Spalten Satz|DBPROP_NOTIFYCOLUMNSET|
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
|IRowsetResynch||
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
|Löschen gelöschter Lesezeichen|DBPROP_BOOKMARKSKIP|
|Starke Zeilen Identität|DBPROP_STRONGIDENTITY|
|Aktualisierbarkeit|DBPROP_UPDATABILITY|
|Verwenden von Lesezeichen|DBPROP_BOOKMARKS|

 Ausführliche Informationen zu bestimmten Implementierungs-und Funktions Informationen zum Microsoft OLE DB-Anbieter für ODBC finden Sie in der [OLE DB Programmierer-Referenz](/previous-versions/windows/desktop/ms713643(v=vs.85)) , oder besuchen Sie die Website des Entwickler Centers für Datenzugriff und-Speicherung auf MSDN.

## <a name="see-also"></a>Weitere Informationen
 [Command Object (ADO)](../../reference/ado-api/command-object-ado.md) [CommandText-Eigenschaft (ADO)](../../reference/ado-api/commandtext-property-ado.md) [Verbindungs Objekt (](../../reference/ado-api/connection-object-ado.md) ADO) [ConnectionString-Eigenschaft (ADO)](../../reference/ado-api/connectionstring-property-ado.md) [Execute-Methode (ADO Command)](../../reference/ado-api/execute-method-ado-command.md) [Open-Methode (ADO-Recordset)](../../reference/ado-api/open-method-ado-recordset.md) [Parameters Collection (](../../reference/ado-api/parameters-collection-ado.md) ADO) [Properties Collection (](../../reference/ado-api/properties-collection-ado.md) ADO) [Provider Property (](../../reference/ado-api/provider-property-ado.md) [ADO)](../../reference/ado-api/recordset-object-ado.md) [unterstützt Methode](../../reference/ado-api/supports-method.md)