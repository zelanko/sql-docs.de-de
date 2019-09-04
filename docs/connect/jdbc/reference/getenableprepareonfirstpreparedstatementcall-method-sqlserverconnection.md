---
title: getenableprepareonfirstpreparedstatus-Methode (SQLServerConnection) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.getEnablePrepareOnFirstPreparedStatementCall
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ac1cf4dbd8c8c14b5c97dbfecbe81d397c1598ce
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67983444"
---
# <a name="getenableprepareonfirstpreparedstatementcall-method-sqlserverconnection"></a>getEnablePrepareOnFirstPreparedStatementCall-Method (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Gibt den Wert der **enableprepareonfirstpreparedstatus** -Verbindungs Eigenschaft zurück. False gibt an, dass bei der ersten Ausführung sp_executesql aufgerufen und keine-Anweisung vorbereitet wird, sobald die zweite Ausführung stattfindet, dann wird sp_prepexec aufgerufen und tatsächlich ein vorbereitetes Anweisungs Handle eingerichtet. Bei den folgenden Ausführungen wird sp_execute aufgerufen. Dadurch ist es nicht mehr erforderlich, sp_unprepare on Prepared Statement CLOSE zu schließen, wenn die Anweisung nur einmal ausgeführt wird. Der Standardwert für diese Option kann durch Aufrufen von setdefaultenableprepareonfirstpreparedstatuementcall () geändert werden.

## <a name="syntax"></a>Syntax  
  
```  
  
public boolean getEnablePrepareOnFirstPreparedStatementCall()  
```  

## <a name="return-value"></a>Rückgabewert
 Ein **boolescher** Wert, der den Wert der **enableprepareonfirstpreparedstatus** -Verbindungs Eigenschaft enthält.

## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Bemerkungen  
 Diese Methode ist über JDBC Driver, Version 6,4 und höher, verfügbar.
 
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
