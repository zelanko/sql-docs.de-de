---
title: getJDBCMinorVersion-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getJDBCMinorVersion
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d9e153b5-51b7-4e44-b342-f147f04dbe19
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 600c1369df2bf71f305ccd10937f9b901212ac98
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80921417"
---
# <a name="getjdbcminorversion-method-sqlserverdatabasemetadata"></a>getJDBCMinorVersion-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft die JDBC-Nebenversionsnummer für diesen Treiber ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public int getJDBCMinorVersion()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Typ **int**, durch den die Nebenversion des JDBC-Treibers angegeben wird.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getJDBCMinorVersion-Methode wird von der getJDBCMinorVersion-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
