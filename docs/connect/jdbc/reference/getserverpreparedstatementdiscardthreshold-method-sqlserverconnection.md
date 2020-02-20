---
title: getServerPreparedStatementDiscardThreshold-Methode (SQLServerConnection) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67979931"
---
# <a name="getserverpreparedstatementdiscardthreshold-method-sqlserverconnection"></a>getServerPreparedStatementDiscardThreshold-Methode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Gibt den Wert der Verbindungseigenschaft **serverPreparedStatementDiscardThreshold** zurück. Mit dieser Einstellung steuern Sie, wie viele ausstehende Aktionen zum Verwerfen von Prepared Statements (sp_unprepare) pro Verbindung vorhanden sein dürfen, bevor ein Aufruf zum Bereinigen der ausstehenden Handles auf dem Server ausgeführt wird. Wenn diese Eigenschaft auf „<= 1“ festgelegt ist, werden unprepare-Aktionen sofort nach Abschluss des Prepared Statements ausgeführt. Wenn die Eigenschaft auf „> 1“ festgelegt ist, werden diese Aufrufe in einem Batch zusammengefasst, um den Aufwand eines zu häufigen Aufrufs von „sp_unprepare“ zu vermeiden. Der Standardwert für diese Option kann durch Aufrufen von „getDefaultServerPreparedStatementDiscardThreshold()“ geändert werden.

## <a name="syntax"></a>Syntax  
  
```  
  
public int getServerPreparedStatementDiscardThreshold()  
```  

## <a name="return-value"></a>Rückgabewert
 Ein **int**-Wert, der den Wert der Verbindungseigenschaft **serverPreparedStatementDiscardThreshold** enthält

## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Bemerkungen  
 Diese Methode ist im JDCB-Treiber, Version 6.4 und höher, verfügbar.
 
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
