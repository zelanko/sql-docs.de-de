---
description: Übersicht über den Microsoft OLE DB-Anbieter für den Index Dienst
title: Microsoft OLE DB-Anbieter für Microsoft-Indizierungs Dienst | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Indexing Service provider [ADO]
- providers [ADO], OLE DB provider for Microsoft Indexing service
- OLE DB provider for Microsoft Indexing service [ADO]
ms.assetid: f86a0598-5097-471b-8318-d2c859d085f2
author: rothja
ms.author: jroth
ms.openlocfilehash: b3e479ca023efb704bf496c9ffaeaca2f1b6ba15
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88991041"
---
# <a name="microsoft-ole-db-provider-for-microsoft-indexing-service-overview"></a>Übersicht über den Microsoft OLE DB-Anbieter für den Index Dienst
Der Microsoft OLE DB-Anbieter für den Index Dienst von Microsoft bietet programmgesteuerten schreibgeschützten Zugriff auf Dateisystem-und Webdaten, die vom Microsoft-Indizierungs Dienst indiziert werden. ADO-Anwendungen können SQL-Abfragen ausgeben, um Inhalt und Datei Eigenschafts Informationen abzurufen.

 Der Anbieter ist frei Thread-und Unicode-fähig.

## <a name="connection-string-parameters"></a>Parameter der Verbindungszeichenfolge
 Um eine Verbindung mit diesem Anbieter herzustellen, legen Sie das **Provider =** -Argument auf die [ConnectionString](../../reference/ado-api/connectionstring-property-ado.md) -Eigenschaft auf fest:

```vb
MSIDXS
```

 Wenn Sie die [Provider](../../reference/ado-api/provider-property-ado.md) -Eigenschaft lesen, wird auch diese Zeichenfolge zurückgegeben.

## <a name="typical-connection-string"></a>Typische Verbindungs Zeichenfolge
 Eine typische Verbindungs Zeichenfolge für diesen Anbieter lautet:

```vb
"Provider=MSIDXS;Data Source=myCatalog;Locale Identifier=nnnn;"
```

 Die Zeichenfolge besteht aus folgenden Schlüsselwörtern:

|Schlüsselwort|Beschreibung|
|-------------|-----------------|
|**Anbieter**|Gibt den OLE DB Anbieter für den Microsoft-Indizierungs Dienst an. In der Regel ist dies das einzige in der Verbindungs Zeichenfolge angegebene Schlüsselwort.|
|**Data Source**|Gibt den Namen des Index Dienst Katalogs an. Wenn dieses Schlüsselwort nicht angegeben wird, wird der Standardsystem Katalog verwendet.|
|**Locale Identifier**|Gibt eine eindeutige 32-Bit-Nummer an (z. b. 1033), die Einstellungen im Zusammenhang mit der Sprache des Benutzers angibt. Wenn dieses Schlüsselwort nicht angegeben wird, wird der standardmäßige System Gebiets Schema Bezeichner verwendet.|

## <a name="command-text"></a>Befehlstext
 Die SQL-Abfrage Syntax des Index Dienstanbieter besteht aus Erweiterungen für die **Select** -Anweisung **von** SQL-92 und deren from-und **Where** -Klauseln. Die Ergebnisse der Abfrage werden über OLE DB Rowsets zurückgegeben, die von ADO verwendet und als [Recordsetobjekte](../../reference/ado-api/recordset-object-ado.md) bearbeitet werden können.

 Sie können nach exakten Wörtern oder Ausdrücken suchen oder Platzhalter verwenden, um nach Mustern oder Formen von Wörtern zu suchen. Die Suchlogik kann auf booleschen Entscheidungen, gewichteten Begriffen oder der Nähe von anderen Wörtern basieren. Sie können auch nach "freiem Text" suchen, wodurch Übereinstimmungen basierend auf der Bedeutung und nicht mit exakten Wörtern gefunden werden.

 Der spezifische Befehls Dialekt ist vollständig in den Abfrage Sprachen für die Indizierungs Dienst Dokumentation dokumentiert.

 Der Anbieter akzeptiert keine Aufrufe gespeicherter Prozeduren oder einfache Tabellennamen (die [CommandType](../../reference/ado-api/commandtype-property-ado.md) -Eigenschaft ist z. b. immer **adCmdText**).

## <a name="recordset-behavior"></a>Recordsetverhalten
 In der folgenden Tabelle sind die verfügbaren Funktionen für ein **Recordset** -Objekt aufgeführt, das mit diesem Anbieter geöffnet wurde. Nur der statische Cursortyp (**adopdestatic**) ist verfügbar.

 Ausführlichere Informationen zum **recordsetverhalten** ihrer Anbieter Konfiguration erhalten Sie, wenn Sie die [unterstützte](../../reference/ado-api/supports-method.md) Methode ausführen und die [Properties](../../reference/ado-api/properties-collection-ado.md) -Auflistung des **Recordsets** auflisten, um zu bestimmen, ob anbieterspezifische dynamische Eigenschaften vorhanden sind.

 **Verfügbarkeit von Eigenschaften des Standard-ADO-Recordsets:**

|Eigenschaft|Verfügbarkeit|
|--------------|------------------|
|[AbsolutePage](../../reference/ado-api/absolutepage-property-ado.md)|Lesen/Schreiben|
|[AbsolutePosition](../../reference/ado-api/absoluteposition-property-ado.md)|Lesen/Schreiben|
|[ActiveConnection](../../reference/ado-api/activeconnection-property-ado.md)|schreibgeschützt|
|[BOF](../../reference/ado-api/bof-eof-properties-ado.md)|schreibgeschützt|
|[Lesezeichen](../../reference/ado-api/bookmark-property-ado.md)*|Lesen/Schreiben|
|[CacheSize](../../reference/ado-api/cachesize-property-ado.md)|Lesen/Schreiben|
|[CursorLocation –](../../reference/ado-api/cursorlocation-property-ado.md)|immer **AD-eServer**|
|[CursorType](../../reference/ado-api/cursortype-property-ado.md)|Always **adop-static**|
|[EditMode](../../reference/ado-api/editmode-property.md)|immer **adEditNone**|
|[EOF](../../reference/ado-api/bof-eof-properties-ado.md)|schreibgeschützt|
|[Filter](../../reference/ado-api/filter-property.md)|Lesen/Schreiben|
|[LockType](../../reference/ado-api/locktype-property-ado.md)|Lesen/Schreiben|
|[MarshalOptions](../../reference/ado-api/marshaloptions-property-ado.md)|nicht verfügbar|
|[MaxRecords](../../reference/ado-api/maxrecords-property-ado.md)|Lesen/Schreiben|
|[PageCount](../../reference/ado-api/pagecount-property-ado.md)|schreibgeschützt|
|[PageSize](../../reference/ado-api/pagesize-property-ado.md)|Lesen/Schreiben|
|[RecordCount](../../reference/ado-api/recordcount-property-ado.md)|schreibgeschützt|
|[Quelle](../../reference/ado-api/source-property-ado-recordset.md)|Lesen/Schreiben|
|[State](../../reference/ado-api/state-property-ado.md)|schreibgeschützt|
|[Status](../../reference/ado-api/status-property-ado-recordset.md)|schreibgeschützt|

 \*Lesezeichen müssen für den Anbieter aktiviert sein, damit diese Funktion im **Recordset**vorhanden ist.

 **Verfügbarkeit der standardmäßigen ADO-recordsetmethoden:**

|Methode|Verfügbar?|
|------------|----------------|
|[AddNew](../../reference/ado-api/addnew-method-ado.md)|Nein|
|[Abbrechen](../../reference/ado-api/cancel-method-ado.md)|Ja|
|[CancelBatch](../../reference/ado-api/cancelbatch-method-ado.md)|Nein|
|[CancelUpdate](../../reference/ado-api/cancelupdate-method-ado.md)|Nein|
|[Klonen](../../reference/ado-api/clone-method-ado.md)|Ja|
|[Schließen](../../reference/ado-api/close-method-ado.md)|Ja|
|[Löschen](../../reference/ado-api/delete-method-ado-recordset.md)|Nein|
|[GetRows](../../reference/ado-api/getrows-method-ado.md)|Ja|
|[Verschieben](../../reference/ado-api/move-method-ado.md)|Ja|
|[MoveFirst](../../reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Ja|
|[NextRecordset](../../reference/ado-api/nextrecordset-method-ado.md)|Ja|
|[Öffnen](../../reference/ado-api/open-method-ado-recordset.md)|Ja|
|[Requery](../../reference/ado-api/requery-method.md)|Ja|
|[Erneut synchronisieren](../../reference/ado-api/resync-method.md)|Ja|
|[Unterstützt](../../reference/ado-api/supports-method.md)|Ja|
|[Aktualisieren](../../reference/ado-api/update-method.md)|Nein|
|[Update Batch](../../reference/ado-api/updatebatch-method.md)|Nein|

 Spezifische Implementierungsdetails und Funktions Informationen zum Microsoft OLE DB-Anbieter für den Index Dienst von Microsoft finden Sie im [OLE DB Programmierer-Handbuch](/previous-versions/windows/desktop/ms713643(v=vs.85)), oder besuchen Sie die Seite "Webdienste" der Windows NT Server-Website.

## <a name="see-also"></a>Weitere Informationen
 [CommandType-Eigenschaft (ADO)](../../reference/ado-api/commandtype-property-ado.md) [ConnectionString-Eigenschaft (ADO)](../../reference/ado-api/connectionstring-property-ado.md) [Properties Collection (](../../reference/ado-api/properties-collection-ado.md) ADO)- [Anbieter Eigenschaft (](../../reference/ado-api/provider-property-ado.md) [ADO)](../../reference/ado-api/recordset-object-ado.md) [unterstützt Methode](../../reference/ado-api/supports-method.md)