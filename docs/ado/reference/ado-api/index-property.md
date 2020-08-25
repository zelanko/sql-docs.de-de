---
description: Index-Eigenschaft
title: Index Eigenschaft | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset21::Index
helpviewer_keywords:
- Index property
ms.assetid: 1c79e271-21ec-41a8-8163-c5e89f0001a7
author: rothja
ms.author: jroth
ms.openlocfilehash: 084c27d5101c5aa08d25e7d073158a859d275d3b
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88774805"
---
# <a name="index-property"></a>Index-Eigenschaft
Gibt den Namen des Indexes an, der aktuell für ein [Recordset](./recordset-object-ado.md) -Objekt wirksam ist.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Zeichen** folgen Wert fest, der den Namen des Indexes angibt, oder gibt ihn zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Der durch die **Index** -Eigenschaft benannte Index muss bereits in der Basistabelle deklariert worden sein, die dem **Recordset** -Objekt zugrunde liegt. Das heißt, der Index muss Programm gesteuert als ADOX- [Index](../adox-api/index-object-adox.md) Objekt oder beim Erstellen der Basistabelle deklariert werden.  
  
 Ein Laufzeitfehler tritt auf, wenn der Index nicht festgelegt werden kann. Die **Index** -Eigenschaft kann unter den folgenden Bedingungen nicht festgelegt werden:  
  
-   Innerhalb eines [WillChangeRecordset](./willchangerecordset-and-recordsetchangecomplete-events-ado.md) -oder **RecordsetChangeComplete** -Ereignis Handlers.  
  
-   , Wenn das **Recordset** weiterhin einen Vorgang ausführt (der von der [State](./state-property-ado.md) -Eigenschaft bestimmt werden kann).  
  
-   Wenn ein Filter für das **Recordset** mit der [Filter](./filter-property.md) -Eigenschaft festgelegt wurde.  
  
 Die **Index** -Eigenschaft kann immer erfolgreich festgelegt werden, wenn das **Recordset** geschlossen ist, das **Recordset** jedoch nicht erfolgreich geöffnet wird oder der Index nicht verwendbar ist, wenn der zugrunde liegende Anbieter keine Indizes unterstützt.  
  
 Wenn der Index festgelegt werden kann, kann sich die aktuelle Zeilen Position ändern. Dies führt zu einem Update der [AbsolutePosition](./absoluteposition-property-ado.md) -Eigenschaft und löst die Ereignisse " **WillChangeRecordset**", " **RecordsetChangeComplete**", " [WillMove](./willmove-and-movecomplete-events-ado.md)" und " [MoveComplete](./willmove-and-movecomplete-events-ado.md) " aus.  
  
 Wenn der Index festgelegt werden kann und die [LockType](./locktype-property-ado.md) -Eigenschaft auf **adlockpessimioder** **adlockoptimistisch**festgelegt ist, wird ein impliziter [UpdateBatch](./updatebatch-method.md) -Vorgang ausgeführt. Dadurch werden die aktuellen und die betroffenen Gruppen freigegeben. Es wird ein beliebiger vorhandener Filter freigegeben, und die aktuelle Zeilen Position wird in die erste Zeile des neu geordneten **Recordsets**geändert.  
  
 Die **Index** -Eigenschaft wird in Verbindung mit der [Seek](./seek-method.md) -Methode verwendet. Wenn der zugrunde liegende Anbieter die **Index** -Eigenschaft und somit die **Seek** -Methode nicht unterstützt, sollten Sie stattdessen die [Find](./find-method-ado.md) -Methode verwenden. Bestimmen Sie, ob das **Recordset** -Objekt Indizes mit der [unterstützten](./supports-method.md)**(adIndex)** -Methode unterstützt.  
  
 Die integrierte **Index** Eigenschaft ist nicht mit der Eigenschaft "dynamische [Optimierung](./optimize-property-dynamic-ado.md) " verknüpft, obwohl beide Indizes behandelt werden.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für die Seek-Methode und Index-Eigenschaft (VB)](./seek-method-and-index-property-example-vb.md)   
 [Index-Objekt (ADOX)](../adox-api/index-object-adox.md)   
 [Seek-Methode](./seek-method.md)