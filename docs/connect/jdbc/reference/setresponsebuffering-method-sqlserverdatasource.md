---
title: setResponseBuffering-Methode (SQLServerDataSource) | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: af2465fa929c47acc1cf39c87d0847c9c4e7d451
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927503"
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
  
## <a name="remarks"></a>Bemerkungen  
 Der Wert **full** gibt an, dass zur Laufzeit das gesamte Ergebnis vom Server gelesen wird.  
  
 Der Wert **adaptive** gibt an, dass im Bedarfsfall die geringstmögliche Menge an Daten gepuffert wird. Der **adaptive**-Wert ist der Standardpuffermodus.  
  
 Weitere Informationen zur Verwendung des Antwortpuffermodus finden Sie unter [Verwenden der adaptiven Pufferung](../../../connect/jdbc/using-adaptive-buffering.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
