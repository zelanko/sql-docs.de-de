---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c3626f91018714fa4d67304c92ce464d82fb5c8e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67917227"
---
# <a name="requery-method"></a>Requery-Methode
Aktualisiert die Daten in einem [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt, indem die Abfrage erneut ausgeführt wird, auf der das Objekt basiert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
recordset.Requery Options  
```  
  
#### <a name="parameters"></a>Parameter  
 *Optionen*  
 Optional. Eine Bitmaske, die die Werte [executeoptionenumum](../../../ado/reference/ado-api/executeoptionenum.md) und [commandtypeenumeration](../../../ado/reference/ado-api/commandtypeenum.md) enthält, die diesen Vorgang beeinflussen.  
  
> [!NOTE]
>  Wenn *Optionen* auf **adAsyncExecute**festgelegt ist, wird dieser Vorgang asynchron ausgeführt, und ein [RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md) -Ereignis wird ausgegeben, wenn es beendet wird. Die **executeopenenumum** -Werte **von adExecuteNoRecords** oder **adExecuteStream** sollten nicht mit der **Anforderung**verwendet werden.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie die **Requery** -Methode, um den gesamten Inhalt eines **Recordset** -Objekts aus der Datenquelle zu aktualisieren, indem Sie den ursprünglichen Befehl neu ausgeben und die Daten ein zweites Mal abrufen. Das Aufrufen dieser Methode entspricht dem Aufrufen der [Close](../../../ado/reference/ado-api/close-method-ado.md) -Methode und der [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) -Methode nacheinander. Wenn Sie den aktuellen Datensatz bearbeiten oder einen neuen Datensatz hinzufügen, tritt ein Fehler auf.  
  
 Während das **Recordset** -Objekt geöffnet ist, sind die Eigenschaften, die die Art des Cursors definieren ([CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md), [LockType](../../../ado/reference/ado-api/locktype-property-ado.md), [maxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md)usw.), schreibgeschützt. Daher kann die **Requery** -Methode nur den aktuellen Cursor aktualisieren. Wenn Sie die Cursor Eigenschaften ändern und die Ergebnisse anzeigen möchten, müssen Sie die [Close](../../../ado/reference/ado-api/close-method-ado.md) -Methode verwenden, damit die Eigenschaften erneut gelesen/geschrieben werden. Sie können dann die Eigenschaften Einstellungen ändern und die [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md) -Methode aufzurufen, um den Cursor erneut zu öffnen.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Execute, Requery und Clear Methods (VB)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vb.md)   
 [Beispiel für Execute, Requery und Clear Methods (VBScript)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vbscript.md)   
 [Beispiel für Execute, Requery und Clear Methods (VC + +)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vc.md)   
 [CommandText-Eigenschaft (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)
