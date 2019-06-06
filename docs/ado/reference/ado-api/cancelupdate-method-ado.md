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
manager: jroth
ms.openlocfilehash: b53fa2e9d69b39218d846b57070b78ae230d81cf
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66698816"
---
# <a name="cancelupdate-method-ado"></a>CancelUpdate-Methode (ADO)
Bricht alle Änderungen an der aktuellen oder der neuen Zeile ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt, oder die [Felder](../../../ado/reference/ado-api/fields-collection-ado.md) Auflistung von einer [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) Objekt vor dem Aufruf der [Update ](../../../ado/reference/ado-api/update-method.md) Methode.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
recordset.CancelUpdaterecord.Fields.CancelUpdate  
```  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="recordset"></a>Recordset  
 Verwenden der **CancelUpdate** Methode zum Abbrechen von Änderungen an der aktuellen Zeile oder eine neu hinzugefügte Zeile verworfen. Änderungen an der aktuellen Zeile oder eine neue Zeile kann nicht abgebrochen werden, nach dem Aufrufen der **Update** -Methode, es sei denn, die Änderungen entweder Teil einer Transaktion, die Sie mit Rollback können die [RollbackTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) -Methode oder Teil von einem BatchUpdate. Im Fall einer Batchaktualisierung, können Sie Abbrechen, die **aktualisieren** mit der **CancelUpdate** oder [CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md) Methode.  
  
 Wenn Sie eine neue Zeile, beim Aufrufen Hinzufügen der **CancelUpdate** -Methode, die zur aktuellen Zeile wird die Zeile, die vor dem aktuellen wurde die [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) aufrufen.  
  
 Wenn Sie im Bearbeitungsmodus befindet und Sie den aktuellen Datensatz verschoben werden soll (z. B. durch Verwendung der [verschieben](../../../ado/reference/ado-api/move-method-ado.md), [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md), oder [schließen](../../../ado/reference/ado-api/close-method-ado.md) Methoden), können Sie  **CancelUpdate** , alle ausstehenden Änderungen abzubrechen. Sie müssen möglicherweise dazu, wenn das Update erfolgreich an die Datenquelle gebucht werden kann. Z. B. eine versuchte löschen, ein Fehler auftritt, aufgrund von Verletzungen der referenziellen Integrität zu lassen, werden die **Recordset** im Bearbeitungsmodus befindet, nach einem Aufruf von [löschen](../../../ado/reference/ado-api/delete-method-ado-recordset.md).  
  
## <a name="record"></a>Datensatz  
 Die **CancelUpdate** -Methode bricht alle ausstehenden einfügungen oder löschungen von [Feld](../../../ado/reference/ado-api/field-object.md) Objekte aufweist, und bricht ausstehende Updates vorhandener Felder ab und stellt diese auf ihre ursprünglichen Werte wieder her. Die [Status](../../../ado/reference/ado-api/status-property-ado-recordset.md) Eigenschaft aller Felder in der **Felder** Auflistung nastaven NA hodnotu **AdFieldOK**.  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Fields-Collection (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|[Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [Update- und CancelUpdate-Methode – Beispiel (VB)](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vb.md)   
 [Update- und CancelUpdate-Methode – Beispiel (VC++)](../../../ado/reference/ado-api/update-and-cancelupdate-methods-example-vc.md)   
 [AddNew-Methode (ADO)](../../../ado/reference/ado-api/addnew-method-ado.md)   
 [Cancel-Methode (ADO)](../../../ado/reference/ado-api/cancel-method-ado.md)   
 [Cancel-Methode (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [CancelBatch-Methode (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)   
 [CancelUpdate-Methode (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [EditMode-Eigenschaft](../../../ado/reference/ado-api/editmode-property.md)   
 [Update-Methode](../../../ado/reference/ado-api/update-method.md)
