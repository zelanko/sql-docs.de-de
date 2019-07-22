---
title: "\"nettresponabbuffering\"-Methode (SQLServerDataSource) | Microsoft-Dokumentation"
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setResponseBuffering(String responseBufferingValue)
apilocation:
- SQLServerDataSource.setResponseBuffering(String responseBufferingValue)
apitype: Assembly
ms.assetid: c9e43ff2-8117-4dca-982d-83c863d0c8e1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f5bfc0fb1d1a74131d0e8e71055356f958a9b508
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67973103"
---
# <a name="setresponsebuffering-method-sqlserverdatasource"></a>setResponseBuffering-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den Antwortpuffermodus für Verbindungen fest, die unter Verwendung dieses [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)-Objekts erstellt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setResponseBuffering(java.lang.String value)  
```  
  
#### <a name="parameters"></a>Parameter  
 *value*  
  
 Eine **Zeichenfolge** mit dem Puffer- und Streamingmodus. Gültige Modi (jeweils ohne Berücksichtigung der Groß-/Kleinschreibung): **full** oder **adaptive**.  
  
## <a name="remarks"></a>Remarks  
 Der Wert **full** gibt an, dass zur Laufzeit das gesamte Ergebnis vom Server gelesen wird.  
  
 Der Wert **adaptive** gibt an, dass im Bedarfsfall die geringstmögliche Menge an Daten gepuffert wird. Der **adaptive**-Wert ist der Standardpuffermodus.  
  
 Weitere Informationen zur Verwendung des Antwort Puffer Modus finden Sie unter [Verwenden der adaptiven Pufferung](../../../connect/jdbc/using-adaptive-buffering.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
