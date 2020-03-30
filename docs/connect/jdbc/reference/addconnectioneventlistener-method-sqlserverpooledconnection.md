---
title: addConnectionEventListener-Methode (SQLServerPooledConnection) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPooledConnection.addConnectionEventListener
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 142830a8-8d4e-48ca-911d-85bf195ca4fe
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e1377e29329f43b9ea982f168e394537295ec889
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67955966"
---
# <a name="addconnectioneventlistener-method-sqlserverpooledconnection"></a>addConnectionEventListener-Methode (SQLServerPooledConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Registriert den angegebenen Ereignislistener, damit dieser benachrichtigt wird, wenn in Zusammenhang mit dem [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)-Objekt ein Ereignis auftritt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void addConnectionEventListener(javax.sql.ConnectionEventListener listener)  
```  
  
#### <a name="parameters"></a>Parameter  
 *listener*  
  
 Dies ist ein ConnectionEventListener-Objekt.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese addConnectionEventListener-Methode wird von der addConnectionEventListener-Methode in der javax.sql.PooledConnection-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerPooledConnection-Methoden](../../../connect/jdbc/reference/sqlserverpooledconnection-methods.md)   
 [SQLServerPooledConnection-Elemente](../../../connect/jdbc/reference/sqlserverpooledconnection-members.md)   
 [SQLServerPooledConnection-Klasse](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)  
  
  
