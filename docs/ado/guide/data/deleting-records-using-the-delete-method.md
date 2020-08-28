---
description: Löschen von Datensätzen mit der Delete-Methode
title: Löschen von Datensätzen mit der Delete-Methode | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, deleting records
- deleting records [ADO]
- editing data [ADO], Delete method
- Delete method [ADO]
ms.assetid: bfed5cfa-7f57-463b-9da2-0c612a079d30
author: rothja
ms.author: jroth
ms.openlocfilehash: d01223eae3f72a9a89b5f2e18b19c181a575052b
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88991401"
---
# <a name="deleting-records-using-the-delete-method"></a>Löschen von Datensätzen mit der Delete-Methode
Mithilfe der **Delete** -Methode wird der aktuelle Datensatz oder eine Gruppe von Datensätzen in einem **Recordset** -Objekt zum Löschen markiert. Wenn das **Recordset** -Objekt das Löschen von Datensätzen nicht zulässt, tritt ein Fehler auf. Wenn Sie sich im sofortigen Update Modus befinden, werden Löschungen sofort in der Datenbank ausgeführt. Wenn ein Datensatz nicht erfolgreich gelöscht werden kann (z. b. aufgrund von Daten Bank Integritäts Verstößen), verbleibt der Datensatz nach dem **Update Update** im Bearbeitungsmodus. Dies bedeutet, dass Sie das Update mit [CancelUpdate](../../reference/ado-api/cancelupdate-method-ado.md) abbrechen müssen, bevor Sie den aktuellen Datensatz verschieben (z. b. " [Close](../../reference/ado-api/close-method-ado.md)", " [Move](../../reference/ado-api/move-method-ado.md)" oder " [NextRecordset](../../reference/ado-api/nextrecordset-method-ado.md)").  
  
 Wenn Sie sich im Batch Aktualisierungs Modus befinden, werden die Datensätze zum Löschen aus dem Cache markiert, und der tatsächliche Löschvorgang erfolgt, wenn Sie die **UpdateBatch** -Methode aufrufen. (Um die gelöschten Datensätze anzuzeigen, legen Sie die **Filter** -Eigenschaft auf **adFilterAffectedRecords** fest, nachdem **Delete** aufgerufen wurde.)  
  
 Der Versuch, Feldwerte aus dem gelöschten Datensatz abzurufen, generiert einen Fehler. Nach dem Löschen des aktuellen Datensatzes bleibt der gelöschte Datensatz aktuell, bis Sie zu einem anderen Datensatz wechseln. Nachdem Sie den gelöschten Datensatz entfernt haben, ist er nicht mehr zugänglich.  
  
 Wenn Sie Löschungen in einer Transaktion Schachteln, können Sie gelöschte Datensätze mithilfe der **RollbackTrans** -Methode wiederherstellen. Wenn Sie sich im Batch Aktualisierungs Modus befinden, können Sie ein ausstehendes löschen oder eine Gruppe von ausstehenden Löschungen mithilfe der **CancelBatch** -Methode abbrechen.  
  
 Wenn der Versuch, Datensätze zu löschen, aufgrund eines Konflikts mit den zugrunde liegenden Daten (z. b. ein Datensatz bereits von einem anderen Benutzer gelöscht) fehlschlägt, gibt der Anbieter Warnungen an die **Fehler** Auflistung zurück, hält die Ausführung des Programms jedoch nicht an. Ein Laufzeitfehler tritt nur auf, wenn für alle angeforderten Datensätze Konflikte vorliegen.  
  
 Wenn die dynamische Eigenschaft der **eindeutigen Tabelle** festgelegt ist und das **Recordset** das Ergebnis der Ausführung eines Verknüpfungs Vorgangs für mehrere Tabellen ist, löscht die **Delete** -Methode Zeilen nur aus der Tabelle, die in der **eindeutigen Table** -Eigenschaft benannt ist.  
  
 Die **Delete** -Methode nimmt ein optionales Argument an, mit dem Sie angeben können, welche Datensätze vom **Lösch** Vorgang betroffen sind. Die einzigen gültigen Werte für dieses Argument sind eine der folgenden Enumerationskonstanten von ADO **affectenum** :  
  
-   **adaffectcurrent** Wirkt sich nur auf den aktuellen Datensatz aus.  
  
-   **adAffectGroup** Wirkt sich nur auf Datensätze aus, die die aktuelle **Filter** Eigenschaften Einstellung erfüllen. Die **Filter** -Eigenschaft muss auf einen **filtergroupum** -Wert oder ein Array von **Lesezeichen** festgelegt werden, um diese Option zu verwenden.  
  
 Der folgende Code zeigt ein Beispiel für die Angabe von **adAffectGroup** beim Aufrufen der **Delete** -Methode. In diesem Beispiel werden dem Beispiel **Recordset** einige Datensätze hinzugefügt und die-Datenbank aktualisiert. Anschließend wird das **Recordset** mithilfe der Enumerationskonstante **adFilterAffectedRecords** gefiltert, sodass nur die neu hinzugefügten Datensätze im **Recordset** sichtbar sind. Zum Schluss ruft Sie die **Delete** -Methode auf und gibt an, dass alle Datensätze, die die aktuelle **Filter** Eigenschafts Einstellung (die neuen Datensätze) erfüllen, gelöscht werden sollen.  
  
```  
'BeginDeleteGroup  
    'add some bogus records  
    With objRs  
        For i = 0 To 8  
            .AddNew  
            .Fields("CompanyName") = "Shipper Number " & i + 1  
            .Fields("Phone") = "(425) 555-000" & (i + 1)  
            .Update  
        Next i  
  
        ' update  
        .UpdateBatch  
  
        'filter on newly added records  
        .Filter = adFilterAffectedRecords  
        Debug.Print "Deleting the " & .RecordCount & _  
                    " records you just added."  
  
        'delete the newly added bogus records  
        .Delete adAffectGroup  
        .Filter = adFilterNone  
        Debug.Print .RecordCount & " records remain."  
    End With  
'EndDeleteGroup  
```