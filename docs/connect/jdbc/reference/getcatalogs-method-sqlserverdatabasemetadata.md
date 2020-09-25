---
description: getCatalogs-Methode (SQLServerDatabaseMetaData)
title: getCatalogs-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getCatalogs
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7f8bd0f1-f340-4bb9-b559-0a6176124033
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a31fca087c206104d197a3121db90991ff38f8c8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88436902"
---
# <a name="getcatalogs-method-sqlserverdatabasemetadata"></a>getCatalogs-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft die Katalognamen ab, die auf dem Server verfügbar sind, mit dem eine Verbindung besteht.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.ResultSet getCatalogs()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getCatalogs-Methode wird von der getCatalogs-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
> [!NOTE]  
>  Sie sollten in Azure SQL-Datenbank eine Verbindung mit der Datenbank herstellen, um **SQLServerDatabaseMetaData.getCatalogs** aufzurufen. SQL-Datenbank unterstützt nicht die Rückgabe sämtlicher Kataloge aus einer Benutzerdatenbank. **SQLServerDatabaseMetaData.getCatalogs** verwendet die Ansicht „sys.databases“, um die Kataloge abzurufen. Erläuterung zum Verhalten von **SQLServerDatabaseMetaData.getCatalogs** in SQL Azure finden Sie im Abschnitt „Berechtigungen“ des Artikels [sys.database_usage (Azure SQL Database)](../../../relational-databases/system-catalog-views/sys-database-usage-azure-sql-database.md) > In Azure SQL-Datenbank sollten Sie eine Verbindung mit der Masterdatenbank herstellen, um **SQLServerDatabaseMetaData.getCatalogs** aufzurufen. SQL-Datenbank unterstützt nicht die Rückgabe sämtlicher Kataloge aus einer Benutzerdatenbank. **SQLServerDatabaseMetaData.getCatalogs** verwendet die Ansicht „sys.databases“, um die Kataloge abzurufen. Erläuterung zum Verhalten von **SQLServerDatabaseMetaData.getCatalogs** in Azure SQL-Datenbank finden Sie im Abschnitt „Berechtigungen“ des Artikels [sys.database_usage (Azure SQL Database)](../../../relational-databases/system-catalog-views/sys-database-usage-azure-sql-database.md).                      .  
  
 Das von der getCatalogs-Methode zurückgegebene Resultset enthält die folgenden Informationen:  
  
|Name|Typ|BESCHREIBUNG|  
|----------|----------|-----------------|  
|TABLE_CAT|**String**|Der Name des Katalogs, einschließlich der Systemdatenbanken in [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie die getCatalogs-Methode verwendet wird, um die Namen aller Datenbanken einschließlich der Systemdatenbanken zurückzugegeben, die in [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] enthalten sind.  
  
```  
public static void executeGetCatalogs(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getCatalogs();  
      ResultSetMetaData rsmd = rs.getMetaData();  
  
      // Display the result set data.  
      int cols = rsmd.getColumnCount();  
      while(rs.next()) {  
         for (int i = 1; i <= cols; i++) {  
            System.out.println(rs.getString(i));  
         }  
      }  
      rs.close();  
   }   
  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
