---
title: getenableprepareonfirstpreparedstatus-Methode (SQLServerDataSource) | Microsoft-Dokumentation
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
ms.openlocfilehash: ce67d0e688ae3ad8909915d9906608f5370830b1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67983394"
---
# <a name="getenableprepareonfirstpreparedstatementcall-method-sqlserverdatasource"></a>getEnablePrepareOnFirstPreparedStatementCall-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt den Wert der **enableprepareonfirstpreparedstatus** -Verbindungs Eigenschaft zurück. Wenn diese Konfiguration false zurückgibt, ruft die erste Ausführung einer vorbereiteten Anweisung sp_executesql auf, und es wird keine Anweisung vorbereitet. Sobald die zweite Ausführung erfolgt, ruft Sie sp_prepexec auf und erstellt tatsächlich ein vorbereitetes Anweisungs Handle. Bei den folgenden Ausführungen wird sp_execute aufgerufen. Dadurch ist es nicht mehr erforderlich, sp_unprepare on Prepared Statement CLOSE zu schließen, wenn die Anweisung nur einmal ausgeführt wird. 
  
## <a name="syntax"></a>Syntax  
  
```
public boolean getEnablePrepareOnFirstPreparedStatementCall();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt den **booleschen** Wert der **enableprepareonfirstpreparedstatus** -Verbindungs Eigenschaft zurück.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Bemerkungen  
 Diese Methode ist über JDBC Driver, Version 6,4 und höher, verfügbar.
 
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
