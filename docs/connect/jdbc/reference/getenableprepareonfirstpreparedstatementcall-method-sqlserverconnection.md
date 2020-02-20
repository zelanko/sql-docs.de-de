---
title: getEnablePrepareOnFirstPreparedStatementCall-Methode (SQLServerConnection) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67983444"
---
# <a name="getenableprepareonfirstpreparedstatementcall-method-sqlserverconnection"></a>getEnablePrepareOnFirstPreparedStatementCall-Method (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Diese gibt den Wert der Verbindungseigenschaft **enablePrepareOnFirstPreparedStatementCall** zurück. Bei FALSE ruft die erste Ausführung „sp_executesql“ auf und erstellt kein Prepared Statement. Sobald die zweite Ausführung erfolgt, ruft diese „sp_prepexec“ auf und richtet tatsächlich ein Handle für Prepared Statements ein. Bei den folgenden Ausführungen wird „sp_execute“ aufgerufen. Dadurch ist „sp_unprepare“ nicht mehr für den Abschluss eines Prepared Statements erforderlich, falls dieses nur einmal ausgeführt wird. Der Standardwert für diese Option kann durch Aufrufen von „setDefaultEnablePrepareOnFirstPreparedStatementCall()“ geändert werden.

## <a name="syntax"></a>Syntax  
  
```  
  
public boolean getEnablePrepareOnFirstPreparedStatementCall()  
```  

## <a name="return-value"></a>Rückgabewert
 Ein **boolescher** Wert, der den Wert der Verbindungseigenschaft **enablePrepareOnFirstPreparedStatementCall** enthält

## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Bemerkungen  
 Diese Methode ist im JDCB-Treiber ab Version 6.4 verfügbar.
 
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
