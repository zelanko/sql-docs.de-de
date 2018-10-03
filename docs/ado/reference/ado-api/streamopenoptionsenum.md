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
manager: craigg
ms.openlocfilehash: a1e7e685e9d3f23d4d1c3317e24f63d7bdac23db
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47730278"
---
# <a name="streamopenoptionsenum"></a>StreamOpenOptionsEnum
Gibt Optionen zum Öffnen einer [Stream](../../../ado/reference/ado-api/stream-object-ado.md) Objekt. Die Werte können mit einer OR-Operation kombiniert werden.  
  
|Konstante|value|Description|  
|--------------|-----------|-----------------|  
|**adOpenStreamAsync**|1|Öffnet die **Stream** Objekt im asynchronen Modus ausgeführt.|  
|**adOpenStreamFromRecord**|4|Identifiziert den Inhalt der *Quelle* Parameter einen Parameter eines bereits geöffneten [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) Objekt. Das Standardverhalten ist, behandeln *Quelle* als eine URL, die direkt auf einen Knoten in einer Struktur verweist. Die diesem Knoten zugeordnete Standarddatenstrom wird geöffnet.|  
|**adOpenStreamUnspecified**|-1|Standard. Gibt an, öffnen die **Stream** Objekt mit den Standardoptionen.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Diese Konstanten keine ADO/WFC-Entsprechungen.  
  
## <a name="applies-to"></a>Gilt für  
 [Open-Methode (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)
