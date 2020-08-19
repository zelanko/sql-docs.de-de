---
description: EventStatusEnum
title: EventStatus usenum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EventStatusEnum
helpviewer_keywords:
- EventStatusEnum enumeration [ADO]
ms.assetid: ebfd4cda-4017-4873-9d28-38b1c7db12a8
author: rothja
ms.author: jroth
ms.openlocfilehash: 3d696d7b971b5f6624a85addb3f023f2090ac90d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443902"
---
# <a name="eventstatusenum"></a>EventStatusEnum
Gibt den aktuellen Status der Ausführung eines Ereignisses an.  
  
|Konstant|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adStatus Cancel**|4|Fordert den Abbruch des Vorgangs an, durch den das Ereignis aufgetreten ist.|  
|**adStatus-kandeny**|3|Gibt an, dass der Vorgang keinen Abbruch des ausstehenden Vorgangs anfordern kann.|  
|**adstatuuserrorsoccurrred**|2|Gibt an, dass der Vorgang, der das Ereignis verursacht hat, aufgrund eines Fehlers oder Fehlers fehlgeschlagen ist.|  
|**adStatus**|1|Gibt an, dass der Vorgang, der das Ereignis ausgelöst hat, erfolgreich war.|  
|**adStatus-unwantedebug**|5|Verhindert nachfolgende Benachrichtigungen, bevor die Ausführung der Ereignismethode abgeschlossen ist.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstant|  
|--------------|  
|Adoerums. EventStatus. Cancel|  
|Adoerums. EventStatus. cantdeny|  
|Adoerums. EventStatus. errorsoccurrred|  
|Adoerums. EventStatus. OK|  
|Adoerums. EventStatus. unwantedevent|  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [BeginTransComplete-, CommitTransComplete-und RollbackTransComplete-Ereignis (ADO)](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)  

        [ConnectComplete- und Disconnect-Ereignis (ADO)](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)  

        [EndOfRecordset-Ereignis (ADO)](../../../ado/reference/ado-api/endofrecordset-event-ado.md)  

        [ExecuteComplete-Ereignis (ADO)](../../../ado/reference/ado-api/executecomplete-event-ado.md)  
    :::column-end:::
    :::column:::
        [FetchComplete-Ereignis (ADO)](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)  

        [InfoMessage-Ereignis (ADO)](../../../ado/reference/ado-api/infomessage-event-ado.md)  

        [WillChangeField- und FieldChangeComplete-Ereignis (ADO)](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)  

        [WillChangeRecord- und RecordChangeComplete-Ereignis (ADO)](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)  
    :::column-end:::
    :::column:::
        [WillChangeRecordset- und RecordsetChangeComplete-Ereignis (ADO)](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)  

        [WillConnect-Ereignis (ADO)](../../../ado/reference/ado-api/willconnect-event-ado.md)  

        [WillExecute-Ereignis (ADO)](../../../ado/reference/ado-api/willexecute-event-ado.md)  

        [WillMove- und MoveComplete-Ereignis (ADO)](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)  
    :::column-end:::
:::row-end:::
