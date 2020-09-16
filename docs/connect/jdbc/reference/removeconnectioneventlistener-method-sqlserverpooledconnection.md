---
description: removeConnectionEventListener-Methode (SQLServerPooledConnection)
title: removeConnectionEventListener-Methode (SQLServerPooledConnection) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPooledConnection.removeConnectionEventListener
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 46902e89-f512-40af-a2d9-a896f03d1200
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ba6472207d42379a3c1d5fe04f4313db986ab0d2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88432742"
---
# <a name="removeconnectioneventlistener-method-sqlserverpooledconnection"></a>removeConnectionEventListener-Methode (SQLServerPooledConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Entfernt den vorhandenen Ereignislistener.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void removeConnectionEventListener(javax.sql.ConnectionEventListener listener)  
```  
  
#### <a name="parameters"></a>Parameter  
 *listener*  
  
 Dies ist ein ConnectionEventListener-Objekt.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese removeConnectionEventListener-Methode wird von der removeConnectionEventListener-Methode in der javax.sql.PooledConnection-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerPooledConnection-Methoden](../../../connect/jdbc/reference/sqlserverpooledconnection-methods.md)   
 [SQLServerPooledConnection-Elemente](../../../connect/jdbc/reference/sqlserverpooledconnection-members.md)   
 [SQLServerPooledConnection-Klasse](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)  
  
  
