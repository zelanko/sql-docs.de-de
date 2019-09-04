---
title: getserverpreparedstatus-Methode (SQLServerDataSource) | Microsoft-Dokumentation
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
ms.openlocfilehash: 3f91b75b5c70029d53582b8b6ed4655485fd3fcf
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67979904"
---
# <a name="getserverpreparedstatementdiscardthreshold-method-sqlserverdatasource"></a>getServerPreparedStatementDiscardThreshold-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt den Wert der **serverpreparedstatuementverwerdthreshold** -Verbindungs Eigenschaft zurück. Mit dieser Einstellung wird gesteuert, wie viele ausstehende vorbereitete Aktionen für die Anweisungs Verwerfungs Aktion (sp_unprepare) pro Verbindung ausstehend sein können, bevor ein Cleanup der ausstehenden Handles auf dem Server ausgeführt wird. Wenn die Einstellung auf < = 1 festgelegt ist, werden die Aktionen zum Beenden der Vorbereitung direkt für die vorbereitete Anweisung Close ausgeführt Wenn dieser Wert auf > 1 festgelegt wird, werden diese Aufrufe zusammengefasst, um den mehr Aufwand des Aufrufs von sp_unprepare zu vermeiden.

  
## <a name="syntax"></a>Syntax  
  
```
public int getServerPreparedStatementDiscardThreshold();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt den **int** -Wert der **serverpreparedstatuementverwerdthreshold** -Verbindungs Eigenschaft zurück.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Bemerkungen  
 Diese Methode ist über JDBC Driver, Version 6,4 und höher, verfügbar.
 
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
