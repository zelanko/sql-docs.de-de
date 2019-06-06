---
title: ExecuteComplete-Ereignis (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection::ExecuteComplete
- ExecuteComplete
helpviewer_keywords:
- ExecuteComplete event [ADO]
ms.assetid: 62470d42-e511-494c-bec4-ad4591734b7b
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: df6437e80ab746a7d6aa219fb3299cb54712b5c3
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66697902"
---
# <a name="executecomplete-event-ado"></a>ExecuteComplete-Ereignis (ADO)
Die **ExecuteComplete** Ereignis wird immer dann aufgerufen, nachdem ein Befehl beendet wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
ExecuteComplete RecordsAffected, pError, adStatus, pCommand, pRecordset, pConnection  
```  
  
#### <a name="parameters"></a>Parameter  
 *RecordsAffected*  
 Ein **lange** Wert, der angibt, der Anzahl der Datensätze, die von dem Befehl betroffen sind.  
  
 *pError*  
 Ein [Fehler](../../../ado/reference/ado-api/error-object.md) Objekt. Es wird beschrieben, den aufgetretenen Wenn der Wert des **AdStatus** ist **AdStatusErrorsOccurred**; andernfalls ist es nicht festgelegt.  
  
 *adStatus*  
 Ein [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) Statuswert. Wenn dieses Ereignis aufgerufen wird, wird dieser Parameter festgelegt, um **AdStatusOK** , wenn der Vorgang, der das Ereignis ausgelöst wurde erfolgreich war, oder mit **AdStatusErrorsOccurred** bei fehlgeschlagenem Vorgang.  
  
 Bevor Sie dieses Ereignis zurückgegeben wird, legen Sie diesen Parameter auf **AdStatusUnwantedEvent** , nachfolgende Benachrichtigungen zu verhindern.  
  
 *pCommand*  
 Die [Befehl](../../../ado/reference/ado-api/command-object-ado.md) -Objekt, das ausgeführt wurde. Enthält eine **Befehl** -Objekt, selbst wenn **Connection.Execute** oder **Recordset.Open** ohne explizite Erstellung einer **Befehl** , in welchen Fällen die **Befehl** objekterstellung wird intern von ADO.  
  
 *pRecordset*  
 Ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt, das das Ergebnis des ausgeführten Befehls ist. Dies **Recordset** kann leer sein. Sie sollten dieses Recordsetobjekt innerhalb dieser Ereignishandler nicht zerstört. Dies führt zu einer Zugriffsverletzung beim ADO versucht, Zugriff auf ein Objekt, das nicht mehr vorhanden ist.  
  
 *pConnection*  
 Ein [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt. Die Verbindung, über die Sie der Vorgang ausgeführt wurde.  
  
## <a name="remarks"></a>Hinweise  
 Ein **ExecuteComplete** Ereignis kann auftreten, aufgrund der **Verbindung.** [Ausführen](../../../ado/reference/ado-api/execute-method-ado-connection.md), **Befehl.** [Ausführen](../../../ado/reference/ado-api/execute-method-ado-command.md), **Recordset.** [Öffnen](../../../ado/reference/ado-api/open-method-ado-recordset.md), **Recordset.** [Requery](../../../ado/reference/ado-api/requery-method.md), oder **Recordset.** [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md) Methoden.  
  
## <a name="see-also"></a>Siehe auch  
 [ADO-Ereignismodell – Beispiel (VC++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO-Ereignishandler – Zusammenfassung](../../../ado/guide/data/ado-event-handler-summary.md)
