---
title: Close-Methode (SQLServerConnection) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.close
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f0f26585-bdf7-4737-b434-8c7e115c8e94
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 87bce635f81db5c2b5e98768524d79082a940e2e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67955678"
---
# <a name="close-method-sqlserverconnection"></a>close-Methode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt die Datenbank- und JDBC-Ressourcen dieses [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)-Objekts umgehend frei, sodass nicht auf deren automatische Freigabe gewartet werden muss.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void close()  
```  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese close-Methode wird von der close-Methode in der java.sql.Connection-Schnittstelle angegeben.  
  
 Durch Aufrufen der close-Methode in der Mitte einer Transaktion wird ein Rollback für die Transaktion ausgeführt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
