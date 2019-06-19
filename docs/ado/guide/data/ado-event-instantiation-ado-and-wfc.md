---
title: 'ADO-Ereignisinstanziierung: ADO und WFC | Microsoft-Dokumentation'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 9ee4be21-657b-407a-afa4-0b27a6b096ce
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 1a4bb76e9172458c26e59dc366e8a321a548f34e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66702606"
---
# <a name="ado-event-instantiation-ado-and-wfc"></a>ADO-Ereignisinstanziierung: ADO und WFC
ADO für die Windows Foundation Classes (ADO/WFC) baut auf das ADO-Ereignismodell und stellt eine vereinfachte Application programming Interface. Im allgemeinen ADO/WFC-ADO-Ereignisse abfängt konsolidiert die Ereignisparameter in einer einzelnen Event-Klasse und ruft dann den Ereignishandler.  
  
### <a name="to-use-ado-events-in-adowfc"></a>Verwenden von ADO-Ereignissen in ADO/WFC  
  
1.  Definieren Sie einen eigenen Ereignishandler, um ein Ereignis zu verarbeiten. Angenommen, Sie verarbeiten möchten die **ConnectComplete** Ereignis in der **ConnectionEvent** Familie, Sie können diesen Code:  
  
    ```  
    public void onConnectComplete(Object sender,ConnectionEvent e)  
    {  
        System.out.println("onConnectComplete:" + e);  
    }  
    ```  
  
2.  Definieren Sie eine Handlerobjekt, um Ihren Ereignishandler darzustellen. Das Handlerobjekt muss der Datentyp **ConnectEventHandler** für ein Ereignis vom Typ **ConnectionEvent**, Datentyp oder **RecordsetEventHandler** für ein Ereignis vom Typ  **RecordsetEvent**. Z. B. den folgenden code für Ihre **ConnectComplete** -Ereignishandler:  
  
    ```  
    ConnectionEventHandler handler =   
        new ConnectionEventHandler(this, "onConnectComplete");  
    ```  
  
     Das erste Argument von der **ConnectionEventHandler** Konstruktor ist ein Verweis auf die Klasse, die den Ereignishandler mit dem Namen in das zweite Argument enthält.  
  
3.  Fügen Sie Ihrem Ereignishandler zu einer Liste von Handlern, die festgelegt werden, um einen bestimmten Typ von Ereignis zu verarbeiten. Verwenden Sie die Methode mit einem Namen, z. B. **AddOn** *EventName*(*Handler*).  
  
4.  ADO/WFC-implementiert intern die ADO-Ereignishandler. Aus diesem Grund ein Ereignis ausgelöst wurde, indem eine **Verbindung** oder **Recordset** Vorgang von einem ADO/WFC-Ereignishandler abgefangen wird.  
  
     Der ADO/WFC-Ereignishandler übergibt ADO **ConnectionEvent** Parameter in einer Instanz von der ADO/WFC **ConnectionEvent** Klassen- oder ADO **RecordsetEvent** Parameter in einer Instanz von der ADO/WFC **RecordsetEvent** Klasse. Diese Klassen ADO/WFC-konsolidieren, die ADO-Ereignis-Parameter; d. h., jede ADO/WFC-Klasse enthält einen Datenmember für jeden eindeutigen Parameter im alle ADO.NET **ConnectionEvent** oder **RecordsetEvent** Methoden.  
  
5.  ADO/WFC-ruft dann den Ereignishandler mit dem ADO/WFC-Ereignisobjekt. Angenommen, Ihre **OnConnectComplete** Handler hat eine Signatur wie folgt:  
  
    ```  
    public void onConnectComplete(Object sender,ConnectionEvent e)  
    ```  
  
     Das erste Argument ist der Typ des Objekts, das das Ereignis gesendet ([Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) oder [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)), und das zweite Argument ist das Ereignisobjekt ADO/WFC-(**ConnectionEvent** oder **RecordsetEvent**).  
  
     Die Signatur der Ereignishandler ist einfacher als ein ADO-Ereignis. Allerdings müssen Sie dennoch wissen das ADO-Ereignismodell wissen, welche Parameter für ein Ereignis gelten und wie Sie reagieren.  
  
6.  Geben Sie an der ADO/WFC-Handler für das ADO-Ereignis über den Ereignishandler zurück. ADO/WFC-kopiert relevante ADO/WFC-Event-Datenmember zurück auf die ADO-Ereignis-Parameter und gibt dann der ADO-Ereignishandler zurück.  
  
7.  Wenn Sie fertig sind Verarbeitung, entfernen Sie den Handler aus der Liste der ADO/WFC-Ereignishandler. Verwenden Sie die Methode mit einem Namen, z. B. **RemoveOn** *EventName*(*Handler*).  
  
## <a name="see-also"></a>Siehe auch  
 [ADO-Ereignishandler – Zusammenfassung](../../../ado/guide/data/ado-event-handler-summary.md)   
 [ADO / WFC-Syntaxindex](../../../ado/reference/ado-api/ado-wfc-syntax-index.md)   
 [Ereignisparameter](../../../ado/guide/data/event-parameters.md)   
 [Zusammenwirken der Ereignishandler](../../../ado/guide/data/how-event-handlers-work-together.md)   
 [Typen von Ereignissen](../../../ado/guide/data/types-of-events.md)
