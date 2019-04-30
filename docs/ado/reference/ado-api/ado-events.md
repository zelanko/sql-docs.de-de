---
title: ADO-Ereignisse | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- events [ADO]
- ADO, events
ms.assetid: 0ded5ad9-8f83-4224-95af-38512783b972
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 50bdb3117b01d68f03208d6db501d44f05a849ce
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63248937"
---
# <a name="ado-events"></a>ADO-Ereignisse

|||  
|-|-|  
|[BeginTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|Wird aufgerufen, nachdem die **BeginTrans** Vorgang.|  
|[CommitTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|Wird aufgerufen, nachdem die **CommitTrans** Vorgang.|  
|[ConnectComplete](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|Wird aufgerufen, nachdem eine Verbindung gestartet.|  
|[Trennen](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|Wird aufgerufen, nachdem eine Verbindung beendet wird.|  
|[EndOfRecordset](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|Wird aufgerufen, wenn es versucht wird, wechseln auf eine Zeile nach dem Ende der **Recordset**.|  
|[ExecuteComplete](../../../ado/reference/ado-api/executecomplete-event-ado.md)|Wird aufgerufen, nachdem ein Befehl beendet wurde.|  
|[FetchComplete](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|Wird aufgerufen, nachdem alle Datensätze in einer langen asynchronen Operation in abgerufen wurden die **Recordset**.|  
|[FetchProgress](../../../ado/reference/ado-api/fetchprogress-event-ado.md)|Wird aufgerufen, in regelmäßigen Abständen während einer langen asynchronen Operation zu melden, wie viele Zeilen in das aktuell abgerufen wurden die **Recordset**.|  
|[FieldChangeComplete](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Wird aufgerufen, nachdem der Wert von einem oder mehreren **Feld** -Quellobjekten geändert wurde.|  
|[InfoMessage](../../../ado/reference/ado-api/infomessage-event-ado.md)|Wird aufgerufen, wenn eine Warnung ausgegeben, während wird eine **ConnectionEvent** Vorgang.|  
|[MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|Wird aufgerufen, nachdem die aktuelle Position in der **Recordset** Änderungen.|  
|[RecordChangeComplete](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Wird aufgerufen, nach einem oder mehreren Datensätzen ändern.|  
|[RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|Wird aufgerufen, nachdem die **Recordset** hat sich geändert.|  
|[RollbackTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|Wird aufgerufen, nachdem die **RollbackTrans** Vorgang.|  
|[WillChangeField](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Wird aufgerufen, bevor Sie ein ausstehender Vorgang ändert sich den Wert einer oder mehreren **Feld** Objekte in der **Recordset**.|  
|[WillChangeRecord](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Wird aufgerufen, bevor eine oder mehrere von Datensätzen (Zeilen) in der **Recordset** ändern.|  
|[WillChangeRecordset](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|Wird aufgerufen, bevor Sie ein ausstehender Vorgang ändert die **Recordset**.|  
|[WillConnect](../../../ado/reference/ado-api/willconnect-event-ado.md)|Wird aufgerufen, bevor eine Verbindung gestartet wird.|  
|[WillExecute](../../../ado/reference/ado-api/willexecute-event-ado.md)|Wird aufgerufen, kurz bevor ein ausstehenden Befehls für diese Verbindung führt aus und gibt dem Benutzer die Möglichkeit zum Überprüfen und ändern die ausstehende Ausführung-Parameter.|  
|[WillMove](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|Die **WillMove** -Ereignis wird aufgerufen, *vor* ein ausstehender Vorgang ändert die aktuelle Position in der **Recordset**.|  
  
## <a name="see-also"></a>Siehe auch  
 [ADO-API-Referenz](../../../ado/reference/ado-api/ado-api-reference.md)   
 [ADO-Collections](../../../ado/reference/ado-api/ado-collections.md)   
 [ADO – dynamische Eigenschaften](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [ADO – Enumerationskonstanten](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Anhang B: ADO-Fehler](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [Behandeln von ADO-Ereignissen](../../../ado/guide/data/handling-ado-events.md)   
 [ADO-Methoden](../../../ado/reference/ado-api/ado-methods.md)   
 [ADO-Objektmodell](../../../ado/reference/ado-api/ado-object-model.md)   
 [ADO-Objekte und Schnittstellen](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [ADO-Eigenschaften](../../../ado/reference/ado-api/ado-properties.md)
