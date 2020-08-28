---
description: ExecuteComplete-Ereignis (ADO)
title: ExecuteComplete-Ereignis (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 36e27f8a86fce348dbf2061a1c7be91f43be9adc
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88973391"
---
# <a name="executecomplete-event-ado"></a>ExecuteComplete-Ereignis (ADO)
Das **ExecuteComplete** -Ereignis wird aufgerufen, nachdem die Ausführung eines Befehls abgeschlossen wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
ExecuteComplete RecordsAffected, pError, adStatus, pCommand, pRecordset, pConnection  
```  
  
#### <a name="parameters"></a>Parameter  
 *RecordsAffected*  
 Ein **langer** Wert, der die Anzahl der vom Befehl betroffenen Datensätze angibt.  
  
 *pError*  
 Ein [Fehler](../../../ado/reference/ado-api/error-object.md) Objekt. Es wird der Fehler beschrieben, der aufgetreten ist, wenn der Wert von **adStatus** **adstatuserrorsoccurrred**ist. Andernfalls ist es nicht festgelegt.  
  
 *adStatus*  
 Ein [eventstatusenum](../../../ado/reference/ado-api/eventstatusenum.md) -Statuswert. Wenn dieses Ereignis aufgerufen wird, wird dieser Parameter auf **adstatuusok** festgelegt, wenn der Vorgang, der das Ereignis verursacht hat, erfolgreich war, oder auf **adstatuuserrorsoccurrred** , wenn der Vorgang fehlgeschlagen ist.  
  
 Bevor dieses Ereignis zurückkehrt, legen Sie diesen Parameter auf **adStatus-unwantedevent** fest, um nachfolgende Benachrichtigungen zu verhindern.  
  
 *pCommand*  
 Das [Befehls](../../../ado/reference/ado-api/command-object-ado.md) Objekt, das ausgeführt wurde. Enthält ein **Befehls** Objekt, auch wenn **Connection.Exe"niedlich** " oder " **Recordset. Open** " aufgerufen wird, ohne explizit einen **Befehl**zu erstellen. in diesem Fall wird das **Befehls** Objekt intern von ADO erstellt.  
  
 *pRecordset*  
 Ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt, das das Ergebnis des ausgeführten Befehls ist. Das **Recordset** ist möglicherweise leer. Dieses Recordset-Objekt sollte in diesem Ereignishandler niemals zerstört werden. Dies führt zu einer Zugriffsverletzung, wenn ADO versucht, auf ein Objekt zuzugreifen, das nicht mehr vorhanden ist.  
  
 *pConnection*  
 Ein [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekt. Die Verbindung, über die der Vorgang ausgeführt wurde.  
  
## <a name="remarks"></a>Bemerkungen  
 Ein **ExecuteComplete** -Ereignis kann aufgrund der **Verbindung auftreten.** [Führen](../../../ado/reference/ado-api/execute-method-ado-connection.md)Sie den **Befehl aus.** [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md), **Recordset.** [Open](../../../ado/reference/ado-api/open-method-ado-recordset.md), **Recordset.** Die [Anforderung](../../../ado/reference/ado-api/requery-method.md)oder das **Recordset.** [NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md) -Methoden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für das ADO-Ereignis Modell (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO-Ereignishandler – Übersicht](../../../ado/guide/data/ado-event-handler-summary.md)
