---
title: StreamOpenOptionsEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StreamOpenOptionsEnum
helpviewer_keywords:
- StreamOpenOptionsEnum enumeration [ADO]
ms.assetid: 85b6c57f-47ed-46ba-bd92-07882ae9e9d2
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 091c640ab09cf70cff5e6f7ce3d7bf1dc9dd34ab
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66710714"
---
# <a name="streamopenoptionsenum"></a>StreamOpenOptionsEnum
Gibt Optionen zum Öffnen einer [Stream](../../../ado/reference/ado-api/stream-object-ado.md) Objekt. Die Werte können mit einer OR-Operation kombiniert werden.  
  
|Konstante|Wert|Description|  
|--------------|-----------|-----------------|  
|**adOpenStreamAsync**|1|Öffnet die **Stream** Objekt im asynchronen Modus ausgeführt.|  
|**adOpenStreamFromRecord**|4|Identifiziert den Inhalt der *Quelle* Parameter einen Parameter eines bereits geöffneten [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) Objekt. Das Standardverhalten ist, behandeln *Quelle* als eine URL, die direkt auf einen Knoten in einer Struktur verweist. Die diesem Knoten zugeordnete Standarddatenstrom wird geöffnet.|  
|**adOpenStreamUnspecified**|-1|Standard. Gibt an, öffnen die **Stream** Objekt mit den Standardoptionen.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Diese Konstanten keine ADO/WFC-Entsprechungen.  
  
## <a name="applies-to"></a>Gilt für  
 [Open-Methode (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)
