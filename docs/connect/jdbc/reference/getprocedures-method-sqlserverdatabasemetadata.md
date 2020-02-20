---
title: getProcedures-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getProcedures
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 66c9a8b0-dc4c-4cbb-8004-c7157368cab4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 054ce4f6f646f873d4aff05fbe1d31aa9903ded9
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67980739"
---
# <a name="getprocedures-method-sqlserverdatabasemetadata"></a>getProcedures-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft eine Beschreibung der gespeicherten Prozeduren ab, die im angegebenen Katalog, Schema oder Namensmuster für gespeicherte Prozeduren verfügbar sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.ResultSet getProcedures(java.lang.String sCatalog,  
                                        java.lang.String sSchema,  
                                        java.lang.String proc)  
```  
  
#### <a name="parameters"></a>Parameter  
 *sCatalog*  
  
 Ein **String-Objekt**, das den Katalognamen enthält. Durch Festlegen dieses Parameters auf NULL wird angegeben, dass der Katalogname nicht verwendet werden muss.  
  
 *sSchema*  
  
 Ein **String-Objekt**, das das Schemanamenmuster enthält. Durch Festlegen dieses Parameters auf NULL wird angegeben, dass der Schemaname nicht verwendet werden muss.  
  
 *proc*  
  
 Ein **String-Objekt**, das das Prozedurnamenmuster enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getProcedures-Methode wird von der getProcedures-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
 Das von der getProcedures-Methode zurückgegebene Resultset enthält folgende Informationen:  
  
|Name|type|Beschreibung|  
|----------|----------|-----------------|  
|PROCEDURE_CAT|**String**|Der Name der Datenbank, in der sich die angegebene gespeicherte Prozedur befindet.|  
|PROCEDURE_SCHEM|**String**|Das Schema für die gespeicherte Prozedur.|  
|PROCEDURE_NAME|**String**|Name der gespeicherten Prozedur|  
|NUM_INPUT_PARAMS|**int**|Reserviert für zukünftige Verwendung. Gibt derzeit den Wert "-1" zurück.|  
|NUM_OUTPUT_PARAMS|**int**|Reserviert für zukünftige Verwendung. Gibt derzeit den Wert "-1" zurück.|  
|NUM_RESULT_SETS|**int**|Reserviert für zukünftige Verwendung. Gibt derzeit den Wert "-1" zurück.|  
|ANMERKUNGEN|**String**|Die Beschreibung der Prozedurspalte.<br /><br /> <br /><br /> **Hinweis:** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gibt für diese Spalte keinen Wert zurück.|  
|PROCEDURE_TYPE|**smallint**|Der Typ der gespeicherten Prozedur. Es kann sich um einen der folgenden Werte handeln:<br /><br /> SQL_PT_UNKNOWN (0)<br /><br /> SQL_PT_PROCEDURE (1)<br /><br /> SQL_PT_FUNCTION (2)|  
  
> [!NOTE]  
>  Weitere Informationen zu den Daten, die von der getProcedures-Methode zurückgegeben werden, finden Sie in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Onlinedokumentation unter „sp_stored_procedures (Transact-SQL)“.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie mithilfe der getProcedures-Methode Informationen zur gespeicherten Prozedur „uspGetBillOfMaterials“ aus der [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]-Beispieldatenbank zurückgegeben werden können.  
  
```  
public static void executeGetProcedures(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getProcedures(null, null, "uspGetBillOfMaterials");  
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
  
  
