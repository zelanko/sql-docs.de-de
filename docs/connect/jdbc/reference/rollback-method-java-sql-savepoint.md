---
title: rollback(java.sql.Savepoint)-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.rollback (java.sql.Savepoint)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d5dbd9ef-194f-4130-bfcc-7901a4fa8ded
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2e1ac014ddeee1d3763dc3cebe720751c4c1ec94
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80903885"
---
# <a name="rollback-method-javasqlsavepoint"></a>rollback-Methode (java.sql.Savepoint)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Macht alle nach dem Festlegen des vorhandenen [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md)-Objekts festgelegten Änderungen rückgängig.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void rollback(java.sql.Savepoint s)  
```  
  
#### <a name="parameters"></a>Parameter  
 *s*  
  
 Das SavePoint-Objekt, auf die das Rollback ausgeführt werden soll  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese rollBack-Methode wird von der rollBack-Methode in der java.sql.Connection-Schnittstelle angegeben.  
  
 Die Methode sollte nur bei deaktiviertem Modus für automatische Commits verwendet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [rollback-Methode &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/rollback-method-sqlserverconnection.md)   
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
