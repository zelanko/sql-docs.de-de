---
title: IsClosed-Methode (SQLServerConnection) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 508b3d1fe22ff58e91865204d6b74822ba6f5763
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47647629"
---
# <a name="isclosed-method-sqlserverconnection"></a>isClosed-Methode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt an, ob dieses [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekt geschlossen wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean isClosed()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** ist die Verbindung schließen, **"false"** ist dies nicht.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese IsClosed-Methode wird von der IsClosed-Methode in der java.sql.Connection-Schnittstelle angegeben.  
  
 Überprüft den Zustand des aufgerufenen SQLServerConnection-Objekts. Eine Verbindung wird geschlossen, wenn für sie die [close](../../../connect/jdbc/reference/close-method-sqlserverconnection.md)-Methode aufgerufen wurde oder bestimmte schwerwiegende Fehler aufgetreten sind. Diese Methode gibt nur dann **true** zurück, wenn sie nach dem Aufrufen der close-Methode aufgerufen wurde.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
