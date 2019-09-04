---
title: getserverpreparedstatus-Methode (SQLServerConnection) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.getServerPreparedStatementDiscardThreshold
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 87d7f85799524e3ac7c0e4d99608ce1d82b8f2fc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67979931"
---
# <a name="getserverpreparedstatementdiscardthreshold-method-sqlserverconnection"></a>getServerPreparedStatementDiscardThreshold-Methode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Gibt den Wert der **serverpreparedstatuementverwerdthreshold** -Verbindungs Eigenschaft zurück. Mit dieser Einstellung wird gesteuert, wie viele ausstehende vorbereitete Aktionen für die Anweisungs Verwerfungs Aktion (sp_unprepare) pro Verbindung ausstehend sein können, bevor ein Cleanup der ausstehenden Handles auf dem Server ausgeführt wird. Wenn die Einstellung auf < = 1 festgelegt ist, werden die Aktionen zum Vorbereiten von Aktionen sofort für die vorbereitete Anweisung Close ausgeführt. Wenn > 1 festgelegt ist, werden diese Aufrufe in einem Batch zusammengefasst, um den mehr Aufwand des Aufrufs von sp_unprepare zu vermeiden. Der Standardwert für diese Option kann durch Aufrufen von getdefaultserverpreparedstatus Token () geändert werden.

## <a name="syntax"></a>Syntax  
  
```  
  
public int getServerPreparedStatementDiscardThreshold()  
```  

## <a name="return-value"></a>Rückgabewert
 Ein **int** -Wert, der den Wert der **serverpreparedstatuementverwerdthreshold** -Verbindungs Eigenschaft enthält.

## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Bemerkungen  
 Diese Methode ist über JDBC Driver, Version 6,4 und höher, verfügbar.
 
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
