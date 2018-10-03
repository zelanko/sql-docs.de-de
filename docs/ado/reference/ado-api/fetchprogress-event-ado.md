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
manager: craigg
ms.openlocfilehash: f47fb473d0120c124fd07fbb0b30bdecf991926f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47682154"
---
# <a name="fetchprogress-event-ado"></a>FetchProgress-Ereignis (ADO)
Die **FetchProgress**Ereignis wird aufgerufen, in regelmäßigen Abständen während einer langen asynchronen Operation zu melden, wie viele weitere Zeilen in das aktuell abgerufen wurden die [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
FetchProgress Progress, MaxProgress, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Parameter  
 *Status*  
 Ein **lange** Wert, der angibt, der Anzahl der Datensätze, die derzeit von der Abrufvorgang abgerufen wurden.  
  
 *MaxProgress*  
 Ein **lange** erwartet, dass Wert, der angibt, der maximale Anzahl der Datensätze abgerufen werden.  
  
 *adStatus*  
 Ein [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) Statuswert.  
  
 *pRecordset*  
 Ein **Recordset** -Objekt, das das Objekt ist für die die Datensätze abgerufen werden.  
  
## <a name="remarks"></a>Hinweise  
 Bei Verwendung **FetchProgress** mit einem untergeordneten Element **Recordset**, beachten Sie, die die *Fortschritt* und *MaxProgress* Parameterwerten abgeleitet werden aus der zugrunde liegenden [Cursordiensts](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) Rowset. Die zurückgegebenen Werte stellen die Gesamtzahl der Datensätze in der zugrunde liegenden Rowsets, nicht nur die Anzahl der Datensätze in das aktuelle Kapitel dar.  
  
> [!NOTE]
>  Verwendung von **FetchProgress** mit Microsoft Visual Basic, Visual Basic 6.0 oder höher ist erforderlich.  
  
## <a name="see-also"></a>Siehe auch  
 [ADO-Ereignismodell – Beispiel (VC++)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO-Ereignishandler – Zusammenfassung](../../../ado/guide/data/ado-event-handler-summary.md)
