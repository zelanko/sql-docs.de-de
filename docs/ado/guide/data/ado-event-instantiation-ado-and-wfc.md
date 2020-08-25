---
description: 'ADO-Ereignisinstanziierung: ADO und WFC'
title: 'ADO-Ereignis Instanziierung: ADO und wfc | Microsoft-Dokumentation'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 9ee4be21-657b-407a-afa4-0b27a6b096ce
author: rothja
ms.author: jroth
ms.openlocfilehash: 98719e10e837b83ac522743e120f037b1fedbd99
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88806450"
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
  
     Das erste Argument ist der Typ des Objekts, das das Ereignis gesendet hat ([Verbindung](../../reference/ado-api/connection-object-ado.md) oder [Recordset](../../reference/ado-api/recordset-object-ado.md)), und das zweite Argument ist das ADO/WFC-Ereignis Objekt (**ConnectionEvent** oder **RecordsetEvent**).  
  
     Die Signatur des Ereignis Handlers ist einfacher als ein ADO-Ereignis. Sie müssen jedoch weiterhin das ADO-Ereignis Modell verstehen, um zu wissen, welche Parameter für ein Ereignis gelten und wie Sie reagieren.  
  
6.  Kehren Sie vom Ereignishandler zum ADO/WFC-Handler für das ADO-Ereignis zurück. ADO/WFC kopiert relevante ADO/WFC-ereignisdatenmember zurück in die ADO-Ereignis Parameter, und dann gibt der ADO-Ereignishandler zurück.  
  
7.  Wenn die Verarbeitung abgeschlossen ist, entfernen Sie den Handler aus der Liste der ADO/WFC-Ereignishandler. Verwenden Sie die-Methode mit einem Namen wie **RemoveOn**_EventName_(*Handler*).  
  
## <a name="see-also"></a>Weitere Informationen  
 [ADO-Ereignis Handler-Zusammenfassung](./ado-event-handler-summary.md)   
 [ADO-WFC-Syntax Index](../../reference/ado-api/ado-wfc-syntax-index.md)   
 [Ereignis Parameter](./event-parameters.md)   
 [Zusammenarbeiten von Ereignis Handlern](./how-event-handlers-work-together.md)   
 [Ereignistypen](./types-of-events.md)