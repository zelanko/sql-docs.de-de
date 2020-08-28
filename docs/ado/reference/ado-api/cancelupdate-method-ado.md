---
description: CancelUpdate-Methode (ADO)
title: CancelUpdate-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::CancelUpdate
helpviewer_keywords:
- CancelUpdate method [ADO]
ms.assetid: eaa856cc-c786-462e-890c-c896261b1741
author: rothja
ms.author: jroth
ms.openlocfilehash: 2355d2a0b2ff0bbe14eb9b7d2a9a373164a4f5e5
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88975561"
---
# <a name="cancelupdate-method-ado"></a>CancelUpdate-Methode (ADO)
Bricht vor dem Aufrufen der [Update](./update-method.md) -Methode alle Änderungen ab, die an der aktuellen oder neuen Zeile eines [Recordset](./recordset-object-ado.md) -Objekts oder der [Fields](./fields-collection-ado.md) -Auflistung eines [Datensatz](./record-object-ado.md) -Objekts vorgenommen wurden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
recordset.CancelUpdaterecord.Fields.CancelUpdate  
```  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="recordset"></a>Recordset  
 Verwenden Sie die **CancelUpdate** -Methode, um Änderungen, die an der aktuellen Zeile vorgenommen wurden, abzubrechen oder eine neu hinzugefügte Zeile zu verwerfen Nachdem Sie die **Update** -Methode aufgerufen haben, können Sie keine Änderungen an der aktuellen Zeile oder einer neuen Zeile abbrechen, es sei denn, die Änderungen sind entweder Teil einer Transaktion, die Sie mit der [RollbackTrans](./begintrans-committrans-and-rollbacktrans-methods-ado.md) -Methode oder einem Teil eines Batch Updates zurücksetzen können. Im Fall eines Batch Updates können Sie das **Update** mit der **CancelUpdate** -Methode oder der [CancelBatch](./cancelbatch-method-ado.md) -Methode abbrechen.  
  
 Wenn Sie beim aufzurufen der **CancelUpdate** -Methode eine neue Zeile hinzufügen, wird die aktuelle Zeile zur Zeile, die vor dem [AddNew](./addnew-method-ado.md) -Befehl aktuell war.  
  
 Wenn Sie sich im Bearbeitungsmodus befinden und aus dem aktuellen Datensatz wechseln möchten (z. b. mithilfe der [Move](./move-method-ado.md)-, [NextRecordset](./nextrecordset-method-ado.md)-oder [Close](./close-method-ado.md) -Methode), können Sie mit **CancelUpdate** alle ausstehenden Änderungen abbrechen. Dies ist möglicherweise erforderlich, wenn das Update nicht erfolgreich an die Datenquelle gesendet werden kann. Beispielsweise wird bei einem versuchten Löschvorgang, der aufgrund von Verstößen gegen die referenzielle Integrität fehlschlägt, das **Recordset** nach einem [Lösch](./delete-method-ado-recordset.md)Vorgang im Bearbeitungsmodus belassen.  
  
## <a name="record"></a>Datensatz  
 Mit der **CancelUpdate** -Methode werden alle ausstehenden Einfügungen oder Löschungen von [Feld](./field-object.md) Objekten abgebrochen und ausstehende Updates vorhandener Felder abgebrochen und auf die ursprünglichen Werte wieder hergestellt. Die [Status](./status-property-ado-recordset.md) -Eigenschaft aller Felder in der **Fields** -Auflistung ist auf **adFieldOK**festgelegt.  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Fields-Collection (ADO)](./fields-collection-ado.md)  
    :::column-end:::
    :::column:::
        [Recordset-Objekt (ADO)](./recordset-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Update-und CancelUpdate-Methoden (VB)](./update-and-cancelupdate-methods-example-vb.md)   
 [Beispiel für Update-und CancelUpdate-Methoden (VC + +)](./update-and-cancelupdate-methods-example-vc.md)   
 [AddNew-Methode (ADO)](./addnew-method-ado.md)   
 [Cancel-Methode (ADO)](./cancel-method-ado.md)   
 [Cancel-Methode (RDS)](../rds-api/cancel-method-rds.md)   
 [CancelBatch-Methode (ADO)](./cancelbatch-method-ado.md)   
 [CancelUpdate-Methode (RDS)](../rds-api/cancelupdate-method-rds.md)   
 [EditMode-Eigenschaft](./editmode-property.md)   
 [Update-Methode](./update-method.md)