---
title: isClosed-Methode (SQLServerConnection) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.isClosed
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3560ab18-4350-4d02-9716-439f0c2f7142
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 776c719a01378a30198b7a3bcc4134478ebeb742
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928678"
---
# <a name="isclosed-method-sqlserverconnection"></a>isClosed-Methode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt an, ob dieses [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt geschlossen wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean isClosed()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Der Wert lautet **TRUE**, wenn die Verbindung geschlossen wurde, andernfalls **FALSE**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese isClosed-Methode wird von der isClosed-Methode in der java.sql.Connection-Schnittstelle angegeben.  
  
 Damit wird der Zustand des aufgerufenen SQLServerConnection-Objekts überprüft. Eine Verbindung wird geschlossen, wenn für sie die [close](../../../connect/jdbc/reference/close-method-sqlserverconnection.md)-Methode aufgerufen wurde oder bestimmte schwerwiegende Fehler aufgetreten sind. Diese Methode gibt nur dann **true** zurück, wenn sie nach dem Aufrufen der close-Methode aufgerufen wurde.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
