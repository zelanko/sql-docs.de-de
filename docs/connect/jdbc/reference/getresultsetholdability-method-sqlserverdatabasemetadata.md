---
title: getresultltholdability-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData,getResultSetHoldability
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f0bd6283-83ab-4a0a-b825-ec4cdccf03e1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f6fbf7a0cf66db8bbcc2f2f69d603bc5d32fb74d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67980371"
---
# <a name="getresultsetholdability-method-sqlserverdatabasemetadata"></a>getResultSetHoldability-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft die Standardhaltbarkeit von Resultsets für diese Datenbank ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public int getResultSetHoldability()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Typ **int** zum Angeben der Standardhaltbarkeit.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getresultltholdability-Methode wird von der getresultltholdability-Methode in der Java. SQL. DatabaseMetaData-Schnittstelle angegeben.  
  
 Wird [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] mit einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank verwendet, wird von dieser Methode der Wert „1“ (entspricht der ResultSet.HOLD_CURSORS_OVER_COMMIT-Konstanten) zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
