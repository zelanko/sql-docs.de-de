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
manager: craigg
ms.openlocfilehash: 433f5d279e638e3ccdf7ba3a7bb2590f80b04a6b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63062368"
---
# <a name="requery-method"></a>Requery-Methode
Aktualisiert die Daten in einem [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt durch erneutes Ausführen der Abfrage, die auf dem das Objekt basiert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
recordset.Requery Options  
```  
  
#### <a name="parameters"></a>Parameter  
 *Optionen*  
 Dies ist optional. Eine Bitmaske, die enthält [ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md) und [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md) Werte, die diesen Vorgang beeinflussen.  
  
> [!NOTE]
>  Wenn *Optionen* nastaven NA hodnotu **AdAsyncExecute**, dieser Vorgang wird asynchron ausgeführt und ein [RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md) Ereignis wird ausgelöst werden, wenn es endet. Die **ExecuteOpenEnum** Werte **AdExecuteNoRecords** oder **AdExecuteStream** sollte nicht verwendet werden, mit **Requery**.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **Requery** Methode, um den gesamten Inhalt aktualisieren eine **Recordset** Objekt aus der Datenquelle, indem Sie den ursprünglichen Befehl erneut ausführen und zum Abrufen der Daten eines zweiten Mal. Das Aufrufen dieser Methode entspricht dem Aufrufen der [schließen](../../../ado/reference/ado-api/close-method-ado.md) und [öffnen](../../../ado/reference/ado-api/open-method-ado-recordset.md) Methoden nacheinander. Wenn Sie den aktuellen Datensatz bearbeiten oder einen neuen Datensatz hinzufügen, tritt ein Fehler auf.  
  
 Während der **Recordset** Objekt geöffnet ist, die Eigenschaften, die Art des Cursors definieren ([CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md), [LockType](../../../ado/reference/ado-api/locktype-property-ado.md), [MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md) und so weiter) sind schreibgeschützt. Daher die **Requery** Methode kann nur den aktuellen Cursor aktualisieren. Sie müssen zum Ändern der Eigenschaften des Standardcursors und die Ergebnisse anzuzeigen, verwenden die [schließen](../../../ado/reference/ado-api/close-method-ado.md) Methode, um die Eigenschaften erneut Lese-/Schreibzugriff zu machen. Sie können dann ändern, das eigenschafteneinstellungen, und rufen die [öffnen](../../../ado/reference/ado-api/open-method-ado-recordset.md) Methode, um den Cursor zu öffnen.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Execute, Requery und Clear-Methode – Beispiel (VB)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vb.md)   
 [Execute, Requery und Clear-Methode – Beispiel (VBScript)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vbscript.md)   
 [Execute, Requery und Clear-Methode – Beispiel (VC++)](../../../ado/reference/ado-api/execute-requery-and-clear-methods-example-vc.md)   
 [CommandText-Eigenschaft (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)
