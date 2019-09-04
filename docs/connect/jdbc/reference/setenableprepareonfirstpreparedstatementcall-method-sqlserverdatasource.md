---
title: "\"ltenableprepareonfirstpreparedstatus\"-Methode (SQLServerDataSource) | Microsoft-Dokumentation"
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
ms.openlocfilehash: 26ac2cac075d08b8029ac0e85dacffd1674fb0da
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67974312"
---
# <a name="setenableprepareonfirstpreparedstatementcall-method-sqlserverdatasource"></a>setEnablePrepareOnFirstPreparedStatementCall-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt das Verhalten für eine bestimmte Verbindungs Instanz an. Wenn diese Konfiguration false ist, ruft die erste Ausführung einer vorbereiteten Anweisung sp_executesql auf, und es wird keine Anweisung vorbereitet, sobald die zweite Ausführung stattfindet, ruft Sie sp_prepexec auf und richtet tatsächlich ein vorbereitetes Anweisungs Handle ein. Bei den folgenden Ausführungen wird sp_execute aufgerufen. Dadurch ist es nicht mehr erforderlich, sp_unprepare on Prepared Statement CLOSE zu schließen, wenn die Anweisung nur einmal ausgeführt wird.  
## <a name="syntax"></a>Syntax  
  
```
public void setEnablePrepareOnFirstPreparedStatementCall(boolean enablePrepareOnFirstPreparedStatementCall);  
```  
  
#### <a name="parameters"></a>Parameter  
 *enablePrepareOnFirstPreparedStatementCall*  
  
 Der neue Wert der **enableprepareonfirstpreparedstatus** -Verbindungs Eigenschaft.  

## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Bemerkungen  
 Diese Methode ist über JDBC Driver, Version 6,4 und höher, verfügbar.
 
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
