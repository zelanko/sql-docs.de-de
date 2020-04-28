---
title: Hinzufügen von Einträgen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- AddNew method [ADO]
- ADO, editing data
- editing data [ADO], AddNew method
- editing data [ADO], adding data
ms.assetid: dd34669e-6f06-403b-9241-1c85c82aecc2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1f4ec0934fbf75de18f460abae84b8117e99f452
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67926263"
---
# <a name="adding-records-to-a-recordset"></a>Hinzufügen von Datensätzen zu einem Recordset
Verwenden Sie die **AddNew** -Methode, um einen neuen Datensatz in einem vorhandenen **Recordset**zu erstellen und zu initialisieren. Mithilfe der **unterstützten** -Methode mit einem **Cursor** Wert von **adAddNew** können Sie überprüfen, ob dem aktuellen **Recordset** -Objektdaten Sätze hinzugefügt werden können.

 Nachdem Sie die **AddNew** -Methode aufgerufen haben, wird der neue Datensatz zum aktuellen Datensatz und bleibt nach dem Abrufen der **Update** -Methode aktuell. Wenn das **Recordset** -Objekt keine Lesezeichen unterstützt, können Sie möglicherweise nicht mehr auf den neuen Datensatz zugreifen, wenn Sie zu einem anderen Datensatz wechseln. Daher müssen Sie je nach Cursortyp möglicherweise die **Requery** -Methode aufzurufen, um den neuen Datensatz zugänglich zu machen.

 Wenn Sie beim Bearbeiten des aktuellen Datensatzes oder beim Hinzufügen eines neuen Datensatzes **AddNew** aufrufen, ruft ADO die **Update** -Methode auf, um alle Änderungen zu speichern und dann den neuen Datensatz zu erstellen.

 In diesem Abschnitt werden die folgenden Themen behandelt:

-   [Hinzufügen von Datensätzen mithilfe von AddNew](../../../ado/guide/data/adding-records-using-addnew.md)

-   [Hinzufügen von mehreren Feldern](../../../ado/guide/data/adding-multiple-fields.md)

-   [Bestimmen des Bearbeitungsmodus](../../../ado/guide/data/determining-edit-mode.md)

-   [Verwenden von AddNew im unmittelbaren und im Batchmodus](../../../ado/guide/data/using-addnew-in-immediate-and-batch-modes.md)
