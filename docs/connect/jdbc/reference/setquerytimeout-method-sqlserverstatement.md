---
title: setQueryTimeout-Methode (SQLServerStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.setQueryTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0c513265-cd0c-4b38-9494-94458c17a16d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9a4a271e07dea5a533dcb19b098a3e3de29e535e
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67973182"
---
# <a name="setquerytimeout-method-sqlserverstatement"></a>setQueryTimeout-Methode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt die Anzahl von Sekunden, die vom Treiber auf die Ausführung eines [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekts gewartet wird, auf die angegebene Anzahl von Sekunden fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final void setQueryTimeout(int seconds)  
```  
  
#### <a name="parameters"></a>Parameter  
 *Sekunden*  
  
 Ein Wert vom Typ **int** zum Angeben der Anzahl der Sekunden, die gewartet werden soll, bzw. 0, wenn keine Beschränkung festgelegt wurde.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese setQueryTimeout-Methode wird von der setQueryTimeout-Methode in der java.sql.Statement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
