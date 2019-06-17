---
title: BeginTrans, CommitTrans und RollbackTrans-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::raw_RollbackTrans
- Connection15::CommitTrans
- Connection15::raw_CommitTrans
- Connection15::raw_BeginTrans
- Connection15::BeginTrans
- Connection15::RollbackTrans
helpviewer_keywords:
- BeginTrans method [ADO]
- CommitTrans method [ADO]
- RollbackTrans method [ADO]
ms.assetid: d4683472-4120-4236-8640-fa9ae289e23e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ee5560a27f7df49a82e964753f792bd46270d3a6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66696486"
---
# <a name="begintrans-committrans-and-rollbacktrans-methods-ado"></a>BeginTrans-, CommitTrans- und RollbackTrans-Methode (ADO)
Diese Transaktionsmethoden verwalten transaktionsverarbeitung in einem [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) -Objekt wie folgt:  
  
-   **BeginTrans** beginnt eine neue Transaktion.  
  
-   **CommitTrans** speichert Änderungen und beendet die aktuelle Transaktion. Sie können auch eine neue Transaktion starten.  
  
-   **RollbackTrans** verwirft alle Änderungen, die während der aktuellen Transaktion vorgenommen wurden, und beendet die Transaktion. Sie können auch eine neue Transaktion starten.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
level = object.BeginTrans()  
object.BeginTrans  
object.CommitTrans  
object.RollbackTrans  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **BeginTrans** aufgerufen werden können, wie eine Funktion, zurückgibt eine **lange** Variable, der angibt, der Schachtelungsebene der Transaktion.  
  
#### <a name="parameters"></a>Parameter  
 *object*  
 Ein **Verbindung** Objekt.  
  
## <a name="connection"></a>Verbindung  
 Verwenden Sie diese Methoden mit einem **Verbindung** Objekt, wenn Sie speichern oder eine Reihe von Änderungen an den Quelldaten als einzelne Einheit abbrechen möchten. Z. B. um Geld zwischen Konten zu übertragen, Sie Subtraktion einen Betrag von einem, und fügen die gleiche Menge in die andere. Wenn die Updates entweder ein Fehler auftritt, Wägen Sie die Konten nicht mehr. Diese Änderungen innerhalb einer geöffneten Transaktion wird sichergestellt, dass entweder alle oder keine der Änderungen durch.  
  
> [!NOTE]
>  Nicht alle Anbieter unterstützen Transaktionen. Überprüfen Sie, ob der Anbieter definierte Eigenschaft "**Transaktion DDL**" wird in der **Verbindung** des Objekts [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Sammlung, der angibt, dass der Anbieter unterstützt Transaktionen. Wenn der Anbieter keine Transaktionen unterstützt, wird das Aufrufen einer der folgenden Methoden einen Fehler zurück.  
  
 Nach dem Aufrufen der **BeginTrans** -Methode der Anbieter wird nicht mehr sofort ein Commit ausgeführt bis zum Aufruf von **CommitTrans** oder **RollbackTrans** zum Beenden der die Transaktion.  
  
 Für Anbieter, die Unterstützung von geschachtelten Transaktionen, die Aufrufen der **BeginTrans** Methode innerhalb einer geöffneten Transaktion startet, eine neue, geschachtelte Transaktion. Der Rückgabewert gibt an, der Schachtelungsebene: der Rückgabewert von "1" gibt an, Sie haben eine Transaktion der obersten Ebene geöffnet (d. h. die Transaktion ist nicht geschachtelt innerhalb einer anderen Transaktion), "2" gibt an, dass Sie eine Transaktion der zweiten Ebene (a geöffnet haben Transaktion geschachtelt innerhalb einer Transaktion der obersten Ebene), und so weiter. Aufrufen von **CommitTrans** oder **RollbackTrans** wirkt sich auf nur die zuletzt geöffnete Transaktion; müssen Sie schließen oder Rollback für die aktuelle Transaktion aus, bevor Sie alle auf höherer Ebene Transaktionen auflösen können.  
  
 Aufrufen der **CommitTrans** Methode speichert die Änderungen in einer geöffneten Transaktion für die Verbindung, und beendet die Transaktion. Aufrufen der **RollbackTrans** Methode kehrt alle Änderungen innerhalb einer geöffneten Transaktion und beendet die Transaktion. Beide Methoden aufrufen, wenn es keine Transaktion geöffnet ist, wird ein Fehler generiert.  
  
 Je die **Verbindung** des Objekts [Attribute](../../../ado/reference/ado-api/attributes-property-ado.md) Eigenschaft, die durch Aufrufen der **CommitTrans** oder **RollbackTrans** Methoden möglicherweise eine neue Transaktion wird automatisch gestartet. Wenn die **Attribute** -Eigenschaftensatz auf **AdXactCommitRetaining**, des Anbieters startet automatisch eine neue Transaktion nach einem **CommitTrans** aufrufen. Wenn die **Attribute** -Eigenschaftensatz auf **AdXactAbortRetaining**, des Anbieters startet automatisch eine neue Transaktion nach einem **RollbackTrans** aufrufen.  
  
## <a name="remote-data-service"></a>Remote Data Service  
 Die **BeginTrans**, **CommitTrans**, und **RollbackTrans** Methoden sind nicht verfügbar für eine clientseitige **Verbindung** Objekt.  
  
## <a name="applies-to"></a>Gilt für  
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [BeginTrans, CommitTrans und RollbackTrans-Methoden – Beispiel (VB)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-example-vb.md)   
 [BeginTrans, CommitTrans und RollbackTrans-Methode – Beispiel (VC++)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-example-vc.md)   
 [Attributes-Eigenschaft (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
