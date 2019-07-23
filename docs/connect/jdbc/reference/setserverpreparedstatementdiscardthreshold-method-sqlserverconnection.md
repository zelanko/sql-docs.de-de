---
title: setserverpreparedstatus-Methode (SQLServerConnection) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setServerPreparedStatementDiscardThreshold
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8f66746b15e96f49d96b428e8cf8844eeea12a12
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67972919"
---
# <a name="setserverpreparedstatementdiscardthreshold-method-sqlserverconnection"></a>setServerPreparedStatementDiscardThreshold-Methode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Gibt das Verhalten für eine bestimmte Verbindungs Instanz an. Mit dieser Einstellung wird gesteuert, wie viele ausstehende vorbereitete Aktionen für die Anweisungs Verwerfungs Aktion (sp_unprepare) pro Verbindung ausstehend sein können, bevor ein Cleanup der ausstehenden Handles auf dem Server ausgeführt wird. Wenn die Einstellung < = 1 ist, werden die Vorbereitungs Aktionen sofort nach dem Schließen der vorbereiteten Anweisung ausgeführt. Wenn der Wert auf > 1 festgelegt ist, werden diese Aufrufe in einem Batch zusammengefasst, um den mehr Aufwand des Aufrufs von sp_unprepare zu vermeiden.


## <a name="syntax"></a>Syntax  
  
```  
  
public void setServerPreparedStatementDiscardThreshold(boolean thresholdValue)  
```  

#### <a name="parameters"></a>Parameter  
 *thresholdValue*  
 
 Der neue Wert der **serverpreparedstatuementverwerdthreshold** -Verbindungs Eigenschaft.  
 
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Diese Methode ist über JDBC Driver, Version 6,4 und höher, verfügbar.
 
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
