---
title: Microsoft OLE DB-Anbieter für Microsoft Indexdienst | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Indexing Service provider [ADO]
- providers [ADO], OLE DB provider for Microsoft Indexing service
- OLE DB provider for Microsoft Indexing service [ADO]
ms.assetid: f86a0598-5097-471b-8318-d2c859d085f2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1b4dfa4771fa60286e054270cb644c72cabe8e40
ms.sourcegitcommit: 96b2355d54dfad259826e88bdff91cc9344e16f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51350354"
---
# <a name="microsoft-ole-db-provider-for-microsoft-indexing-service-overview"></a>Microsoft OLE DB-Anbieter für Microsoft, die Indizierung Service – Übersicht
Microsoft OLE DB-Anbieter für Microsoft Indexdienst ermöglicht programmgesteuerten schreibgeschützten Zugriff auf System- und Webdaten indiziert, die vom Microsoft Indexdienst-Datei. ADO-Anwendungen können SQL-Abfragen zum Abrufen von Inhalten und Informationen ausgeben.

 Der Anbieter Freethread- und UNICODE aktiviert ist.

## <a name="connection-string-parameters"></a>Parameter für Verbindungszeichenfolgen
 Legen Sie zum Verbinden mit diesem Anbieter die **Anbieter =** Argument für die ["ConnectionString"](../../../ado/reference/ado-api/connectionstring-property-ado.md) Eigenschaft:

```vb
MSIDXS
```

 Lesen der [Anbieter](../../../ado/reference/ado-api/provider-property-ado.md) Eigenschaft auch dieser Zeichenfolge zurück.

## <a name="typical-connection-string"></a>Typische Verbindungszeichenfolge
 Eine typische Verbindungszeichenfolge für diesen Anbieter ist:

```vb
"Provider=MSIDXS;Data Source=myCatalog;Locale Identifier=nnnn;"
```

 Die Zeichenfolge, die dieser Schlüsselwörter besteht aus:

|Schlüsselwort|Description|
|-------------|-----------------|
|**Anbieter**|Gibt an, den OLE DB-Anbieter für Microsoft Indexdienst. In der Regel ist dies das einzige in der Verbindungszeichenfolge angegebene Schlüsselwort.|
|**Data Source**|Gibt den Namen der Indexdienst-Katalog. Wenn dieses Schlüsselwort nicht angegeben ist, wird der Standardkatalog für das System verwendet.|
|**Locale Identifier**|Gibt eine eindeutige 32-Bit-Zahl (z. B. 1033), die angibt, Einstellungen, die im Zusammenhang mit der Sprache des Benutzers an. Wenn dieses Schlüsselwort nicht angegeben ist, wird die System Standardgebietsschema-ID verwendet.|

## <a name="command-text"></a>Befehlstext
 Die Indizierung von Dienst-SQL-Abfragesyntax besteht aus Erweiterungen für die SQL-92 **wählen** Anweisung und die zugehörige **FROM** und **, in denen** Klauseln. Die Ergebnisse der Abfrage werden zurückgegeben, über OLE DB-Rowsets, die von ADO genutzt und als bearbeitet werden können [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekte.

 Sie können genau den Wörtern oder Ausdrücken suchen oder Platzhalter verwenden, um Muster oder Wortstämmen suchen. Die Suchlogik kann für boolesche Entscheidungen, gewichteten Begriffen oder geografischer Nähe zu anderen Wörtern basieren. Sie können auch suchen, indem "freiem Text" der Übereinstimmungen anhand von Bedeutung, anstatt genauen Wörter findet.

 Der bestimmte Befehlsdialekt wird vollständig in den Abfragesprachen zum Indexdienst-Dokumentation dokumentiert.

 Der Anbieter akzeptiert keine Aufrufe von gespeicherten Prozeduren oder einfache Tabellennamen (z. B. die [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) Eigenschaft werden immer **AdCmdText**).

## <a name="recordset-behavior"></a>Recordset-Verhalten
 Die folgenden Tabellen enthalten die Features von einem **Recordset** Objekt mit diesem Anbieter geöffnet. Nur der statische Cursor-Datentyp (**"adOpenStatic"**) verfügbar ist.

 Ausführlichere Informationen zu **Recordset** Verhalten für die Anbieterkonfiguration, und führen Sie die [unterstützt](../../../ado/reference/ado-api/supports-method.md) Methode eine Aufzählung der [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Auflistung von der **Recordset** zu bestimmen, ob die anbieterspezifische dynamische Eigenschaften vorhanden sind.

 **Verfügbarkeit der standard-ADO-Recordset-Eigenschaften:**

|Eigenschaft|Verfügbarkeit|
|--------------|------------------|
|[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)|Lese-/Schreibzugriff|
|[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|Lese-/Schreibzugriff|
|[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)|Schreibgeschützt|
|[BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|Schreibgeschützt|
|[Lesezeichen](../../../ado/reference/ado-api/bookmark-property-ado.md)*|Lese-/Schreibzugriff|
|[CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)|Lese-/Schreibzugriff|
|[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)|immer **AdUseServer**|
|[CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|immer **"adOpenStatic"**|
|[EditMode](../../../ado/reference/ado-api/editmode-property.md)|immer **AdEditNone**|
|[EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|Schreibgeschützt|
|[Filter](../../../ado/reference/ado-api/filter-property.md)|Lese-/Schreibzugriff|
|[LockType](../../../ado/reference/ado-api/locktype-property-ado.md)|Lese-/Schreibzugriff|
|[MarshalOptions](../../../ado/reference/ado-api/marshaloptions-property-ado.md)|Nicht verfügbar.|
|[MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md)|Lese-/Schreibzugriff|
|[PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)|Schreibgeschützt|
|[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)|Lese-/Schreibzugriff|
|[RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)|Schreibgeschützt|
|[Quelle](../../../ado/reference/ado-api/source-property-ado-recordset.md)|Lese-/Schreibzugriff|
|[Status](../../../ado/reference/ado-api/state-property-ado.md)|Schreibgeschützt|
|[Status](../../../ado/reference/ado-api/status-property-ado-recordset.md)|Schreibgeschützt|

 \*Lesezeichen müssen aktiviert sein, auf den Anbieter in der Reihenfolge für dieses Feature, auf die **Recordset**.

 **Verfügbarkeit des standard-ADO-Recordset-Methoden:**

|Methode|Verfügbar?|
|------------|----------------|
|[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)|nein|
|[Abbrechen](../../../ado/reference/ado-api/cancel-method-ado.md)|Benutzerkontensteuerung|
|[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|nein|
|[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)|nein|
|[Klonen](../../../ado/reference/ado-api/clone-method-ado.md)|Benutzerkontensteuerung|
|[Schließen](../../../ado/reference/ado-api/close-method-ado.md)|Benutzerkontensteuerung|
|[Delete](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|nein|
|[GetRows](../../../ado/reference/ado-api/getrows-method-ado.md)|Benutzerkontensteuerung|
|[Verschieben](../../../ado/reference/ado-api/move-method-ado.md)|Benutzerkontensteuerung|
|[MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Benutzerkontensteuerung|
|[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)|Benutzerkontensteuerung|
|[Datei](../../../ado/reference/ado-api/open-method-ado-recordset.md)|Benutzerkontensteuerung|
|[Requery](../../../ado/reference/ado-api/requery-method.md)|Benutzerkontensteuerung|
|[Erneute Synchronisierung](../../../ado/reference/ado-api/resync-method.md)|Benutzerkontensteuerung|
|[Unterstützt](../../../ado/reference/ado-api/supports-method.md)|Benutzerkontensteuerung|
|[Update](../../../ado/reference/ado-api/update-method.md)|nein|
|[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|nein|

 Bestimmte Implementierungsdetails und funktionalen Informationen zu den Microsoft OLE DB-Anbieter für Microsoft Indexdienst, finden Sie in der [OLE DB Programmer's Guide](https://msdn.microsoft.com/library/windows/desktop/ms713643.aspx), oder besuchen Sie die Web Services-Seite von den Windows NT Server-Webdienst Website.

## <a name="see-also"></a>Siehe auch
 [CommandType-Eigenschaft (ADO)](../../../ado/reference/ado-api/commandtype-property-ado.md) [ConnectionString-Eigenschaft (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md) [Properties-Auflistung (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md) [Provider-Eigenschaft (ADO)](../../../ado/reference/ado-api/provider-property-ado.md) [ Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) [unterstützt-Methode](../../../ado/reference/ado-api/supports-method.md)
