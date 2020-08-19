---
description: Verarbeiten von Transaktionen
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 5b4d8e959cab799c5436b1c1357ae1e734d3d5a0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452702"
---
# <a name="transaction-processing"></a>Verarbeiten von Transaktionen
Eine *Transaktion* begrenzt den Anfang und das Ende einer Reihe von Datenzugriffs Vorgängen, die über eine Verbindung ausgeführt werden. Gemäß den Transaktionsfunktionen der Datenquelle ermöglicht das **Verbindungs** Objekt auch das Erstellen und Verwalten von Transaktionen. Wenn Sie z. b. den Microsoft OLE DB-Anbieter für SQL Server verwenden, um auf Microsoft SQL Server auf eine Datenbank zuzugreifen, können Sie für die Befehle, die Sie ausführen.  
  
 ADO stellt sicher, dass Änderungen an einer Datenquelle, die durch Vorgänge in einer Transaktion entstehen, erfolgreich oder überhaupt nicht ausgeführt werden.  
  
 Wenn Sie die Transaktion abbrechen oder einer der Vorgänge fehlschlägt, wird das Ergebnis so lauten, als ob keine der Vorgänge in der Transaktion erfolgt ist. Die Datenquelle bleibt unverändert, bevor die Transaktion gestartet wurde.  
  
 ADO bietet die folgenden Methoden zum Steuern von Transaktionen: **BeginTrans**, **CommitTrans**und **RollbackTrans**. Verwenden Sie diese Methoden mit einem **Verbindungs** Objekt, wenn Sie eine Reihe von Änderungen, die an den Quelldaten vorgenommen wurden, als einzelne Einheit speichern oder abbrechen möchten. Wenn Sie z. b. Geld zwischen Konten übertragen möchten, subtrahieren Sie einen Betrag von einem-Wert, und fügen Sie dem anderen denselben Betrag hinzu. Wenn ein Update fehlschlägt, werden die Konten nicht mehr ausgeglichen. Durch die Durchführung dieser Änderungen innerhalb einer geöffneten Transaktion wird sichergestellt, dass entweder alle oder keine der Änderungen durchlaufen werden.  
  
> [!NOTE]
>  Nicht alle Anbieter unterstützen Transaktionen. Vergewissern Sie sich, dass die vom Anbieter definierte Eigenschaft "**Transaction DDL**" in der [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) -Auflistung des **Verbindungs** Objekts angezeigt wird. Dies deutet darauf hin, dass der Anbieter Transaktionen unterstützt. Wenn der Anbieter keine Transaktionen unterstützt, wird beim Aufrufen einer dieser Methoden ein Fehler zurückgegeben.  
  
 Nachdem Sie die **BeginTrans** -Methode aufgerufen haben, führt der Anbieter die von Ihnen vorgenommenen Änderungen nicht mehr sofort aus, bevor Sie **CommitTrans** oder **RollbackTrans** aufrufen, um die Transaktion zu beenden.  
  
 Durch Aufrufen der **CommitTrans** -Methode werden Änderungen gespeichert, die innerhalb einer geöffneten Transaktion für die Verbindung vorgenommen werden, und die Transaktion wird beendet. Durch Aufrufen der **RollbackTrans** -Methode werden alle Änderungen, die innerhalb einer geöffneten Transaktion vorgenommen wurden, zurückgesetzt und die Transaktion beendet. Wenn Sie eine der Methoden aufrufen, wenn keine geöffnete Transaktion vorhanden ist, wird ein Fehler generiert.  
  
 Abhängig von der Eigenschaft [Attribute](../../../ado/reference/ado-api/attributes-property-ado.md) des **Verbindungs** Objekts wird durch das Aufrufen der **CommitTrans** -Methode oder der **RollbackTrans** -Methode möglicherweise automatisch eine neue Transaktion gestartet. Wenn die Eigenschaft **Attribute** auf **adxactcommitbehält**festgelegt ist, startet der Anbieter nach einem **CommitTrans** -Rückruf automatisch eine neue Transaktion. Wenn die Eigenschaft **Attribute** auf **adxactabortretribute**festgelegt ist, startet der Anbieter nach einem **RollbackTrans** -Rückruf automatisch eine neue Transaktion.  
  
## <a name="transaction-isolation-level"></a>Transaktionsisolationsstufe  
 Verwenden Sie die **IsolationLevel** -Eigenschaft, um die Isolationsstufe einer Transaktion für ein **Verbindungs** Objekt festzulegen. Die-Einstellung wird erst beim nächsten Aufrufen der [BeginTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md) -Methode wirksam. Wenn die Isolationsstufe, die Sie anfordern, nicht verfügbar ist, kann der Anbieter die nächsthöhere Isolationsstufe zurückgeben. Weitere Informationen zu gültigen Werten finden Sie unter der **IsolationLevel** -Eigenschaft in der ADO-Programmier Referenz.  
  
## <a name="nested-transactions"></a>Nicht mehr als Transaktionen  
 Für Anbieter, die geschachtelte Transaktionen unterstützen, wird beim Aufrufen der **BeginTrans** -Methode innerhalb einer geöffneten Transaktion eine neue geschachtelte Transaktion gestartet. Der Rückgabewert gibt die Schachtelungs Ebene an: der Rückgabewert "1" gibt an, dass Sie eine Transaktion der obersten Ebene geöffnet haben (d. h. die Transaktion ist nicht in einer anderen Transaktion geschachtelt), "2" zeigt an, dass Sie eine Transaktion der zweiten Ebene (eine Transaktion, die in einer Transaktion der obersten Ebene geschachtelt ist) geöffnet hat. Der Aufruf von **CommitTrans** oder **RollbackTrans** wirkt sich nur auf die zuletzt geöffnete Transaktion aus. Sie müssen die aktuelle Transaktion schließen oder zurücksetzen, bevor Sie Transaktionen höherer Ebene auflösen können.
