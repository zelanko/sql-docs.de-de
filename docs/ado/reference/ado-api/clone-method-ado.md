---
title: Clone-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::Clone
- Recordset20::raw_Clone
helpviewer_keywords:
- Clone method [ADO]
ms.assetid: ad49265f-1c05-4271-9bbf-7c00010ac18c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: fbeedf9e56c1f0606a7c8f842baedc9d11ad3929
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66698795"
---
# <a name="clone-method-ado"></a>Clone-Methode (ADO)
Erstellt ein Duplikat [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt aus einem vorhandenen **Recordset** Objekt. Optional gibt an, dass der Klon schreibgeschützt sein.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Set rstDuplicate = rstOriginal.Clone (LockType)  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine **Recordset** Objektverweis.  
  
#### <a name="parameters"></a>Parameter  
 *rstDuplicate*  
 Eine Objektvariable, die das Duplikat identifiziert **Recordset** zu erstellenden Objekts.  
  
 *rstOriginal*  
 Eine Objektvariable, die identifiziert die **Recordset** Objekt, das dupliziert werden.  
  
 *LockType*  
 Optional. Ein [LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md) Wert, der angibt, entweder die Sperre den ursprünglichen Objekttyp **Recordset**, oder ein schreibgeschütztes **Recordset**. Gültige Werte sind **AdLockUnspecified** oder **AdLockReadOnly**.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **Klon** dupliziert-Methode zum Erstellen mehrerer **Recordset** Objekte, insbesondere, wenn Sie mehr als einem aktuellen Datensatz in einer bestimmten Gruppe von Datensätzen beibehalten möchten. Mithilfe der **Klon** Methode ist effizienter als das Erstellen und öffnen ein neues **Recordset** Objekt, das die gleiche Definition wie das Original verwendet.  
  
 Die [Filter](../../../ado/reference/ado-api/filter-property.md) Eigenschaft des ursprünglichen **Recordset**, sofern vorhanden, werden nicht in den Klon angewendet. Legen Sie die **Filter** -Eigenschaft des neuen **Recordset** zum Filtern der Ergebnisse. Die einfachste Möglichkeit, kopieren Sie alle vorhandenen **Filter** wird der Wert direkt, wie folgt zugewiesen.  
  
```  
rsNew.Filter = rsOriginal.Filter  
```  
  
 Der aktuelle Datensatz des neu erstellten Klons wird auf den ersten Eintrag festgelegt.  
  
 Änderungen an einer **Recordset** Objekt im aller seiner Klone unabhängig vom Cursortyp sichtbar sind. Jedoch nach der Ausführung [Requery](../../../ado/reference/ado-api/requery-method.md) auf dem ursprünglichen **Recordset**, Klone werden nicht mehr auf den ursprünglichen synchronisiert werden.  
  
 Schließen die ursprüngliche **Recordset** schließt nicht seine Datenbankkopien ebenso wie die ursprünglichen oder einen der anderen Kopien nicht schließen eine Kopie zu schließen.  
  
 Sie können nur Klonen eine **Recordset** -Objekt, das Lesezeichen unterstützt. Lesezeichenwerte sind austauschbar. d. h. ein Lesezeichenverweis von einem **Recordset** -Objekt verweist auf den gleichen Datensatz in einer seiner Klone.  
  
 Einige **Recordset** Ereignisse, die ausgelöst werden, tritt auch in allen **Recordset** klont. Da der aktuelle Datensatz unterscheiden kann allerdings geklont **Recordsets**, die Ereignisse möglicherweise nicht gültig für den Klon. Wenn Sie einen Wert eines Felds ändern, z. B. eine [WillChangeField](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md) Ereignis tritt auf, in den geänderten **Recordset** und in allen klonen. Die *Felder* Parameter, der die **WillChangeField** Ereignis eines geklonten **Recordset** (der die Änderung nicht vorgenommen wurde) verweist auf die Felder des aktuellen Datensatzes des Klons, die möglicherweise einen anderen Datensatz als den aktuellen Datensatz des ursprünglichen **Recordset** , in dem die Änderung aufgetreten ist.  
  
 Die folgende Tabelle enthält eine vollständige Liste aller **Recordset** Ereignisse. Gibt an, ob sie gültig ist und für alle Recordsetklone mit generiert ausgelösten befinden die **Klon** Methode.  
  
|Ereignis|Ausgelöst in Klonen?|  
|-----------|--------------------------|  
|[EndOfRecordset](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|Nein|  
|[FetchComplete](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|Nein|  
|[FetchProgress](../../../ado/reference/ado-api/fetchprogress-event-ado.md)|Nein|  
|[FieldChangeComplete](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Ja|  
|[MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|Nein|  
|[RecordChangeComplete](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Ja|  
|[RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|Nein|  
|[WillChangeField](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Ja|  
|[WillChangeRecord](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Ja|  
|[WillChangeRecordset](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|Nein|  
|[WillMove](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|Nein|  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Clone – Methodenbeispiel (VB)](../../../ado/reference/ado-api/clone-method-example-vb.md)   
 [Clone – Methodenbeispiel (VBScript)](../../../ado/reference/ado-api/clone-method-example-vbscript.md)   
 [Clone-Methode – Beispiel (VC++)](../../../ado/reference/ado-api/clone-method-example-vc.md)   
