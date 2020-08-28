---
description: ADO-Methoden
title: ADO-Methoden | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 13e126f070f188e47582227fabf4a1e37d6901a3
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88976371"
---
# <a name="ado-methods"></a>ADO-Methoden

|Methode|Beschreibung|  
|-|-|  
|[AddNew](./addnew-method-ado.md)|Erstellt einen neuen Datensatz für ein Aktualisier bares **Recordset** -Objekt.|  
|[Append](./append-method-ado.md) (Anfügen)|Fügt ein Objekt an eine Auflistung an. Wenn es sich bei der Auflistung um **Felder**handelt, kann ein neues **Feld** Objekt erstellt werden, bevor es an die Auflistung angefügt wird.|  
|[AppendChunk](./appendchunk-method-ado.md)|Fügt Daten an ein großes Textfeld oder ein binäres **Datenfeld**oder an ein **Parameter** Objekt an.|  
|[BeginTrans, CommitTrans und RollbackTrans](./begintrans-committrans-and-rollbacktrans-methods-ado.md)|Verwaltet die Transaktionsverarbeitung innerhalb eines **Verbindungs** Objekts wie folgt:<br /><br /> **BeginTrans** -startet eine neue Transaktion.<br /><br /> **CommitTrans** -speichert alle Änderungen und beendet die aktuelle Transaktion. Möglicherweise wird auch eine neue Transaktion gestartet.<br /><br /> **RollbackTrans** -bricht alle Änderungen ab und beendet die aktuelle Transaktion. Möglicherweise wird auch eine neue Transaktion gestartet.|  
|[Abbrechen](./cancel-method-ado.md)|Bricht die Ausführung eines ausstehenden asynchronen Methoden Aufrufes ab.|  
|[CancelBatch](./cancelbatch-method-ado.md)|Bricht ein ausstehendes Batch Update ab.|  
|[CancelUpdate](./cancelupdate-method-ado.md)|Bricht vor dem Aufrufen der **Update** -Methode alle Änderungen ab, die an der aktuellen oder neuen Zeile eines **Recordset** -Objekts oder der **Fields** -Auflistung eines **Datensatz** -Objekts vorgenommen wurden.|  
|[Clear](./clear-method-ado.md)|Entfernt alle **Fehler** Objekte aus der **Fehler** Auflistung.|  
|[Klonen](./clone-method-ado.md)|Erstellt ein doppeltes **Recordset** -Objekt aus einem vorhandenen **Recordset** -Objekt. Gibt optional an, dass der Klon schreibgeschützt ist.|  
|[Schließen](./close-method-ado.md)|Schließt ein offenes Objekt und alle abhängigen Objekte.|  
|[CompareBookmarks](./comparebookmarks-method-ado.md)|Vergleicht zwei Lesezeichen und gibt eine Angabe über das Verhältnis der entsprechenden Werte zurück.|  
|[CopyRecord](./copyrecord-method-ado.md)|Kopiert eine Datei oder ein Verzeichnis und seinen Inhalt an einen anderen Speicherort.|  
|[CopyTo](./copyto-method-ado.md)|Kopiert die angegebene Anzahl von Zeichen oder bytes (abhängig vom **Typ**) im **Stream** in ein anderes **Streamobjekt** .|  
|[CreateParameter](./createparameter-method-ado.md)|Erstellt ein neues **Parameter** Objekt, das über die angegebenen Eigenschaften verfügt.|  
|[Delete (ADO Parameters-Sammlung)](./delete-method-ado-parameters-collection.md)|Löscht ein-Objekt aus der **Parameter** Auflistung.|  
|[Delete (ADO Fields-Auflistung)](./delete-method-ado-fields-collection.md)|Löscht ein-Objekt aus der **Fields** -Auflistung.|  
|[Delete (ADO-Recordset)](./delete-method-ado-recordset.md)|Löscht den aktuellen Datensatz oder eine Gruppe von Datensätzen.|  
|[DeleteRecord](./deleterecord-method-ado.md)|Löscht eine Datei oder ein Verzeichnis und alle Unterverzeichnisse.|  
|[Execute (ADO-Befehl)](./execute-method-ado-command.md)|Führt die Abfrage, die SQL-Anweisung oder die gespeicherte Prozedur aus, die in der **CommandText** -Eigenschaft angegeben ist.|  
|[Ausführen (ADO-Verbindung)](./execute-method-ado-connection.md)|Führt die angegebene Abfrage, die SQL-Anweisung, die gespeicherte Prozedur oder den anbieterspezifischen Text aus.|  
|[Suchen](./find-method-ado.md)|Durchsucht ein **Recordset** nach der Zeile, die die angegebenen Kriterien erfüllt.|  
|[Leerung](./flush-method-ado.md)|Erzwingt den Inhalt des verbleibenden **Streams** im ADO-Puffer für das zugrunde liegende Objekt, dem der **Stream** zugeordnet ist.|  
|[get_OLEDBCommand-Methode](./get-oledbcommand-method.md)|Gibt den zugrunde liegenden OLEDB-Befehl zurück, wobei zuerst alle Parameterinformationen weitergegeben werden, die für den ADO-Befehl an den OLEDB-Befehl festgelegt|  
|[GetChildren](./getchildren-method-ado.md)|Gibt ein **Recordset** zurück, dessen Zeilen die Dateien und Unterverzeichnisse in dem von diesem **Datensatz**dargestellten Verzeichnis darstellen.|  
|[GetChunk](./getchunk-method-ado.md)|Gibt alle oder einen Teil von, den Inhalt eines großen **Textfelds** oder eines Binärdaten Feld Objekts zurück.|  
|[GetDataProviderDSO-Methode](./getdataproviderdso-method.md)|Ruft das zugrunde liegende OLEDB-Datenquellen Objekt vom Shape-Anbieter ab.|  
|[GetRows](./getrows-method-ado.md)|Ruft mehrere Datensätze eines **Recordset** -Objekts in ein Array ab.|  
|[GetString](./getstring-method-ado.md)|Gibt das **Recordset** als Zeichenfolge zurück.|  
|[LoadFromFile](./loadfromfile-method-ado.md)|Lädt den Inhalt einer vorhandenen Datei in einen **Stream**.|  
|[Verschieben](./move-method-ado.md)|Verschiebt die Position des aktuellen Datensatzes in einem **Recordset** -Objekt.|  
|["Muvefirst", "muvelast", "muvenext" und "muveprevious"](./movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Wechselt zum ersten, letzten, nächsten oder vorherigen Datensatz in einem angegebenen **Recordset** -Objekt und legt diesen Datensatz auf den aktuellen Datensatz fest.|  
|[Der Pfad](./moverecord-method-ado.md)|Verschiebt eine Datei oder ein Verzeichnis und seinen Inhalt an einen anderen Speicherort.|  
|[NextRecordset](./nextrecordset-method-ado.md)|Löscht das aktuelle **Recordset** -Objekt und gibt das nächste **Recordset** zurück, indem eine Reihe von Befehlen durchlaufen wird.|  
|[Öffnen (ADO-Verbindung)](./open-method-ado-connection.md)|Öffnet eine Verbindung mit einer Datenquelle.|  
|[Öffnen (ADO-Datensatz)](./open-method-ado-record.md)|Öffnet ein vorhandenes **Daten Satz** Objekt oder erstellt eine neue Datei oder ein neues Verzeichnis.|  
|[Open (ADO-Recordset)](./open-method-ado-recordset.md)|Öffnet einen Cursor.|  
|[Open (ADO-Stream)](./open-method-ado-stream.md)|Öffnet ein **Stream** -Objekt, um Datenströme von Binär-oder Textdaten zu bearbeiten.|  
|[OpenSchema](./openschema-method.md)|Ruft Datenbankschema Informationen vom Anbieter ab.|  
|[put_OLEDBCommand-Methode](./put-oledbcommand-method.md)|Diese Methode führt keinen Vorgang aus, sondern gibt immer S_OK zurück.|  
|[Lesen](./read-method.md)|Liest eine angegebene Anzahl von Bytes aus einem **Streamobjekt** .|  
|[READTEXT](./readtext-method.md)|Liest eine angegebene Anzahl von Zeichen aus einem **Textstreamobjekt** .|  
|[Aktualisieren](./refresh-method-ado.md)|Aktualisiert die Objekte in einer Auflistung, um die Objekte widerzuspiegeln, die von und für den Anbieter verfügbar sind.|  
|[Requery](./requery-method.md)|Aktualisiert die Daten in einem **Recordset** -Objekt, indem die Abfrage erneut ausgeführt wird, auf der das Objekt basiert.|  
|[Erneut synchronisieren](./resync-method.md)|Aktualisiert die Daten im aktuellen **Recordset** -Objekt oder der **Fields** -Auflistung eines **Datensatz** -Objekts aus der zugrunde liegenden Datenbank.|  
|[Speichern](./save-method.md)|Speichert das **Recordset** in einer Datei oder einem **Streamobjekt** .|  
|[SaveToFile](./savetofile-method.md)|Speichert den binären Inhalt eines **Streams** in einer Datei.|  
|[Seek](./seek-method.md)|Durchsucht den Index eines **Recordsets** , um die Zeile, die mit den angegebenen Werten übereinstimmt, schnell zu finden und die aktuelle Zeilen Position in diese Zeile zu ändern.|  
|[-Betriebssystem](./seteos-method.md)|Legt die Position fest, die das Ende des Streams ist.|  
|[SkipLine](./skipline-method.md)|Überspringt beim Lesen eines Textstreams eine gesamte Zeile.|  
|[Ierende](./stat-method.md)|Ruft statistische Informationen zu einem geöffneten Stream ab.|  
|[Unterstützt](./supports-method.md)|Bestimmt, ob ein angegebenes **Recordsetobjekt** einen bestimmten Funktionstyp unterstützt.|  
|[Aktualisieren](./update-method.md)|Speichert alle Änderungen, die Sie an der aktuellen Zeile eines **Recordset** -Objekts vornehmen, oder die **Fields** -Auflistung eines **Datensatz** -Objekts.|  
|[Update Batch](./updatebatch-method.md)|Schreibt alle ausstehenden Batch Aktualisierungen auf den Datenträger.|  
|[Schreiben](./write-method.md)|Schreibt Binärdaten in ein Daten **Strom** Objekt.|  
|[WRITETEXT](./writetext-method.md)|Schreibt eine angegebene Text Zeichenfolge in ein Daten **Strom** Objekt.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ADO-API-Referenz](./ado-api-reference.md)   
 [ADO-Sammlungen](./ado-collections.md)   
 [Dynamische ADO-Eigenschaften](./ado-dynamic-properties.md)   
 [ADO-Enumerationskonstanten](./ado-enumerated-constants.md)   
 [Anhang B: ADO-Fehler](../../guide/appendixes/appendix-b-ado-errors.md)   
 [ADO-Ereignisse](./ado-events.md)   
 [ADO-Objektmodell](./ado-object-model.md)   
 [ADO-Objekte und-Schnittstellen](./ado-objects-and-interfaces.md)   
 [ADO-Eigenschaften](./ado-properties.md)