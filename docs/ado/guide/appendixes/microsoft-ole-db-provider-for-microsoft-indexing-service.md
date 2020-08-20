---
description: Übersicht über den Microsoft OLE DB-Anbieter für den Index Dienst
title: Microsoft OLE DB-Anbieter für Microsoft-Indizierungs Dienst | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: dd6e4c3a60cd0c052fec7b474154684ef6c03127
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88454082"
---
# <a name="microsoft-ole-db-provider-for-microsoft-indexing-service-overview"></a>Übersicht über den Microsoft OLE DB-Anbieter für den Index Dienst
Der Microsoft OLE DB-Anbieter für den Index Dienst von Microsoft bietet programmgesteuerten schreibgeschützten Zugriff auf Dateisystem-und Webdaten, die vom Microsoft-Indizierungs Dienst indiziert werden. ADO-Anwendungen können SQL-Abfragen ausgeben, um Inhalt und Datei Eigenschafts Informationen abzurufen.

 Der Anbieter ist frei Thread-und Unicode-fähig.

## <a name="connection-string-parameters"></a>Parameter der Verbindungszeichenfolge
 Um eine Verbindung mit diesem Anbieter herzustellen, legen Sie das **Provider =** -Argument auf die [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) -Eigenschaft auf fest:

```vb
MSIDXS
```

 Wenn Sie die [Provider](../../../ado/reference/ado-api/provider-property-ado.md) -Eigenschaft lesen, wird auch diese Zeichenfolge zurückgegeben.

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
 Die SQL-Abfrage Syntax des Index Dienstanbieter besteht aus Erweiterungen für die **Select** -Anweisung **von** SQL-92 und deren from-und **Where** -Klauseln. Die Ergebnisse der Abfrage werden über OLE DB Rowsets zurückgegeben, die von ADO verwendet und als [Recordsetobjekte](../../../ado/reference/ado-api/recordset-object-ado.md) bearbeitet werden können.

 Sie können nach exakten Wörtern oder Ausdrücken suchen oder Platzhalter verwenden, um nach Mustern oder Formen von Wörtern zu suchen. Die Suchlogik kann auf booleschen Entscheidungen, gewichteten Begriffen oder der Nähe von anderen Wörtern basieren. Sie können auch nach "freiem Text" suchen, wodurch Übereinstimmungen basierend auf der Bedeutung und nicht mit exakten Wörtern gefunden werden.

 Der spezifische Befehls Dialekt ist vollständig in den Abfrage Sprachen für die Indizierungs Dienst Dokumentation dokumentiert.

 Der Anbieter akzeptiert keine Aufrufe gespeicherter Prozeduren oder einfache Tabellennamen (die [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) -Eigenschaft ist z. b. immer **adCmdText**).

## <a name="recordset-behavior"></a>Recordsetverhalten
 In der folgenden Tabelle sind die verfügbaren Funktionen für ein **Recordset** -Objekt aufgeführt, das mit diesem Anbieter geöffnet wurde. Nur der statische Cursortyp (**adopdestatic**) ist verfügbar.

 Ausführlichere Informationen zum **recordsetverhalten** ihrer Anbieter Konfiguration erhalten Sie, wenn Sie die [unterstützte](../../../ado/reference/ado-api/supports-method.md) Methode ausführen und die [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) -Auflistung des **Recordsets** auflisten, um zu bestimmen, ob anbieterspezifische dynamische Eigenschaften vorhanden sind.

 **Verfügbarkeit von Eigenschaften des Standard-ADO-Recordsets:**

|Eigenschaft|Verfügbarkeit|
|--------------|------------------|
|[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)|Lesen/Schreiben|
|[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|Lesen/Schreiben|
|[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)|schreibgeschützt|
|[BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|schreibgeschützt|
|[Lesezeichen](../../../ado/reference/ado-api/bookmark-property-ado.md)*|Lesen/Schreiben|
|[CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)|Lesen/Schreiben|
|[CursorLocation –](../../../ado/reference/ado-api/cursorlocation-property-ado.md)|immer **AD-eServer**|
|[CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|Always **adop-static**|
|[EditMode](../../../ado/reference/ado-api/editmode-property.md)|immer **adEditNone**|
|[EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|schreibgeschützt|
|[Filter](../../../ado/reference/ado-api/filter-property.md)|Lesen/Schreiben|
|[LockType](../../../ado/reference/ado-api/locktype-property-ado.md)|Lesen/Schreiben|
|[MarshalOptions](../../../ado/reference/ado-api/marshaloptions-property-ado.md)|nicht verfügbar|
|[MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md)|Lesen/Schreiben|
|[PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)|schreibgeschützt|
|[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)|Lesen/Schreiben|
|[RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)|schreibgeschützt|
|[Quelle](../../../ado/reference/ado-api/source-property-ado-recordset.md)|Lesen/Schreiben|
|[State](../../../ado/reference/ado-api/state-property-ado.md)|schreibgeschützt|
|[Status](../../../ado/reference/ado-api/status-property-ado-recordset.md)|schreibgeschützt|

 \*Lesezeichen müssen für den Anbieter aktiviert sein, damit diese Funktion im **Recordset**vorhanden ist.

 **Verfügbarkeit der standardmäßigen ADO-recordsetmethoden:**

|Methode|Verfügbar?|
|------------|----------------|
|[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)|Nein|
|[Abbrechen](../../../ado/reference/ado-api/cancel-method-ado.md)|Ja|
|[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|Nein|
|[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)|Nein|
|[Klonen](../../../ado/reference/ado-api/clone-method-ado.md)|Ja|
|[Schließen](../../../ado/reference/ado-api/close-method-ado.md)|Ja|
|[Löschen](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|Nein|
|[GetRows](../../../ado/reference/ado-api/getrows-method-ado.md)|Ja|
|[Verschieben](../../../ado/reference/ado-api/move-method-ado.md)|Ja|
|[MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Ja|
|[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)|Ja|
|[Öffnen](../../../ado/reference/ado-api/open-method-ado-recordset.md)|Ja|
|[Requery](../../../ado/reference/ado-api/requery-method.md)|Ja|
|[Erneut synchronisieren](../../../ado/reference/ado-api/resync-method.md)|Ja|
|[Unterstützt](../../../ado/reference/ado-api/supports-method.md)|Ja|
|[Aktualisieren](../../../ado/reference/ado-api/update-method.md)|Nein|
|[Update Batch](../../../ado/reference/ado-api/updatebatch-method.md)|Nein|

 Spezifische Implementierungsdetails und Funktions Informationen zum Microsoft OLE DB-Anbieter für den Index Dienst von Microsoft finden Sie im [OLE DB Programmierer-Handbuch](https://msdn.microsoft.com/library/windows/desktop/ms713643.aspx), oder besuchen Sie die Seite "Webdienste" der Windows NT Server-Website.

## <a name="see-also"></a>Weitere Informationen
 [CommandType-Eigenschaft (ADO)](../../../ado/reference/ado-api/commandtype-property-ado.md) [ConnectionString-Eigenschaft (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md) [Properties Collection (](../../../ado/reference/ado-api/properties-collection-ado.md) ADO)- [Anbieter Eigenschaft (](../../../ado/reference/ado-api/provider-property-ado.md) [ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) [unterstützt Methode](../../../ado/reference/ado-api/supports-method.md)
