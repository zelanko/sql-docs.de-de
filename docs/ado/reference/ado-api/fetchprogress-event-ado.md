---
title: FetchProgress-Ereignis (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FetchProgress
- Recordset::FetchProgress
helpviewer_keywords:
- FetchProgress event [ADO]
ms.assetid: 301716fd-81fc-40eb-8a04-221ef7ab410e
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 88f5fafb3bc6f4a244d642c0ca18204977a79161
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35278499"
---
# <a name="fetchprogress-event-ado"></a>FetchProgress-Ereignis (ADO)
Die **FetchProgress**Ereignis wird aufgerufen, in regelmäßigen Abständen während eines längeren asynchronen Vorgangs gemeldet wird, wie viele weitere Zeilen derzeit in abgerufen wurden die [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
FetchProgress Progress, MaxProgress, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>Parameter  
 *Status*  
 Ein **lange** Wert, der angibt, der Anzahl der Datensätze, die derzeit von der Abrufvorgang abgerufen wurden.  
  
 *MaxProgress*  
 Ein **lange** Wert, der angibt, die maximalen Anzahl von Datensätzen abgerufen werden soll.  
  
 *adStatus*  
 Ein [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) Statuswert.  
  
 *pRecordset*  
 Ein **Recordset** -Objekt, das das Objekt ist für das die Einträge abgerufen werden.  
  
## <a name="remarks"></a>Hinweise  
 Bei Verwendung **FetchProgress** mit einem untergeordneten **Recordset**, beachten Sie, die *Status* und *MaxProgress* Parameterwerte werden abgeleitet. aus der zugrunde liegenden [Cursordiensts](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) Rowset. Die zurückgegebenen Werte stellen die Gesamtanzahl von Datensätzen in der zugrunde liegenden Rowset, nicht nur die Anzahl der Datensätze in der aktuellen Kapitel dar.  
  
> [!NOTE]
>  Mit **FetchProgress** mit Microsoft Visual Basic, Visual Basic 6.0 oder höher ist erforderlich.  
  
## <a name="see-also"></a>Siehe auch  
 [ADO-Ereignisse Modell (VC++-Beispiel)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO-Ereignishandler – Zusammenfassung](../../../ado/guide/data/ado-event-handler-summary.md)
