---
title: "\"ltenableprepareonfirstpreparedstatus\"-Methode (SQLServerConnection) | Microsoft-Dokumentation"
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setEnablePrepareOnFirstPreparedStatementCall
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 187a195a831955b65f4af113fb80e5f99308e1a5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67974447"
---
# <a name="setenableprepareonfirstpreparedstatementcall-method-sqlserverconnection"></a>setEnablePrepareOnFirstPreparedStatementCall-Methode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Gibt das Verhalten für eine bestimmte Verbindungs Instanz an. Wenn value auf false festgelegt ist, ruft die erste Ausführung sp_executesql auf, und es wird keine Anweisung vorbereitet, sobald die zweite Ausführung stattfindet, ruft Sie sp_prepexec auf und richtet tatsächlich ein vorbereitetes Anweisungs Handle ein. Bei den folgenden Ausführungen wird sp_execute aufgerufen. Dadurch ist es nicht mehr erforderlich, sp_unprepare on Prepared Statement CLOSE zu schließen, wenn die Anweisung nur einmal ausgeführt wird.

## <a name="syntax"></a>Syntax  
  
```  
  
public void setEnablePrepareOnFirstPreparedStatementCall(boolean enablePrepareOnFirstPreparedStatementCall)  
```  
  
#### <a name="parameters"></a>Parameter  
 *enablePrepareOnFirstPreparedStatementCall*  
  
 Der neue Wert der **enableprepareonfirstpreparedstatus** -Verbindungs Eigenschaft.  
 
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Bemerkungen  
 Diese Methode ist über JDBC Driver, Version 6,4 und höher, verfügbar.
 
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
