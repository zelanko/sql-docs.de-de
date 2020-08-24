---
description: Status-Eigenschaft (ADO-Recordset)
title: Status-Eigenschaft (ADO-Recordset) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::GetStatus
- Recordset15::Status
helpviewer_keywords:
- Status property [ADO Recordset]
ms.assetid: 41d70d89-880f-4850-9d17-19d9790cc8eb
author: rothja
ms.author: jroth
ms.openlocfilehash: cea09babfd2dacf35705adc71cddcdee99aad544
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777299"
---
# <a name="status-property-ado-recordset"></a>Status-Eigenschaft (ADO-Recordset)
Gibt den Status des aktuellen Datensatzes in Bezug auf Batch Updates oder andere Massen Vorgänge an.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine Summe von einem oder mehreren [recordstatuusenum](./recordstatusenum.md) -Werten zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Mit der Eigenschaft **Status** können Sie feststellen, welche Änderungen für Datensätze ausstehen, die beim Aktualisieren des Batches geändert wurden Sie können auch die **Status** -Eigenschaft verwenden, um den Status von Datensätzen anzuzeigen, die während Massen Vorgängen fehlschlagen, z. b. Wenn Sie die Methoden [Resync](./resync-method.md), [UpdateBatch](./updatebatch-method.md)oder [CancelBatch](./cancelbatch-method-ado.md) für ein [Recordset](./recordset-object-ado.md) -Objekt aufrufen oder die [Filter](./filter-property.md) -Eigenschaft für ein **Recordset** -Objekt auf ein Array von Lesezeichen festlegen. Mit dieser Eigenschaft können Sie feststellen, wie ein bestimmter Datensatz fehlgeschlagen ist, und ihn entsprechend auflösen.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Status Eigenschafts Beispiel (Recordset) (VB)](./status-property-example-recordset-vb.md)   
 [Status-Eigenschaft – Beispiel (VC++)](./status-property-example-vc.md)