---
title: Rollback-Methode (java.sql.Savepoint) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f5d3aff96e90dd5de4e283697084ab0614d12f05
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66765514"
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
  
 Der Sicherungspunkt Objekt wiederhergestellt werden.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese RollBack-Methode wird von der RollBack-Methode in der java.sql.Connection-Schnittstelle angegeben.  
  
 Die Methode sollte nur bei deaktiviertem Modus für automatische Commits verwendet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Rollback-Methode &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/rollback-method-sqlserverconnection.md)   
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
