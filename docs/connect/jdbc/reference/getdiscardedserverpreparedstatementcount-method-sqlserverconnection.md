---
title: GetDiscardedServerPreparedStatementCount-Methode (SQLServerConnection) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.getDiscardedServerPreparedStatementCount
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 2910453562cf78c4b88140de15885d4ddca5fe3a
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66776869"
---
# <a name="getdiscardedserverpreparedstatementcount-method-sqlserverconnection"></a>getDiscardedServerPreparedStatementCount-Methode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Gibt die Anzahl der derzeit ausstehenden vorbereitete Anweisung unprepare Aktionen.

## <a name="syntax"></a>Syntax  
  
```  
  
public int getDiscardedServerPreparedStatementCount()  
```  

## <a name="return-value"></a>Rückgabewert
 Ein **Int** , enthält die Anzahl der derzeit ausstehenden vorbereitete unprepare Aktionen.

## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Diese Methode wird von JDBC Driver, Version 6.4 verfügbar und auf dem Weg.
 
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
