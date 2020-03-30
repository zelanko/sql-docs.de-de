---
title: Methode „valueOf“ (java.sql.Timestamp, int) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 114f55af-62ab-4c60-8724-0affbbbbbcdc
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c13438851fdc543a3567abdc001af5b5b9e726fc
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "68001557"
---
# <a name="valueof-method-javasqltimestamp-int"></a>valueOf-Methode (java.sql.Timestamp, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Erstellt ein **DateTimeOffset**-Objekt, das einen Zeitpunkt in einem bestimmten Offset von GMT darstellt, wenn ein java.sql.Timestamp-Wert sowie ein den Offset in Minuten angegebener Wert gegeben ist.  
  
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
 Gibt ein DateTimeOffset-Objekt zurück, das den vom java.sql.Timestamp-Objekt gegebenen Zeitpunkt zum gegebenen Offset in Minuten ausgehend von GMT darstellt  
  
## <a name="see-also"></a>Weitere Informationen  
 [DateTimeOffset-Klasse](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [DateTimeOffset-Elemente](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
