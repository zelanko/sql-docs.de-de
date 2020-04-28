---
title: FetchProgress-Ereignis (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FetchProgress
- Recordset::FetchProgress
helpviewer_keywords:
- FetchProgress event [ADO]
ms.assetid: 301716fd-81fc-40eb-8a04-221ef7ab410e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ab93d8117a5fb3d2bbc95ea33bbacdc7fba3f151
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67932822"
---
# <a name="fetchprogress-event-ado"></a>FetchProgress-Ereignis (ADO)
Das **FetchProgress**-Ereignis wird in regelmäßigen Abständen aufgerufen, um zu melden, wie viele weitere Zeilen momentan in das [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)abgerufen wurden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
FetchProgress Progress, MaxProgress, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Parameter  
 *Progress*  
 Ein **langer** Wert, der die Anzahl der Datensätze angibt, die zurzeit vom Abruf Vorgang abgerufen wurden.  
  
 *Maxprogress*  
 Ein **langer** Wert, der die maximale Anzahl von Datensätzen angibt, die abgerufen werden sollen.  
  
 *adStatus*  
 Ein [eventstatusenum](../../../ado/reference/ado-api/eventstatusenum.md) -Statuswert.  
  
 *pRecordset*  
 Ein **Recordset** -Objekt, bei dem es sich um das Objekt handelt, für das die Datensätze abgerufen werden.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn Sie **FetchProgress** mit einem untergeordneten **Recordset**verwenden, beachten Sie, dass die Parameterwerte *Progress* und *maxprogress* vom zugrunde liegenden [Cursor Dienst](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) -Rowset abgeleitet werden. Die zurückgegebenen Werte stellen die Gesamtanzahl der Datensätze im zugrunde liegenden Rowset dar, nicht nur die Anzahl der Datensätze im aktuellen Kapitel.  
  
> [!NOTE]
>  Um **FetchProgress** mit Microsoft Visual Basic zu verwenden, ist Visual Basic 6,0 oder höher erforderlich.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für das ADO-Ereignis Modell (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO-Ereignishandler – Übersicht](../../../ado/guide/data/ado-event-handler-summary.md)
