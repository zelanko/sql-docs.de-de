---
description: Hinzufügen von Datensätzen zu einem Recordset
title: Hinzufügen von Einträgen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: b833bc78a75d09c8f58ae12532f446ec94a097e0
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88991751"
---
# <a name="adding-records-to-a-recordset"></a>Hinzufügen von Datensätzen zu einem Recordset
Verwenden Sie die **AddNew** -Methode, um einen neuen Datensatz in einem vorhandenen **Recordset**zu erstellen und zu initialisieren. Mithilfe der **unterstützten** -Methode mit einem **Cursor** Wert von **adAddNew** können Sie überprüfen, ob dem aktuellen **Recordset** -Objektdaten Sätze hinzugefügt werden können.

 Nachdem Sie die **AddNew** -Methode aufgerufen haben, wird der neue Datensatz zum aktuellen Datensatz und bleibt nach dem Abrufen der **Update** -Methode aktuell. Wenn das **Recordset** -Objekt keine Lesezeichen unterstützt, können Sie möglicherweise nicht mehr auf den neuen Datensatz zugreifen, wenn Sie zu einem anderen Datensatz wechseln. Daher müssen Sie je nach Cursortyp möglicherweise die **Requery** -Methode aufzurufen, um den neuen Datensatz zugänglich zu machen.

 Wenn Sie beim Bearbeiten des aktuellen Datensatzes oder beim Hinzufügen eines neuen Datensatzes **AddNew** aufrufen, ruft ADO die **Update** -Methode auf, um alle Änderungen zu speichern und dann den neuen Datensatz zu erstellen.

 In diesem Abschnitt werden die folgenden Themen behandelt:

-   [Hinzufügen von Datensätzen mithilfe von AddNew](./adding-records-using-addnew.md)

-   [Hinzufügen von mehreren Feldern](./adding-multiple-fields.md)

-   [Bestimmen des Bearbeitungsmodus](./determining-edit-mode.md)

-   [Verwenden von AddNew im unmittelbaren und im Batchmodus](./using-addnew-in-immediate-and-batch-modes.md)