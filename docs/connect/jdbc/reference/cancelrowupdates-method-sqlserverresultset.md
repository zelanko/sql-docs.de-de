---
title: cancelRowUpdates-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.cancelRowUpdates
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2ecacca4-f7bc-4f5d-886a-da7747fdccae
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d1598bca994ae41ccee56ca68e12e74e8d18fd0c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67955791"
---
# <a name="cancelrowupdates-method-sqlserverresultset"></a>cancelRowUpdates-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Bricht die Aktualisierungen ab, die an der aktuellen Zeile in diesem [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt vorgenommen wurden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void cancelRowUpdates()  
```  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese cancelRowUpdates-Methode wird von der cancelRowUpdates-Methode in der Java. SQL. Resultset-Schnittstelle angegeben.  
  
 Die Methode kann nach dem Aufruf einer Aktualisierungsmethode und vor dem Aufruf der [updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md)-Methode aufgerufen werden, um für die an einer Zeile vorgenommenen Aktualisierungen ein Rollback auszuführen. Wenn keine Aktualisierungen vorgenommen wurden oder updateRow bereits aufgerufen wurde, hat diese Methode keine Auswirkungen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
