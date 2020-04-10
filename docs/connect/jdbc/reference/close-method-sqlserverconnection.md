---
title: close-Methode (SQLServerConnection) | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 64ad1bcc06af74296b441fcd0b22cf488c58ef8a
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923666"
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
  
## <a name="remarks"></a>Bemerkungen  
 Diese close-Methode wird von der close-Methode in der java.sql.Connection-Schnittstelle angegeben.  
  
 Durch Aufrufen der close-Methode in der Mitte einer Transaktion wird ein Rollback für die Transaktion ausgeführt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnection-Elemente](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
