---
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
ms.openlocfilehash: d3ba9ad977fe02a712a675b8a9e4bae4b3d038b1
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82759736"
---
# <a name="status-property-ado-recordset"></a>Status-Eigenschaft (ADO-Recordset)
Gibt den Status des aktuellen Datensatzes in Bezug auf Batch Updates oder andere Massen Vorgänge an.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine Summe von einem oder mehreren [recordstatuusenum](../../../ado/reference/ado-api/recordstatusenum.md) -Werten zurück.  
  
## <a name="remarks"></a>Bemerkungen  
 Mit der Eigenschaft **Status** können Sie feststellen, welche Änderungen für Datensätze ausstehen, die beim Aktualisieren des Batches geändert wurden Sie können auch die **Status** -Eigenschaft verwenden, um den Status von Datensätzen anzuzeigen, die während Massen Vorgängen fehlschlagen, z. b. Wenn Sie die Methoden [Resync](../../../ado/reference/ado-api/resync-method.md), [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)oder [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) für ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt aufrufen oder die [Filter](../../../ado/reference/ado-api/filter-property.md) -Eigenschaft für ein **Recordset** -Objekt auf ein Array von Lesezeichen festlegen. Mit dieser Eigenschaft können Sie feststellen, wie ein bestimmter Datensatz fehlgeschlagen ist, und ihn entsprechend auflösen.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Status Eigenschafts Beispiel (Recordset) (VB)](../../../ado/reference/ado-api/status-property-example-recordset-vb.md)   
 [Status-Eigenschaft – Beispiel (VC++)](../../../ado/reference/ado-api/status-property-example-vc.md)   
