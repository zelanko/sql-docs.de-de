---
title: Microsoft OLE DB-Anbieter für ODBC | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB provider for ODBC [ADO]
- providers [ADO], OLE DB provider for ODBC
ms.assetid: 2dc0372d-e74d-4d0f-9c8c-04e5a168c148
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 565217e494b753ee22c2fa3715f17108a9fab5da
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47638308"
---
# <a name="microsoft-ole-db-provider-for-odbc-overview"></a>Microsoft OLE DB-Anbieter für ODBC-Übersicht
Ein ADO- oder RDS-Programmierer wäre eine ideale Welt eine Datenquelle in dem jeder eine OLE DB-Schnittstelle verfügbar macht, damit ADO direkt in der Datenquelle aufgerufen werden kann. Obwohl Datenbankanbieter zunehmend OLE DB-Schnittstellen implementieren, werden einige Datenquellen nicht noch auf diese Weise verfügbar gemacht. Allerdings können die meisten DBMS-Systeme heutzutage über ODBC zugegriffen werden.

 ODBC-Treiber sind für alle wichtigen DBMS-Systeme heute, einschließlich Microsoft SQL Server, Microsoft Access (Microsoft Jet-Datenbank-Engine) und Microsoft FoxPro, zusätzlich zur für nicht-Microsoft-Datenbankprodukte wie Oracle verfügbar.

 Der Microsoft ODBC-Datenanbieter, ermöglicht jedoch ADO eine ODBC-Datenquelle herstellen. Der Anbieter Freethread- und Unicode aktiviert ist.

 Der Anbieter unterstützt Transaktionen, auch wenn unterschiedliche DBMS-Module auf verschiedene Arten von transaktionsunterstützung bieten. Beispielsweise unterstützt Microsoft Access geschachtelte Transaktionen bis zu fünf Ebenen tief.

 Dies ist der Standardanbieter für ADO, und alle vom Anbieter abhängig ADO-Eigenschaften und Methoden werden unterstützt.

## <a name="connection-string-parameters"></a>Parameter für Verbindungszeichenfolgen
 Legen Sie zum Verbinden mit diesem Anbieter die **Anbieter =** Argument der ["ConnectionString"](../../../ado/reference/ado-api/connectionstring-property-ado.md) Eigenschaft:

```
MSDASQL
```

 Lesen der [Anbieter](../../../ado/reference/ado-api/provider-property-ado.md) Eigenschaft auch dieser Zeichenfolge zurück.

## <a name="typical-connection-string"></a>Typische Verbindungszeichenfolge
 Eine typische Verbindungszeichenfolge für diesen Anbieter ist:

```
"Provider=MSDASQL;DSN=dsnName;UID=MyUserID;PWD=MyPassword;"
```

 Die Zeichenfolge, die dieser Schlüsselwörter besteht aus:

|Schlüsselwort|Description|
|-------------|-----------------|
|**Anbieter**|Gibt an, die OLE DB-Anbieter für ODBC.|
|**DSN**|Gibt die Namen der Datenquelle an.|
|**UID**|Gibt den Benutzernamen an.|
|**PWD**|Gibt das Kennwort des Benutzers an.|
|**URL**|Gibt die URL einer Datei oder Verzeichnis in einen Webordner veröffentlicht.|

 Da dies den Standardanbieter für ADO ist, wenn Sie weglassen der **Provider =** Parameter aus der Verbindungszeichenfolge, ADO wird versucht, zum Herstellen einer Verbindung zu diesem Anbieter.

> [!NOTE]
>  Wenn Sie für einen Datenanbieter der Datenquelle, der Windows-Authentifizierung unterstützt herstellen, sollten Sie angeben **Trusted_Connection = Yes** oder **Integrated Security = SSPI** anstelle von Benutzer-ID und Kennwort die Informationen in der Verbindungszeichenfolge.

 Der Anbieter unterstützt keine bestimmten Verbindungsparameter zusätzlich zu den von ADO definiert. Allerdings wird der Anbieter alle nicht-ADO-Verbindung-Parameter auf dem ODBC-Treiber-Manager übergeben.

 Da Sie weglassen können die **Anbieter** -Parameter können aus diesem Grund erstellen Sie eine ADO-Verbindungszeichenfolge, die mit einer ODBC-Verbindungszeichenfolge für die gleiche Datenquelle identisch ist. Verwenden Sie die gleichen Parameternamen (**Treiber =**, **Datenbank =**, **DSN =** und so weiter), Werte und wie Sie die Syntax wie bei der eine ODBC-Verbindungszeichenfolge zu erstellen. Sie können mit oder ohne eine vordefinierte Datenquellenname (DSN) oder die Datei-DSN verbinden.

## <a name="syntax-with-a-dsn-or-filedsn"></a>Die Syntax mit einem DSN oder Datei-DSN:

```
"[Provider=MSDASQL;] { DSN=name | FileDSN=filename } ;
[DATABASE=database;] UID=user; PWD=password"
```

## <a name="syntax-without-a-dsn-dsn-less-connection"></a>Die Syntax ohne einen DSN (DSN-lose Verbindung):

```
"[Provider=MSDASQL;] DRIVER=driver; SERVER=server;
DATABASE=database; UID=MyUserID; PWD=MyPassword"
```

## <a name="remarks"></a>Hinweise
 Bei Verwendung einer **DSN** oder **FileDSN**, er muss über die ODBC-Datenquellen-Administrator in der Windows-Systemsteuerung definiert werden. Der ODBC-Administrator befindet sich in Microsoft Windows 2000 unter Verwaltung. In früheren Versionen von Windows, das Symbol "ODBC-Administrator" heißt **32-Bit-ODBC-** oder nur **ODBC**.

 Als Alternative zum Festlegen einer **DSN**, können Sie angeben, den ODBC-Treiber (**Treiber =**), z. B. "SQLServer;" den Namen des Servers (**SERVER =**); und den Datenbanknamen (**Datenbank =**).

 Sie können auch einen Benutzernamen für das Konto angeben (**UID =**), und das Kennwort für das Benutzerkonto (**PWD =**) in der ODBC-spezifische Parameter oder in der Standard ADO definierten *Benutzer* und *Kennwort* Parameter.

 Obwohl eine **DSN** bereits Definition gibt es sich um eine Datenbank, können Sie angeben, *eine* *Datenbank* Parameter zusätzlich zu einer **DSN** eine Verbindung herstellen mit einer anderen Datenbank. Es ist eine gute Idee, immer *der* *Datenbank* Parameter bei Verwendung einer **DSN**. Dadurch wird sichergestellt, dass Sie eine Verbindung mit der richtigen Datenbank herstellen, wenn ein anderer Benutzer den Standardparameter für die Datenbank geändert, seit Sie zuletzt überprüft die **DSN** Definition.

## <a name="provider-specific-connection-properties"></a>Anbieter-spezifischen Verbindungseigenschaften
 Der OLE DB-Datenanbieter für ODBC fügt mehrere Eigenschaften, die [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Auflistung von der **Verbindung** Objekt. In der folgende Tabelle werden diese Eigenschaften mit dem entsprechenden Namen der OLE DB-Eigenschaft in Klammern aufgeführt.

|Eigenschaftsname|Description|
|-------------------|-----------------|
|Zugegriffen werden Prozeduren (KAGPROP_ACCESSIBLEPROCEDURES)|Gibt an, ob der Benutzer den Zugriff auf gespeicherte Prozeduren.|
|Zugegriffen werden Tabellen (KAGPROP_ACCESSIBLETABLES)|Gibt an, ob der Benutzer die Berechtigung zum Ausführen von SELECT-Anweisungen für Tabellen der Datenbank.|
|Aktive Anweisungen (KAGPROP_ACTIVESTATEMENTS)|Gibt die Anzahl der Handles, die ein ODBC-Treiber für eine Verbindung unterstützen kann.|
|Treibername (KAGPROP_DRIVERNAME)|Gibt den Dateinamen des ODBC-Treibers an.|
|ODBC-Treiberversion (KAGPROP_DRIVERODBCVER)|Gibt die Version von ODBC, die diese Treiber unterstützt.|
|Verwendung der Datei (KAGPROP_FILEUSAGE)|Gibt an, wie der Treiber für eine Datei in einer Datenquelle behandelt; als eine Tabelle oder eines Katalogs.|
|LIKE Escape-Klausel (KAGPROP_LIKEESCAPECLAUSE)|Gibt an, ob der Treiber die Definition und Verwendung eines Escapezeichens unterstützt für das Prozentzeichen (%) und Unterstrich (_) im LIKE-Prädikat einer WHERE-Klausel.|
|Max-Spalten in Group By (KAGPROP_MAXCOLUMNSINGROUPBY)|Gibt die maximale Anzahl von Spalten, die in der GROUP BY-Klausel einer SELECT-Anweisung aufgeführt werden können.|
|Maximale Anzahl von Spalten im Index (KAGPROP_MAXCOLUMNSININDEX)|Gibt die maximale Anzahl von Spalten, die in einem Index aufgenommen werden kann.|
|Maximale Anzahl von Spalten in Order By-(KAGPROP_MAXCOLUMNSINORDERBY)|Gibt die maximale Anzahl von Spalten, die in der ORDER BY-Klausel einer SELECT-Anweisung aufgeführt werden können.|
|Maximale Anzahl von Spalten in wählen (KAGPROP_MAXCOLUMNSINSELECT)|Gibt die maximale Anzahl von Spalten, die in der SELECT-Teil einer SELECT-Anweisung aufgeführt werden können.|
|Maximale Anzahl von Spalten in der Tabelle (KAGPROP_MAXCOLUMNSINTABLE)|Gibt die maximale Anzahl zulässiger Spalten in einer Tabelle an.|
|Numerische Funktionen (KAGPROP_NUMERICFUNCTIONS)|Gibt an, die numerischen Funktionen der ODBC-Treiber unterstützt werden. Eine Liste der Namen von Funktionen und die zugehörigen Werte in dieser Bitmaske verwendet, finden Sie unter [Anhang E: Skalarfunktionen](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md), in der Dokumentation zu ODBC.|
|Inklusionsverknüpfungs-Funktionen (KAGPROP_OJCAPABILITY)|Gibt an, die Arten von ÄUßEREN JOINs vom Anbieter unterstützt werden.|
|Äußere Joins (KAGPROP_OUTERJOINS)|Gibt an, ob der Anbieter ÄUßERE Verknüpfungen unterstützt.|
|Sonderzeichen (KAGPROP_SPECIALCHARACTERS)|Gibt an, welche Zeichen für den ODBC-Treiber eine besondere Bedeutung haben.|
|Gespeicherte Prozeduren (KAGPROP_PROCEDURES)|Gibt an, ob gespeicherte Prozeduren für die Verwendung mit diesen ODBC-Treiber verfügbar sind.|
|Zeichenfolgenfunktionen (KAGPROP_STRINGFUNCTIONS)|Gibt an, welche Zeichenfolgenfunktionen vom ODBC-Treiber unterstützt werden. Eine Liste der Namen von Funktionen und die zugehörigen Werte in dieser Bitmaske verwendet, finden Sie unter [Anhang E: Skalarfunktionen](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md), in der Dokumentation zu ODBC.|
|Systemfunktionen (KAGPROP_SYSTEMFUNCTIONS)|Gibt an, welche Systemfunktionen, die vom ODBC-Treiber unterstützt werden. Eine Liste der Namen von Funktionen und die zugehörigen Werte in dieser Bitmaske verwendet, finden Sie unter [Anhang E: Skalarfunktionen](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md), in der Dokumentation zu ODBC.|
|Datum/Uhrzeit-Funktionen (KAGPROP_TIMEDATEFUNCTIONS)|Gibt an, welche Funktionen für Datum und Uhrzeit von der ODBC-Treiber unterstützt werden. Eine Liste der Namen von Funktionen und die zugehörigen Werte in dieser Bitmaske verwendet, finden Sie unter [Anhang E: Skalarfunktionen](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md), in der Dokumentation zu ODBC.|
|Unterstützung für SQL-Grammatik (KAGPROP_ODBCSQLCONFORMANCE)|Gibt an, die SQL-Grammatik, die der ODBC-Treiber unterstützt.|

## <a name="provider-specific-recordset-and-command-properties"></a>Anbieterspezifische Recordset und Befehlseigenschaften
 Der OLE DB-Datenanbieter für ODBC fügt mehrere Eigenschaften, die **Eigenschaften** Auflistung von der **Recordset** und **Befehl** Objekte. In der folgende Tabelle werden diese Eigenschaften mit dem entsprechenden Namen der OLE DB-Eigenschaft in Klammern aufgeführt.

|Eigenschaftsname|Description|
|-------------------|-----------------|
|Abfragebasiert Aktualisierungen/Löschungen/Einfügevorgänge (KAGPROP_QUERYBASEDUPDATES)|Gibt an, ob Updates, löschungen und einfügungen mithilfe von SQL-Abfragen ausgeführt werden können.|
|ODBC-Parallelitätstyp (KAGPROP_CONCURRENCY)|Gibt die Methode zum Verringern des möglichen Problemen aufgrund von zwei Benutzern, die die gleichen Daten gleichzeitig aus der Datenquelle zugreifen möchten.|
|BLOB-Zugriff auf die Forward-Only-Cursor (KAGPROP_BLOBSONFOCURSOR)|Gibt an, ob BLOB- **Felder** kann zugegriffen werden, wenn ein Vorwärtscursor verwenden.|
|Schließen Sie SQL_FLOAT SQL_DOUBLE und SQL_REAL in QBU WHERE-Klauseln (KAGPROP_INCLUDENONEXACT)|Gibt an, ob es sich bei SQL_FLOAT SQL_DOUBLE und SQL_REAL Werte in einer QBU WHERE-Klausel aufgenommen werden können.|
|Position in der letzten Zeile nach dem Einfügen (KAGPROP_POSITIONONNEWROW)|Gibt an, dass nach dem ein neuer Datensatz in einer Tabelle eingefügt wurde, die letzte Zeile in der Tabelle wird die aktuelle Zeile stammen.|
|IRowsetChangeExtInfo (KAGPROP_IROWSETCHANGEEXTINFO)|Gibt an, ob die **IRowsetChange** Schnittstelle stellt Informationen zur erweiterten Unterstützung bereit.|
|ODBC-Cursor-Datentyp (KAGPROP_CURSOR)|Gibt den Typ des verwendeten von Cursors die **Recordset**.|
|Generieren ein Rowsets, die gemarshallt werden kann (KAGPROP_MARSHALLABLE)|Gibt an, dass der ODBC-Treiber ein Recordset generiert, die gemarshallt werden kann|

## <a name="command-text"></a>Befehlstext
 Informationen zur Verwendung der [Befehl](../../../ado/reference/ado-api/command-object-ado.md) Objekt hängt zum größten Teil der Datenquelle, und welche Art von Abfrage- oder Befehlsinformationen-Anweisung, die es annehmen wird.

 ODBC stellt eine spezielle Syntax zum Aufrufen von gespeicherter Prozeduren bereit. Für die [CommandText-Eigenschaft](../../../ado/reference/ado-api/commandtext-property-ado.md) Eigenschaft eine **Befehl** -Objekt, die *CommandText* Argument für die **ausführen** Methode für eine [ Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt oder die *Quelle* Argument für die **öffnen** Methode für eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt übergibt eine Zeichenfolge mit folgender Syntax:

```
"{ [ ? = ] call procedure [ ( ? [, ? [ , … ]] ) ] }"
```

 Jede **?** verweist auf ein Objekt in der [Parameter](../../../ado/reference/ado-api/parameters-collection-ado.md) Auflistung. Die erste **?** Verweise **Parameter**(0), die nächste **?** Verweise **Parameter**(1), und so weiter.

 Die Parameterverweise sind optional und hängen von der Struktur der gespeicherten Prozedur. Wenn eine gespeicherte Prozedur aufrufen, die keine Parameter definiert werden sollen, würde die Zeichenfolge wie folgt aussehen:

```
"{ call procedure }"
```

 Wenn Sie zwei Abfrageparametern haben, würden Ihre Zeichenfolge folgendermaßen aussehen:

```
"{ call procedure ( ?, ? ) }"
```

 Wenn die gespeicherte Prozedur einen Wert zurückgibt, wird der Rückgabewert als ein anderer Parameter behandelt. Wenn Sie haben keine Abfrageparameter vor, aber Sie einen Rückgabewert müssen, würde die Zeichenfolge wie folgt aussehen:

```
"{ ? = call procedure }"
```

 Abschließend würden, wenn Sie einen Rückgabewert haben, und zwei Abfrageparameter, Ihre Zeichenfolge folgendermaßen aussehen:

```
"{ ? = call procedure ( ?, ? ) }"
```

## <a name="recordset-behavior"></a>Recordset-Verhalten
 Die folgenden Tabellen enthalten die standard-ADO-Methoden und Eigenschaften, die auf eine **Recordset** Objekt mit diesem Anbieter geöffnet.

 Ausführlichere Informationen zu **Recordset** Verhalten für die Anbieterkonfiguration, und führen Sie die [unterstützt](../../../ado/reference/ado-api/supports-method.md) Methode eine Aufzählung der **Eigenschaften** Auflistung von der **Recordset** zu bestimmen, ob die anbieterspezifische dynamische Eigenschaften vorhanden sind.

 Verfügbarkeit von standard-ADO- **Recordset** Eigenschaften:

|Eigenschaft|"ForwardOnly"|Dynamic|Keyset|STATIC-Cursor|
|--------------|-----------------|-------------|------------|------------|
|[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)|Nicht verfügbar.|Nicht verfügbar.|Lese-/Schreibzugriff|Lese-/Schreibzugriff|
|[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|Nicht verfügbar.|Nicht verfügbar.|Lese-/Schreibzugriff|Lese-/Schreibzugriff|
|[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)|Lese-/Schreibzugriff|Lese-/Schreibzugriff|Lese-/Schreibzugriff|Lese-/Schreibzugriff|
|[BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|Schreibgeschützt|Schreibgeschützt|Schreibgeschützt|Schreibgeschützt|
|[Lesezeichen](../../../ado/reference/ado-api/bookmark-property-ado.md)|Nicht verfügbar.|Nicht verfügbar.|Lese-/Schreibzugriff|Lese-/Schreibzugriff|
|[CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)|Lese-/Schreibzugriff|Lese-/Schreibzugriff|Lese-/Schreibzugriff|Lese-/Schreibzugriff|
|[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)|Lese-/Schreibzugriff|Lese-/Schreibzugriff|Lese-/Schreibzugriff|Lese-/Schreibzugriff|
|[CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|Lese-/Schreibzugriff|Lese-/Schreibzugriff|Lese-/Schreibzugriff|Lese-/Schreibzugriff|
|[EditMode](../../../ado/reference/ado-api/editmode-property.md)|Schreibgeschützt|Schreibgeschützt|Schreibgeschützt|Schreibgeschützt|
|[Filter](../../../ado/reference/ado-api/filter-property.md)|Lese-/Schreibzugriff|Lese-/Schreibzugriff|Lese-/Schreibzugriff|Lese-/Schreibzugriff|
|[LockType](../../../ado/reference/ado-api/locktype-property-ado.md)|Lese-/Schreibzugriff|Lese-/Schreibzugriff|Lese-/Schreibzugriff|Lese-/Schreibzugriff|
|[MarshalOptions](../../../ado/reference/ado-api/marshaloptions-property-ado.md)|Lese-/Schreibzugriff|Lese-/Schreibzugriff|Lese-/Schreibzugriff|Lese-/Schreibzugriff|
|[MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md)|Lese-/Schreibzugriff|Lese-/Schreibzugriff|Lese-/Schreibzugriff|Lese-/Schreibzugriff|
|[PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)|Lese-/Schreibzugriff|Nicht verfügbar.|Schreibgeschützt|Schreibgeschützt|
|[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)|Lese-/Schreibzugriff|Lese-/Schreibzugriff|Lese-/Schreibzugriff|Lese-/Schreibzugriff|
|[RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)|Lese-/Schreibzugriff|Nicht verfügbar.|Schreibgeschützt|Schreibgeschützt|
|[Quelle](../../../ado/reference/ado-api/source-property-ado-recordset.md)|Lese-/Schreibzugriff|Lese-/Schreibzugriff|Lese-/Schreibzugriff|Lese-/Schreibzugriff|
|[Status](../../../ado/reference/ado-api/state-property-ado.md)|Schreibgeschützt|Schreibgeschützt|Schreibgeschützt|Schreibgeschützt|
|[Status](../../../ado/reference/ado-api/status-property-ado-recordset.md)|Schreibgeschützt|Schreibgeschützt|Schreibgeschützt|Schreibgeschützt|

 Die [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) und [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) Eigenschaften sind schreibgeschützt, wenn Sie ADO mit Version 1.0 von Microsoft OLE DB-Anbieter für ODBC verwendet wird.

 Verfügbarkeit von standard-ADO- **Recordset** Methoden:

|Methode|"ForwardOnly"|Dynamic|Keyset|STATIC-Cursor|
|------------|-----------------|-------------|------------|------------|
|[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|
|[Abbrechen](../../../ado/reference/ado-api/cancel-method-ado.md)|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|
|[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|
|[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|
|[Klonen](../../../ado/reference/ado-api/clone-method-ado.md)|nein|nein|Benutzerkontensteuerung|Benutzerkontensteuerung|
|[Schließen](../../../ado/reference/ado-api/close-method-ado.md)|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|
|[Delete](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|
|[GetRows](../../../ado/reference/ado-api/getrows-method-ado.md)|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|
|[Verschieben](../../../ado/reference/ado-api/move-method-ado.md)|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|
|[MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|
|[MoveLast](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|nein|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|
|[MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|
|[MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|nein|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|
|[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)*|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|
|[Datei](../../../ado/reference/ado-api/open-method-ado-recordset.md)|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|
|[Requery](../../../ado/reference/ado-api/requery-method.md)|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|
|[Erneute Synchronisierung](../../../ado/reference/ado-api/resync-method.md)|nein|nein|Benutzerkontensteuerung|Benutzerkontensteuerung|
|[Unterstützt](../../../ado/reference/ado-api/supports-method.md)|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|
|[Update](../../../ado/reference/ado-api/update-method.md)|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|
|[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|Benutzerkontensteuerung|

 * Nicht Microsoft Access-Datenbanken unterstützt.

## <a name="dynamic-properties"></a>Dynamische Eigenschaften
 Microsoft OLE DB-Anbieter für ODBC fügt verschiedene Eigenschaften in der **Eigenschaften** Auflistung von nicht geöffneten [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md), [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), und [Befehl](../../../ado/reference/ado-api/command-object-ado.md) Objekte.

 Die folgenden Tabellen sind ein Cross-Index der ADO und OLE DB-Namen für jede dynamische Eigenschaft. Der OLE DB Programmer's Reference bezieht sich auf den Namen einer ADO-Eigenschaft, wird der Begriff "Description". Weitere Informationen zu diesen Eigenschaften finden Sie in der OLE DB Programmer's Reference. Suchen Sie nach den Namen des OLE DB-Eigenschaft im Index oder finden Sie unter [Anhang C: OLE DB-Eigenschaften](http://msdn.microsoft.com/deded3ff-f508-4e1b-b2b1-fd9afd3bd292).

## <a name="connection-dynamic-properties"></a>Dynamische Eigenschaften der Verbindung
 Die folgenden Eigenschaften werden hinzugefügt, um die **Verbindung** des Objekts **Eigenschaften** Auflistung.

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
|Datenquellenname|RÜCKGABEWERT|
|Datenquellenobjekt Threading-Modell|DBPROP_DSOTHREADMODEL|
|Der DBMS-Name|DBPROP_DBMSNAME|
|DBMS-Version|DBPROP_DBMSVER|
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
|Mode|DBPROP_INIT_MODE|
|Mehrere Parametersätze|DBPROP_MULTIPLEPARAMSETS|
|Mehrere Ergebnisse|DBPROP_MULTIPLERESULTS|
|Mehrere Speicherobjekte|DBPROP_MULTIPLESTORAGEOBJECTS|
|Aktualisierung mehrerer Tabellen|DBPROP_MULTITABLEUPDATE|
|NULL-Zusammenstellungsreihenfolge|DBPROP_NULLCOLLATION|
|NULL-Verkettungsverhalten|DBPROP_CONCATNULLBEHAVIOR|
|OLE DB-Diensten|DBPROP_INIT_OLEDBSERVICES|
|OLE DB-Version|DBPROP_PROVIDEROLEDBVER|
|OLE-Objektunterstützung|DBPROP_OLEOBJECTS|
|Öffnen Sie die Schemarowset-Unterstützung|DBPROP_OPENROWSETSUPPORT|
|ORDER BY-Spalten in Auswahlliste|DBPROP_ORDERBYCOLUMNSINSELECT|
|Verfügbarkeit der Ausgabeparameter|DBPROP_OUTPUTPARAMETERAVAILABILITY|
|Kennwort|DBPROP_AUTH_PASSWORD|
|Übergabe durch Verweiszugriffe|DBPROP_BYREFACCESSORS|
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
 Die folgenden Eigenschaften werden hinzugefügt, um die **Recordset** des Objekts **Eigenschaften** Auflistung.

|ADO-Eigenschaftenname|OLE DB-Eigenschaftenname|
|-----------------------|--------------------------|
|Zugriffsreihenfolge|DBPROP_ACCESSORDER|
|Speicherobjekte blockieren|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Lesezeichentyp|DBPROP_BOOKMARKTYPE|
|Jeden|DBPROP_IROWSETLOCATE|
|Eingefügte Zeilen ändern|DBPROP_CHANGEINSERTEDROWS|
|Spaltenprivilegien|DBPROP_COLUMNRESTRICT|
|Spaltenmengenbenachrichtigung|DBPROP_NOTIFYCOLUMNSET|
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
|IRowsetResynch||
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
|Eindeutige Zeilen|DBPROP_UNIQUEROWS|
|Aktualisierbarkeit|DBPROP_UPDATABILITY|
|Verwenden von Lesezeichen|DBPROP_BOOKMARKS|

## <a name="command-dynamic-properties"></a>Dynamische Eigenschaften-Befehl
 Die folgenden Eigenschaften werden hinzugefügt, um die **Befehl** des Objekts **Eigenschaften** Auflistung.

|ADO-Eigenschaftenname|OLE DB-Eigenschaftenname|
|-----------------------|--------------------------|
|Zugriffsreihenfolge|DBPROP_ACCESSORDER|
|Speicherobjekte blockieren|DBPROP_BLOCKINGSTORAGEOBJECTS|
|Lesezeichentyp|DBPROP_BOOKMARKTYPE|
|Jeden|DBPROP_IROWSETLOCATE|
|Eingefügte Zeilen ändern|DBPROP_CHANGEINSERTEDROWS|
|Spaltenprivilegien|DBPROP_COLUMNRESTRICT|
|Spaltenmengenbenachrichtigung|DBPROP_NOTIFYCOLUMNSET|
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
|IRowsetResynch||
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
|Gelöschte Lesezeichen überspringen|DBPROP_BOOKMARKSKIP|
|Starke Zeilenidentität|DBPROP_STRONGIDENTITY|
|Aktualisierbarkeit|DBPROP_UPDATABILITY|
|Verwenden von Lesezeichen|DBPROP_BOOKMARKS|

 Details zur Implementierung und funktionalen Informationen zu den Microsoft OLE DB-Anbieter für ODBC, finden Sie unter den [OLE DB-Programmierreferenz](http://msdn.microsoft.com/3c5e2dd5-35e5-4a93-ac3a-3818bb43bbf8) oder finden Sie auf der Website-Datenzugriff und Storage Developer Center auf MSDN.

## <a name="see-also"></a>Siehe auch
 [Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md) [CommandText-Eigenschaft (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md) [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md) [ConnectionString-Eigenschaft (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md) [ausführen Methode (ADO Command)](../../../ado/reference/ado-api/execute-method-ado-command.md) [Open-Methode (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md) [Parameters-Auflistung (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md) [Properties-Auflistung (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) [Provider-Eigenschaft (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) [unterstützt-Methode](../../../ado/reference/ado-api/supports-method.md)
