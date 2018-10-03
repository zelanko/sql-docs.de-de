---
title: ADO-Ereignishandler – Zusammenfassung | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- events [ADO], about event handlers
- event handlers [ADO]
ms.assetid: b34f4472-5e04-4a2c-ab64-38d6eca31a69
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2398da9dde430d18aad38dd03cfc2816978b571c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47828328"
---
# <a name="ado-connection-and-recordset-events"></a>ADO-Verbindung und Recordsetereignisse
ADO-Objekte, die zwei Ereignisse auslösen können: die [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt und die [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt. Die **ConnectionEvent** Familie bezieht sich auf die Vorgänge auf den **Verbindung** -Objekt, und die **RecordsetEvent** Familie bezieht sich auf die Vorgänge auf die  **Recordset** Objekt.

-   **Verbindungsereignisse**: Ereignisse werden ausgegeben, wenn eine Transaktion für eine Verbindung beginnt, wird ein Commit ausgeführt oder ein Rollback, wenn ausgeführt wird eine [Befehl](../../../ado/reference/ado-api/command-object-ado.md) ausgeführt wird; beim Auftreten einer Warnung bei der ein **Verbindungsereignis**-Vorgang. oder wenn eine **Verbindung** beginnt oder endet.

-   **Recordset-Ereignisse**: Ereignisse werden ausgegeben, um asynchrone Abrufvorgänge auch beim Navigieren durch die Zeilen der einen **Recordset** Objekt, das Ändern eines Felds in einer Zeile eine **Recordset**, Ändern eine Zeile in eine **Recordset**öffnen eine **Recordset** mit einem serverseitigen Cursor zu schließen eine **Recordset**, oder überhaupt im Ändern der  **Recordset**.

 Die folgenden Tabellen fassen die Ereignisse und deren Beschreibungen.

|ConnectionEvent|Description|
|---------------------|-----------------|
|[BeginTransComplete-, CommitTransComplete, RollbackTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|**Verwalten von Transaktionen** – Benachrichtigung, die für die Verbindung die aktuelle Transaktion gestartet wurde, ein Commit oder Rollback ausgeführt.|
|[WillConnect](../../../ado/reference/ado-api/willconnect-event-ado.md), [ConnectComplete, trennen](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|**Verbindungsverwaltung** – Benachrichtigung, die die aktuelle Verbindung gestartet werden kann, wurde gestartet oder beendet wurde.|
|[WillExecute](../../../ado/reference/ado-api/willexecute-event-ado.md), [ExecuteComplete](../../../ado/reference/ado-api/executecomplete-event-ado.md)|**Verwaltung der Ausführung Befehl** – Benachrichtigung, dass die Ausführung des aktuellen Befehls für die Verbindung wird gestartet oder beendet wurde.|
|[InfoMessage](../../../ado/reference/ado-api/infomessage-event-ado.md)|**Nur zu Informationszwecken** – Benachrichtigung, dass zusätzliche Informationen zu den aktuellen Vorgang.|

|RecordsetEvent|Description|
|--------------------|-----------------|
|[FetchProgress](../../../ado/reference/ado-api/fetchprogress-event-ado.md), [FetchComplete](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|**Abrufen von Status** – Benachrichtigung über den Fortschritt von einem Datenabrufvorgang oder, dass der Vorgang abgeschlossen wurde. Diese Ereignisse sind nur verfügbar wenn die **Recordset** mit einem clientseitigen Cursor geöffnet wurde.|
|[WillChangeField, FieldChangeComplete](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|**Feld Change Management** – Benachrichtigung, die der Wert des aktuellen Felds geändert wird oder wurde geändert.|
|[WillMove-, MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md), [EndOfRecordset](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|**Verwaltung der Navigation** – Benachrichtigung, die die aktuelle Zeile zu positionieren, in einem **Recordset** geändert wird, hat sich geändert oder das Ende erreicht hat die **Recordset**.|
|[WillChangeRecord, RecordChangeComplete](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|**Change Management Zeile** – Benachrichtigung, dass etwas in der aktuellen Zeile die **Recordset** geändert wird oder wurde geändert.|
|[WillChangeRecordset, RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|**Recordset-Change Management** – Benachrichtigung, dass etwas in der aktuellen **Recordset** geändert wird oder wurde geändert.|

## <a name="see-also"></a>Siehe auch
 [ADO-Ereignisinstanziierung nach Sprache](../../../ado/guide/data/ado-event-instantiation-by-language.md) [ADO-Ereignissen](../../../ado/reference/ado-api/ado-events.md) [Ereignisparameter](../../../ado/guide/data/event-parameters.md) [Zusammenwirken der Ereignishandler](../../../ado/guide/data/how-event-handlers-work-together.md) [Arten von Ereignissen](../../../ado/guide/data/types-of-events.md)
