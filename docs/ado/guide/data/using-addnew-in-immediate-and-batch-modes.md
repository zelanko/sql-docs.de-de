---
title: AddNew-Methode im unmittelbaren mit Batch-Modi | Microsoft-Dokumentation
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
- ADO, adding data
- editing data [ADO], AddNew method
ms.assetid: ed314bb9-e188-4658-a68c-a2abc49610be
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 7bcd9d42ef214d7b1a2a40d2f00eeba85f9399b7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66704624"
---
# <a name="using-addnew-in-immediate-and-batch-modes"></a>Verwenden von AddNew im unmittelbaren und im Batchmodus
Das Verhalten von der **AddNew** Methode hängt von der Updatemodus von der **Recordset** Objekt und gibt an, ob Sie übergeben die *FieldList* und *Werte*Argumente.  
  
 Im sofortupdatemodus (in dem der Anbieter schreibt Änderungen in der zugrunde liegenden Datenquelle nach Aufrufen der **aktualisieren** Methode), wird beim Aufruf der **AddNew** -Methode ohne Argumente legt die  **EditMode** Eigenschaft **AdEditAdd.** Der Anbieter wird jeder Wert feldänderungen lokal zwischengespeichert. Aufrufen der **Update** Methode wird der neue Datensatz in der Datenbank und setzt die **EditMode** Eigenschaft **AdEditNone.** Übergeben der *FieldList* und *Werte* Argumente ADO sofort wird der neue Datensatz in der Datenbank (keine **Update** Aufruf erforderlich ist); die **EditMode**  Eigenschaftswert nicht ändert (**AdEditNone**).  
  
 Im Batchmodus Update Aufrufen der **AddNew** -Methode ohne Argumente legt die **EditMode** Eigenschaft **AdEditAdd**. Der Anbieter wird jeder Wert feldänderungen lokal zwischengespeichert. Aufrufen der **Update** Methode fügt den neuen Eintrag mit dem aktuellen **Recordset** und setzt die **EditMode** Eigenschaft **AdEditNone**, aber der Anbieter nicht die Änderungen an der zugrunde liegenden Datenbank gesendet, bis zum Aufruf der **UpdateBatch** Methode. Übergeben der *FieldList* und *Werte* Argumente ADO sendet des neuen Eintrags an den Anbieter für die Speicherung in einem Cache, muss die **UpdateBatch** Methode, um die neue Posten Notieren Sie sich an den zugrunde liegenden Datenbank. Weitere Informationen zu **Update** und **UpdateBatch**, finden Sie unter [wird aktualisiert und Beibehalten von Daten](../../../ado/guide/data/updating-and-persisting-data.md).
