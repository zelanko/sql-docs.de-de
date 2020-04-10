---
title: Methode „getGeneratedKeys“ (SQLServerStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getGeneratedKeys
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a3325950-0e81-4ae8-aa0c-e1f6d371adcd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1f0c1d8b605cb0decea6c5bfae08d5e27d841217
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80921535"
---
# <a name="getgeneratedkeys-method-sqlserverstatement"></a>getGeneratedKeys-Methode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft sämtliche automatisch generierte Schlüssel ab, die aufgrund der Ausführung dieses [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekts erstellt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final java.sql.ResultSet getGeneratedKeys()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein ResultSet-Objekt  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getGeneratedKeys-Methode wird von der getGeneratedKeys-Methode in der java.sql.Statement-Schnittstelle angegeben.  
  
 Weitere Informationen zur Verwendung dieser Methode finden Sie unter [Verwenden automatisch generierter Schlüssel](../../../connect/jdbc/using-auto-generated-keys.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
