---
title: MoveFirst, MoveLast, MoveNext und MovePrevious-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::MoveLast
- Recordset15::MoveNext
- Recordset15::raw_MoveNext
- Recordset15::raw_MovePrevious
- Recordset15::MoveFirst
- Recordset15::raw_MoveLast
- Recordset15::MovePrevious
- Recordset15::raw_MoveFirst
helpviewer_keywords:
- MoveNext method [ADO]
- MoveLast method [ADO]
- MoveFirst method [ADO]
- MovePrevious method [ADO]
ms.assetid: a61a01a7-5b33-4150-9126-21dfa63654cb
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 83e216f15da49150481af18ee98aac1f604b2394
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66707479"
---
# <a name="movefirst-movelast-movenext-and-moveprevious-methods-ado"></a>MoveFirst, MoveLast, MoveNext und MovePrevious-Methode (ADO)
Wechselt zum ersten, letzten, nächsten oder vorherigen Datensatz in einem angegebenen [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt und macht, die zum aktuellen Datensatz.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
recordset.{MoveFirst | MoveLast | MoveNext | MovePrevious}  
```  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **MoveFirst** -Methode verschieben die Position des aktuelle Datensatzes auf den ersten Eintrag in der **Recordset**.  
  
 Verwenden der **MoveLast** Notieren Sie die Methode, um die Position des aktuellen Datensatzes auf die letzte verschieben in die **Recordset**. Die **Recordset** -Objekt Lesezeichen oder Bewegung des Cursors von Abwärtskompatibilität unterstützt; andernfalls wird der Methodenaufruf ein Fehler generiert.  
  
 Ein Aufruf von **MoveFirst** oder **MoveLast** bei der **Recordset** ist leer (beide **BOF** und **EOF** Gibt "true") wird ein Fehler generiert.  
  
 Verwenden der **MoveNext** -Methode des aktuellen Datensatzes verschieben positionieren einen Datensatz nach vorne (am unteren Rand der **Recordset**). Wenn der letzte Eintrag der aktuelle Datensatz ist ein, und Sie rufen die **MoveNext** -Methode, ADO legt den aktuellen Datensatz auf die Position hinter dem letzten Datensatz in die **Recordset** ([EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) ist **"True"** ). Der Versuch, forward When Verschieben der **EOF** Eigenschaft ist bereits **"true"** wird ein Fehler generiert.  
  
 In ADO 2.5 und höher, bei der **Recordset** gefiltert wurde oder sortiert, und die Daten des aktuellen Datensatzes geändert werden, Aufrufen der **MoveNext** Methode springt der Cursor zwei Datensätze aus dem aktuellen Datensatz weitergeleitet . Das liegt, wenn der aktuelle Datensatz geändert wird, der nächste Datensatz der neuen aktuellen Datensatz wird. Aufrufen von **MoveNext** nach die Änderung aus der neuen aktuellen Datensatz wird der Cursor um einen Datensatz nach vorn verschoben. Dies ist das sich vom Verhalten in ADO 2.1 und früher. Ändern Sie bei diesen älteren Versionen, die Daten von einem aktuellen Datensatz in der sortierten oder gefilterten **Recordset** ändert sich nicht auf die Position des aktuellen Datensatzes, und **MoveNext** verschiebt den Cursor auf den nächsten Datensatz unmittelbar nach den aktuellen Datensatz.  
  
 Verwenden der **MovePrevious** -Methode des aktuellen Datensatzes verschieben positionieren, einen Datensatz nach hinten (bis zum Anfang der **Recordset**). Die **Recordset** -Objekt Lesezeichen oder Bewegung des Cursors von Abwärtskompatibilität unterstützt; andernfalls wird der Methodenaufruf ein Fehler generiert. Wenn der erste Datensatz der aktuelle Datensatz ist ein, und Sie rufen die **MovePrevious** -Methode legt ADO des aktuellen Datensatzes auf die Position vor dem ersten Datensatz in die **Recordset** ([BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)ist **"true"** ). Der Versuch, verschieben Abwärtskompatibilität bei der **BOF** Eigenschaft ist bereits **"true"** wird ein Fehler generiert. Wenn die **Recordset** Objekt unterstützt keine Lesezeichen oder rückwärtsgerichtete Verschiebung des Cursors, entweder die **MovePrevious** Methode wird ein Fehler generiert.  
  
 Wenn die **Recordset** ist nur vorwärts und unterstützt sowohl vorwärts und rückwärts zu scrollen, werden sollen können Sie die [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md) Eigenschaft, um einen Datensatzcache zu erstellen, die Bewegung des Cursors von Abwärtskompatibilität unterstützt durch die [verschieben](../../../ado/reference/ado-api/move-method-ado.md) Methode. Da der zwischengespeicherten Einträge in den Arbeitsspeicher geladen werden, sollten Sie Zwischenspeichern mehrere Datensätze als erforderlich erledigt wird. Rufen Sie die **MoveFirst** -Methode in der eine vorwärts gerichtete **Recordset** Objekt; Dies kann dazu führen, dass den Anbieter beim erneuten Ausführen des Befehls, die generiert die **Recordset** Objekt .  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [MoveFirst, MoveLast, MoveNext und MovePrevious-Methoden – Beispiel (VB)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-example-vb.md)   
 [MoveFirst, MoveLast, MoveNext und MovePrevious-Methoden – Beispiel (VBScript)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-example-vbscript.md)   
 [MoveFirst, MoveLast, MoveNext und MovePrevious-Methode – Beispiel (VC++)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-example-vc.md)   
 [Move-Methode (ADO)](../../../ado/reference/ado-api/move-method-ado.md)   
 [MoveFirst, MoveLast, MoveNext und MovePrevious-Methode (RDS)](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md)   
 [MoveRecord-Methode (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)
