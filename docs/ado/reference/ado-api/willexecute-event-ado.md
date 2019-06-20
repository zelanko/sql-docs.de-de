---
title: WillExecute-Ereignis (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- WillExecute
- Connection::WillExecute
helpviewer_keywords:
- WillExecute event [ADO]
ms.assetid: dd755e46-f589-48a3-93a9-51ff998d44b5
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 571c63e0b8e06c08fb066c3bb6b2d42a019895e5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66710032"
---
# <a name="willexecute-event-ado"></a>WillExecute-Ereignis (ADO)
Die **WillExecute** Ereignis wird immer dann aufgerufen, unmittelbar bevor ein ausstehenden Befehls für eine Verbindung ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
WillExecute Source, CursorType, LockType, Options, adStatus, pCommand, pRecordset, pConnection  
```  
  
#### <a name="parameters"></a>Parameter  
 *Quelle*  
 Ein **Zeichenfolge** , der einen SQL-Befehl oder Name einer gespeicherten Prozedur enthält.  
  
 *CursorType*  
 Ein [CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md) , enthält den Typ des Cursors für die **Recordset** , die geöffnet wird. Mit diesem Parameter können Sie den Cursor in einen beliebigen Typ während der ändern eine **Recordset**[Open-Methode (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md) Vorgang. *CursorType* für andere Vorgänge ignoriert werden.  
  
 *LockType*  
 Ein [LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md) , enthält den Sperrentyp für die **Recordset** , die geöffnet wird. Sie können die Sperre mit diesem Parameter ändern, auf einen beliebigen Typ während einer **RecordsetOpen** Vorgang. *LockType* für andere Vorgänge ignoriert werden.  
  
 *Options*  
 Ein **lange** Wert, der Optionen, die verwendet werden können angibt, führen Sie den Befehl aus, oder Öffnen der **Recordset**.  
  
 *adStatus*  
 Ein [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) Statuswert, der möglicherweise **AdStatusCantDeny** oder **AdStatusOK** Wenn dieses Ereignis aufgerufen wird. Ist dies **AdStatusCantDeny**, dieses Ereignis kann den Abbruch des ausstehenden Vorgangs nicht anfordern.  
  
 *pCommand*  
 Die [Befehl Objekt (ADO)](../../../ado/reference/ado-api/command-object-ado.md) -Objekt für die dieser ereignisbenachrichtigung angewendet wird.  
  
 *pRecordset*  
 Die [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt für die dieser ereignisbenachrichtigung angewendet wird.  
  
 *pConnection*  
 Die [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md) -Objekt für die dieser ereignisbenachrichtigung angewendet wird.  
  
## <a name="remarks"></a>Hinweise  
 Ein **WillExecute** Ereignis kann auftreten, weil eine Verbindung besteht.  [Execute-Methode (ADO Connection)](../../../ado/reference/ado-api/execute-method-ado-connection.md), [Execute-Methode (ADO Command)](../../../ado/reference/ado-api/execute-method-ado-command.md), oder [Open-Methode (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md) Methode der *pConnection* sollte der Parameter enthält immer einen gültigen Verweis auf eine **Verbindung** Objekt. Wenn das Ereignis aufgrund von **Connection.Execute**, *pRecordset* und *pCommand* Parameter werden festgelegt, um **"Nothing"** . Wenn das Ereignis aufgrund von **Recordset.Open**, *pRecordset* Parameter verweist auf die **Recordset** Objekt und die *pCommand* Parametersatz zu **nichts**. Wenn das Ereignis aufgrund von **Recordset.Open**, *pCommand* Parameter verweist auf die **Befehl** Objekt und die *pRecordset* Parametersatz zu **nichts**.  
  
 **WillExecute** können Sie zum Überprüfen und ändern die ausstehende Ausführung-Parameter. Dieses Ereignis kann eine Anforderung zurückgeben, dass der ausstehende Befehl abgebrochen werden.  
  
> [!NOTE]
>  Wenn die ursprüngliche für die Datenquelle eine **Befehl** ist ein Datenstrom, der gemäß der [CommandStream-Eigenschaft (ADO)](../../../ado/reference/ado-api/commandstream-property-ado.md) -Eigenschaft, eine neue Zeichenfolge zuweisen der **WillExecute** _Quelle_ Änderung der Quelle des Parameters der **Befehl**. Die **' CommandStream '** Eigenschaft gelöscht und die [CommandText-Eigenschaft (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md) Eigenschaft wird mit der neuen Quelle aktualisiert werden. Anhand des ursprünglichen Streams **' CommandStream '** veröffentlicht und kann nicht zugegriffen werden.  
  
 Wenn die ursprüngliche Einstellung der Dialekt, der die neue Quellzeichenfolge unterscheidet die [Dialect-Eigenschaft](../../../ado/reference/ado-api/dialect-property.md) Eigenschaft (die entsprach, um die **' CommandStream '** ), durch Festlegen der richtigen Dialekt angegeben werden die **Dialekt** Eigenschaft des Befehlsobjekts auf die verwiesen wird durch *pCommand*.  
  
## <a name="see-also"></a>Siehe auch  
 [ADO-Ereignismodell – Beispiel (VC++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO-Ereignishandler – Zusammenfassung](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Connection-Objekt (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
