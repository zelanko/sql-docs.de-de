---
title: GetJDBCMajorVersion-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getJDBCMajorVersion
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 67b2bb4b-9714-4ba5-8739-50c632830451
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 4233b011af9df0b646f19965d636f7384887cd95
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66781102"
---
# <a name="getjdbcmajorversion-method-sqlserverdatabasemetadata"></a>getJDBCMajorVersion-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft die JDBC-Hauptversionsnummer für diesen Treiber ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public int getJDBCMajorVersion()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Typ **int**, durch den die Nebenversion des JDBC-Treibers angegeben wird.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese GetJDBCMajorVersion-Methode wird von der GetJDBCMajorVersion-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
