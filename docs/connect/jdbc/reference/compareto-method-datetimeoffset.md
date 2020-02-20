---
title: compareTo-Methode (DateTimeOffset) | Microsoft-Dokumentation
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
ms.openlocfilehash: 3f70413a7624b9bbd380a664fbf61b9a33f8989b
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67955518"
---
# <a name="compareto-method-datetimeoffset"></a>compareTo-Methode (DateTimeOffset)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Vergleicht dieses **DateTimeOffset**-Objekt mit einem anderen **DateTimeOffset**-Objekt basierend auf deren Zeit in GMT.  
  
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
|0|Beide **DateTimeOffset**-Objekte stellen denselben Zeitpunkt dar.|  
|Negative Zahl|Dieses**DateTimeOffset**-Objekt stellt einen vor *other* liegenden Zeitpunkt dar.|  
|Positive Zahl|Dieses**DateTimeOffset**-Objekt stellt einen nach *other* liegenden Zeitpunkt dar.|  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn zwei **DateTimeOffset**-Objekte dieselbe Uhrzeit nach GMT haben, werden die Objekte nicht zusätzlich nach Offset geordnet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [DateTimeOffset-Klasse](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset-Elemente](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
