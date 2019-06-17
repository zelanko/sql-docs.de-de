---
title: Finalize-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.finalize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 49bc879d-822b-42da-bc20-2394865f1f0f
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 854da2b16cf680ac6ce54ae44a4bf1296cdbfd2c
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66796854"
---
# <a name="finalize-method-sqlserverresultset"></a>finalize-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Schließt dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt explizit.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void finalize()  
```  
  
## <a name="remarks"></a>Remarks  
 Schließt das Resultset, wenn dies nicht durch die Anwendung geschieht. Diese Methode entspricht der JDBC-Spezifikation. Da die Java Virtual Machine (JVM) keine Garantie dafür bietet, wann ein Finalizer ausgeführt werden kann, können Anwendungen, von denen ihre Resultsets nicht explizit geschlossen werden, einen Deadlock für eine andere Anweisung auslösen, von der die gleiche Verbindung verwendet wird und die für eine gemeinsame Serverressource (z. B. Zeilensperren) blockiert wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
