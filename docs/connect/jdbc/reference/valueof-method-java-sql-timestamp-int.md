---
title: ValueOf-Methode (java.sql.Timestamp, Int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 114f55af-62ab-4c60-8724-0affbbbbbcdc
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 290878fc0a3687a95fd6335eba4b6ed6e1c2fda2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32848885"
---
# <a name="valueof-method-javasqltimestamp-int"></a>valueOf-Methode (java.sql.Timestamp, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Erstellt eine **"DateTimeOffset"** Objekt, einen Zeitpunkt in einem bestimmten Offset von GMT erhält ein java.sql.Timestamp-Wert und einen Wert, der angibt, der des Offsets in Minuten darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public static DateTimeOffset valueOf(java.sql.Timestamp timestamp, int minutesOffset)  
```  
  
#### <a name="parameters"></a>Parameter  
 *timestamp*  
  
 Einjava.sql.Timestamp-Wert.  
  
 *minutesOffset*  
  
 Das Offset in Minuten.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt ein "DateTimeOffset"-Objekt, das den Zeitpunkt gegebenen Zeitpunkt vom java.sql.Timestamp-Objekt am angegebenen Offset in Minuten von GMT darstellt.  
  
## <a name="see-also"></a>Siehe auch  
 ["DateTimeOffset"-Klasse](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset-Elemente](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
