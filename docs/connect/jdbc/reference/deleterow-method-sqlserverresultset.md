---
title: deleteRow-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/20/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.deleteRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: aa04a644-c7c2-4738-8b6e-7fea566d2c16
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bc02d31a1d13a3d32f581da6fb3367473cb88bbb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67955138"
---
# <a name="deleterow-method-sqlserverresultset"></a>deleteRow-Methode (SQLServerResultSet)

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Löscht die aktuelle Zeile aus diesem [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt sowie aus der zugrunde liegenden Datenbank.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
public void deleteRow()  
```  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese deleteRow-Methode wird von der deleteRow-Methode in der Java. SQL. Resultset-Schnittstelle angegeben.  
  
 Diese Methode kann nicht aufgerufen werden, wenn sich der Cursor in der Einfügezeile befindet.  
  
 Bei der Verwendung von Keysetcursorn hinterlässt diese Methode eine Lücke im Resultset. Ob diese Lücke vorhanden ist, können Sie mit der [rowDeleted](../../../connect/jdbc/reference/rowdeleted-method-sqlserverresultset.md)-Methode überprüfen. Die Zeilennummern der Zeilen im Resultset ändern sich nicht.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
