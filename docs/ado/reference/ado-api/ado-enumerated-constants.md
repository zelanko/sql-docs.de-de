---
title: ADO-Enumerationskonstanten | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 00b33a9fa92dd6ec86cbac5a939fe593725bc091
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82749217"
---
# <a name="ado-enumerated-constants"></a>ADO – Enumerationskonstanten
Um das Debuggen zu unterstützen, listet die ADO-Enumerationen einen Wert für jede Konstante auf. Dieser Wert ist jedoch rein beratend und kann sich von einem Release von ADO zu einem anderen ändern. Der Code sollte nur vom Namen und nicht vom tatsächlichen Wert der einzelnen Enumerationskonstanten abhängen.  
  
|||  
|-|-|  
|[ADCPROP_ASYNCTHREADPRIORITY_ENUM](../../../ado/reference/ado-api/adcprop-asyncthreadpriority-enum.md)|Gibt für ein **Recordset** RDS-Recordsetobjekt die Ausführungs Priorität des asynchronen Threads an, der Daten abruft.|  
|[ADCPROP_AUTORECALC_ENUM](../../../ado/reference/ado-api/adcprop-autorecalc-enum.md)|Gibt an, wann der **MSDataShape** -Anbieter aggregierte und berechnete Spalten in einem hierarchischen **Recordset**neu berechnet.|  
|[ADCPROP_UPDATECRITERIA_ENUM](../../../ado/reference/ado-api/adcprop-updatecriteria-enum.md)|Gibt an, welche Felder zum Erkennen von Konflikten während einer vollständigen Aktualisierung einer Zeile der Datenquelle mit einem **Recordset** -Objekt verwendet werden können.|  
|[ADCPROP_UPDATERESYNC_ENUM](../../../ado/reference/ado-api/adcprop-updateresync-enum.md)|Gibt an, ob auf die **UpdateBatch** -Methode ein impliziter Vorgang zum **erneuten Synchronisieren** der Methode folgt, und wenn ja, der Gültigkeitsbereich dieses Vorgangs.|  
|[AffectEnum](../../../ado/reference/ado-api/affectenum.md)|Gibt an, welche Datensätze von einem Vorgang betroffen sind.|  
|[BookmarkEnum](../../../ado/reference/ado-api/bookmarkenum.md)|Gibt ein Lesezeichen an, das angibt, wo der Vorgang beginnen soll.|  
|[CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)|Gibt an, wie ein Befehls Argument interpretiert werden soll.|  
|[CompareEnum](../../../ado/reference/ado-api/compareenum.md)|Gibt die relative Position von zwei Datensätzen an, die durch Ihre Lesezeichen dargestellt werden.|  
|[ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md)|Gibt die verfügbaren Berechtigungen zum Ändern von Daten in einer **Verbindung**, zum Öffnen eines Daten **Satzes**oder zum Angeben von Werten für die **Mode** -Eigenschaft des **Datensatz** -und des **Stream** -Objekts an.|  
|[ConnectOptionEnum](../../../ado/reference/ado-api/connectoptionenum.md)|Gibt an, ob die **Open** -Methode eines **Verbindungs** Objekts nach (synchron) oder vor (asynchron) der Verbindung zurückgegeben werden soll.|  
|[ConnectPromptEnum](../../../ado/reference/ado-api/connectpromptenum.md)|Gibt an, ob ein Dialogfeld angezeigt werden soll, um beim Öffnen einer Verbindung mit einer ODBC-Datenquelle nach fehlenden Parametern zu suchen.|  
|[CopyRecordOptionsEnum](../../../ado/reference/ado-api/copyrecordoptionsenum.md)|Gibt das Verhalten der **CopyRecord** -Methode an.|  
|[CursorLocationEnum](../../../ado/reference/ado-api/cursorlocationenum.md)|Gibt den Speicherort der Cursor-Engine an.|  
|[CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md)|Gibt an, auf welche Funktionalität die **unterstützte** Methode testen soll.|  
|[CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md)|Gibt den Typ des Cursors an, der in einem **Recordset** -Objekt verwendet wird.|  
|[DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md)|Gibt den Datentyp eines **Felds**, eines **Parameters**oder einer **Eigenschaft**an.|  
|[EditModeEnum](../../../ado/reference/ado-api/editmodeenum.md)|Gibt den Bearbeitungsstatus eines Datensatzes an.|  
|[ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md)|Gibt den Typ des ADO-Lauf Zeit Fehlers an.|  
|[EventReasonEnum](../../../ado/reference/ado-api/eventreasonenum.md)|Gibt den Grund an, warum ein Ereignis aufgetreten ist.|  
|[EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md)|Gibt den aktuellen Status der Ausführung eines Ereignisses an.|  
|[ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md)|Gibt an, wie ein Anbieter einen Befehl ausführen soll.|  
|[FieldEnum](../../../ado/reference/ado-api/fieldenum.md)|Gibt die speziellen Felder an, auf die in der **Fields** -Auflistung eines **Datensatz** -Objekts verwiesen wird.|  
|[FieldAttributeEnum](../../../ado/reference/ado-api/fieldattributeenum.md)|Gibt ein oder mehrere Attribute eines **Feld** Objekts an.|  
|[FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md)|Gibt den Status eines **Feld** Objekts an.|  
|[FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md)|Gibt die Gruppe von Datensätzen an, die von einem **Recordset**gefiltert werden sollen.|  
|[GetRowsOptionEnum](../../../ado/reference/ado-api/getrowsoptionenum.md)|Gibt an, wie viele Datensätze aus einem **Recordset**abgerufen werden sollen.|  
|[IsolationLevelEnum](../../../ado/reference/ado-api/isolationlevelenum.md)|Gibt die Ebene der Transaktions Isolation für ein **Verbindungs** Objekt an.|  
|[LineSeparatorsEnum](../../../ado/reference/ado-api/lineseparatorsenum.md)|Gibt das Zeichen an, das als Zeilen Trennzeichen in **textstreamobjekten** verwendet wird.|  
|[LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md)|Gibt den Typ der Sperre an, die während der Bearbeitung in Datensätzen eingefügt wird|  
|[MarshalOptionsEnum](../../../ado/reference/ado-api/marshaloptionsenum.md)|Gibt an, welche Datensätze an den Server zurückgegeben werden sollen.|  
|[MoveRecordOptionsEnum](../../../ado/reference/ado-api/moverecordoptionsenum.md)|Gibt das Verhalten des **Daten Satz** Objekts **an** .|  
|[ObjectStateEnum](../../../ado/reference/ado-api/objectstateenum.md)|Gibt an, ob ein Objekt geöffnet oder geschlossen ist, ob eine Verbindung mit einer Datenquelle hergestellt wird, ob ein Befehl ausgeführt oder Daten abgerufen werden.|  
|[ParameterAttributesEnum](../../../ado/reference/ado-api/parameterattributesenum.md)|Gibt die Attribute eines **Parameter** Objekts an.|  
|[ParameterDirectionEnum](../../../ado/reference/ado-api/parameterdirectionenum.md)|Gibt an, ob der **Parameter** einen Eingabeparameter, einen Ausgabeparameter oder beides darstellt oder ob der Parameter der Rückgabewert einer gespeicherten Prozedur ist.|  
|[PersistFormatEnum](../../../ado/reference/ado-api/persistformatenum.md)|Gibt das Format an, in dem ein **Recordset**gespeichert werden soll.|  
|[PositionEnum](../../../ado/reference/ado-api/positionenum.md)|Gibt die aktuelle Position des Daten Satz Zeigers innerhalb eines **Recordsets**an.|  
|[PropertyAttributesEnum](../../../ado/reference/ado-api/propertyattributesenum.md)|Gibt die Attribute eines **Eigenschafts** Objekts an.|  
|[RecordCreateOptionsEnum](../../../ado/reference/ado-api/recordcreateoptionsenum.md)|Gibt für die **Open** -Methode des **Daten Satz** Objekts an, ob ein vorhandener **Datensatz** geöffnet werden soll oder ob ein neuer **Datensatz** erstellt werden soll.|  
|[RecordOpenOptionsEnum](../../../ado/reference/ado-api/recordopenoptionsenum.md)|Gibt Optionen für das Öffnen eines **Datensatzes**an. Diese Werte können mit einem or-Operator kombiniert werden.|  
|[RecordStatusEnum](../../../ado/reference/ado-api/recordstatusenum.md)|Gibt den Status eines Datensatzes in Bezug auf Batch Updates und andere Massen Vorgänge an.|  
|[RecordTypeEnum](../../../ado/reference/ado-api/recordtypeenum.md)|Gibt den Typ des **Daten Satz** Objekts an.|  
|[ResyncEnum](../../../ado/reference/ado-api/resyncenum.md)|Gibt an, ob zugrunde liegende Werte durch einen Rückruf von **Resync**überschrieben werden.|  
|[SaveOptionsEnum](../../../ado/reference/ado-api/saveoptionsenum.md)|Gibt an, ob eine Datei beim Speichern aus einem **Streamobjekt** erstellt oder überschrieben werden soll. Die Werte können mit einem and-Operator kombiniert werden.|  
|[SchemaEnum](../../../ado/reference/ado-api/schemaenum.md)|Gibt den Typ des Schema- **Recordsets** an, das von der **OpenSchema** -Methode abgerufen wird. Gibt die Richtung einer Daten Satz Suche innerhalb eines **Recordsets**an.|  
|[SearchDirectionEnum](../../../ado/reference/ado-api/searchdirectionenum.md)|Gibt die Richtung einer Daten Satz Suche innerhalb eines **Recordsets**an. Gibt den Typ des auszuführenden **Suchtyps** an.|  
|[SeekEnum](../../../ado/reference/ado-api/seekenum.md)|Gibt den Typ des auszuführenden **Suchtyps** an. Gibt Optionen für das Öffnen eines Daten **Strom** Objekts an. Die Werte können mit einem and-Operator kombiniert werden.|  
|[StreamOpenOptionsEnum](../../../ado/reference/ado-api/streamopenoptionsenum.md)|Gibt Optionen für das Öffnen eines Daten **Strom** Objekts an. Die Werte können mit einem and-Operator kombiniert werden. Gibt an, ob der gesamte Stream oder die nächste Zeile aus einem **Streamobjekt** gelesen werden soll.|  
|[StreamReadEnum](../../../ado/reference/ado-api/streamreadenum.md)|Gibt an, ob der gesamte Stream oder die nächste Zeile aus einem **Streamobjekt** gelesen werden soll. Gibt den Typ der in einem **Streamobjekt** gespeicherten Daten an.|  
|[StreamTypeEnum](../../../ado/reference/ado-api/streamtypeenum.md)|Gibt den Typ der in einem **Streamobjekt** gespeicherten Daten an. Gibt an, ob ein Zeilen Trennzeichen an die Zeichenfolge angefügt wird, die in ein **Streamobjekt** geschrieben wird|  
|[StreamWriteEnum](../../../ado/reference/ado-api/streamwriteenum.md)|Gibt an, ob ein Zeilen Trennzeichen an die Zeichenfolge angefügt wird, die in ein **Streamobjekt** geschrieben wird Gibt das Format beim Abrufen eines **Recordsets** als Zeichenfolge an.|  
|[StringFormatEnum](../../../ado/reference/ado-api/stringformatenum.md)|Gibt das Format beim Abrufen eines **Recordsets** als Zeichenfolge an. Gibt die Transaktions Attribute eines **Verbindungs** Objekts an.|  
|[XactAttributeEnum](../../../ado/reference/ado-api/xactattributeenum.md)|Gibt die Transaktions Attribute eines **Verbindungs** Objekts an.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ADO-API-Referenz](../../../ado/reference/ado-api/ado-api-reference.md)   
 [ADO-Sammlungen](../../../ado/reference/ado-api/ado-collections.md)   
 [Dynamische ADO-Eigenschaften](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [Anhang B: ADO-Fehler](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [ADO-Ereignisse](../../../ado/reference/ado-api/ado-events.md)   
 [ADO-Methoden](../../../ado/reference/ado-api/ado-methods.md)   
 [ADO-Objektmodell](../../../ado/reference/ado-api/ado-object-model.md)   
 [ADO-Objekte und-Schnittstellen](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [ADO-Eigenschaften](../../../ado/reference/ado-api/ado-properties.md)
