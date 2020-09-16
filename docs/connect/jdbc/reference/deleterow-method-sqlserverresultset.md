---
description: deleteRow-Methode (SQLServerResultSet)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9302a3ee26137c693f4711fc5501c5b715b16a71
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88437842"
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
 Diese deleteRow-Methode wird von der deleteRow-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Diese Methode kann nicht aufgerufen werden, wenn sich der Cursor in der Einfügezeile befindet.  
  
 Bei der Verwendung von Keysetcursorn hinterlässt diese Methode eine Lücke im Resultset. Ob diese Lücke vorhanden ist, können Sie mit der [rowDeleted](../../../connect/jdbc/reference/rowdeleted-method-sqlserverresultset.md)-Methode überprüfen. Die Zeilennummern der Zeilen im Resultset ändern sich nicht.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
