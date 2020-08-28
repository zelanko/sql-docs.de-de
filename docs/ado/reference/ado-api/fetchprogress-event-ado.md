---
description: FetchProgress-Ereignis (ADO)
title: FetchProgress-Ereignis (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: b84b963f42c83191c613dbb4849288fc862df474
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88973331"
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
