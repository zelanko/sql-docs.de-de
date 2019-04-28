---
title: Move-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c8306a7d8e3247e77579d0bebc9147c3f9a1cc56
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62863487"
---
# <a name="move-method-ado"></a>Move-Methode (ADO)
Verschiebt die Position des aktuellen Datensatzes in einem [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
recordset.Move NumRecords, Start  
```  
  
#### <a name="parameters"></a>Parameter  
 *NumRecords*  
 Eine signierte **lange** Ausdruck, der die Anzahl von Datensätzen angibt, die die Position des aktuelle Datensatzes verschiebt.  
  
 *Start*  
 Dies ist optional. Ein **Zeichenfolge** Wert oder **Variant** , die ein Lesezeichen ergibt. Sie können auch eine [BookmarkEnum](../../../ado/reference/ado-api/bookmarkenum.md) Wert.  
  
## <a name="remarks"></a>Hinweise  
 Die **verschieben** -Methode wird für alle unterstützt **Recordset** Objekte.  
  
 Wenn die *NumRecords* Argument ist größer als 0 (null), die Position des aktuelle Datensatzes wird vorwärts verschoben (gegen Ende der **Recordset**). Wenn *NumRecords* ist kleiner als 0 (null), die Position des aktuelle Datensatzes verschiebt diesen rückwärts (bis zum Anfang der **Recordset**).  
  
 Wenn die **verschieben** aufrufen würde die Position des aktuelle Datensatzes auf einen Zeitpunkt vor dem ersten Datensatz verschoben, ADO legt den aktuellen Datensatz an die Position vor dem ersten Datensatz im Recordset ([BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) ist **"true"** ). Der Versuch, verschieben Abwärtskompatibilität bei der **BOF** Eigenschaft ist bereits **"true"** wird ein Fehler generiert.  
  
 Wenn die **verschieben** Aufruf wird die Position des aktuelle Datensatzes zu einem Zeitpunkt nach dem letzten Datensatz verschieben, ADO legt den aktuellen Datensatz auf die Position hinter dem letzten Datensatz im Recordset ([EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md) ist **"true"** ). Der Versuch, forward When Verschieben der **EOF** Eigenschaft ist bereits **"true"** wird ein Fehler generiert.  
  
 Aufrufen der **verschieben** Methode aus einer leeren **Recordset** Objekt wird ein Fehler generiert.  
  
 Übergeben der *starten* Argument der Verschiebevorgang ist relativ zu dem Datensatz mit diesem Lesezeichen, vorausgesetzt die **Recordset** -Objekt Lesezeichen unterstützt. Wenn nicht angegeben, ist die Verschiebung, relativ zum aktuellen Datensatz.  
  
 Bei Verwendung der [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md) Eigenschaft lokal Datensätze aus den Anbieter übergeben Zwischenspeichern einer *NumRecords* Argument, das die Position des aktuelle Datensatzes außerhalb der aktuellen Gruppe der zwischengespeicherten Einträge verschiebt Erzwingt, dass ADO zum Abrufen einer neuen Gruppe von Datensätzen aus dem Zieldatensatz ab. Die **CacheSize** Eigenschaft bestimmt die Größe der Gruppe "neu abgerufener", und der Zieldatensatz ist der erste Datensatz abgerufen.  
  
 Wenn die **Recordset** Objekt ist eine vorwärtsenumeration, Benutzer kann weiterhin übergeben, eine *NumRecords* Argument kleiner als 0 (null), zur Verfügung gestellt, das Ziel ist in den aktuellen Satz von zwischengespeicherten Einträge. Wenn die **verschieben** Aufruf würde verschiebt die Position des aktuelle Datensatzes auf einen Datensatz, bevor Sie den ersten zwischengespeicherten Eintrag, wird eine Fehlermeldung. Daher können Sie einen Datensatzcache verwenden, der über einen Anbieter, der unterstützt der Bildlauf ausschließlich vorwärts ausgeführt, vollständigen Bildlauf unterstützt. Da der zwischengespeicherten Einträge in den Arbeitsspeicher geladen werden, sollten Sie Zwischenspeichern mehrere Datensätze als erforderlich sind. Auch wenn ein Vorwärtscursor **Recordset** Objekt unterstützt das rückwärts verschoben werden, auf diese Weise Aufrufen der [MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md) Methode auf einem Vorwärtscursor **Recordset** Objekt weiterhin ein Fehler generiert.  
  
> [!NOTE]
>  Unterstützung für in einem Vorwärtscursor rückwärts verschieben **Recordset** ist nicht vorhersagbar, abhängig von Ihrem Anbieter. Wenn Sie nach dem letzten Datensatz in der aktuelle Datensatz positioniert ist die **Recordset**, **verschieben** rückwärts führt möglicherweise nicht zu der richtigen Position.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Move – Methodenbeispiel (VB)](../../../ado/reference/ado-api/move-method-example-vb.md)   
 [Move – Methodenbeispiel (VBScript)](../../../ado/reference/ado-api/move-method-example-vbscript.md)   
 [Move – Methodenbeispiel (VC++)](../../../ado/reference/ado-api/move-method-example-vc.md)   
 [MoveFirst, MoveLast, MoveNext und MovePrevious-Methode (ADO)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)   
 [MoveFirst, MoveLast, MoveNext und MovePrevious-Methode (RDS)](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md)   
 [MoveRecord-Methode (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)
