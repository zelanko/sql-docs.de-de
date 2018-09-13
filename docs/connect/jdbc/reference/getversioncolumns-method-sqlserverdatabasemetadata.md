---
title: GetVersionColumns-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
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
- SQLServerDatabaseMetaData.getVersionColumns
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6dd275d3-d9b2-4db7-938a-d4406c940a7a
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 449af2fc385e569c8a08051f155f704108153f84
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42784234"
---
# <a name="getversioncolumns-method-sqlserverdatabasemetadata"></a>getVersionColumns-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft eine Beschreibung der Spalten einer Tabelle ab, die automatisch aktualisiert wird, wenn ein Wert in einer Zeile aktualisiert wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.ResultSet getVersionColumns(java.lang.String catalog,  
                                            java.lang.String schema,  
                                            java.lang.String table)  
```  
  
#### <a name="parameters"></a>Parameter  
 *catalog*  
  
 Ein **String-Objekt**, das den Katalognamen enthält.  
  
 *schema*  
  
 Ein **String-Objekt**, das das Schemanamenmuster enthält.  
  
 *table*  
  
 Ein **String-Objekt**, das den Tabellennamen enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese GetVersionColumns-Methode wird von der GetVersionColumns-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
 Das von der getVersionColumns-Methode zurückgegebene Resultset enthält die folgenden Informationen:  
  
|Name|Typ|und Beschreibung|  
|----------|----------|-----------------|  
|SCOPE|**short**|Wird vom JDBC-Treiber nicht unterstützt.|  
|COLUMN_NAME|**String**|Der Spaltenname.|  
|DATA_TYPE|**short**|Der SQL-Datentyp aus "java.sql.Types".|  
|TYPE_NAME|**String**|Der Name des Datentyps.|  
|COLUMN_SIZE|**int**|Die Genauigkeit der Spalte.|  
|BUFFER_LENGTH|**int**|Die Länge der Spalten in Bytes.|  
|DECIMAL_DIGITS|**short**|Die Dezimalstellen der Spalte.|  
|PSEUDO_COLUMN|**short**|Gibt an, ob die Spalte eine Pseudospalte ist. Mögliche Werte:<br /><br /> versionColumnUnknown (0)<br /><br /> versionColumnNotPseudo (1)<br /><br /> versionColumnPseudo (2)|  
  
> [!NOTE]  
>  Weitere Informationen zu den Daten, die von der getVersionColumns-Methode zurückgegeben werden, finden Sie in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Onlinedokumentation unter „sp_datatype_info (Transact-SQL)“.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie mithilfe der getVersionColumns-Methode Informationen zu den Spalten, die in der Tabelle „Person.Contact“ in der [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]-Beispieldatenbank automatisch aktualisiert werden, zurückgegeben werden.  
  
```  
public static void executeGetVersionColumns(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getVersionColumns("AdventureWorks", "Person", "Contact");  
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
  
  
