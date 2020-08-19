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
ms.openlocfilehash: 80d15588279e584ec4d63d4336239952f22405cc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443462"
---
# <a name="index-property"></a>Index-Eigenschaft
Gibt den Namen des Indexes an, der aktuell für ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt wirksam ist.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Zeichen** folgen Wert fest, der den Namen des Indexes angibt, oder gibt ihn zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Der durch die **Index** -Eigenschaft benannte Index muss bereits in der Basistabelle deklariert worden sein, die dem **Recordset** -Objekt zugrunde liegt. Das heißt, der Index muss Programm gesteuert als ADOX- [Index](../../../ado/reference/adox-api/index-object-adox.md) Objekt oder beim Erstellen der Basistabelle deklariert werden.  
  
 Ein Laufzeitfehler tritt auf, wenn der Index nicht festgelegt werden kann. Die **Index** -Eigenschaft kann unter den folgenden Bedingungen nicht festgelegt werden:  
  
-   Innerhalb eines [WillChangeRecordset](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md) -oder **RecordsetChangeComplete** -Ereignis Handlers.  
  
-   , Wenn das **Recordset** weiterhin einen Vorgang ausführt (der von der [State](../../../ado/reference/ado-api/state-property-ado.md) -Eigenschaft bestimmt werden kann).  
  
-   Wenn ein Filter für das **Recordset** mit der [Filter](../../../ado/reference/ado-api/filter-property.md) -Eigenschaft festgelegt wurde.  
  
 Die **Index** -Eigenschaft kann immer erfolgreich festgelegt werden, wenn das **Recordset** geschlossen ist, das **Recordset** jedoch nicht erfolgreich geöffnet wird oder der Index nicht verwendbar ist, wenn der zugrunde liegende Anbieter keine Indizes unterstützt.  
  
 Wenn der Index festgelegt werden kann, kann sich die aktuelle Zeilen Position ändern. Dies führt zu einem Update der [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) -Eigenschaft und löst die Ereignisse " **WillChangeRecordset**", " **RecordsetChangeComplete**", " [WillMove](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)" und " [MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md) " aus.  
  
 Wenn der Index festgelegt werden kann und die [LockType](../../../ado/reference/ado-api/locktype-property-ado.md) -Eigenschaft auf **adlockpessimioder** **adlockoptimistisch**festgelegt ist, wird ein impliziter [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md) -Vorgang ausgeführt. Dadurch werden die aktuellen und die betroffenen Gruppen freigegeben. Es wird ein beliebiger vorhandener Filter freigegeben, und die aktuelle Zeilen Position wird in die erste Zeile des neu geordneten **Recordsets**geändert.  
  
 Die **Index** -Eigenschaft wird in Verbindung mit der [Seek](../../../ado/reference/ado-api/seek-method.md) -Methode verwendet. Wenn der zugrunde liegende Anbieter die **Index** -Eigenschaft und somit die **Seek** -Methode nicht unterstützt, sollten Sie stattdessen die [Find](../../../ado/reference/ado-api/find-method-ado.md) -Methode verwenden. Bestimmen Sie, ob das **Recordset** -Objekt Indizes mit der [unterstützten](../../../ado/reference/ado-api/supports-method.md)**(adIndex)** -Methode unterstützt.  
  
 Die integrierte **Index** Eigenschaft ist nicht mit der Eigenschaft "dynamische [Optimierung](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md) " verknüpft, obwohl beide Indizes behandelt werden.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für die Seek-Methode und Index-Eigenschaft (VB)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vb.md)   
 [Index-Objekt (ADOX)](../../../ado/reference/adox-api/index-object-adox.md)   
 [Seek-Methode](../../../ado/reference/ado-api/seek-method.md)
