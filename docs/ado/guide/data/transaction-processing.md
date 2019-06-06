---
title: Transaktionsverarbeitung | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- transactions [ADO]
- data updates [ADO], transaction processing
- updating data [ADO], transaction processing
- nested transactions [ADO]
ms.assetid: 74ab6706-e2dc-42cb-af77-dbc58a9cf4ce
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 032677452fa80502d37383af8172ff9475dea363
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66704812"
---
# <a name="transaction-processing"></a>Transaktionsverarbeitung
Ein *Transaktion* begrenzt den Anfang und Ende einer Reihe von Datenzugriffsvorgängen, die über eine Verbindung ausgeführt. Unterliegt die Transaktionsfunktionen von Ihrer Datenquelle den **Verbindung** Objekt kann auch die Ihnen das Erstellen und Verwalten von Transaktionen. Beispielsweise können mithilfe von Microsoft OLE DB-Anbieter für SQL Server auf eine Datenbank auf Microsoft SQL Server zugreifen, Sie mehrere geschachtelte Transaktionen für die Befehle erstellen, die Sie ausführen.  
  
 ADO wird sichergestellt, dass Änderungen an einer Datenquelle, die durch Vorgänge in einer Transaktion erfolgreich zusammen oder überhaupt nicht ausgeführt.  
  
 Wenn Sie die Transaktion abbrechen oder bei einem Ausfall einer der Vorgänge, wird das Ergebnis sein, als ob keiner der Vorgänge in der Transaktion aufgetreten ist. Die Datenquelle bleibt, wie vor dem Beginn der Transaktion.  
  
 ADO bietet die folgenden Methoden zum Steuern von Transaktionen: **BeginTrans**, **CommitTrans**, und **RollbackTrans**. Verwenden Sie diese Methoden mit einem **Verbindung** Objekt, wenn Sie speichern oder eine Reihe von Änderungen an den Quelldaten als einzelne Einheit abbrechen möchten. Z. B. um Geld zwischen Konten zu übertragen, Sie Subtraktion einen Betrag von einem, und fügen die gleiche Menge in die andere. Wenn die Updates entweder ein Fehler auftritt, Wägen Sie die Konten nicht mehr. Diese Änderungen innerhalb einer geöffneten Transaktion wird sichergestellt, dass entweder alle oder keine der Änderungen durch.  
  
> [!NOTE]
>  Nicht alle Anbieter unterstützen Transaktionen. Überprüfen Sie, ob der Anbieter definierte Eigenschaft "**Transaktion DDL**" wird in der **Verbindung** des Objekts [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Sammlung, der angibt, dass der Anbieter unterstützt Transaktionen. Wenn der Anbieter keine Transaktionen unterstützt, wird das Aufrufen einer der folgenden Methoden einen Fehler zurück.  
  
 Nach dem Aufrufen der **BeginTrans** -Methode der Anbieter wird nicht mehr sofort ein Commit ausgeführt bis zum Aufruf von **CommitTrans** oder **RollbackTrans** zum Beenden der die Transaktion.  
  
 Aufrufen der **CommitTrans** Methode speichert die Änderungen in einer geöffneten Transaktion für die Verbindung, und beendet die Transaktion. Aufrufen der **RollbackTrans** Methode kehrt alle Änderungen innerhalb einer geöffneten Transaktion und beendet die Transaktion. Beide Methoden aufrufen, wenn es keine Transaktion geöffnet ist, wird ein Fehler generiert.  
  
 Je die **Verbindung** des Objekts [Attribute](../../../ado/reference/ado-api/attributes-property-ado.md) Eigenschaft, die durch Aufrufen der **CommitTrans** oder **RollbackTrans** Methode möglicherweise eine neue Transaktion wird automatisch gestartet. Wenn die **Attribute** -Eigenschaftensatz auf **AdXactCommitRetaining**, des Anbieters startet automatisch eine neue Transaktion nach einem **CommitTrans** aufrufen. Wenn die **Attribute** -Eigenschaftensatz auf **AdXactAbortRetaining**, des Anbieters startet automatisch eine neue Transaktion nach einem **RollbackTrans** aufrufen.  
  
## <a name="transaction-isolation-level"></a>Transaktionsisolationsstufe  
 Verwenden der **IsolationLevel** -Eigenschaft zum Festlegen der Isolationsstufe einer Transaktion auf eine **Verbindung** Objekt. Die Einstellung wird wirksam, bis das nächste Mal Sie rufen die [BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) Methode. Wenn die Ebene der Isolation, die Sie anfordern, nicht verfügbar ist, kann der Anbieter der nächsten größere Maß an Isolation zurückgegeben. Finden Sie in der **IsolationLevel** -Eigenschaft in der ADO-Programmierreferenz für Weitere Informationen zu gültigen Werten.  
  
## <a name="nested-transactions"></a>Geschachtelte Transaktionen  
 Für Anbieter, die Unterstützung von geschachtelten Transaktionen, die Aufrufen der **BeginTrans** Methode innerhalb einer geöffneten Transaktion startet, eine neue, geschachtelte Transaktion. Der Rückgabewert gibt an, der Schachtelungsebene: der Rückgabewert von "1" gibt an, Sie haben eine Transaktion der obersten Ebene geöffnet (d. h. die Transaktion ist nicht geschachtelt innerhalb einer anderen Transaktion), "2" gibt an, dass Sie eine Transaktion der zweiten Ebene (a geöffnet haben Transaktion geschachtelt innerhalb einer Transaktion der obersten Ebene), und so weiter. Aufrufen von **CommitTrans** oder **RollbackTrans** wirkt sich auf nur die zuletzt geöffnete Transaktion; müssen Sie schließen oder Rollback für die aktuelle Transaktion aus, bevor Sie alle auf höherer Ebene Transaktionen auflösen können.
