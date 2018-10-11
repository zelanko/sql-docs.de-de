---
title: GetSQLStateType-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a4a01e2bb8ef76af91c4dede71ae7457351d430b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47733198"
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
  
-   Java Runtime Environment, Version 5.0: Wenn die **xopenstates-Eigenschaft** Connection-Eigenschaft wird festgelegt, um **"true"**, gibt diese Methode DatabaseMetaData.sqlStateXOpen zurück. Andernfalls DatabaseMetaData.sqlStateSQL99.  
  
-   Java Runtime Environment, Version 6.0: Wenn die **xopenstates-Eigenschaft** Connection-Eigenschaft auf festgelegt ist **"true"**, gibt diese Methode DatabaseMetaData.sqlStateXOpen zurück. Andernfalls DatabaseMetaData.sqlStateSQL.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese GetSQLStateType-Methode wird von der GetSQLStateType-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
