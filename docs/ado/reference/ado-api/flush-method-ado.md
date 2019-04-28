---
title: Flush-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Flush
- _Stream::raw_Flush
helpviewer_keywords:
- Flush method [ADO]
ms.assetid: 938522b4-f836-4c80-8d27-a598a000f0ee
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 66deae3833a738075259928855881f87b64ef0dd
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63028112"
---
# <a name="flush-method-ado"></a>Flush-Methode (ADO)
Erzwingt, dass der Inhalt der [Stream](../../../ado/reference/ado-api/stream-object-ado.md) im ADO-Puffer auf das zugrunde liegende Objekt mit dem verbleibenden der **Stream** zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Stream.Flush  
```  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode kann verwendet werden, um den Inhalt des Streampuffers an das zugrunde liegende Objekt zu senden: z. B. den Knoten oder eine Datei, die von der URL, die die Quelle des dargestellt die **Stream** Objekt. Diese Methode aufgerufen werden soll, wenn Sie möchten sicherstellen, dass alle Änderungen, die vorgenommen, um den Inhalt einer **Stream** geschrieben wurden. Mit ADO es ist jedoch nicht in der Regel notwendig, **leeren**, wie ADO kontinuierlich den Puffer so weit wie möglich im Hintergrund leert. Änderungen an den Inhalt des eine **Stream** erfolgt automatisch, nicht zwischengespeichert, bis **leeren** aufgerufen wird.  
  
 Schließen einer **Stream** mit der [schließen](../../../ado/reference/ado-api/close-method-ado.md) Methode leert den Inhalt des eine **Stream** automatisch; es ist nicht erforderlich, explizit aufzurufen **leeren**unmittelbar vor dem **schließen**.  
  
## <a name="applies-to"></a>Gilt für  
 [Stream-Objekt (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
