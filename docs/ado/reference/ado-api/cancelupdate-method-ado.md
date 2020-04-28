---
title: CancelUpdate-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fa9e680e1626311f2cc10aa7c79fb583841fbc38
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67920116"
---
# <a name="cancelupdate-method-ado"></a>CancelUpdate-Methode (ADO)
Bricht vor dem Aufrufen der [Update](../../../ado/reference/ado-api/update-method.md) -Methode alle Änderungen ab, die an der aktuellen oder neuen Zeile eines [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekts oder der [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) -Auflistung eines [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) -Objekts vorgenommen wurden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
recordset.CancelUpdaterecord.Fields.CancelUpdate  
```  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="recordset"></a>Recordset  
 Verwenden Sie die **CancelUpdate** -Methode, um Änderungen, die an der aktuellen Zeile vorgenommen wurden, abzubrechen oder eine neu hinzugefügte Zeile zu verwerfen Nachdem Sie die **Update** -Methode aufgerufen haben, können Sie keine Änderungen an der aktuellen Zeile oder einer neuen Zeile abbrechen, es sei denn, die Änderungen sind entweder Teil einer Transaktion, die Sie mit der [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) -Methode oder einem Teil eines Batch Updates zurücksetzen können. Im Fall eines Batch Updates können Sie das **Update** mit der **CancelUpdate** -Methode oder der [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) -Methode abbrechen.  
  
 Wenn Sie beim aufzurufen der **CancelUpdate** -Methode eine neue Zeile hinzufügen, wird die aktuelle Zeile zur Zeile, die vor dem [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) -Befehl aktuell war.  
  
 Wenn Sie sich im Bearbeitungsmodus befinden und aus dem aktuellen Datensatz wechseln möchten (z. b. mithilfe der [Move](../../../ado/reference/ado-api/move-method-ado.md)-, [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)-oder [Close](../../../ado/reference/ado-api/close-method-ado.md) -Methode), können Sie mit **CancelUpdate** alle ausstehenden Änderungen abbrechen. Dies ist möglicherweise erforderlich, wenn das Update nicht erfolgreich an die Datenquelle gesendet werden kann. Beispielsweise wird bei einem versuchten Löschvorgang, der aufgrund von Verstößen gegen die referenzielle Integrität fehlschlägt, das **Recordset** nach einem [Lösch](../../../ado/reference/ado-api/delete-method-ado-recordset.md)Vorgang im Bearbeitungsmodus belassen.  
  
## <a name="record"></a>Datensatz  
 Mit der **CancelUpdate** -Methode werden alle ausstehenden Einfügungen oder Löschungen von [Feld](../../../ado/reference/ado-api/field-object.md) Objekten abgebrochen und ausstehende Updates vorhandener Felder abgebrochen und auf die ursprünglichen Werte wieder hergestellt. Die [Status](../../../ado/reference/ado-api/status-property-ado-recordset.md) -Eigenschaft aller Felder in der **Fields** -Auflistung ist auf **adFieldOK**festgelegt.  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Fields-Collection (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|[Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für Update-und CancelUpdate-Methoden (VB)](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vb.md)   
 [Beispiel für Update-und CancelUpdate-Methoden (VC + +)](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vc.md)   
 [AddNew-Methode (ADO)](../../../ado/reference/ado-api/addnew-method-ado.md)   
 [Cancel-Methode (ADO)](../../../ado/reference/ado-api/cancel-method-ado.md)   
 [Cancel-Methode (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [CancelBatch-Methode (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [CancelUpdate-Methode (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [EditMode-Eigenschaft](../../../ado/reference/ado-api/editmode-property.md)   
 [Update-Methode](../../../ado/reference/ado-api/update-method.md)
