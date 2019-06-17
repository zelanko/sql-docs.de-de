---
title: 'Schritt 3: Auffüllen des Listenfelds "Fields" | Microsoft-Dokumentation'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 315c32dc-aeb1-4629-b30e-87b44e8f84d1
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f69ab97a522e148d8027042ff7e2c6b09a690424
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66704826"
---
# <a name="step-3-populate-the-fields-list-box"></a>Schritt 3: Auffüllen des Listenfelds „Fields“
Fügen Sie zum Auffüllen der Listenfelds "Fields" den folgenden Code in der Click-Ereignishandler der `lstMain`:  
  
```  
Private Sub lstMain_Click()  
    Dim rec As Record  
    Dim rs As Recordset  
    Set rec = New Record  
    Set rs = New Recordset  
    grs.MoveFirst  
    grs.Move lstMain.ListIndex  
    lstDetails.Clear  
    rec.Open grs  
    Select Case rec.RecordType  
        Case adCollectionRecord:  
            Set rs = rec.GetChildren  
            While Not rs.EOF  
                lstDetails.AddItem rs(0)  
                rs.MoveNext  
            Wend  
        Case adSimpleRecord:  
            recFields rec, lstDetails, txtDetails  
  
        Case adStructDoc:  
    End Select  
  
End Sub  
```  
  
 Dieser Code deklariert und instanziiert Objekte des lokalen Datensatz und Recordset, `rec` und `rs`bzw.  
  
 Die Zeile, die im ausgewählten Ressource entspricht `lstMain` erfolgt die aktuelle Zeile `grs`. Und dann im Listenfeld "Details" deaktiviert ist und `rec` wird geöffnet, mit der aktuellen Zeile `grs` als Quelle.  
  
 Wenn die Ressource einen Auflistungsdatensatz gemäß ["RecordType"](../../../ado/reference/ado-api/recordtype-property-ado.md), lokalen Recordset `rs` in den untergeordneten Elementen Datensatztyp geöffnet wird. Klicken Sie dann `lstDetails` wird mit den Werten aus den Zeilen gefüllt `rs`.  
  
 Wenn die Ressource einen einfachen Datensatz `recFields` aufgerufen wird. Weitere Informationen zu `recFields`, finden Sie im nächsten Schritt.  
  
 Wenn die Ressource ein strukturiertes Dokument ist kein Code implementiert.  
  
## <a name="see-also"></a>Siehe auch  
 [Internet Publishing-Szenario](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Schritt 2: Initialisieren der wichtigsten Listenfelder](../../../ado/guide/data/step-2-initialize-the-main-list-box.md)   
 [Schritt 4: Auffüllen des Texfelds "Details"](../../../ado/guide/data/step-4-populate-the-details-text-box.md)
