---
title: getXAResource-Methode (sqlserverxaconnetction) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerXAConnection.getXAResource
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e1d2828f-fd20-44b0-b796-dc70f77c5b03
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c3d4b2132c3bbcf5612faa5f319a5358f158e2b7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67977984"
---
# <a name="getxaresource-method-sqlserverxaconnection"></a>getXAResource-Methode (SQLServerXAConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft ein [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)-Objekt ab, mit dem der Transaktions-Manager die Beteiligung des [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)-Objekts in einer verteilten Transaktion verwaltet.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public javax.transaction.xa.XAResource getXAResource()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein XAResource-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 java.sql.SQLException  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getXAResource-Methode wird von der getXAResource-Methode in der javax. SQL. xaconnetction-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerXAConnection-Methoden](../../../connect/jdbc/reference/sqlserverxaconnection-methods.md)   
 [SQLServerXAConnection-Elemente](../../../connect/jdbc/reference/sqlserverxaconnection-members.md)   
 [SQLServerXAConnection-Klasse](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)  
  
  
