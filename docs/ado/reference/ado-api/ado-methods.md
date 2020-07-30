---
title: ADO-Methoden | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, methods
- methods [ADO]
ms.assetid: a38c5670-ba28-44f3-bd5b-fcb46880e904
author: rothja
ms.author: jroth
ms.openlocfilehash: a08f7c896b48f6cb76c9805d3bea9910a8f5bda8
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242860"
---
# <a name="ado-methods"></a>ADO-Methoden

|Methode|BESCHREIBUNG|  
|-|-|  
|[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)|Erstellt einen neuen Datensatz für ein Aktualisier bares **Recordset** -Objekt.|  
|[Append](../../../ado/reference/ado-api/append-method-ado.md)|Fügt ein Objekt an eine Auflistung an. Wenn es sich bei der Auflistung um **Felder**handelt, kann ein neues **Feld** Objekt erstellt werden, bevor es an die Auflistung angefügt wird.|  
|[AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md)|Fügt Daten an ein großes Textfeld oder ein binäres **Datenfeld**oder an ein **Parameter** Objekt an.|  
|[BeginTrans, CommitTrans und RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)|Verwaltet die Transaktionsverarbeitung innerhalb eines **Verbindungs** Objekts wie folgt:<br /><br /> **BeginTrans** -startet eine neue Transaktion.<br /><br /> **CommitTrans** -speichert alle Änderungen und beendet die aktuelle Transaktion. Möglicherweise wird auch eine neue Transaktion gestartet.<br /><br /> **RollbackTrans** -bricht alle Änderungen ab und beendet die aktuelle Transaktion. Möglicherweise wird auch eine neue Transaktion gestartet.|  
|[Abbrechen](../../../ado/reference/ado-api/cancel-method-ado.md)|Bricht die Ausführung eines ausstehenden asynchronen Methoden Aufrufes ab.|  
|[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|Bricht ein ausstehendes Batch Update ab.|  
|[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)|Bricht vor dem Aufrufen der **Update** -Methode alle Änderungen ab, die an der aktuellen oder neuen Zeile eines **Recordset** -Objekts oder der **Fields** -Auflistung eines **Datensatz** -Objekts vorgenommen wurden.|  
|[Clear](../../../ado/reference/ado-api/clear-method-ado.md) (Deaktiviert)|Entfernt alle **Fehler** Objekte aus der **Fehler** Auflistung.|  
|[Klonen](../../../ado/reference/ado-api/clone-method-ado.md)|Erstellt ein doppeltes **Recordset** -Objekt aus einem vorhandenen **Recordset** -Objekt. Gibt optional an, dass der Klon schreibgeschützt ist.|  
|[Close](../../../ado/reference/ado-api/close-method-ado.md)|Schließt ein offenes Objekt und alle abhängigen Objekte.|  
|[CompareBookmarks](../../../ado/reference/ado-api/comparebookmarks-method-ado.md)|Vergleicht zwei Lesezeichen und gibt eine Angabe über das Verhältnis der entsprechenden Werte zurück.|  
|[CopyRecord](../../../ado/reference/ado-api/copyrecord-method-ado.md)|Kopiert eine Datei oder ein Verzeichnis und seinen Inhalt an einen anderen Speicherort.|  
|[CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md)|Kopiert die angegebene Anzahl von Zeichen oder bytes (abhängig vom **Typ**) im **Stream** in ein anderes **Streamobjekt** .|  
|[CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md)|Erstellt ein neues **Parameter** Objekt, das über die angegebenen Eigenschaften verfügt.|  
|[Delete (ADO Parameters-Sammlung)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)|Löscht ein-Objekt aus der **Parameter** Auflistung.|  
|[Delete (ADO Fields-Auflistung)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)|Löscht ein-Objekt aus der **Fields** -Auflistung.|  
|[Delete (ADO-Recordset)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|Löscht den aktuellen Datensatz oder eine Gruppe von Datensätzen.|  
|[DeleteRecord](../../../ado/reference/ado-api/deleterecord-method-ado.md)|Löscht eine Datei oder ein Verzeichnis und alle Unterverzeichnisse.|  
|[Execute (ADO-Befehl)](../../../ado/reference/ado-api/execute-method-ado-command.md)|Führt die Abfrage, die SQL-Anweisung oder die gespeicherte Prozedur aus, die in der **CommandText** -Eigenschaft angegeben ist.|  
|[Ausführen (ADO-Verbindung)](../../../ado/reference/ado-api/execute-method-ado-connection.md)|Führt die angegebene Abfrage, die SQL-Anweisung, die gespeicherte Prozedur oder den anbieterspezifischen Text aus.|  
|[Suchen](../../../ado/reference/ado-api/find-method-ado.md)|Durchsucht ein **Recordset** nach der Zeile, die die angegebenen Kriterien erfüllt.|  
|[Leerung](../../../ado/reference/ado-api/flush-method-ado.md)|Erzwingt den Inhalt des verbleibenden **Streams** im ADO-Puffer für das zugrunde liegende Objekt, dem der **Stream** zugeordnet ist.|  
|[get_OLEDBCommand-Methode](../../../ado/reference/ado-api/get-oledbcommand-method.md)|Gibt den zugrunde liegenden OLEDB-Befehl zurück, wobei zuerst alle Parameterinformationen weitergegeben werden, die für den ADO-Befehl an den OLEDB-Befehl festgelegt|  
|[GetChildren](../../../ado/reference/ado-api/getchildren-method-ado.md)|Gibt ein **Recordset** zurück, dessen Zeilen die Dateien und Unterverzeichnisse in dem von diesem **Datensatz**dargestellten Verzeichnis darstellen.|  
|[GetChunk](../../../ado/reference/ado-api/getchunk-method-ado.md)|Gibt alle oder einen Teil von, den Inhalt eines großen **Textfelds** oder eines Binärdaten Feld Objekts zurück.|  
|[GetDataProviderDSO-Methode](../../../ado/reference/ado-api/getdataproviderdso-method.md)|Ruft das zugrunde liegende OLEDB-Datenquellen Objekt vom Shape-Anbieter ab.|  
|[GetRows](../../../ado/reference/ado-api/getrows-method-ado.md)|Ruft mehrere Datensätze eines **Recordset** -Objekts in ein Array ab.|  
|[GetString](../../../ado/reference/ado-api/getstring-method-ado.md)|Gibt das **Recordset** als Zeichenfolge zurück.|  
|[LoadFromFile](../../../ado/reference/ado-api/loadfromfile-method-ado.md)|Lädt den Inhalt einer vorhandenen Datei in einen **Stream**.|  
|[Verschieben](../../../ado/reference/ado-api/move-method-ado.md)|Verschiebt die Position des aktuellen Datensatzes in einem **Recordset** -Objekt.|  
|["Muvefirst", "muvelast", "muvenext" und "muveprevious"](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Wechselt zum ersten, letzten, nächsten oder vorherigen Datensatz in einem angegebenen **Recordset** -Objekt und legt diesen Datensatz auf den aktuellen Datensatz fest.|  
|[Der Pfad](../../../ado/reference/ado-api/moverecord-method-ado.md)|Verschiebt eine Datei oder ein Verzeichnis und seinen Inhalt an einen anderen Speicherort.|  
|[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)|Löscht das aktuelle **Recordset** -Objekt und gibt das nächste **Recordset** zurück, indem eine Reihe von Befehlen durchlaufen wird.|  
|[Öffnen (ADO-Verbindung)](../../../ado/reference/ado-api/open-method-ado-connection.md)|Öffnet eine Verbindung mit einer Datenquelle.|  
|[Öffnen (ADO-Datensatz)](../../../ado/reference/ado-api/open-method-ado-record.md)|Öffnet ein vorhandenes **Daten Satz** Objekt oder erstellt eine neue Datei oder ein neues Verzeichnis.|  
|[Open (ADO-Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|Öffnet einen Cursor.|  
|[Open (ADO-Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)|Öffnet ein **Stream** -Objekt, um Datenströme von Binär-oder Textdaten zu bearbeiten.|  
|[OpenSchema](../../../ado/reference/ado-api/openschema-method.md)|Ruft Datenbankschema Informationen vom Anbieter ab.|  
|[put_OLEDBCommand-Methode](../../../ado/reference/ado-api/put-oledbcommand-method.md)|Diese Methode führt keinen Vorgang aus, sondern gibt immer S_OK zurück.|  
|[Lesen](../../../ado/reference/ado-api/read-method.md)|Liest eine angegebene Anzahl von Bytes aus einem **Streamobjekt** .|  
|[READTEXT](../../../ado/reference/ado-api/readtext-method.md)|Liest eine angegebene Anzahl von Zeichen aus einem **Textstreamobjekt** .|  
|[Aktualisieren](../../../ado/reference/ado-api/refresh-method-ado.md)|Aktualisiert die Objekte in einer Auflistung, um die Objekte widerzuspiegeln, die von und für den Anbieter verfügbar sind.|  
|[Requery](../../../ado/reference/ado-api/requery-method.md)|Aktualisiert die Daten in einem **Recordset** -Objekt, indem die Abfrage erneut ausgeführt wird, auf der das Objekt basiert.|  
|[Erneut synchronisieren](../../../ado/reference/ado-api/resync-method.md)|Aktualisiert die Daten im aktuellen **Recordset** -Objekt oder der **Fields** -Auflistung eines **Datensatz** -Objekts aus der zugrunde liegenden Datenbank.|  
|[Speichern](../../../ado/reference/ado-api/save-method.md)|Speichert das **Recordset** in einer Datei oder einem **Streamobjekt** .|  
|[SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)|Speichert den binären Inhalt eines **Streams** in einer Datei.|  
|[Seek](../../../ado/reference/ado-api/seek-method.md)|Durchsucht den Index eines **Recordsets** , um die Zeile, die mit den angegebenen Werten übereinstimmt, schnell zu finden und die aktuelle Zeilen Position in diese Zeile zu ändern.|  
|[-Betriebssystem](../../../ado/reference/ado-api/seteos-method.md)|Legt die Position fest, die das Ende des Streams ist.|  
|[SkipLine](../../../ado/reference/ado-api/skipline-method.md)|Überspringt beim Lesen eines Textstreams eine gesamte Zeile.|  
|[Ierende](../../../ado/reference/ado-api/stat-method.md)|Ruft statistische Informationen zu einem geöffneten Stream ab.|  
|[Unterstützt](../../../ado/reference/ado-api/supports-method.md)|Bestimmt, ob ein angegebenes **Recordsetobjekt** einen bestimmten Funktionstyp unterstützt.|  
|[Aktualisieren](../../../ado/reference/ado-api/update-method.md)|Speichert alle Änderungen, die Sie an der aktuellen Zeile eines **Recordset** -Objekts vornehmen, oder die **Fields** -Auflistung eines **Datensatz** -Objekts.|  
|[Update Batch](../../../ado/reference/ado-api/updatebatch-method.md)|Schreibt alle ausstehenden Batch Aktualisierungen auf den Datenträger.|  
|[Schreiben](../../../ado/reference/ado-api/write-method.md)|Schreibt Binärdaten in ein Daten **Strom** Objekt.|  
|[WRITETEXT](../../../ado/reference/ado-api/writetext-method.md)|Schreibt eine angegebene Text Zeichenfolge in ein Daten **Strom** Objekt.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ADO-API-Referenz](../../../ado/reference/ado-api/ado-api-reference.md)   
 [ADO-Sammlungen](../../../ado/reference/ado-api/ado-collections.md)   
 [Dynamische ADO-Eigenschaften](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [ADO-Enumerationskonstanten](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Anhang B: ADO-Fehler](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [ADO-Ereignisse](../../../ado/reference/ado-api/ado-events.md)   
 [ADO-Objektmodell](../../../ado/reference/ado-api/ado-object-model.md)   
 [ADO-Objekte und-Schnittstellen](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [ADO-Eigenschaften](../../../ado/reference/ado-api/ado-properties.md)
