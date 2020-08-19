---
description: 'Schritt 3: Auffüllen des Listenfelds „Fields“'
title: 'Schritt 3: Auffüllen des Listen Felds "Felder" | Microsoft-Dokumentation'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 315c32dc-aeb1-4629-b30e-87b44e8f84d1
author: rothja
ms.author: jroth
ms.openlocfilehash: d3a7378cfdce29094f5ae4271b9fe7bff7516753
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452792"
---
# <a name="step-3-populate-the-fields-list-box"></a>Schritt 3: Auffüllen des Listenfelds „Fields“
Fügen Sie den folgenden Code in den Click-Ereignishandler von ein, um das Listenfeld Felder aufzufüllen `lstMain` :  
  
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
  
 Dieser Code deklariert und instanziiert lokale Datensatz-und Recordset- `rec` Objekte `rs` bzw..  
  
 Die Zeile, die der in ausgewählten Ressource entspricht, `lstMain` wird zur aktuellen Zeile von `grs` . Anschließend wird das Listenfeld Details gelöscht und `rec` mit der aktuellen Zeile von `grs` als Quelle geöffnet.  
  
 Handelt es sich bei der Ressource um einen Sammlungs Daten Satz gemäß [RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md), wird das lokale Recordset `rs` für die untergeordneten Elemente von REC geöffnet. Anschließend `lstDetails` wird mit den Werten aus den Zeilen von gefüllt `rs` .  
  
 Wenn es sich bei der Ressource um einen einfachen Datensatz handelt, `recFields` wird aufgerufen. Weitere Informationen zu `recFields` finden Sie im nächsten Schritt.  
  
 Wenn die Ressource ein strukturiertes Dokument ist, wird kein Code implementiert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Szenario für die Internet Veröffentlichung](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Schritt 2: Initialisieren des Haupt Listen Felds](../../../ado/guide/data/step-2-initialize-the-main-list-box.md)   
 [Schritt 4: Auffüllen des Textfelds „Details“](../../../ado/guide/data/step-4-populate-the-details-text-box.md)
