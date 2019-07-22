---
title: "\"ltresponabbuffering\"-Methode (SQLServerStatement) | Microsoft-Dokumentation"
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.setResponseBuffering(String responseBufferingValue)
apilocation:
- SQLServerStatement.setResponseBuffering(String responseBufferingValue)
apitype: Assembly
ms.assetid: 9f489835-6cda-4c8c-b139-079639a169cf
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a55f1d5695c2595b5ea721680fc77f88d13494ed
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67973109"
---
# <a name="setresponsebuffering-method-sqlserverstatement"></a>setResponseBuffering-Methode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den Antwortpuffermodus für dieses [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt auf **String full** oder auf **adaptive** (jeweils ohne Berücksichtigung der Groß-/Kleinschreibung) fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final void setResponseBuffering(java.lang.String value)  
```  
  
#### <a name="parameters"></a>Parameter  
 *value*  
  
 Eine **Zeichenfolge** mit dem Antwortpuffermodus. Gültige Modi (jeweils ohne Berücksichtigung der Groß-/Kleinschreibung): **full** oder **adaptive**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Der Wert **adaptive** gibt an, dass im Bedarfsfall die geringstmögliche Menge an Daten gepuffert wird.  
  
 Der Wert **full** gibt an, dass zur Laufzeit das gesamte Ergebnis vom Server gelesen wird.  
  
 Adaptive ist der Standardwert in JDBC Driver, Version 2,0 und 3,0. Full war der Standardwert vor JDBC Driver, Version 2,0.  
  
 Mithilfe der [setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)-Methode kann die **responseBuffering**-Verbindungseigenschaft vom Typ **Zeichenfolge** für das aktuelle [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt überschrieben werden. Weitere Informationen zur Verwendung des Antwort Puffer Modus finden Sie unter [Verwenden der adaptiven Pufferung](../../../connect/jdbc/using-adaptive-buffering.md).  
  
 Wird von der Anwendung ein ungültiger Parameterwert für die [setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)-Methode angegeben, wird ein Fehler vom Typ [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) ausgelöst.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)   
 [Verwenden der adaptiven Pufferung](../../../connect/jdbc/using-adaptive-buffering.md)  
  
  
