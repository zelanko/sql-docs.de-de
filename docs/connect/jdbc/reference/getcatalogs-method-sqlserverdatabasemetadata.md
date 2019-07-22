---
title: getkatalogen-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 786f55e436b9582eaed875f8c7cd265b1d3e2cc5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67953454"
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
  
## <a name="remarks"></a>Remarks  
 Diese getCatalogs-Methode wird von der getCatalogs-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
> [!NOTE]  
>  Auf SQL Azure sollten Sie eine Verbindung mit der Master-Datenbank herstellen, um **SQLServerDatabaseMetaData. getkatalogen**aufzurufen. SQL Azure unterstützt nicht die Rückgabe sämtlicher Kataloge aus einer Benutzerdatenbank. **SQLServerDatabaseMetaData. getkatalogen** verwendet die sys. Database-Sicht, um die Kataloge zu erhalten. Informationen zum Verhalten von **SQLServerDatabaseMetaData. getkataloge** auf SQL Azure finden Sie in der Erörterung der Berechtigungen in [sys. database_usage (Azure SQL-Datenbank)](../../../relational-databases/system-catalog-views/sys-database-usage-azure-sql-database.md) .  
  
 Das von der getCatalogs-Methode zurückgegebene Resultset enthält die folgenden Informationen:  
  
|Name|Typ|und Beschreibung|  
|----------|----------|-----------------|  
|TABLE_CAT|**String**|Der Name des Katalogs einschließlich der Systemdatenbanken in [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
  
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
  
  
