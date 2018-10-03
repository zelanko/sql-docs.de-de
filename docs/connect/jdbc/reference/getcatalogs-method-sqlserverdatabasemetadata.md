---
title: GetCatalogs-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: e81c905a483972ab0dfe7b03573bc30bf6d474e7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47727188"
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
 Diese GetCatalogs-Methode wird von der GetCatalogs-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
> [!NOTE]  
>  Auf SQL Azure, Sie müssen eine Verbindung mit der master-Datenbank aufrufen **SQLServerDatabaseMetaData.getCatalogs**. SQL Azure unterstützt nicht die Rückgabe sämtlicher Kataloge aus einer Benutzerdatenbank. **SQLServerDatabaseMetaData.getCatalogs** Ansicht "sys.databases" verwendet, um die Kataloge abzurufen. Finden Sie in der Diskussion zu Berechtigungen in [sys.databases (SQL Azure-Datenbank)](http://go.microsoft.com/fwlink/?LinkId=217396) zu **SQLServerDatabaseMetaData.getCatalogs** Verhalten auf SQL Azure.  
  
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
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
