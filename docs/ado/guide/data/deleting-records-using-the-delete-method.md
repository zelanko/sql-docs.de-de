---
title: Löschen von Datensätzen, die mit der Delete-Methode | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5a862a244f06c64767f41529b4fff36881895a0b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67925559"
---
# <a name="deleting-records-using-the-delete-method"></a>Löschen von Datensätzen mit der Delete-Methode
Mithilfe der **löschen** Methode kennzeichnet den aktuellen Datensatz oder eine Gruppe von Datensätzen in einer **Recordset** Objekt zum Löschen. Wenn die **Recordset** Objekt lässt keine Datensätze löschen, ein Fehler auftritt. Wenn Sie sich im sofortupdatemodus sind, werden die Löschvorgänge in der Datenbank sofort. Wenn ein Datensatz (aufgrund von Datenbank-integritätsverletzungen, z. B.) wurde erfolgreich gelöscht werden kann, der Datensatz bleibt im Bearbeitungsmodus nach dem Aufruf von **aktualisieren.** Dies bedeutet, dass Sie das Update mit abbrechen müssen [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md) vor dem Verlassen des aktuellen Datensatzes (z. B. [schließen](../../../ado/reference/ado-api/close-method-ado.md), [verschieben](../../../ado/reference/ado-api/move-method-ado.md), oder [ NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)).  
  
 Wenn Sie im Modus "Batch-Update" sind, werden die Datensätze zum Löschen aus dem Cache markiert und das eigentliche löschen erfolgt beim Aufrufen der **UpdateBatch** Methode. (Legen Sie zum Anzeigen der gelöschten Datensätze der **Filter** Eigenschaft **AdFilterAffectedRecords** nach **löschen** aufgerufen wird.)  
  
 Es wird versucht, die Feldwerte aus den gelöschten Datensatz abzurufen, wird ein Fehler generiert. Nach dem Löschen des aktuellen Datensatzes, bleibt der gelöschte Datensatz aktuell, bis Sie zu einem anderen Datensatz verschieben. Sobald Sie Abkehr von den gelöschten Datensatz, es nicht mehr zugänglich ist.  
  
 Wenn Sie Löschvorgänge in einer Transaktion schachteln, können Sie gelöschte Datensätze wiederherstellen, mit der **RollbackTrans** Methode. Wenn Sie im Modus "Batch-Update" sind, können Sie Abbrechen einen ausstehenden Löschvorgang oder eine Gruppe von ausstehenden Löschvorgängen mithilfe der **CancelBatch** Methode.  
  
 Wenn der Versuch zum Löschen von Datensätzen aufgrund eines Konflikts mit dem zugrunde liegenden fehlschlägt (z. B. ein Datensatz wurde bereits gelöscht von einem anderen Benutzer), der Anbieter gibt Warnungen an, die die **Fehler** Auflistung jedoch kein Programm angehalten wird die Ausführung. Ein Laufzeitfehler tritt auf, nur dann, wenn Konflikte für alle angeforderten Datensätze bestehen.  
  
 Wenn die **eindeutige Tabelle** dynamische Eigenschaft festgelegt ist und die **Recordset** ist das Ergebnis der Ausführung einer JOIN-Operation für mehrere Tabellen, die **löschen** Methode werden nur Zeilen löschen aus der Tabelle, die mit dem Namen in der **eindeutige Tabelle** Eigenschaft.  
  
 Die **löschen** Methode akzeptiert ein optionales Argument, das können Sie angeben, welche Datensätze betroffen sind der **löschen** Vorgang. Die einzigen gültigen Werte für dieses Argument sind entweder die folgenden ADO **AffectEnum** aufgezählte Konstanten:  
  
-   **AdAffectCurrent** wirkt sich auf die nur den aktuellen Datensatz.  
  
-   **AdAffectGroup** betrifft nur die Datensätze, die die aktuelle erfüllen **Filter** Einstellung der Eigenschaft. Die **Filter** Eigenschaft muss festgelegt werden, um eine **FilterGroupEnum** Wert oder ein Array von **Lesezeichen** auf diese Option verwenden.  
  
 Der folgende Code zeigt ein Beispiel für **AdAffectGroup** beim Aufrufen der **löschen** Methode. In diesem Beispiel fügt einige Datensätze, zum Beispiel **Recordset** und die Datenbank aktualisiert. Anschließend Filtern der **Recordset** mithilfe der **AdFilterAffectedRecords** aufgelisteten Filter-Konstante, die nur die neu hinzugefügte Datensätze im sichtbar bleibt die **Recordset.** Schließlich ruft es die **löschen** Methode und gibt an, dass alle Datensätze, die die aktuelle erfüllen **Filter** (die neue Einträge) für die Einstellung der Eigenschaft gelöscht werden soll.  
  
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
