---
description: ADO-Eigenschaften
title: ADO-Eigenschaften | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- properties [ADO]
- ADO properties
ms.assetid: 0ac0d1a7-6c7a-4f4c-b115-428935e0f98b
author: rothja
ms.author: jroth
ms.openlocfilehash: a8a53f4b901209a1ef59be6ca2eb8b531bc52d7c
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88976281"
---
# <a name="ado-properties"></a>ADO-Eigenschaften

|Eigenschaft|Beschreibung|  
|-|-|  
|[AbsolutePage](./absolutepage-property-ado.md)|Gibt an, auf welcher Seite sich der aktuelle Datensatz befindet.|  
|[AbsolutePosition](./absoluteposition-property-ado.md)|Gibt die Ordnungsposition des aktuellen Datensatzes eines **Recordset** -Objekts an.|  
|[ActiveCommand](./activecommand-property-ado.md)|Gibt das **Befehls** Objekt an, das das zugeordnete **Recordset** -Objekt erstellt hat.|  
|[ActiveConnection](./activeconnection-property-ado.md)|Gibt an, zu welchem **Verbindungs** Objekt der angegebene **Befehl**, das **Recordset**oder das **Datensatz** -Objekt derzeit gehört.|  
|[ActualSize](./actualsize-property-ado.md)|Gibt die tatsächliche Länge eines Feldwerts an.|  
|[Attribute](./attributes-property-ado.md)|Gibt eine oder mehrere Eigenschaften eines Objekts an.|  
|[BOF und EOF](./bof-eof-properties-ado.md)|**BOF** gibt an, dass die aktuelle Daten Satz Position vor dem ersten Datensatz in einem Recordset-Objekt liegt.<br /><br /> **EOF** gibt an, dass die aktuelle Daten Satz Position hinter dem letzten Datensatz in einem Recordset-Objekt liegt.|  
|[Lesezeichen](./bookmark-property-ado.md)|Gibt ein Lesezeichen an, das den aktuellen Datensatz in einem **Recordset** -Objekt eindeutig identifiziert, oder legt den aktuellen Datensatz in einem **Recordset** -Objekt auf den Datensatz fest, der durch ein gültiges Lesezeichen identifiziert wird.|  
|[CacheSize](./cachesize-property-ado.md)|Gibt die Anzahl von Datensätzen aus einem **Recordset** -Objekt an, die lokal im Arbeitsspeicher zwischengespeichert werden.|  
|[Kapitel](./chapter-property-ado.md)|Ruft ein OLE DB **Kapitel** Objekt aus/für ein **adorecordsetconstruction** -Objekt ab oder legt es fest.|  
|[CharSet](./charset-property-ado.md)|Gibt den Zeichensatz an, in den der Inhalt eines **Textstreams** übersetzt werden soll.|  
|[CommandStream](./commandstream-property-ado.md)|Gibt den Datenstrom an, der als Eingabe für ein **Command** -Objekt verwendet wird.|  
|[CommandText](./commandtext-property-ado.md)|Gibt den Text eines Befehls an, der für einen Anbieter ausgegeben werden soll.|  
|[CommandTimeout](./commandtimeout-property-ado.md)|Gibt an, wie lange beim Ausführen eines Befehls gewartet werden soll, bevor der Versuch beendet und ein Fehler erzeugt wird.|  
|[CommandType](./commandtype-property-ado.md)|Gibt den Typ eines **Befehls** Objekts an.|  
|[ConnectionString-Eigenschaft](./connectionstring-property-ado.md)|Gibt die Informationen an, die zum Herstellen einer Verbindung mit einer Datenquelle verwendet werden.|  
|[ConnectionTimeout](./connectiontimeout-property-ado.md)|Gibt an, wie lange beim Herstellen einer Verbindung gewartet werden soll, bevor der Versuch beendet und ein Fehler erzeugt wird.|  
|[Count](./count-property-ado.md)|Gibt die Anzahl der-Objekte in einer Auflistung an.|  
|[CursorLocation –](./cursorlocation-property-ado.md)|Gibt den Speicherort des Cursor Dienstanbieter an.|  
|[CursorType](./cursortype-property-ado.md)|Gibt den Typ des Cursors an, der in einem **Recordset** -Objekt verwendet wird.|  
|[DataMember](./datamember-property.md)|Gibt den Namen des Datenmembers an, der aus dem Objekt abgerufen wird, auf das von der **DataSource** -Eigenschaft verwiesen wird.|  
|[DataSource](./datasource-property-ado.md)|Gibt ein Objekt an, das Daten enthält, die als **Recordset** -Objekt dargestellt werden.|  
|[DefaultDatabase](./defaultdatabase-property.md)|Gibt die Standarddatenbank für ein **Verbindungs** Objekt an.|  
|[DefinedSize](./definedsize-property.md)|Gibt die Datenkapazität eines **Feld** Objekts an.|  
|[Beschreibung](./description-property.md)|Beschreibt ein **Fehler** Objekt.|  
|[Twist](./dialect-property.md)|Gibt die Syntax und die allgemeinen Regeln an, die der Anbieter verwendet, um die **CommandText** -oder **CommandStream** -Eigenschaften zu analysieren.|  
|[Richtung](./direction-property.md)|Gibt an, ob der **Parameter** einen Eingabeparameter, einen Ausgabeparameter oder beides darstellt oder ob der Parameter der Rückgabewert einer gespeicherten Prozedur ist.|  
|[EditMode](./editmode-property.md)|Gibt den Bearbeitungsstatus des aktuellen Datensatzes an.|  
|[Stereo](./eos-property.md)|Gibt an, ob sich die aktuelle Position am Ende des Streams befindet.|  
|[Filter](./filter-property.md)|Gibt einen Filter für Daten in einem **Recordset**an.|  
|[HelpContext und HelpFile](./helpcontext-helpfile-properties.md)|Gibt die Hilfedatei und das Thema an, die einem **Fehler** Objekt zugeordnet sind.<br /><br /> **HelpContextID** gibt eine Kontext-ID als **Long** -Wert für ein Thema in einer Hilfedatei zurück.<br /><br /> **HelpFile** gibt einen **Zeichen** folgen Wert zurück, der zu einem vollständig aufgelösten Pfad einer Hilfedatei ausgewertet wird.|  
|[Index](./index-property.md)|Gibt den Namen des Indexes an, der aktuell für ein **Recordset** -Objekt wirksam ist.|  
|[IsolationLevel](./isolationlevel-property.md)|Gibt die Isolationsstufe für ein **Verbindungs** Objekt an.|  
|[Element](./item-property-ado.md)|Gibt einen bestimmten Member einer Auflistung anhand des Namens oder der Ordinalzahl an.|  
|[LineSeparator](./lineseparator-property-ado.md)|Gibt das binäre Zeichen an, das als Zeilen Trennzeichen in **textstreamobjekten** verwendet werden soll.|  
|[LockType](./locktype-property-ado.md)|Gibt den Typ der Sperren an, die während der Bearbeitung in Datensätzen eingefügt werden|  
|[MarshalOptions](./marshaloptions-property-ado.md)|Gibt an, welche Datensätze zurück an den Server gemarshallt werden sollen.|  
|[MaxRecords](./maxrecords-property-ado.md)|Gibt die maximale Anzahl von Datensätzen an, die aus einer Abfrage zu einem **Recordset** zurückgegeben werden sollen.|  
|[Mode](./mode-property-ado.md)|Gibt die verfügbaren Berechtigungen zum Ändern von Daten in einem **Verbindungs**-, **Datensatz**-oder **Streamobjekt** an.|  
|[Name](./name-property-ado.md)|Gibt den Namen eines Objekts an.|  
|[NativeError](./nativeerror-property-ado.md)|Gibt den anbieterspezifischen Fehlercode für ein bestimmtes **Fehler** Objekt an.|  
|[Number](./number-property-ado.md)|Gibt die Zahl an, durch die ein **Fehler** Objekt eindeutig identifiziert wird.|  
|[NumericScale](./numericscale-property-ado.md)|Gibt die Skala numerischer Werte in einem **Parameter** -oder **Feld** Objekt an.|  
|[OriginalValue](./originalvalue-property-ado.md)|Gibt den Wert eines **Felds** an, das im Datensatz vorhanden war, bevor Änderungen vorgenommen wurden.|  
|[PageCount](./pagecount-property-ado.md)|Gibt an, wie viele Datenseiten das **Recordset** -Objekt enthält.|  
|[PageSize](./pagesize-property-ado.md)|Gibt an, wie viele Datensätze eine Seite im **Recordset**darstellen.|  
|[ParentRow](./parentrow-property-ado.md)|Legt den Container eines OLE DB **Row** -Objekts für ein **adorecordconstruction** -Objekt fest, damit das übergeordnete Element der Zeile in ein ADO- **Daten Satz** Objekt umgewandelt wird.|  
|["Parser-URL"](./parenturl-property-ado.md)|Gibt eine absolute URL Zeichenfolge an, die auf den übergeordneten **Datensatz** des aktuellen **Daten Satz** Objekts zeigt.|  
|[Position](./position-property-ado.md)|Gibt die aktuelle Position innerhalb eines **Streamobjekts** an.|  
|[Genauigkeit](./precision-property-ado.md)|Gibt den Genauigkeits Grad für numerische Werte in einem **Parameter** Objekt oder numerischen **Feld** Objekten an.|  
|[Vorbereitet](./prepared-property-ado.md)|Gibt an, ob eine kompilierte Version eines Befehls vor der Ausführung gespeichert werden soll.|  
|[Anbieter](./provider-property-ado.md)|Gibt den Namen des Anbieters für ein **Verbindungs** Objekt an.|  
|[RecordCount](./recordcount-property-ado.md)|Gibt die Anzahl der Datensätze in einem **Recordset** -Objekt an.|  
|[RecordType](./recordtype-property-ado.md)|Gibt den Typ des **Daten Satz** Objekts an.|  
|[Zeile](./row-property-ado.md)|Ruft ein OLE DB **Zeilen** Objekt aus/für ein **adorecordconstruction** -Objekt ab oder legt es fest.|  
|[RowPosition](./rowposition-property-ado.md)|Ruft ein OLE DB **RowPosition** -Objekt von/in einem **adorecordsetconstruction** -Objekt ab oder legt es fest.|  
|[Rowset](./rowset-property-ado.md)|Ruft ein OLE DB Rowsetobjekt aus/in einem **adorecordsetconstruction** -Objekt ab oder legt dieses **fest** .|  
|[Quelle (ADO-Fehler)](./source-property-ado-error.md)|Gibt den Namen des Objekts oder der Anwendung an, das ursprünglich einen Fehler generiert hat.|  
|[Quelle (ADO-Datensatz)](./source-property-ado-record.md)|Gibt die durch das **Daten Satz** Objekt dargestellte Entität an.|  
|[Quelle (ADO-Recordset)](./source-property-ado-recordset.md)|Gibt die Quelle für die Daten in einem **Recordset** -Objekt an.|  
|[SQLSTATE](./sqlstate-property.md)|Gibt den SQL-Status für ein bestimmtes **Fehler** Objekt an.|  
|[State](./state-property-ado.md)|Gibt für alle anwendbaren Objekte an, ob der Status des Objekts geöffnet oder geschlossen ist. Gibt für alle anwendbaren Objekte an, die eine asynchrone Methode ausführen, und zwar unabhängig davon, ob der aktuelle Zustand des Objekts eine Verbindung herstellt, ausführt oder abgerufen wird.|  
|[Status (ADO-Feld)](./status-property-ado-field.md)|Gibt den Status eines **Feld** Objekts an.|  
|[Status (ADO-Recordset)](./status-property-ado-recordset.md)|Gibt den Status des aktuellen Datensatzes zu Batch Aktualisierungen oder anderen Massen Vorgängen an.|  
|[StayInSync](./stayinsync-property.md)|Gibt in einem hierarchischen **Recordsetobjekt** an, ob sich der Verweis auf die zugrunde liegenden untergeordneten Datensätze (d. h. das *Kapitel*) ändert, wenn sich die Position der übergeordneten Zeile ändert.|  
|[Stream-Eigenschaft](./stream-property.md)|Ruft ein OLE DB **Stream** -Objekt von/für ein **adostreamconstruction** -Objekt ab oder legt es fest.|  
|[Type](./type-property-ado.md)|Gibt den Betriebs Typ oder den Datentyp eines **Parameters**, **Felds**oder **Eigenschafts** Objekts an.|  
|[Type (ADO-Stream)](./type-property-ado-stream.md)|Gibt den Datentyp an, der im Daten **Strom** (binär oder Text) enthalten ist.|  
|[UnderlyingValue –](./underlyingvalue-property.md)|Gibt den aktuellen Wert in der Datenbank für ein **Feld** Objekt an.|  
|[Wert](./value-property-ado.md)|Gibt den Wert an, der einem **Feld**, einem **Parameter**oder einem **Eigenschafts** Objekt zugewiesen ist.|  
|[Version](./version-property-ado.md)|Gibt die ADO-Versionsnummer an.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [ADO-API-Referenz](./ado-api-reference.md)   
 [ADO-Sammlungen](./ado-collections.md)   
 [Dynamische ADO-Eigenschaften](./ado-dynamic-properties.md)   
 [ADO-Enumerationskonstanten](./ado-enumerated-constants.md)   
 [Anhang B: ADO-Fehler](../../guide/appendixes/appendix-b-ado-errors.md)   
 [ADO-Ereignisse](./ado-events.md)   
 [ADO-Methoden](./ado-methods.md)   
 [ADO-Objektmodell](./ado-object-model.md)   
 [ADO-Objekte und -Schnittstellen](./ado-objects-and-interfaces.md)