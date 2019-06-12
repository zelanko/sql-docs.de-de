---
title: SetServerPreparedStatementDiscardThreshold-Methode (SQLServerDataSource) | Microsoft-Dokumentation
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
manager: jroth
ms.openlocfilehash: fb2962f6514fec7211b6d3a5ccd5f3af09a1f066
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66782919"
---
# <a name="setserverpreparedstatementdiscardthreshold-method-sqlserverdatasource"></a>setServerPreparedStatementDiscardThreshold-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den Wert der-Verbindungseigenschaft ServerPreparedStatementDiscardThreshold. Diese Einstellung steuert, wie viele ausstehende verwerfen der Anweisung vorbereitet, die Aktionen (Sp_unprepare) pro Verbindung ausstehenden sein können, bevor ein Aufruf zum Bereinigen der ausstehende Handles auf dem Server ausgeführt wird. Wenn die Einstellung ist < = 1 unprepare Aktionen sofort auf Schließen die vorbereitete Anweisung ausgeführt werden. Wenn der Wert 1 > festgelegt ist werden diese Aufrufe zusammengefasst um Mehraufwand Sp_unprepare oft aufrufen zu vermeiden
 
## <a name="syntax"></a>Syntax  
  
```
public void setServerPreparedStatementDiscardThreshold(int enablePrepareOnFirstPreparedStatementCall);  
```  
  
#### <a name="parameters"></a>Parameter  
 *serverPreparedStatementDiscardThreshold*  
  
 Der neue Wert des der **ServerPreparedStatementDiscardThreshold** Connection-Eigenschaft.  

## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Diese Methode wird von JDBC Driver, Version 6.4 verfügbar und auf dem Weg.
 
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
