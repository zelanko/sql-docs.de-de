---
description: cancelRowUpdates-Methode (SQLServerResultSet)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 32e5333f571ff9375bdbdc61e9743d29a57cedfd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88438182"
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
 Diese cancelRowUpdates-Methode wird von der cancelRowUpdates-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Die Methode kann nach dem Aufruf einer Aktualisierungsmethode und vor dem Aufruf der [updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md)-Methode aufgerufen werden, um für die an einer Zeile vorgenommenen Aktualisierungen ein Rollback auszuführen. Wenn keine Aktualisierungen vorgenommen wurden oder updateRow bereits aufgerufen wurde, hat diese Methode keine Auswirkungen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
