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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 050a32c83950d2846ac60d14af0413f0be67110d
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80920747"
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
  
  
