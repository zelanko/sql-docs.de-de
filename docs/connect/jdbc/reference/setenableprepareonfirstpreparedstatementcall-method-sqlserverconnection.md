---
title: setEnablePrepareOnFirstPreparedStatementCall-Methode (SQLServerConnection) | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bf48b4d280e9205a72025a346495f83aca68a064
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922398"
---
# <a name="setenableprepareonfirstpreparedstatementcall-method-sqlserverconnection"></a>setEnablePrepareOnFirstPreparedStatementCall-Methode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Mit dieser Methode geben Sie das Verhalten einer bestimmten Verbindungsinstanz an. Bei FALSE ruft die erste Ausführung „sp_executesql“ auf und bereitet keine Anweisung vor. Sobald die zweite Ausführung erfolgt, ruft diese „sp_prepexec“ auf und richtet tatsächlich ein Handle für Prepared Statements ein. Bei den folgenden Ausführungen wird sp_execute aufgerufen. Dadurch ist „sp_unprepare“ nicht mehr für den Abschluss einer vorbereiteten Anweisung erforderlich, falls diese nur einmal ausgeführt wird.

## <a name="syntax"></a>Syntax  
  
```  
  
public void setEnablePrepareOnFirstPreparedStatementCall(boolean enablePrepareOnFirstPreparedStatementCall)  
```  
  
#### <a name="parameters"></a>Parameter  
 *enablePrepareOnFirstPreparedStatementCall*  
  
 Der neue Wert der Verbindungseigenschaft **enablePrepareOnFirstPreparedStatementCall**  
 
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Bemerkungen  
 Diese Methode ist über Version 6.4 und höher des JDCB-Treibers verfügbar.
 
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
