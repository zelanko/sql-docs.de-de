---
title: LockTypeEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- LockTypeEnum
helpviewer_keywords:
- LockTypeEnum enumeration [ADO]
ms.assetid: d2894eaf-4450-4ace-aa51-c8b875fd3010
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bcd2e4d2a3b84ef913954c1a1a2d7fa76393040c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62864073"
---
# <a name="locktypeenum"></a>LockTypeEnum
Gibt den Typ der Sperre, die auf Datensätze platziert werden, während der Bearbeitung.  
  
|Konstante|Wert|Description|  
|--------------|-----------|-----------------|  
|**adLockBatchOptimistic**|4|Gibt die vollständige BatchUpdates an. Für den Modus "Batch-Update" erforderlich.|  
|**adLockOptimistic**|3|Gibt an, optimistische, Datensätze. Der Anbieter verwendet optimistische, Sperren von Datensätzen nur bei Aufruf der [Update](../../../ado/reference/ado-api/update-method.md) Methode.|  
|**adLockPessimistic**|2|Gibt an, pessimistische Sperrung, Datensätze. Der Anbieter unterstützt, was erforderlich ist, um sicherzustellen, dass erfolgreiche Bearbeitung der Datensätze in der Regel durch Sperren von Datensätzen in der Datenquelle sofort nach der Bearbeitung ist.|  
|**adLockReadOnly**|1|Gibt an, nur-Lese Datensätze. Sie können die Daten nicht ändern.|  
|**adLockUnspecified**|-1|Es gibt keine Art von Sperre. Nach Klonen wird der Klon mit demselben Sperrentyp wie die ursprüngliche erstellt.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Package: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.LockType.BATCHOPTIMISTIC|  
|AdoEnums.LockType.OPTIMISTIC|  
|AdoEnums.LockType.PESSIMISTIC|  
|AdoEnums.LockType.READONLY|  
|AdoEnums.LockType.UNSPECIFIED|  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Clone-Methode (ADO)](../../../ado/reference/ado-api/clone-method-ado.md)|[LockType-Eigenschaft (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)|  
|[Open-Methode (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|[WillExecute-Ereignis (ADO)](../../../ado/reference/ado-api/willexecute-event-ado.md)|
