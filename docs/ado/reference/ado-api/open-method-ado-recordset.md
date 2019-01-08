---
title: Open-Methode (ADO Recordset) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c2b02ac3d8e95bb583515dfa780f473402ea798f
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53206319"
---
# <a name="open-method-ado-recordset"></a>Open-Methode (ADO-Recordset)
Öffnet einen Cursor auf einer [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
recordset.Open Source, ActiveConnection, CursorType, LockType, Options  
```  
  
#### <a name="parameters"></a>Parameter  
 *Quelle*  
 Dies ist optional. Ein **Variant** , ausgewertet wird, auf ein gültiges [Befehl](../../../ado/reference/ado-api/command-object-ado.md) -Objekt, eine SQL-Anweisung, einen Tabellennamen, Aufruf einer gespeicherten Prozedur, eine URL oder den Namen einer Datei oder [Stream](../../../ado/reference/ado-api/stream-object-ado.md) Objekt mit einer dauerhaft gespeichert [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 *ActiveConnection*  
 Dies ist optional. Entweder ein **Variant** , ausgewertet wird, auf ein gültiges [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Namen der Objektvariablen, oder ein **Zeichenfolge** , enthält ["ConnectionString"](../../../ado/reference/ado-api/connectionstring-property-ado.md) Parameter.  
  
 *CursorType*  
 Dies ist optional. Ein [CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md) Wert, der den Typ des Cursors bestimmt, die der Anbieter, beim Öffnen verwenden soll der **Recordset**. Der Standardwert ist **AdOpenForwardOnly**.  
  
 *LockType*  
 Dies ist optional. Ein [LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md) Wert, der bestimmt, welche Art von Sperren (nebenläufigkeit) des Anbieters verwenden soll, beim Öffnen der **Recordset**. Der Standardwert ist **AdLockReadOnly**.  
  
 *Optionen*  
 Dies ist optional. Ein **lange** Wert, der angibt, wie der Anbieter auswerten soll die *Quelle* Argument, wenn es etwas anders als darstellt eine **Befehl** -Objekt, oder dass die **Recordset** wiederhergestellt werden sollen, aus einer Datei, in denen es bereits gespeichert wurde. Kann sein, eine oder mehrere [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) oder [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) Werte, die mit einem bitweisen OR-Operator kombiniert werden können.  
  
> [!NOTE]
>  Beim Öffnen einer **Recordset** aus eine **Stream** , enthält eine persistierte **Recordset**mithilfe einer [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) Wert **AdAsyncFetchNonBlocking** hat keine Auswirkungen; die Fetch werden synchron und blockiert.  
  
> [!NOTE]
>  Die **ExecuteOpenEnum** Werte **AdExecuteNoRecords** oder **AdExecuteStream** sollte nicht verwendet werden, mit **öffnen**.  
  
## <a name="remarks"></a>Hinweise  
 Den Standardcursor für ein ADO **Recordset** ein Vorwärtscursor, schreibgeschützte Cursor, die auf dem Server gespeichert ist.  
  
 Mithilfe der **öffnen** Methode für eine **Recordset** Objekt öffnet einen Cursor, der Datensätze, aus einer Basistabelle, die Ergebnisse einer Abfrage verwendet werden soll, oder eine zuvor gespeicherte darstellt **Recordset**.  
  
 Verwenden Sie das optionale *Quelle* Argument an eine Datenquelle mithilfe eines der folgenden: eine **Befehl** Objektvariable, eine SQL-Anweisung, einer gespeicherten Prozedur, einen Tabellennamen an, eine URL oder einen vollständigen Dateinamen Pfad an. Wenn *Quelle* den Pfadnamen einer Datei, ist es möglich, einen vollständigen Pfad ("c:\dir\file.rst"), einen relativen Pfad ("... \file.rst) oder eine URL ("<https://files/file.rst>").  
  
 Es ist nicht ratsam, verwenden Sie die *Quelle* Argument der **öffnen** Methode, um eine Abfrage auszuführen, die kein Datensätze zurück, weil es keine einfache Möglichkeit gibt zu bestimmen, ob der Aufruf erfolgreich war. Die **Recordset** zurückgegebenes z. B. eine Abfrage wird geschlossen. Aufrufen, um eine Abfrage auszuführen, die keine Datensätze, wie z. B. eine SQL INSERT-Anweisung zurückgibt der [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) -Methode der ein **Befehl** Objekt oder die [Execute](../../../ado/reference/ado-api/execute-method-ado-connection.md) Methode eine [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) stattdessen Objekt.  
  
 Die *ActiveConnection* Argument entspricht der [ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md) Eigenschaft und gibt an, in welcher Verbindung öffnen Sie die **Recordset** Objekt. Wenn Sie eine Definition der Serververbindung für dieses Argument übergeben, wird von ADO mit den angegebenen Parametern eine neue Verbindung geöffnet. Nach dem Öffnen der **Recordset** mit einem clientseitigen Cursor durch Festlegen der [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) Eigenschaft **AdUseClient**, können Sie den Wert dieser Eigenschaft zum Senden von ändern Updates auf einen anderen Anbieter. Oder Sie können diese Eigenschaft festlegen, um **nichts** (in Microsoft Visual Basic) oder NULL, um das Trennen der **Recordset** von einem Anbieter. Ändern der *ActiveConnection* für ein serverseitigen Cursor jedoch einen Fehler generiert.  
  
 Für die anderen Argumente, die direkt an die Eigenschaften der entsprechen einem **Recordset** Objekt (*Quelle*, *CursorType*, und *LockType*), die Beziehung der Argumente, um die Eigenschaften lautet wie folgt aus:  
  
-   Die Eigenschaft ist Lese-/Schreibzugriff, bevor Sie die **Recordset** Objekt geöffnet wird.  
  
-   Die eigenschafteneinstellungen werden verwendet, es sei denn, Sie die entsprechenden Argumente, beim Ausführen übergeben der **öffnen** Methode. Wenn Sie ein Argument übergeben, sie überschreibt die entsprechende Einstellung der Eigenschaft, und die Einstellung der Eigenschaft mit dem Argumentwert aktualisiert wird.  
  
-   Nach dem Öffnen der **Recordset** Objekt diese Eigenschaften sind schreibgeschützt.  
  
> [!NOTE]
>  Die **ActiveConnection** -Eigenschaft ist nur Lesezugriff für **Recordset** Objekte, deren [Quelle](../../../ado/reference/ado-api/source-property-ado-recordset.md) -Eigenschaftensatz auf einen gültigen **Befehl** Objekt auch wenn die **Recordset** Objekt ist nicht geöffnet.  
  
 Übergeben einer **Befehl** -Objekt in der *Quelle* Argument und übergeben Sie ein *ActiveConnection* -Argument, ein Fehler auftritt. Die **ActiveConnection** Eigenschaft der **Befehl** Objekt muss noch festgelegt werden, auf ein gültiges **Verbindung** Objekt oder eine Verbindungszeichenfolge.  
  
 Wenn Sie etwas anders als übergeben eine **Befehl** -Objekt in der *Quelle* Argument können Sie die *Optionen* Argument für die Auswertung von optimieren die *Quelle*  Argument. Wenn die *Optionen* Argument ist nicht definiert ist, treten unter Umständen die Leistung verringert, da ADO Aufrufe an den Anbieter, um festzustellen, ob das Argument, eine SQL-Anweisung, einer gespeicherten Prozedur, eine URL oder einen Tabellennamen ist vornehmen muss. Wenn Sie, was wissen *Quelle* -Typ, Festlegen der *Optionen* Argument weist ADO, um direkt zum entsprechenden Code springen. Wenn die *Optionen* Argument stimmt nicht überein. die *Quelle* eingeben, ein Fehler auftritt.  
  
 Übergeben einer **Stream** -Objekt in der *Quelle* -Argument, sollten Sie nicht übergeben Informationen in die anderen Argumente. Auf diese Weise wird ein Fehler generiert. Die **ActiveConnection** sind keine Informationen beibehalten, wenn eine **Recordset** geöffnet wird eine **Stream**.  
  
 Der Standardwert für die *Optionen* Argument **AdCmdFile** , wenn keine Verbindung zugeordnet ist die **Recordset**. Dies wird in der Regel der Fall sein, für dauerhaft gespeicherte **Recordset** Objekte.  
  
 Wenn die Datenquelle keine Datensätze zurückgibt, legt der Anbieter die [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) und [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) Eigenschaften **"true"**, und die Position des aktuelle Datensatzes ist nicht definiert. Sie können weiterhin neue Daten hinzufügen, um diesem leere **Recordset** Objekt, wenn der Cursor-Datentyp kann.  
  
 Wenn Sie Ihre Vorgänge über ein offenes geschlossen haben **Recordset** -Objekts die [schließen](../../../ado/reference/ado-api/close-method-ado.md) Methode, um eine kostenlose zugeordnete Systemressourcen. Schließen ein Objekt entfernt es nicht aus dem Arbeitsspeicher. Sie können die Einstellungen zu ändern und die **öffnen** Methode, um sie später erneut öffnen. Um ein Objekt vom Arbeitsspeicher vollständig zu vermeiden, legen Sie die Objektvariable auf *nichts*.  
  
 Vor der **ActiveConnection** Eigenschaft festgelegt ist, rufen Sie **öffnen** ohne Operanden zum Erstellen einer Instanz von einer **Recordset** durch Anfügen von Feldern erstellt die  **Recordset** [Felder](../../../ado/reference/ado-api/fields-collection-ado.md) Auflistung.  
  
 Wenn Sie festgelegt haben die [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) Eigenschaft **AdUseClient**, Sie können Zeilen asynchron in eine von zwei Arten abrufen. Die empfohlene Methode ist festzulegende *Optionen* zu **AdAsyncFetch**. Alternativ können Sie die "Asynchrone Rowset Verarbeitung" dynamische Eigenschaft in der [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Sammlung, aber verwandte abgerufenen Ereignisse können verloren, wenn Sie nicht festlegen, die *Optionen* Parameter **AdAsyncFetch**.  
  
> [!NOTE]
>  Wird nur durch Abrufen der Hintergrund im MS-Remote-Anbieter unterstützt die **öffnen** Methode *Optionen* Parameter.  
  
> [!NOTE]
>  URLs, die mit der HTTP-Schema werden automatisch aufgerufen, die [Microsoft OLE DB-Anbieter für Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [Absolute und Relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
 Bestimmte Kombinationen von [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) und [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) Werte sind nicht gültig. Informationen darüber, welche Optionen können nicht kombiniert werden, finden Sie in den Themen der [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md), und [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md).  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Öffnen Sie und schließen Sie die Methode – Beispiel (VB)](../../../ado/reference/ado-api/open-and-close-methods-example-vb.md)   
 [Öffnen Sie und schließen Sie die Methode – Beispiel (VBScript)](../../../ado/reference/ado-api/open-and-close-methods-example-vbscript.md)   
 [Öffnen Sie und schließen Sie die Methode – Beispiel (VC++)](../../../ado/reference/ado-api/open-and-close-methods-example-vc.md)   
 [Speichern Sie und öffnen Sie die Methode – Beispiel (VB)](../../../ado/reference/ado-api/save-and-open-methods-example-vb.md)   
 [Open Sie-Methode (ADO Connection)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open Sie-Methode (ADO Record)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Open Sie-Methode (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [OpenSchema-Methode](../../../ado/reference/ado-api/openschema-method.md)   
 [Save-Methode](../../../ado/reference/ado-api/save-method.md)
