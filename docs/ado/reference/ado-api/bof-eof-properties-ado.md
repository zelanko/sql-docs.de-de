---
description: BOF- und EOF-Eigenschaften (ADO)
title: BOF, EOF-Eigenschaften (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 710a116e28a102eeac8a7a062a9f66cd8dcbe79c
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88975781"
---
# <a name="bof-eof-properties-ado"></a>BOF- und EOF-Eigenschaften (ADO)
-   **BOF** Gibt an, dass sich die aktuelle Daten Satz Position vor dem ersten Datensatz in einem [Recordset](./recordset-object-ado.md) -Objekt befindet.  
  
-   **EOF** Gibt an, dass sich die aktuelle Daten Satz Position hinter dem letzten Datensatz in einem **Recordset** -Objekt befindet.  
  
## <a name="return-value"></a>Rückgabewert  
 Die **BOF** -und **EOF** -Eigenschaften geben **boolesche** Werte zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die Eigenschaften **BOF** und **EOF** , um zu bestimmen, ob ein **Recordset** -Objektdaten Sätze enthält oder ob Sie die Grenzwerte eines **Recordset** -Objekts überschritten haben, wenn Sie von Datensatz zu Datensatz wechseln.  
  
 Die **BOF** -Eigenschaft gibt **true** zurück (-1), wenn die aktuelle Daten Satz Position vor dem ersten Datensatz liegt, und **false** (0), wenn die aktuelle Daten Satz Position am oder nach dem ersten Datensatz liegt.  
  
 Die **EOF** -Eigenschaft gibt **true** zurück, wenn die aktuelle Daten Satz Position nach dem letzten Datensatz liegt, und **false** , wenn die aktuelle Daten Satz Position am oder vor dem letzten Datensatz liegt.  
  
 Wenn die **BOF** -Eigenschaft oder die **EOF** -Eigenschaft den Wert **true**hat, ist kein aktueller Datensatz vorhanden.  
  
 Wenn Sie ein **Recordset** -Objekt öffnen, das keine Datensätze enthält, werden die **BOF** -und **EOF** -Eigenschaften auf **true** festgelegt (Weitere Informationen zu diesem Status eines **Recordsets**finden Sie in der [RecordCount](./recordcount-property-ado.md) -Eigenschaft). Wenn Sie ein **Recordset** -Objekt öffnen, das mindestens einen Datensatz enthält, ist der erste Datensatz der aktuelle Datensatz, und die **BOF** -und **EOF** -Eigenschaften sind **false**.  
  
 Wenn Sie den letzten verbleibenden Datensatz im **Recordset** -Objekt löschen, bleiben die **BOF** -und **EOF** -Eigenschaften möglicherweise **falsch** , bis Sie versuchen, den aktuellen Datensatz neu zu positionieren.  
  
 Diese Tabelle **zeigt, welche** Verschiebungs Methoden mit unterschiedlichen Kombinationen der Eigenschaften **BOF** und **EOF** zulässig sind.  
  
||MoveFirst<br /><br /> MoveLast|MovePrevious<br /><br /> < 0 verschieben|0 verschieben|MoveNext<br /><br /> > 0 verschieben|  
|------|-----------------------------|---------------------------------|------------|-----------------------------|  
|**BOF** = **True**, **EOF** = **false**|Zulässig|Fehler|Fehler|Zulässig|  
|**BOF** = **False**, **EOF** = **true**|Zulässig|Zulässig|Fehler|Fehler|  
|Beide **true**|Fehler|Fehler|Fehler|Fehler|  
|Beide **falsch**|Zulässig|Zulässig|Zulässig|Zulässig|  
  
 Das Zulassen einer Verschiebungs Methode garantiert nicht, dass die **Methode einen Datensatz** erfolgreich findet. Dies bedeutet nur, dass beim Aufrufen **der angegebenen** Verschiebungs Methode kein Fehler generiert wird.  
  
 In der folgenden Tabelle wird gezeigt, was mit den Eigenschaften Einstellungen **BOF** und **EOF** geschieht, wenn **Sie verschiedene** Verschiebungs Methoden aufzurufen, aber einen Datensatz nicht erfolgreich finden können.  
  
||BOF|EOF|  
|------|---------|---------|  
|" **Muvefirst**", " **muvelast** "|Auf " **true** " festlegen|Auf " **true** " festlegen|  
|0 **verschieben**|Keine Änderung|Keine Änderung|  
|**MovePrevious**, **verschieben** < 0|Auf " **true** " festlegen|Keine Änderung|  
|**MoveNext**, **verschieben** > 0|Keine Änderung|Auf " **true** " festlegen|  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [BOF-, EOF-und Bookmark Properties-Beispiel (VB)](./bof-eof-and-bookmark-properties-example-vb.md)   
 [BOF-, EOF-und Bookmark-Eigenschaften Beispiel (VC + +)](./bof-eof-and-bookmark-properties-example-vc.md)