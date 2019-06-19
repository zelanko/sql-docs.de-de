---
title: BOF-und EOF-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::BOF
- Recordset15::EOF
helpviewer_keywords:
- EOF property [ADO]
- BOF property [ADO]
ms.assetid: 36c31ab2-f3b6-4281-89b6-db7e04e38fd2
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9a449c0e635c7fe0e63bc1f4d8b1b0b91712135d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66696289"
---
# <a name="bof-eof-properties-ado"></a>BOF- und EOF-Eigenschaften (ADO)
-   **BOF** gibt an, der die Position des aktuelle Datensatzes vor dem ersten Datensatz in einem [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt.  
  
-   **EOF** gibt an, der die Position des aktuelle Datensatzes nach dem letzten Datensatz in einem **Recordset** Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Die **BOF** und **EOF** Eigenschaften zurückgeben **booleschen** Werte.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden der **BOF** und **EOF** Eigenschaften fest, um, ob eine **Recordset** Objekt enthält Datensätze oder gibt an, ob Sie die Grenzen eines überschritten haben eine **Recordset**  Objekt, wenn Sie von Datensatz zu Datensatz verschoben.  
  
 Die **BOF** -Eigenschaft gibt **"true"** (1), wenn die aktuelle Position des Datensatzes vor dem ersten Datensatz ist und **"false"** (0), wenn die Position des aktuelle Datensatzes auf oder nach dem ersten ist Datensatz.  
  
 Die **EOF** -Eigenschaft gibt **"true"** ist die Position des aktuelle Datensatzes nach dem letzten Datensatz und **"false"** die Position des aktuelle Datensatzes ist am oder vor den letzten Datensatz.  
  
 Wenn entweder die **BOF** oder **EOF** Eigenschaft **"true"** , es ist kein aktueller Datensatz.  
  
 Beim Öffnen einer **Recordset** -Objekt, enthält keine Datensätze, die **BOF** und **EOF** Eigenschaften festgelegt werden, um **"true"** (finden Sie unter der [ RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md) -Eigenschaft für Weitere Informationen zu diesem Zustand, der eine **Recordset**). Beim Öffnen einer **Recordset** Objekt, das mindestens ein Datensatz, der erste Datensatz enthält, ist der aktuelle Datensatz und die **BOF** und **EOF** Eigenschaften sind **"false"** .  
  
 Wenn Sie den letzten verbleibenden Datensatz im Löschen der **Recordset** Objekt die **BOF** und **EOF** Eigenschaften bleiben möglicherweise **"false"** bis Es wurde versucht, den aktuellen Datensatz neu zu positionieren.  
  
 Diese Tabelle zeigt, welche **verschieben** Methoden dürfen nur mit verschiedenen Kombinationen von der **BOF** und **EOF** Eigenschaften.  
  
||MoveFirst,<br /><br /> MoveLast|MovePrevious,<br /><br /> Verschieben Sie die < 0|Verschieben von 0|MoveNext,<br /><br /> Verschieben Sie die > 0|  
|------|-----------------------------|---------------------------------|------------|-----------------------------|  
|**BOF**=**True**, **EOF**=**False**|Zulässig|Fehler|Fehler|Zulässig|  
|**BOF**=**False**, **EOF**=**True**|Zulässig|Zulässig|Fehler|Fehler|  
|Beide **"true"**|Fehler|Fehler|Fehler|Fehler|  
|Beide **"false"**|Zulässig|Zulässig|Zulässig|Zulässig|  
  
 Ermöglicht einem **verschieben** -Methode garantiert nicht, dass die Methode erfolgreich einen Datensatz findet, sondern bedeutet, dass ein Aufruf der angegebenen **verschieben** Methode generiert keine Fehler.  
  
 Die folgende Tabelle zeigt, was geschieht mit den **BOF** und **EOF** eigenschafteneinstellungen, die beim Aufrufen von verschiedenen **verschieben** Methoden sind jedoch nicht erfolgreich einem Datensatz zu suchen.  
  
||BOF|EOF|  
|------|---------|---------|  
|**MoveFirst**, **MoveLast**|Legen Sie auf **"true"**|Legen Sie auf **"true"**|  
|**Verschieben Sie** 0|Keine Änderung|Keine Änderung|  
|**MovePrevious**, **verschieben** < 0|Legen Sie auf **"true"**|Keine Änderung|  
|**MoveNext**, **verschieben** > 0|Keine Änderung|Legen Sie auf **"true"**|  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [BOF-, EOF- und Bookmark Eigenschaften – Beispiel (VB)](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vb.md)   
 [BOF-, EOF- und Bookmark Eigenschaften – Beispiel (VC++)](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vc.md)   
