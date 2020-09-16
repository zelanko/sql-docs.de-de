---
description: executeBatch-Methode (SQLServerStatement)
title: executeBatch-Methode (SQLServerStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.executeBatch
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: fb034f63-2532-4da8-a1b0-bc125734585a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bd3c7d62d9ed35c5bacab061134531c9f03580c6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88437722"
---
# <a name="executebatch-method-sqlserverstatement"></a>executeBatch-Methode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Übermittelt einen Befehlsbatch zur Ausführung an die Datenbank. Werden alle Befehle erfolgreich ausgeführt, wird ein Array mit Updatezählungen zurückgegeben.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public int[] executeBatch()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Array aus **int**-Elementen, die die Updatezählungen enthalten.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
 java.sql.BatchUpdateException  
  
## <a name="remarks"></a>Bemerkungen  
 Diese executeBatch-Methode wird von der executeBatch-Methode in der java.sql.Statement-Schnittstelle angegeben.  
  
 Nach dem Übertragen von Befehlen an die Datenbank werden von der Methode alle Befehle im Stapel gelöscht.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
