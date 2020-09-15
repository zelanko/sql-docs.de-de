---
description: setStatementPoolingCacheSize-Methode (SQLServerConnection)
title: setStatementPoolingCacheSize-Methode (SQLServerConnection) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setStatementPoolingCacheSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c14abd6c5251883d348f56d4a1f37d7bb8512f72
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88355286"
---
# <a name="setstatementpoolingcachesize-method-sqlserverconnection"></a>setStatementPoolingCacheSize-Methode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Mit dieser Methode wird die Größe des Caches für Prepared Statements für diese Verbindung festgelegt. Die Methode funktioniert nur, wenn disableStatementPooling auf FALSE festgelegt und der Wert > 0 (null) ist.

## <a name="syntax"></a>Syntax  
  
```  
  
public void setStatementPoolingCacheSize(int statementPoolingCacheSize)  
```  

#### <a name="parameters"></a>Parameter  
 *statementPoolingCacheSize*  
  
 Dies ist der neue Wert der Verbindungseigenschaft **statementPoolingCacheSize**.  

## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Bemerkungen  
 Diese Methode ist über Version 6.4 und höher des JDCB-Treibers verfügbar.
 
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
