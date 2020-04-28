---
title: 'ADO-Ereignis Instanziierung: ADO und wfc | Microsoft-Dokumentation'
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
ms.openlocfilehash: 7dbbbf92c751093d2a7333b7ac1f76888d41d345
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "70212339"
---
# <a name="ado-event-instantiation-ado-and-wfc"></a>ADO-Ereignisinstanziierung: ADO und WFC
ADO für Windows Foundation Classes (ADO/WFC) baut auf dem ADO-Ereignis Modell auf und stellt eine vereinfachte Anwendungsprogrammierschnittstelle dar. Im allgemeinen fängt ADO/WFC ADO-Ereignisse ab, konsolidiert die Ereignis Parameter in einer einzelnen Ereignisklasse und ruft dann Ihren Ereignishandler auf.  
  
### <a name="to-use-ado-events-in-adowfc"></a>So verwenden Sie ADO-Ereignisse in ADO/WFC  
  
1.  Definieren Sie einen eigenen Ereignishandler, um ein Ereignis zu verarbeiten. Wenn Sie z. b. das **ConnectComplete** -Ereignis in der **ConnectionEvent** -Familie verarbeiten möchten, können Sie diesen Code verwenden:  
  
    ```  
    public void onConnectComplete(Object sender,ConnectionEvent e)  
    {  
        System.out.println("onConnectComplete:" + e);  
    }  
    ```  
  
2.  Definieren Sie ein Handlerobjekt, das Ihren Ereignishandler darstellt. Das Handlerobjekt muss vom Datentyp **ConnectEventHandler** für ein Ereignis des Typs **ConnectionEvent**oder der Datentyp **RecordsetEventHandler** für ein Ereignis vom Typ **RecordsetEvent**sein. Beispielsweise können Sie Folgendes für Ihren **ConnectComplete** -Ereignishandler programmieren:  
  
    ```  
    ConnectionEventHandler handler =   
        new ConnectionEventHandler(this, "onConnectComplete");  
    ```  
  
     Das erste Argument des **ConnectionEventHandler** -Konstruktors ist ein Verweis auf die-Klasse, die den Ereignishandler mit dem Namen im zweiten Argument enthält.  
  
3.  Fügen Sie den Ereignishandler einer Liste von Handlern hinzu, die für die Verarbeitung eines bestimmten Ereignis Typs vorgesehen sind. Verwenden Sie die-Methode mit einem Namen wie z. b. " **addOn**_EventName_(*Handler*)".  
  
4.  ADO/WFC implementiert intern alle ADO-Ereignishandler. Daher wird ein Ereignis, das durch einen **Verbindungs** -oder **recordsetvorgang** verursacht wurde, von einem ADO/WFC-Ereignishandler abgefangen.  
  
     Der ADO/WFC-Ereignishandler übergibt ADO **ConnectionEvent** -Parameter in einer Instanz der ADO/WFC **ConnectionEvent** -Klasse oder ADO **recordstitevent** -Parameter in einer Instanz der ADO/WFC **recordmentevent** -Klasse. Diese ADO/WFC-Klassen konsolidieren die ADO-Ereignis Parameter. Das heißt, jede ADO/WFC-Klasse enthält einen Datenmember für jeden eindeutigen Parameter in allen ADO **ConnectionEvent** -oder **recordmentevent** -Methoden.  
  
5.  ADO/WFC ruft dann Ihren Ereignishandler mit dem ADO/WFC-Ereignis Objekt auf. Der **onConnectComplete** -Handler hat z. b. eine Signatur wie die folgende:  
  
    ```  
    public void onConnectComplete(Object sender,ConnectionEvent e)  
    ```  
  
     Das erste Argument ist der Typ des Objekts, das das Ereignis gesendet hat ([Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) oder [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)), und das zweite Argument ist das ADO/WFC-Ereignis Objekt (**ConnectionEvent** oder **RecordsetEvent**).  
  
     Die Signatur des Ereignis Handlers ist einfacher als ein ADO-Ereignis. Sie müssen jedoch weiterhin das ADO-Ereignis Modell verstehen, um zu wissen, welche Parameter für ein Ereignis gelten und wie Sie reagieren.  
  
6.  Kehren Sie vom Ereignishandler zum ADO/WFC-Handler für das ADO-Ereignis zurück. ADO/WFC kopiert relevante ADO/WFC-ereignisdatenmember zurück in die ADO-Ereignis Parameter, und dann gibt der ADO-Ereignishandler zurück.  
  
7.  Wenn die Verarbeitung abgeschlossen ist, entfernen Sie den Handler aus der Liste der ADO/WFC-Ereignishandler. Verwenden Sie die-Methode mit einem Namen wie **RemoveOn**_EventName_(*Handler*).  
  
## <a name="see-also"></a>Weitere Informationen  
 [ADO-Ereignis Handler-Zusammenfassung](../../../ado/guide/data/ado-event-handler-summary.md)   
 [ADO-WFC-Syntax Index](../../../ado/reference/ado-api/ado-wfc-syntax-index.md)   
 [Ereignis Parameter](../../../ado/guide/data/event-parameters.md)   
 [Zusammenarbeiten von Ereignis Handlern](../../../ado/guide/data/how-event-handlers-work-together.md)   
 [Ereignis Typen](../../../ado/guide/data/types-of-events.md)
