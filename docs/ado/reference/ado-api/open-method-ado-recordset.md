---
title: Open-Methode (ADO-Recordset) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::raw_Open
- Recordset15::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: 3236749c-4b71-4235-89e2-ccdfaaa9319d
author: rothja
ms.author: jroth
ms.openlocfilehash: 8a091a606cf3049c055794bc16cc51db78a40978
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762178"
---
# <a name="open-method-ado-recordset"></a>Open-Methode (ADO-Recordset)
Öffnet einen Cursor für ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
recordset.Open Source, ActiveConnection, CursorType, LockType, Options  
```  
  
#### <a name="parameters"></a>Parameter  
 *Quelle*  
 Dies ist optional. Eine **Variante** , die ein gültiges [Befehls](../../../ado/reference/ado-api/command-object-ado.md) Objekt, eine SQL-Anweisung, einen Tabellennamen, einen gespeicherten Prozedur Aufrufe, eine URL oder den Namen einer Datei oder eines [Streamobjekts](../../../ado/reference/ado-api/stream-object-ado.md) mit einem permanent gespeicherten [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)ergibt.  
  
 *ActiveConnection*  
 Dies ist optional. Entweder eine **Variante** , die einen gültigen [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objektvariablen Namen ergibt, oder eine **Zeichenfolge** , die [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) -Parameter enthält.  
  
 *CursorType*  
 Dies ist optional. Ein [CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md) -Wert, der den Typ des Cursors bestimmt, den der Anbieter beim Öffnen des **Recordsets**verwenden soll. Der Standardwert ist ' **adOpenForwardOnly**'.  
  
 *LockType*  
 Dies ist optional. Ein [LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md) -Wert, der bestimmt, welche Art von Sperre (Parallelität) der Anbieter beim Öffnen des **Recordsets**verwenden soll. Der Standardwert ist **adlockread only**.  
  
 *Optionen*  
 Dies ist optional. Ein **Long** -Wert, der angibt, wie der Anbieter das *Quell* Argument auswerten soll, wenn es etwas anderes als ein **Befehls** Objekt darstellt, oder dass das **Recordset** aus einer Datei wieder hergestellt werden soll, in der es zuvor gespeichert wurde. Kann ein oder mehrere [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) -oder [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) -Werte sein, die mit einem bitweisen OR-Operator kombiniert werden können.  
  
> [!NOTE]
>  Wenn Sie ein **Recordset** aus einem **Stream** öffnen, der ein persistente **Recordset**enthält, hat die Verwendung eines [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) -Werts von **adasyncfetchnonblocking** keine Auswirkung. das Abrufen erfolgt synchron und wird blockiert.  
  
> [!NOTE]
>  Die **executeopenenumum** -Werte **von adExecuteNoRecords** oder **adExecuteStream** sollten nicht mit **Open**verwendet werden.  
  
## <a name="remarks"></a>Bemerkungen  
 Der Standard Cursor für ein ADO- **Recordset** ist ein Schreib geschützter Vorwärts Cursor, der sich auf dem Server befindet.  
  
 Mithilfe der **Open** -Methode für ein **Recordset** -Objekt wird ein Cursor geöffnet, der Datensätze aus einer Basistabelle, die Ergebnisse einer Abfrage oder ein zuvor gespeicherter **Recordset**darstellt.  
  
 Verwenden Sie das optionale *Source* -Argument zum Angeben einer Datenquelle, indem Sie eine der folgenden Aktionen verwenden: eine **Befehls** Objekt Variable, eine SQL-Anweisung, eine gespeicherte Prozedur, ein Tabellenname, eine URL oder ein kompletter Dateipfadname. Wenn die *Quelle* ein Dateipfadname ist, kann es sich um einen vollständigen Pfad ("c:\dir\file.RST"), einen relativen Pfad (".. \file.RST ") oder eine URL (" <https://files/file.rst> ").  
  
 Es empfiehlt sich nicht, das *Source* -Argument der **Open** -Methode zu verwenden, um eine Aktions Abfrage auszuführen, die keine Datensätze zurückgibt, da es keine einfache Möglichkeit gibt, zu bestimmen, ob der-Befehl erfolgreich ausgeführt wurde. Das von einer solchen Abfrage zurückgegebene **Recordset** wird geschlossen. Um eine Abfrage auszuführen, die keine Datensätze zurückgibt, wie z. b. eine SQL INSERT-Anweisung, wird stattdessen die [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) -Methode eines **Befehls** Objekts oder die [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) -Methode eines [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekts aufgerufen.  
  
 Das *ActiveConnection* -Argument entspricht der [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) -Eigenschaft und gibt an, in welcher Verbindung das **Recordset** -Objekt geöffnet werden soll. Wenn Sie eine Verbindungs Definition für dieses Argument übergeben, öffnet ADO mit den angegebenen Parametern eine neue Verbindung. Nachdem Sie das **Recordset** mit einem Client seitigen Cursor geöffnet haben, indem Sie die [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) -Eigenschaft auf **adUseClient**festgelegt haben, können Sie den Wert dieser Eigenschaft ändern, um Updates an einen anderen Anbieter zu senden. Oder Sie können diese Eigenschaft auf " **Nothing** " (in Microsoft Visual Basic) oder "Null" festlegen, um das **Recordset** von einem beliebigen Anbieter zu trennen. Wenn *ActiveConnection* für einen serverseitigen Cursor geändert wird, wird jedoch ein Fehler generiert.  
  
 Für die anderen Argumente, die direkt den Eigenschaften eines **Recordset** -Objekts (*Quelle*, *Cursor Type*und *LockType*) entsprechen, lautet die Beziehung der Argumente zu den Eigenschaften wie folgt:  
  
-   Die-Eigenschaft ist Lese-/Schreibzugriff, bevor das **Recordset** -Objekt geöffnet wird.  
  
-   Die Eigenschaften Einstellungen werden verwendet, es sei denn, Sie übergeben die entsprechenden Argumente, wenn Sie die **Open** -Methode ausführen. Wenn Sie ein Argument übergeben, wird die entsprechende Eigenschaften Einstellung überschrieben, und die Eigenschafts Einstellung wird mit dem Argument Wert aktualisiert.  
  
-   Nachdem Sie das **Recordset** -Objekt geöffnet haben, werden diese Eigenschaften schreibgeschützt.  
  
> [!NOTE]
>  Die **ActiveConnection** -Eigenschaft ist für **Recordset** -Objekte, deren [Source](../../../ado/reference/ado-api/source-property-ado-recordset.md) -Eigenschaft auf ein gültiges **Befehls** Objekt festgelegt ist, schreibgeschützt, auch wenn das **Recordset** -Objekt nicht geöffnet ist.  
  
 Wenn Sie ein **Command** -Objekt im *Source* -Argument übergeben und auch ein *ActiveConnection* -Argument übergeben, tritt ein Fehler auf. Die **ActiveConnection** -Eigenschaft des **Command** -Objekts muss bereits auf ein gültiges **Verbindungs** Objekt oder eine gültige Verbindungs Zeichenfolge festgelegt sein.  
  
 Wenn Sie etwas anderes als ein **Befehls** Objekt im *Source* -Argument übergeben, können Sie das *options* -Argument verwenden, um die Auswertung des *Quell* Arguments zu optimieren. Wenn das *options* -Argument nicht definiert ist, kann die Leistung beeinträchtigt werden, da ADO Aufrufe an den Anbieter ausführen muss, um zu bestimmen, ob es sich bei dem Argument um eine SQL-Anweisung, eine gespeicherte Prozedur, eine URL oder einen Tabellennamen handelt. Wenn Sie wissen, welcher *Quelltyp* Sie verwenden, weist das *options* -Argument ADO an, direkt zum relevanten Code zu springen. Wenn das *options* -Argument nicht mit dem *Quelltyp* identisch ist, tritt ein Fehler auf.  
  
 Wenn Sie ein **Stream** -Objekt im *Source* -Argument übergeben, sollten Sie keine Informationen an die anderen Argumente übergeben. Andernfalls wird ein Fehler generiert. Die **ActiveConnection** -Informationen werden nicht beibehalten, wenn ein **Recordset** von einem **Stream**aus geöffnet wird.  
  
 Der Standardwert für das *options* -Argument ist **adcmdfile** , wenn keine Verbindung mit dem **Recordset**verknüpft ist. Dies ist in der Regel der Fall bei dauerhaft gespeicherten **recordsetobjekten** .  
  
 Wenn die Datenquelle keine Datensätze zurückgibt, legt der Anbieter die Eigenschaften [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) und [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) auf **true**fest, und die aktuelle Daten Satz Position ist nicht definiert. Sie können diesem leeren **Recordset** -Objekt weiterhin neue Daten hinzufügen, wenn der Cursortyp dies zulässt.  
  
 Wenn Sie die Vorgänge für ein offenes **Recordset** -Objekt abgeschlossen haben, verwenden Sie die [Close](../../../ado/reference/ado-api/close-method-ado.md) -Methode, um alle zugeordneten Systemressourcen freizugeben. Durch das Schließen eines Objekts wird es nicht aus dem Arbeitsspeicher entfernt. Sie können die Eigenschafts Einstellungen ändern und die **Open** -Methode verwenden, um Sie zu einem späteren Zeitpunkt erneut zu öffnen. Wenn Sie ein Objekt vollständig aus dem Arbeitsspeicher entfernen möchten, legen Sie die Objekt Variable auf *Nothing*fest.  
  
 Bevor die **ActiveConnection** -Eigenschaft festgelegt ist, rufen Sie **Open** ohne Operanden auf, um eine Instanz eines **Recordsets** zu erstellen, das durch Anhängen [von Feldern an](../../../ado/reference/ado-api/fields-collection-ado.md) die **Recordset** -Feldauflistung erstellt wurde.  
  
 Wenn Sie die [Cursor Location](../../../ado/reference/ado-api/cursorlocation-property-ado.md) -Eigenschaft auf **adUseClient**festgelegt haben, können Sie Zeilen auf zwei Arten asynchron abrufen. Die empfohlene Methode ist die Festlegung von *Optionen* auf **adasyncfetch**. Alternativ können Sie die dynamische Eigenschaft "asynchrone Rowsetverarbeitung" in der [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) -Auflistung verwenden, aber zugehörige abgerufene Ereignisse können verloren gehen, wenn Sie den *options* -Parameter nicht auf " **adasyncfetch**" festlegen.  
  
> [!NOTE]
>  Das Abrufen von hintergrundzeichen im MS-Remote Anbieter wird nur über den *options* -Parameter der **Open** -Methode unterstützt.  
  
> [!NOTE]
>  URLs, die das http-Schema verwenden, rufen automatisch den [Microsoft OLE DB-Anbieter für die Internet Veröffentlichung auf](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [absolute und relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
 Bestimmte Kombinationen von [commandtypeenumeration](../../../ado/reference/ado-api/commandtypeenum.md) -und [executeoptionenumum](../../../ado/reference/ado-api/executeoptionenum.md) -Werten sind ungültig. Informationen dazu, welche Optionen nicht kombiniert werden können, finden Sie in den Themen zu [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md)und [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md).  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Open-und Close-Methoden Beispiel (VB)](../../../ado/reference/ado-api/open-and-close-methods-example-vb.md)   
 [Open-und Close-Methoden Beispiel (VBScript)](../../../ado/reference/ado-api/open-and-close-methods-example-vbscript.md)   
 [Open-und Close-Methoden Beispiel (VC + +)](../../../ado/reference/ado-api/open-and-close-methods-example-vc.md)   
 [Beispiel für das Speichern und Öffnen von Methoden (VB)](../../../ado/reference/ado-api/save-and-open-methods-example-vb.md)   
 [Open-Methode (ADO-Verbindung)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open-Methode (ADO-Datensatz)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Open-Methode (ADO-Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [OpenSchema-Methode](../../../ado/reference/ado-api/openschema-method.md)   
 [Save-Methode](../../../ado/reference/ado-api/save-method.md)
