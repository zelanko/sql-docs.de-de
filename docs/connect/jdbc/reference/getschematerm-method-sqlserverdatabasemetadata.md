---
title: getSchemaTerm-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getSchemaTerm
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3e4a400f-0859-4ac3-983e-c25633b33683
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b0c2355ce38cbaabedeaa3e62da894ee6e67d67c
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67980071"
---
# <a name="getschematerm-method-sqlserverdatabasemetadata"></a>getSchemaTerm-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den bevorzugten Begriff für "schema" in dieser Datenbank ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.lang.String getSchemaTerm()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **String-Objekt**, das den bevorzugten Begriff enthält.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getSchemaTerm-Methode wird von der getSchemaTerm-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
 Wird [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] mit einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank verwendet, wird „schema“ als bevorzugter Begriff zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
