---
description: CancelBatch-Methode (ADO)
title: CancelBatch-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::raw_CancelBatch
- Recordset15::CancelBatch
helpviewer_keywords:
- CancelBatch method [ADO]
ms.assetid: dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c
author: rothja
ms.author: jroth
ms.openlocfilehash: 0baf8d291bbb45961163dfc80106724c48d71613
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88975581"
---
# <a name="cancelbatch-method-ado"></a>CancelBatch-Methode (ADO)
Bricht ein ausstehendes Batch Update ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
recordset.CancelBatchAffectRecords  
```  
  
#### <a name="parameters"></a>Parameter  
 *AffectRecords*  
 Optional. Ein [affectenum](./affectenum.md) -Wert, der angibt, wie viele Datensätze von der **CancelBatch** -Methode betroffen sind.  
  
## <a name="remarks"></a>Bemerkungen  
 Verwenden Sie die **CancelBatch** -Methode, um ausstehende Updates in einem [Recordset](./recordset-object-ado.md) im Batch Aktualisierungs Modus abzubrechen. Wenn sich das **Recordset** im sofortigen Update Modus befindet, wird beim Aufrufen von **CancelBatch** ohne **adaffectcurrent** ein Fehler generiert.  
  
 Wenn Sie den aktuellen Datensatz bearbeiten oder einen neuen Datensatz hinzufügen, wenn Sie **CancelBatch**aufrufen, ruft ADO zuerst die [CancelUpdate](./cancelupdate-method-ado.md) -Methode auf, um alle zwischengespeicherten Änderungen abzubrechen. Anschließend werden alle ausstehenden Änderungen im **Recordset** abgebrochen.  
  
 Der aktuelle Datensatz kann nach einem **CancelBatch** -Aufruf indetierbar sein, insbesondere, wenn Sie gerade einen neuen Datensatz hinzugefügt haben. Aus diesem Grund ist es ratsam, die aktuelle Daten Satz Position nach dem **CancelBatch** -Befehl auf einen bekannten Speicherort im **Recordset** festzulegen. Nennen Sie z. b. die Methode " [muvefirst](./movefirst-movelast-movenext-and-moveprevious-methods-ado.md) ".  
  
 Wenn der Versuch, ausstehende Updates abzubrechen, aufgrund eines Konflikts mit den zugrunde liegenden Daten (z. b. Wenn ein Datensatz von einem anderen Benutzer gelöscht wurde) fehlschlägt, gibt der Anbieter Warnungen an die [Fehler](./errors-collection-ado.md) Auflistung zurück, hält die Ausführung des Programms jedoch nicht an. Ein Laufzeitfehler tritt nur auf, wenn für alle angeforderten Datensätze Konflikte vorliegen. Verwenden Sie die [Filter](./filter-property.md) -Eigenschaft (**adFilterAffectedRecords**) und die [Status](./status-property-ado-recordset.md) -Eigenschaft, um Datensätze mit Konflikten zu suchen.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für UpdateBatch und CancelBatch-Methoden (VB)](./updatebatch-and-cancelbatch-methods-example-vb.md)   
 [Beispiel für UpdateBatch und CancelBatch-Methoden (VC + +)](./updatebatch-and-cancelbatch-methods-example-vc.md)   
 [Cancel-Methode (ADO)](./cancel-method-ado.md)   
 [Cancel-Methode (RDS)](../rds-api/cancel-method-rds.md)   
 [CancelUpdate-Methode (ADO)](./cancelupdate-method-ado.md)   
 [CancelUpdate-Methode (RDS)](../rds-api/cancelupdate-method-rds.md)   
 [Clear-Methode (ADO)](./clear-method-ado.md)   
 [LockType-Eigenschaft (ADO)](./locktype-property-ado.md)   
 [UpdateBatch-Methode](./updatebatch-method.md)