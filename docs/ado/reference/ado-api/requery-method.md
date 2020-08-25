---
description: Requery-Methode
title: Requery-Methode | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Requery
- Recordset15::raw_Requery
helpviewer_keywords:
- Requery method [ADO]
ms.assetid: d81ab76f-1aa8-4ccf-92ec-b65254dc3ea1
author: rothja
ms.author: jroth
ms.openlocfilehash: a8b9a5d3ab52fdbd3e219104ce3553cd69753a40
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777689"
---
# <a name="requery-method"></a>Requery-Methode
Aktualisiert die Daten in einem [Recordset](./recordset-object-ado.md) -Objekt, indem die Abfrage erneut ausgeführt wird, auf der das Objekt basiert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
recordset.Requery Options  
```  
  
#### <a name="parameters"></a>Parameter  
 *Optionen*  
 Optional. Eine Bitmaske, die die Werte [executeoptionenumum](./executeoptionenum.md) und [commandtypeenumeration](./commandtypeenum.md) enthält, die diesen Vorgang beeinflussen.  
  
> [!NOTE]
>  Wenn *Optionen* auf **adAsyncExecute**festgelegt ist, wird dieser Vorgang asynchron ausgeführt, und ein [RecordsetChangeComplete](./willchangerecordset-and-recordsetchangecomplete-events-ado.md) -Ereignis wird ausgegeben, wenn es beendet wird. Die **executeopenenumum** -Werte **von adExecuteNoRecords** oder **adExecuteStream** sollten nicht mit der **Anforderung**verwendet werden.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **Requery** -Methode, um den gesamten Inhalt eines **Recordset** -Objekts aus der Datenquelle zu aktualisieren, indem Sie den ursprünglichen Befehl neu ausgeben und die Daten ein zweites Mal abrufen. Das Aufrufen dieser Methode entspricht dem Aufrufen der [Close](./close-method-ado.md) -Methode und der [Open](./open-method-ado-recordset.md) -Methode nacheinander. Wenn Sie den aktuellen Datensatz bearbeiten oder einen neuen Datensatz hinzufügen, tritt ein Fehler auf.  
  
 Während das **Recordset** -Objekt geöffnet ist, sind die Eigenschaften, die die Art des Cursors definieren ([CursorType](./cursortype-property-ado.md), [LockType](./locktype-property-ado.md), [maxRecords](./maxrecords-property-ado.md)usw.), schreibgeschützt. Daher kann die **Requery** -Methode nur den aktuellen Cursor aktualisieren. Wenn Sie die Cursor Eigenschaften ändern und die Ergebnisse anzeigen möchten, müssen Sie die [Close](./close-method-ado.md) -Methode verwenden, damit die Eigenschaften erneut gelesen/geschrieben werden. Sie können dann die Eigenschaften Einstellungen ändern und die [Open](./open-method-ado-recordset.md) -Methode aufzurufen, um den Cursor erneut zu öffnen.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Execute, Requery und Clear Methods (VB)](./execute-requery-and-clear-methods-example-vb.md)   
 [Beispiel für Execute, Requery und Clear Methods (VBScript)](./execute-requery-and-clear-methods-example-vbscript.md)   
 [Beispiel für Execute, Requery und Clear Methods (VC + +)](./execute-requery-and-clear-methods-example-vc.md)   
 [CommandText-Eigenschaft (ADO)](./commandtext-property-ado.md)