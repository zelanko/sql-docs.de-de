---
title: State-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command25::State
helpviewer_keywords:
- State property [ADO]
ms.assetid: 0b993bac-2653-40b1-bcbb-5b57b6aae2bf
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e8a46dd9358b085fb6079f03df88474b72440068
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66711255"
---
# <a name="state-property-ado"></a>State-Eigenschaft (ADO)
Gibt für alle entsprechenden Objekte an, ob der Zustand des Objekts offen oder geschlossen ist. Wenn das Objekt eine asynchrone Methode ausgeführt wird, gibt Sie an, ob der aktuelle Zustand des Objekts eine Verbindung herstellen, abgerufen werden oder ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine **lange** , umfassen kann, ein [ObjectStateEnum](../../../ado/reference/ado-api/objectstateenum.md) Wert. Der Standardwert ist **AdStateClosed**.  
  
## <a name="remarks"></a>Hinweise  
 Können Sie die **Zustand** Eigenschaft, um den aktuellen Status eines bestimmten Objekts zu einem beliebigen Zeitpunkt zu ermitteln.  
  
 Des Objekts **Zustand** Eigenschaft kann eine Kombination von Werten haben. Z. B. wenn eine Anweisung ausgeführt wird, diese Eigenschaft müssen den kombinierten Wert **AdStateOpen** und **AdStateExecuting**.  
  
 Die **Zustand** Eigenschaft ist schreibgeschützt.  
  
## <a name="applies-to"></a>Gilt für  
  
||||  
|-|-|-|  
|[Command-Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Record-Objekt (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|  
|[Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)||  
  
## <a name="see-also"></a>Siehe auch  
 [ConnectionString und ConnectionTimeout State-Eigenschaften – Beispiel (VB)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [ConnectionString und ConnectionTimeout State-Eigenschaften – Beispiel (VC++)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
