---
title: CancelRowUpdates-Methode (SQLServerResultSet) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: c80123c2cc08d01c4fb41c945954288bb999f897
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47810648"
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
  
## <a name="remarks"></a>Remarks  
 Diese CancelRowUpdates-Methode wird von der CancelRowUpdates-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Die Methode kann nach dem Aufruf einer Aktualisierungsmethode und vor dem Aufruf der [updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md)-Methode aufgerufen werden, um für die an einer Zeile vorgenommenen Aktualisierungen ein Rollback auszuführen. Wenn keine Aktualisierungen vorgenommen wurden oder updateRow bereits aufgerufen wurde, hat diese Methode keine Auswirkungen.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
