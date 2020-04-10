---
title: getSuperTables-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getSuperTables
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 085461de-367b-4832-88aa-010813d2bc41
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1caaa96d303e892d9bd729181d7dba1f327b6852
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80926139"
---
# <a name="getsupertables-method-sqlserverdatabasemetadata"></a>getSuperTables-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft eine Beschreibung der Tabellenhierarchien ab, die in einem bestimmten Schema in dieser Datenbank definiert sind.  
  
> [!NOTE]  
>  Diese Methode wird für [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] derzeit nicht unterstützt. Bei Verwendung der Methode wird immer ein leeres Resultset zurückgegeben.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.ResultSet getSuperTables(java.lang.String catalog,  
                                         java.lang.String schemaPattern,  
                                         java.lang.String tableNamePattern)  
```  
  
#### <a name="parameters"></a>Parameter  
 *catalog*  
  
 Ein **String-Objekt**, das den Katalognamen enthält.  
  
 *schemaPattern*  
  
 Ein **String-Objekt**, das das Schemanamenmuster enthält.  
  
 *tableNamePattern*  
  
 Ein **String-Objekt**, das das Tabellennamenmuster enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getSuperTables-Methode wird von der getSuperTables-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
