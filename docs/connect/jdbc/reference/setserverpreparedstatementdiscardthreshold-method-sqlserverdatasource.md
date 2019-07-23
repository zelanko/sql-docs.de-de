---
title: setserverpreparedstatus-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 28c3a442f89813a4ce93ded9035c1bc16f9e47c1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67972843"
---
# <a name="setserverpreparedstatementdiscardthreshold-method-sqlserverdatasource"></a>setServerPreparedStatementDiscardThreshold-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den Wert der serverpreparedstatuementverwerdthreshold-Verbindungs Eigenschaft fest. Mit dieser Einstellung wird gesteuert, wie viele ausstehende vorbereitete Aktionen für die Anweisungs Verwerfungs Aktion (sp_unprepare) pro Verbindung ausstehend sein können, bevor ein Cleanup der ausstehenden Handles auf dem Server ausgeführt wird. Wenn die Einstellung auf < = 1 festgelegt ist, werden die Aktionen zum Beenden der Vorbereitung direkt für die vorbereitete Anweisung Close ausgeführt Wenn der Wert auf > 1 festgelegt ist, werden diese Aufrufe in einem Batch zusammengefasst, um den Aufwand für den Aufruf von sp_unprepare zu vermeiden.
 
## <a name="syntax"></a>Syntax  
  
```
public void setServerPreparedStatementDiscardThreshold(int enablePrepareOnFirstPreparedStatementCall);  
```  
  
#### <a name="parameters"></a>Parameter  
 *serverPreparedStatementDiscardThreshold*  
  
 Der neue Wert der **serverpreparedstatuementverwerdthreshold** -Verbindungs Eigenschaft.  

## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Diese Methode ist über JDBC Driver, Version 6,4 und höher, verfügbar.
 
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
