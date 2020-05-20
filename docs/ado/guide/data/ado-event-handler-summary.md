---
title: Übersicht über ADO-Ereignis Handler | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 78c3b19c63025bc77862e7f88f6c4d83350c0313
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82761366"
---
# <a name="ado-connection-and-recordset-events"></a>ADO-Verbindung und Recordset-Ereignisse
Zwei ADO-Objekte können Ereignisse hervorrufen: das [Verbindungs](../../../ado/reference/ado-api/connection-object-ado.md) Objekt und das [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt. Die **ConnectionEvent** -Familie bezieht sich auf Vorgänge für das **Verbindungs** Objekt, und die **RecordsetEvent** -Familie bezieht sich auf Vorgänge für das **Recordset** -Objekt.

-   **Verbindungs Ereignisse**: Ereignisse werden ausgegeben, wenn eine Transaktion für eine Verbindung beginnt, ein Commit ausgeführt wird oder ein Rollback ausgeführt wird. Wenn ein [Befehl](../../../ado/reference/ado-api/command-object-ado.md) ausgeführt wird; Wenn bei einem **Verbindungs Ereignis** Vorgang eine Warnung auftritt. oder wenn eine **Verbindung** gestartet oder beendet wird.

-   **Recordset-Ereignisse**: Ereignisse werden bei asynchronen Abruf Vorgängen sowie beim Navigieren durch die Zeilen eines **recordsetzies** ausgegeben, Ändern eines Felds in einer Zeile eines **Recordsets**, Ändern einer Zeile in einem **Recordset**, Öffnen eines **Recordsets** mit einem serverseitigen Cursor, Schließen eines **Recordsets**oder vornehmen beliebiger Änderungen im **Recordset**.

 In den folgenden Tabellen werden die Ereignisse und ihre Beschreibungen zusammengefasst.

|ConnectionEvent|Beschreibung|
|---------------------|-----------------|
|[BeginTransComplete, CommitTransComplete, RollbackTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|**Transaktions Verwaltung** : Benachrichtigung, dass die aktuelle Transaktion auf der Verbindung gestartet, ein Commit oder ein Rollback ausgeführt wurde.|
|[WillConnect](../../../ado/reference/ado-api/willconnect-event-ado.md), [ConnectComplete, trennen](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|**Verbindungs Verwaltung** : Benachrichtigung, dass die aktuelle Verbindung gestartet wird, gestartet wurde oder beendet wurde.|
|[WillExecute](../../../ado/reference/ado-api/willexecute-event-ado.md), [ExecuteComplete](../../../ado/reference/ado-api/executecomplete-event-ado.md)|**Verwaltung der Befehlsausführung** : Benachrichtigung, dass die Ausführung des aktuellen Befehls auf der Verbindung gestartet oder beendet wird.|
|[Info Message](../../../ado/reference/ado-api/infomessage-event-ado.md)|**Information** : Benachrichtigung, dass zusätzliche Informationen über den aktuellen Vorgang vorhanden sind.|

|Record-tevent|Beschreibung|
|--------------------|-----------------|
|[FetchProgress](../../../ado/reference/ado-api/fetchprogress-event-ado.md), [FetchComplete](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|**Abruf Status** : Benachrichtigung über den Status eines Datenabruf Vorgangs oder, wenn der Abruf Vorgang abgeschlossen wurde. Diese Ereignisse sind nur verfügbar, wenn das **Recordset** mit einem Client seitigen Cursor geöffnet wurde.|
|[WillChangeField, FieldChangeComplete](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|**Verwaltung von Feldänderungen** : Benachrichtigung, dass sich der Wert des aktuellen Felds ändert oder geändert wurde.|
|[WillMove, MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md), [EndOf Recordset](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|**Navigations Verwaltung** : Benachrichtigung, dass sich die aktuelle Zeilen Position in einem **Recordset** ändert, geändert wurde oder das Ende des **Recordsets**erreicht hat.|
|[WillChangeRecord, RecordChangeComplete](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|**Zeilen Änderungs Verwaltung** : Benachrichtigung, dass etwas in der aktuellen Zeile des **Recordsets** geändert wird oder geändert wurde.|
|[WillChangeRecordset, RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|**Recordset Change Management** : Benachrichtigung, dass etwas im aktuellen **Recordset** geändert wird oder geändert wurde.|

## <a name="see-also"></a>Weitere Informationen
 Ereignis Parameter [für die ADO-Ereignis Instanziierung nach Sprache](../../../ado/guide/data/ado-event-instantiation-by-language.md) - [ADO-Ereignissen](../../../ado/reference/ado-api/ado-events.md) [Ereignis Parameter](../../../ado/guide/data/event-parameters.md) , [wie Ereignishandler Ereignis Typen zusammenarbeiten](../../../ado/guide/data/how-event-handlers-work-together.md) [Types of Events](../../../ado/guide/data/types-of-events.md)
