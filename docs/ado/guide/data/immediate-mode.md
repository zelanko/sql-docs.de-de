---
title: Unmittelbarer Modus | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- data updates [ADO], immediate mode
- immediate mode [ADO]
- updating data [ADO], immediate mode
ms.assetid: 31fc53d0-97de-4315-a87b-3bf5cdd1f432
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2ff8782287f5a6cbeb3f22ca58eaa3bd061c6c89
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63161501"
---
# <a name="immediate-mode"></a>Unmittelbarer Modus
Unmittelbarer Modus gilt bei der **LockType** -Eigenschaftensatz auf **AdLockOptimistic** oder **AdLockPessimistic**. Im unmittelbaren Modus werden Änderungen an einem Datensatz mit der Datenquelle weitergegeben, sobald Sie die Arbeit auf eine Zeile abgeschlossen durch Aufrufen von deklarieren die **Update** Methode.  
  
## <a name="calling-update"></a>Aufrufen von Update  
 Wenn Sie aus dem Datensatz verschieben Sie zum Hinzufügen oder bearbeiten Sie vor dem Aufruf der **Update** , ADO wird automatisch Methodenaufruf **Update** zum Speichern der Änderungen. Rufen Sie die **CancelUpdate** Methode vor der Navigation, wenn Sie Änderungen an den aktuellen Datensatz abbrechen oder einen neu hinzugefügten Datensatz verwerfen möchten.  
  
 Der aktuelle Datensatz bleibt die aktuelle aufzurufen, nachdem Sie die **Update** Methode.  
  
## <a name="cancelupdate"></a>CancelUpdate  
 Verwenden der **CancelUpdate** Methode zum Abbrechen von Änderungen an der aktuellen Zeile oder eine neu hinzugefügte Zeile verworfen. Änderungen an der aktuellen Zeile oder eine neue Zeile kann nicht abgebrochen werden, nach dem Aufrufen der **Update** -Methode, es sei denn, die Änderungen entweder Teil einer Transaktion, die Sie mit Rollback können die **RollbackTrans** -Methode oder eines Teils ein BatchUpdate. Im Fall einer Batchaktualisierung, können Sie Abbrechen, die **aktualisieren** mit der **CancelUpdate** oder **CancelBatch** Methode.  
  
 Wenn Sie eine neue Zeile, beim Aufrufen Hinzufügen der **CancelUpdate** -Methode, die zur aktuellen Zeile wird die Zeile, die vor dem aktuellen wurde die **AddNew** aufrufen.  
  
 Wenn Sie nicht die aktuelle Zeile geändert oder eine neue Zeile hinzugefügt haben, wird beim Aufrufen der **CancelUpdate** Methode wird ein Fehler generiert.
