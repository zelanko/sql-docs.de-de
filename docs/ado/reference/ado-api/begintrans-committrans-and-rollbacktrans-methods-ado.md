---
title: BeginTrans-, CommitTrans-und RollbackTrans-Methode (ADO) | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: a2a9f52b24ba4123db1b8e3a919b9fa25a030122
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82762896"
---
# <a name="begintrans-committrans-and-rollbacktrans-methods-ado"></a>BeginTrans-, CommitTrans- und RollbackTrans-Methode (ADO)
Diese Transaktions Methoden verwalten die Transaktionsverarbeitung innerhalb eines [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekts wie folgt:  
  
-   **BeginTrans** Startet eine neue Transaktion.  
  
-   **CommitTrans** Speichert alle Änderungen und beendet die aktuelle Transaktion. Möglicherweise wird auch eine neue Transaktion gestartet.  
  
-   **RollbackTrans** Bricht alle Änderungen ab, die während der aktuellen Transaktion vorgenommen wurden, und beendet die Transaktion. Möglicherweise wird auch eine neue Transaktion gestartet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
level = object.BeginTrans()  
object.BeginTrans  
object.CommitTrans  
object.RollbackTrans  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **BeginTrans** kann als eine Funktion aufgerufen werden, die eine **lange** Variable zurückgibt, die die Schachtelungs Ebene der Transaktion angibt.  
  
#### <a name="parameters"></a>Parameter  
 *object*  
 Ein **Verbindungs** Objekt.  
  
## <a name="connection"></a>Verbindung  
 Verwenden Sie diese Methoden mit einem **Verbindungs** Objekt, wenn Sie eine Reihe von Änderungen, die an den Quelldaten vorgenommen wurden, als einzelne Einheit speichern oder abbrechen möchten. Wenn Sie z. b. Geld zwischen Konten übertragen möchten, subtrahieren Sie einen Betrag von einem-Wert, und fügen Sie dem anderen denselben Betrag hinzu. Wenn ein Update fehlschlägt, werden die Konten nicht mehr ausgeglichen. Durch die Durchführung dieser Änderungen innerhalb einer geöffneten Transaktion wird sichergestellt, dass entweder alle oder keine der Änderungen durchlaufen werden.  
  
> [!NOTE]
>  Nicht alle Anbieter unterstützen Transaktionen. Vergewissern Sie sich, dass die vom Anbieter definierte Eigenschaft "**Transaction DDL**" in der [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) -Auflistung des **Verbindungs** Objekts angezeigt wird. Dies deutet darauf hin, dass der Anbieter Transaktionen unterstützt. Wenn der Anbieter keine Transaktionen unterstützt, wird beim Aufrufen einer dieser Methoden ein Fehler zurückgegeben.  
  
 Nachdem Sie die **BeginTrans** -Methode aufgerufen haben, führt der Anbieter die von Ihnen vorgenommenen Änderungen nicht mehr sofort aus, bevor Sie **CommitTrans** oder **RollbackTrans** aufrufen, um die Transaktion zu beenden.  
  
 Für Anbieter, die geschachtelte Transaktionen unterstützen, wird beim Aufrufen der **BeginTrans** -Methode innerhalb einer geöffneten Transaktion eine neue geschachtelte Transaktion gestartet. Der Rückgabewert gibt die Schachtelungs Ebene an: der Rückgabewert "1" gibt an, dass Sie eine Transaktion der obersten Ebene geöffnet haben (d. h. die Transaktion ist nicht in einer anderen Transaktion geschachtelt), "2" zeigt an, dass Sie eine Transaktion der zweiten Ebene (eine Transaktion, die in einer Transaktion der obersten Ebene geschachtelt ist) geöffnet hat. Der Aufruf von **CommitTrans** oder **RollbackTrans** wirkt sich nur auf die zuletzt geöffnete Transaktion aus. Sie müssen die aktuelle Transaktion schließen oder zurücksetzen, bevor Sie Transaktionen höherer Ebene auflösen können.  
  
 Durch Aufrufen der **CommitTrans** -Methode werden Änderungen gespeichert, die innerhalb einer geöffneten Transaktion für die Verbindung vorgenommen werden, und die Transaktion wird beendet. Durch Aufrufen der **RollbackTrans** -Methode werden alle Änderungen, die innerhalb einer geöffneten Transaktion vorgenommen wurden, zurückgesetzt und die Transaktion beendet. Wenn Sie eine der Methoden aufrufen, wenn keine geöffnete Transaktion vorhanden ist, wird ein Fehler generiert.  
  
 Abhängig von der Eigenschaft [Attribute](../../../ado/reference/ado-api/attributes-property-ado.md) des **Verbindungs** Objekts wird durch das Aufrufen der **CommitTrans** -Methode oder der **RollbackTrans** -Methode möglicherweise automatisch eine neue Transaktion gestartet. Wenn die Eigenschaft **Attribute** auf **adxactcommitbehält**festgelegt ist, startet der Anbieter nach einem **CommitTrans** -Rückruf automatisch eine neue Transaktion. Wenn die Eigenschaft **Attribute** auf **adxactabortretribute**festgelegt ist, startet der Anbieter nach einem **RollbackTrans** -Rückruf automatisch eine neue Transaktion.  
  
## <a name="remote-data-service"></a>Remote Data Service  
 Die Methoden **BeginTrans**, **CommitTrans**und **RollbackTrans** sind auf einem Client seitigen **Verbindungs** Objekt nicht verfügbar.  
  
## <a name="applies-to"></a>Gilt für  
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [BeginTrans-, CommitTrans-und RollbackTrans-Methoden Beispiel (VB)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-example-vb.md)   
 [BeginTrans-, CommitTrans-und RollbackTrans-Methoden Beispiel (VC + +)](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-example-vc.md)   
 [Attributes-Eigenschaft (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
