---
title: CompareTo-Methode (DateTimeOffset) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e4cf2ea4-0fe9-40ce-ba79-f2a2b616997e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 04f19f08deda9cd42affa0a5ced28255c1bb521b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47742928"
---
# <a name="compareto-method-datetimeoffset"></a>compareTo-Methode (DateTimeOffset)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Vergleicht diese **DateTimeOffset** Objekt in ein anderes **DateTimeOffset** -Objekt basierend auf der Uhrzeit nach GMT.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public int compareTo(DateTimeOffset other)  
```  
  
#### <a name="parameters"></a>Parameter  
 Ein [DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)-Wert, der mit der aktuellen Instanz verglichen werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 In der folgenden Tabelle wird der Rückgabewert für diese Methode beschrieben:  
  
|Rückgabewert|Beschreibung|  
|------------------|-----------------|  
|0|Beide **DateTimeOffset** Objekte den gleichen Zeitpunkt darstellen.|  
|Negative Zahl|Dies **DateTimeOffset** Objekt einen Zeitpunkt darstellt, die vor dem *andere*.|  
|Positive Zahl|Dies **DateTimeOffset** Objekt einen Zeitpunkt darstellt, die nach dem *andere*.|  
  
## <a name="remarks"></a>Remarks  
 Wenn zwei **DateTimeOffset**-Objekte dieselbe Uhrzeit nach GMT haben, werden die Objekte nicht zusätzlich nach Offset geordnet.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [DateTimeOffset-Klasse](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset-Elemente](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
