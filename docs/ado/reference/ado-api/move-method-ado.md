---
description: Move-Methode (ADO)
title: Move-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Move
- Recordset15::raw_Move
helpviewer_keywords:
- Move method [ADO]
ms.assetid: 13fe9381-d00b-4f4a-9162-83c3f21b3837
author: rothja
ms.author: jroth
ms.openlocfilehash: 6b394d64a9d1b1f403137e9875db83fdd82c2ac1
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990591"
---
# <a name="move-method-ado"></a>Move-Methode (ADO)
Verschiebt die Position des aktuellen Datensatzes in einem [Recordset](./recordset-object-ado.md) -Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
recordset.Move NumRecords, Start  
```  
  
#### <a name="parameters"></a>Parameter  
 *Numrecords*  
 Ein signed **Long** -Ausdruck, der die Anzahl der Datensätze angibt, die die aktuelle Daten Satz Position verschiebt.  
  
 *Starten*  
 Optional. Ein **Zeichen** folgen Wert oder **Variant** , der zu einem Lesezeichen ausgewertet wird. Sie können auch einen [bookmarkenum](./bookmarkenum.md) -Wert verwenden.  
  
## <a name="remarks"></a>Bemerkungen  
 Die **Move** -Methode wird für alle **Recordset** -Objekte unterstützt.  
  
 Wenn das *numrecords* -Argument größer als 0 (null) ist, wird die aktuelle Daten Satz Position nach vorne verschoben (am Ende des **Recordsets**). Wenn *numrecords* kleiner als 0 (null) ist, wird die aktuelle Daten Satz Position rückwärts (am Anfang des **Recordsets**) verschoben.  
  
 Wenn der **Verschiebungs Versuch die** aktuelle Daten Satz Position an einen Punkt vor dem ersten Datensatz verschiebt, legt ADO den aktuellen Datensatz auf die Position vor dem ersten Datensatz im Recordset ([BOF](./bof-eof-properties-ado.md) ist **true**) fest. Ein Versuch, rückwärts zu wechseln, wenn die **BOF** -Eigenschaft bereits **true** ist, generiert einen Fehler.  
  
 Wenn der **Verschiebungs Versuch die** aktuelle Daten Satz Position an einen Punkt nach dem letzten Datensatz verschiebt, legt ADO den aktuellen Datensatz auf die Position hinter dem letzten Datensatz im Recordset fest ([EOF](./bof-eof-properties-ado.md) ist **true**). Ein Versuch, vorwärts zu wechseln, wenn die **EOF** -Eigenschaft bereits **true** ist, generiert einen Fehler.  
  
 Wenn Sie die **Move** -Methode von einem leeren **Recordset** -Objekt aufrufen, wird ein Fehler generiert.  
  
 Wenn Sie das *Start* -Argument übergeben, ist der Verschiebe Vorgang relativ zum Datensatz mit diesem Lesezeichen, vorausgesetzt, das **Recordset** -Objekt unterstützt Lesezeichen. Wenn nicht angegeben, ist der Verschiebe Vorgang relativ zum aktuellen Datensatz.  
  
 Wenn Sie die [CacheSize](./cachesize-property-ado.md) -Eigenschaft verwenden, um Datensätze vom Anbieter lokal zwischenzuspeichern, wird durch das Übergeben eines *numrecords* -Arguments, das die aktuelle Daten Satz Position außerhalb der aktuellen Gruppe von zwischengespeicherten Datensätzen verschiebt, erzwungen, dass ADO eine neue Gruppe von Datensätzen aus dem Zieldatensatz abruft Die **CacheSize** -Eigenschaft bestimmt die Größe der neu abgerufenen Gruppe, und der Zieldatensatz ist der erste Datensatz, der abgerufen wird.  
  
 Wenn das **Recordset** -Objekt nur vorwärts ist, kann ein Benutzer ein *numrecords* -Argument weitergeben, das kleiner als NULL ist, vorausgesetzt, das Ziel liegt innerhalb des aktuellen Satzes zwischen gespeicherter Datensätze. Wenn beim **Verschiebungs Versuch die** aktuelle Daten Satz Position vor dem ersten zwischengespeicherten Datensatz in einen Datensatz verschoben wird, tritt ein Fehler auf. Daher können Sie einen Daten Satz Cache verwenden, der einen vollständigen Bildlauf für einen Anbieter unterstützt, der nur vorwärts Scrollen unterstützt. Da zwischengespeicherte Datensätze in den Arbeitsspeicher geladen werden, sollten Sie das Zwischenspeichern von mehr Datensätzen als notwendig vermeiden. Selbst wenn ein Forward-Only- **Recordsetobjekt** rückwärts Verschiebungen auf diese Weise unterstützt, wird beim Aufrufen der " [muveprevious](./movefirst-movelast-movenext-and-moveprevious-methods-ado.md) "-Methode für ein vorwärts **Recordset** -Objekt weiterhin ein Fehler generiert.  
  
> [!NOTE]
>  Die Unterstützung für das rückwärts verschieben in ein vorwärts **Recordset** ist abhängig von Ihrem Anbieter nicht vorhersagbar. Wenn der aktuelle Datensatz nach dem letzten Datensatz im **Recordset**positioniert wurde, führt die rückwärts **Bewegung** möglicherweise nicht zur korrekten aktuellen Position.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Move-Methode (VB)](./move-method-example-vb.md)   
 [Move-Methode (Beispiel) (VBScript)](./move-method-example-vbscript.md)   
 [Move-Methode (Beispiel) (VC + +)](./move-method-example-vc.md)   
 [Muvefirst-, muvelast-, muvenext-und muveprevious-Methode (ADO)](./movefirst-movelast-movenext-and-moveprevious-methods-ado.md)   
 ["Muvefirst", "muvelast", "muvenext" und "muveprevious" (RDS)](../rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md)   
 [MoveRecord-Methode (ADO)](./moverecord-method-ado.md)