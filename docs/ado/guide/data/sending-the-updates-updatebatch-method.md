---
title: 'Senden von Updates: UpdateBatch-Methode | Microsoft-Dokumentation'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 87123797-831f-48e0-94b5-f669f9ca194a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3da407de4489ec829151696793f547e31541e6df
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63062876"
---
# <a name="sending-the-updates-updatebatch-method"></a>Senden von Updates: UpdateBatch-Methode
Der folgende Code wird ein Recordset im Modus "Batch" durch Festlegen der LockType-Eigenschaft auf AdLockBatchOptimistic und CursorLocation auf AdUseClient geöffnet. Es fügt zwei neue Datensätze und ändert den Wert eines Felds in einem vorhandenen Datensatz, und speichern die ursprünglichen Werte und ruft dann UpdateBatch zum Senden, dass die Änderungen an die Datenquelle zurück.  
  
## <a name="remarks"></a>Hinweise  
  
```  
'BeginBatchUpdate  
    strConn = "Provider=SQLOLEDB;Initial Catalog=Northwind;" & _  
              "Data Source=MySQLServer;Integrated Security=SSPI;"  
  
    strSQL = "SELECT ShipperId, CompanyName, Phone FROM Shippers"  
  
    Set objRs1 = New ADODB.Recordset  
    objRs1.CursorLocation = adUseClient  
    objRs1.Open strSQL, strConn, adOpenStatic, adLockBatchOptimistic, adCmdText  
  
    ' Change value of Phone field for first record in Recordset, saving value  
    ' for later restoration.  
    intId = objRs1("ShipperId")  
    sPhone = objRs1("Phone")  
  
    objRs1("Phone") = "(111) 555-1111"  
  
    'Add two new records  
    For i = 0 To 1  
        objRs1.AddNew  
        objRs1(1) = "New Shipper #" & CStr((i + 1))  
        objRs1(2) = "(nnn) 555-" & i & i & i & i  
    Next i  
  
    ' Send the updates  
    objRs1.UpdateBatch  
'EndBatchUpdate  
```  
  
 Wenn Sie den aktuellen Datensatz bearbeiten oder einen neuen Datensatz hinzufügen, wenn Sie die UpdateBatch-Methode aufrufen, wird die Update-Methode, um alle ausstehenden Änderungen in den aktuellen Datensatz zu speichern, vor der Übertragung der zusammengefasste Änderungen an den Anbieter von ADO automatisch aufrufen.  
  
## <a name="see-also"></a>Siehe auch  
 [Batchmodus](../../../ado/guide/data/batch-mode.md)
