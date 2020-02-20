---
title: getUDTs-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getUDTs
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c4396453-dcb0-4132-8325-06b3c7896b3b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f51e5345cf7c7b78a0a3a37220927000af7d0fa7
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67978423"
---
# <a name="getudts-method-sqlserverdatabasemetadata"></a>getUDTs-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft eine Beschreibung der benutzerdefinierten Typen ab, die in einem bestimmten Schema definiert sind.  
  
> [!NOTE]  
>  Diese Methode wird mit [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] derzeit nicht unterstützt. Bei Verwendung der Methode wird immer ein leeres Resultset zurückgegeben.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.ResultSet getUDTs(java.lang.String catalog,  
                                  java.lang.String schemaPattern,  
                                  java.lang.String typeNamePattern,  
                                  int[] types)  
```  
  
#### <a name="parameters"></a>Parameter  
 *catalog*  
  
 Ein **String-Objekt**, das den Katalognamen enthält.  
  
 *schemaPattern*  
  
 Ein **String-Objekt**, das das Schemanamenmuster enthält.  
  
 *typeNamePattern*  
  
 Eine **Zeichenfolge**, die das Tabellentypmuster enthält.  
  
 *types*  
  
 Ein Array von int-Werten mit den einzubeziehenden Datentypen. Mit "NULL" wird angegeben, dass alle Typen einbezogen werden sollen.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getUDTs-Methode wird von der getUDTs-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
