---
title: finalize-Methode (SQLServerResultSet) | Microsoft-Dokumentation
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
ms.openlocfilehash: 7afb8728b92ac7460173950bf42e38f968e056af
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67954562"
---
# <a name="finalize-method-sqlserverresultset"></a>finalize-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Schließt dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt explizit.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void finalize()  
```  
  
## <a name="remarks"></a>Bemerkungen  
 Schließt das Resultset, wenn dies nicht durch die Anwendung geschieht. Diese Methode entspricht der JDBC-Spezifikation. Da die Java Virtual Machine (JVM) keine Garantie dafür bietet, wann ein Finalizer ausgeführt werden kann, können Anwendungen, von denen ihre Resultsets nicht explizit geschlossen werden, einen Deadlock für eine andere Anweisung auslösen, von der die gleiche Verbindung verwendet wird und die für eine gemeinsame Serverressource (z. B. Zeilensperren) blockiert wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
