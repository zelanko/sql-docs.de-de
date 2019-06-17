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
manager: jroth
ms.openlocfilehash: 37ad4cbc60ad4c08b65ff7f0db9b5c70245a96e3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66700585"
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
