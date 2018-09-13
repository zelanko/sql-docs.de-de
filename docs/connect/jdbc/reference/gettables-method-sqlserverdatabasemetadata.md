---
title: GetTables-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getTables
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a7514673-3457-4541-9560-28a8284ad9e3
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2bbe1c39895febd9d853afee54c034d6eb77c3b1
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42784921"
---
# <a name="gettables-method-sqlserverdatabasemetadata"></a>getTables-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft eine Beschreibung der Tabellen ab, die im angegebenen Katalog, Schema oder Tabellennamenmuster verfügbar sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.ResultSet getTables(java.lang.String catalog,  
                                    java.lang.String schema,  
                                    java.lang.String table,  
                                    java.lang.String[] types)  
```  
  
#### <a name="parameters"></a>Parameter  
 *catalog*  
  
 Ein **String-Objekt**, das den Katalognamen enthält. Durch Festlegen dieses Parameters auf NULL wird angegeben, dass der Katalogname nicht verwendet werden muss.  
  
 *schema*  
  
 Ein **String-Objekt**, das das Schemanamenmuster enthält. Durch Festlegen dieses Parameters auf NULL wird angegeben, dass der Schemaname nicht verwendet werden muss.  
  
 *tableName*  
  
 Ein **String-Objekt**, das das Tabellennamenmuster enthält.  
  
 *types*  
  
 Ein Zeichenfolgenarray mit den einzubeziehenden Tabellentypen. Mit "NULL" wird angegeben, dass alle Tabellentypen einbezogen werden sollen.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese GetTables-Methode wird von der GetTables-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
 Das von der getTables-Methode zurückgegebene Resultset enthält folgende Informationen:  
  
|Name|Typ|und Beschreibung|  
|----------|----------|-----------------|  
|TABLE_CAT|**String**|Der Name der Datenbank, in der sich die angegebene Tabelle befindet.|  
|TABLE_SCHEM|**String**|Der Tabellenschemaname.|  
|table_name|**String**|Der Tabellenname.|  
|TABLE_TYPE|**String**|Der Tabellentyp.|  
|REMARKS|**String**|Die Beschreibung der Tabelle.<br /><br /> **Hinweis:** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gibt für diese Spalte keinen Wert zurück.|  
|TYPE_CAT|**String**|Wird vom JDBC-Treiber nicht unterstützt.|  
|TYPE_SCHEM|**String**|Wird vom JDBC-Treiber nicht unterstützt.|  
|TYPE_NAME|**String**|Wird vom JDBC-Treiber nicht unterstützt.|  
|SELF_REFERENCING_COL_NAME|**String**|Wird vom JDBC-Treiber nicht unterstützt.|  
|REF_GENERATION|**String**|Wird vom JDBC-Treiber nicht unterstützt.|  
  
> [!NOTE]  
>  Weitere Informationen zu den Daten, die von der getTables-Methode zurückgegeben werden, finden Sie in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Onlinedokumentation unter „sp_tables (Transact-SQL)“.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie mithilfe der getTables-Methode Tabellenbeschreibungsinformationen für die Tabelle „Person.Contact“ aus der [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]-Beispieldatenbank zurückgegeben werden können.  
  
```  
public static void executeGetTables(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getTables("AdventureWorks", "Person", "Contact", null);  
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
  
  
