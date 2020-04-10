---
title: getDisableStatementPooling-Methode (SQLServerConnection) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.getDisableStatementPooling
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: af86780bc2c54dfa504c63d2fc18f11e8bf22f2c
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80917568"
---
# <a name="getdisablestatementpooling-method-sqlserverconnection"></a>getDisableStatementPooling-Methode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Diese Methode gibt den Wert der Verbindungseigenschaft **disableStatementPooling** zurück. Mit dieser Einstellung wird gesteuert, ob für diese Verbindung Anweisungspooling aktiviert ist.

## <a name="syntax"></a>Syntax  
  
```  
  
public boolean getDisableStatementPooling()  
```  

## <a name="return-value"></a>Rückgabewert
 Diese Methode gibt einen **booleschen** Wert zurück, der den Wert der Verbindungseigenschaft **disableStatementPooling** enthält.

## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Bemerkungen  
 Diese Methode ist über Version 6.4 und höher des JDCB-Treibers verfügbar.
 
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
