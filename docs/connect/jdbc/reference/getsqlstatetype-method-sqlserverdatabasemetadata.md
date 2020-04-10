---
title: getSQLStateType-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getSQLStateType
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ee4d6751-68a3-4d04-831c-e6d704c59e63
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 762c22bbf2ed499fc2c0884014e374af17f60292
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80921946"
---
# <a name="getsqlstatetype-method-sqlserverdatabasemetadata"></a>getSQLStateType-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt an, ob "SQLSTATE" (zurückgegeben von der SQLException.getSQLState-Methode) den Wert "X/Open" (jetzt "Open Group"), "SQL CLI", "SQL99" (JDBC 3.0) oder "SQL:2003" (JDBC 4.0) besitzt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public int getSQLStateType()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Typ **int** zum Angeben des SQLSTATE-Typs. Mögliche Werte:  
  
-   Java Runtime Environment-Version 5.0 (JRE): Wenn die Verbindungseigenschaft **xopenstates** auf **TRUE** festgelegt ist, gibt diese Methode DatabaseMetaData.sqlStateXOpen zurück. Andernfalls DatabaseMetaData.sqlStateSQL99.  
  
-   Java Runtime Environment-Version 6.0 (JRE): Wenn die Verbindungseigenschaft **xopenstates** auf **TRUE** festgelegt ist, gibt diese Methode DatabaseMetaData.sqlStateXOpen zurück. Andernfalls DatabaseMetaData.sqlStateSQL.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getSQLStateType-Methode wird von der getSQLStateType-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
