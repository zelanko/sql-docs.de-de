---
title: ADO – Enumerationskonstanten | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- enumerated constants [ADO]
ms.assetid: c97ed131-1a93-463c-9e61-22f029b0c474
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 4d9b2e581bfbce225bd34e78761b9e8ade621172
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66696726"
---
# <a name="ado-enumerated-constants"></a>ADO – Enumerationskonstanten
Um das Debuggen zu erleichtern, Listen die ADO-Enumerationen einen Wert für jede Konstante. Allerdings wird dieser Wert ist nur eine Empfehlung und kann von einer Version von ADO auf einen anderen ändern. Ihr Code sollte nur auf den Namen, die nicht der tatsächliche Wert, der jede Enumerationskonstante abhängen.  
  
|||  
|-|-|  
|[ADCPROP_ASYNCTHREADPRIORITY_ENUM](../../../ado/reference/ado-api/adcprop-asyncthreadpriority-enum.md)|Für eine RDS **Recordset** Objekt, gibt die Ausführungspriorität des asynchronen Threads, die Daten abruft.|  
|[ADCPROP_AUTORECALC_ENUM](../../../ado/reference/ado-api/adcprop-autorecalc-enum.md)|Gibt an, wann die **MSDataShape** -Anbieter erneut berechnet aggregate und berechnete Spalten in einer hierarchischen **Recordset**.|  
|[ADCPROP_UPDATECRITERIA_ENUM](../../../ado/reference/ado-api/adcprop-updatecriteria-enum.md)|Gibt an, welche Felder verwendet werden können, zum Erkennen von Konflikten während einer vollständigen Aktualisierung einer Zeile mit der Datenquelle mit einem **Recordset** Objekt.|  
|[ADCPROP_UPDATERESYNC_ENUM](../../../ado/reference/ado-api/adcprop-updateresync-enum.md)|Gibt an, ob die **UpdateBatch** Methode einen impliziten folgt **Resync** -Methodenvorgangs und wenn Ja, im Rahmen dieses Vorgangs.|  
|[AffectEnum](../../../ado/reference/ado-api/affectenum.md)|Gibt an, welche Datensätze von einem Vorgang betroffen sind.|  
|[BookmarkEnum](../../../ado/reference/ado-api/bookmarkenum.md)|Gibt an, ein Lesezeichen, das angibt, in dem der Vorgang beginnen soll.|  
|[CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)|Gibt an, wie ein Befehlsargument interpretiert werden soll.|  
|[CompareEnum](../../../ado/reference/ado-api/compareenum.md)|Gibt die relative Position von zwei Datensätzen von Textmarken dargestellt werden.|  
|[ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md)|Gibt an, die verfügbaren Berechtigungen zum Ändern von Daten in eine **Verbindung**, öffnen ein **Datensatz**, oder Werte für die **Modus** Eigenschaft der  **Datensatz** und **Stream** Objekte.|  
|[ConnectOptionEnum](../../../ado/reference/ado-api/connectoptionenum.md)|Gibt an, ob der **öffnen** Methode eine **Verbindung** Objekt sollte nach dem zurückgeben (synchron) oder vor (asynchron) die Verbindung hergestellt wird.|  
|[ConnectPromptEnum](../../../ado/reference/ado-api/connectpromptenum.md)|Gibt an, ob ein Dialogfeld angezeigt werden soll, um fehlende Parameter beim Öffnen einer Verbindung mit einer ODBC-Datenquelle anzufordern.|  
|[CopyRecordOptionsEnum](../../../ado/reference/ado-api/copyrecordoptionsenum.md)|Gibt das Verhalten der **CopyRecord** Methode.|  
|[CursorLocationEnum](../../../ado/reference/ado-api/cursorlocationenum.md)|Gibt den Speicherort der Cursor-Engine.|  
|[CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md)|Gibt an, welche Funktionen die **unterstützt** Methode testen sollten.|  
|[CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md)|Gibt den Typ des Cursors verwendet eine **Recordset** Objekt.|  
|[DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md)|Gibt an, der den Datentyp des einen **Feld**, **Parameter**, oder **Eigenschaft**.|  
|[EditModeEnum](../../../ado/reference/ado-api/editmodeenum.md)|Gibt den Bearbeitungsstatus eines Datensatzes an.|  
|[ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md)|Gibt den Typ des ADO-Laufzeitfehler.|  
|[EventReasonEnum](../../../ado/reference/ado-api/eventreasonenum.md)|Gibt den Grund für der Eintreten ein Ereignisses verursacht hat.|  
|[EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md)|Gibt den aktuellen Status der Ausführung eines Ereignisses an.|  
|[ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md)|Gibt an, wie ein Anbieter einen Befehl ausführen soll.|  
|[FieldEnum](../../../ado/reference/ado-api/fieldenum.md)|Gibt an, die spezielle Felder, die auf die verwiesen wird der **Felder** Auflistung von einem **Datensatz** Objekt.|  
|[FieldAttributeEnum](../../../ado/reference/ado-api/fieldattributeenum.md)|Gibt einen oder mehrere Attribute einer **Feld** Objekt.|  
|[FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md)|Gibt den Status einer **Feld** Objekt.|  
|[FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md)|Gibt die Gruppe von Datensätzen, die von gefiltert werden eine **Recordset**.|  
|[GetRowsOptionEnum](../../../ado/reference/ado-api/getrowsoptionenum.md)|Gibt an, wie viele Datensätze abrufen aus einer **Recordset**.|  
|[IsolationLevelEnum](../../../ado/reference/ado-api/isolationlevelenum.md)|Gibt die Ebene der Isolation jeder Transaktion für eine **Verbindung** Objekt.|  
|[LineSeparatorsEnum](../../../ado/reference/ado-api/lineseparatorsenum.md)|Gibt das Zeichen als Zeilentrennzeichen in Text **Stream** Objekte.|  
|[LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md)|Gibt den Typ der Sperre, die auf Datensätze platziert werden, während der Bearbeitung.|  
|[MarshalOptionsEnum](../../../ado/reference/ado-api/marshaloptionsenum.md)|Gibt an, welche Datensätze mit dem Server zurückgegeben werden sollen.|  
|[MoveRecordOptionsEnum](../../../ado/reference/ado-api/moverecordoptionsenum.md)|Gibt das Verhalten der **Datensatz** Objekt **MoveRecord** Methode.|  
|[ObjectStateEnum](../../../ado/reference/ado-api/objectstateenum.md)|Gibt an, ob ein Objekt offen oder geschlossen ist, Herstellen einer Verbindung mit einer Datenquelle Ausführen eines Befehls oder Abrufen von Daten.|  
|[ParameterAttributesEnum](../../../ado/reference/ado-api/parameterattributesenum.md)|Gibt die Attribute einer **Parameter** Objekt.|  
|[ParameterDirectionEnum](../../../ado/reference/ado-api/parameterdirectionenum.md)|Gibt an, ob die **Parameter** stellt einen Eingabeparameter, Ausgabeparameter oder beides, oder wenn der Parameter den Rückgabewert einer gespeicherten Prozedur ist.|  
|[PersistFormatEnum](../../../ado/reference/ado-api/persistformatenum.md)|Gibt das Format zum Speichern einer **Recordset**.|  
|[PositionEnum](../../../ado/reference/ado-api/positionenum.md)|Gibt die aktuelle Position des Datensatzzeigers innerhalb einer **Recordset**.|  
|[PropertyAttributesEnum](../../../ado/reference/ado-api/propertyattributesenum.md)|Gibt die Attribute einer **Eigenschaft** Objekt.|  
|[RecordCreateOptionsEnum](../../../ado/reference/ado-api/recordcreateoptionsenum.md)|Gibt an, für die **Datensatz** Objekt **öffnen** Methode, ob ein vorhandenes **Datensatz** muss geöffnet, oder ein neues **Datensatz** erstellt werden soll.|  
|[RecordOpenOptionsEnum](../../../ado/reference/ado-api/recordopenoptionsenum.md)|Gibt Optionen zum Öffnen einer **Datensatz**. Diese Werte können mithilfe eines OR-Operators kombiniert werden.|  
|[RecordStatusEnum](../../../ado/reference/ado-api/recordstatusenum.md)|Gibt den Status eines Datensatzes in Bezug auf Batch-Updates und andere Massenvorgänge.|  
|[RecordTypeEnum](../../../ado/reference/ado-api/recordtypeenum.md)|Gibt den Typ der **Datensatz** Objekt.|  
|[ResyncEnum](../../../ado/reference/ado-api/resyncenum.md)|Gibt an, ob die zugrunde liegende Werte überschrieben werden, durch einen Aufruf von **Resync**.|  
|[SaveOptionsEnum](../../../ado/reference/ado-api/saveoptionsenum.md)|Gibt an, ob eine Datei erstellt oder überschrieben, wenn von gespeichert werden sollte eine **Stream** Objekt. Die Werte können mit einer AND-Operator kombiniert werden.|  
|[SchemaEnum](../../../ado/reference/ado-api/schemaenum.md)|Gibt den Typ des Schemas **Recordset** , die die **OpenSchema** Methode abgerufen. Gibt die Richtung des einem Datensatz suchen innerhalb einer **Recordset**.|  
|[SearchDirectionEnum](../../../ado/reference/ado-api/searchdirectionenum.md)|Gibt die Richtung des einem Datensatz suchen innerhalb einer **Recordset**. Gibt den Typ der **Seek** ausgeführt.|  
|[SeekEnum](../../../ado/reference/ado-api/seekenum.md)|Gibt den Typ der **Seek** ausgeführt. Gibt Optionen zum Öffnen einer **Stream** Objekt. Die Werte können mit einer AND-Operator kombiniert werden.|  
|[StreamOpenOptionsEnum](../../../ado/reference/ado-api/streamopenoptionsenum.md)|Gibt Optionen zum Öffnen einer **Stream** Objekt. Die Werte können mit einer AND-Operator kombiniert werden. Gibt an, ob der gesamte Datenstrom oder die nächste Zeile aus gelesen werden sollen eine **Stream** Objekt.|  
|[StreamReadEnum](../../../ado/reference/ado-api/streamreadenum.md)|Gibt an, ob der gesamte Datenstrom oder die nächste Zeile aus gelesen werden sollen eine **Stream** Objekt. Gibt den Typ der Daten in einem **Stream** Objekt.|  
|[StreamTypeEnum](../../../ado/reference/ado-api/streamtypeenum.md)|Gibt den Typ der Daten in einem **Stream** Objekt. Gibt an, ob ein Zeilentrennzeichen, auf die Zeichenfolge geschrieben angefügt wird, um eine **Stream** Objekt.|  
|[StreamWriteEnum](../../../ado/reference/ado-api/streamwriteenum.md)|Gibt an, ob ein Zeilentrennzeichen, auf die Zeichenfolge geschrieben angefügt wird, um eine **Stream** Objekt. Gibt das Format an, beim Abrufen von einem **Recordset** als Zeichenfolge.|  
|[StringFormatEnum](../../../ado/reference/ado-api/stringformatenum.md)|Gibt das Format an, beim Abrufen von einem **Recordset** als Zeichenfolge. Gibt die Transaktionsattribute von einem **Verbindung** Objekt.|  
|[XactAttributeEnum](../../../ado/reference/ado-api/xactattributeenum.md)|Gibt die Transaktionsattribute von einem **Verbindung** Objekt.|  
  
## <a name="see-also"></a>Siehe auch  
 [ADO-API-Referenz](../../../ado/reference/ado-api/ado-api-reference.md)   
 [ADO-Collections](../../../ado/reference/ado-api/ado-collections.md)   
 [ADO – dynamische Eigenschaften](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [Anhang B: ADO-Fehler](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [ADO-Ereignisse](../../../ado/reference/ado-api/ado-events.md)   
 [ADO-Methoden](../../../ado/reference/ado-api/ado-methods.md)   
 [ADO-Objektmodell](../../../ado/reference/ado-api/ado-object-model.md)   
 [ADO-Objekte und Schnittstellen](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [ADO-Eigenschaften](../../../ado/reference/ado-api/ado-properties.md)
