---
title: GetProcedureColumns-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getProcedureColumns
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4f0df8fe-3cd6-46e4-ae3c-dc23c35676b2
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8c71218c709921cd9180bff2b9a6b5997ae7450c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66771197"
---
# <a name="getprocedurecolumns-method-sqlserverdatabasemetadata"></a>getProcedureColumns-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft eine Beschreibung der Parameter gespeicherter Prozeduren und Ergebnisspalten ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.ResultSet getProcedureColumns(java.lang.String sCatalog,  
                                              java.lang.String sSchema,  
                                              java.lang.String proc,  
                                              java.lang.String col)  
```  
  
#### <a name="parameters"></a>Parameter  
 *sCatalog*  
  
 Ein **String-Objekt**, das den Katalognamen enthält. Durch Festlegen dieses Parameters auf NULL wird angegeben, dass der Katalogname nicht verwendet werden muss.  
  
 *sSchema*  
  
 Ein **String-Objekt**, das das Schemanamenmuster enthält. Durch Festlegen dieses Parameters auf NULL wird angegeben, dass der Schemaname nicht verwendet werden muss.  
  
 *proc*  
  
 Ein **String-Objekt**, das das Prozedurnamenmuster enthält.  
  
 *col*  
  
 Ein **String-Objekt**, das das Spaltennamensmuster enthält. Wird für diesen Parameter NULL angegeben, wird für jede Spalte eine Zeile zurückgegeben.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese GetProcedureColumns-Methode wird von der GetProcedureColumns-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
 Das von der getProcedureColumns-Methode zurückgegebene Resultset enthält folgende Informationen:  
  
|Name|Typ|und Beschreibung|  
|----------|----------|-----------------|  
|PROCEDURE_CAT|**String**|Der Name der Datenbank, in der sich die angegebene gespeicherte Prozedur befindet.|  
|PROCEDURE_SCHEM|**String**|Das Schema für die gespeicherte Prozedur.|  
|PROCEDURE_NAME|**String**|Name der gespeicherten Prozedur|  
|COLUMN_NAME|**String**|Name der Spalte.|  
|COLUMN_TYPE|**short**|Der Typ der Spalte. Mögliche Werte:<br /><br /> procedureColumnUnknown (0)<br /><br /> procedureColumnIn (1)<br /><br /> procedureColumnInOut (2)<br /><br /> procedureColumnOut (4)<br /><br /> procedureColumnReturn (5)<br /><br /> procedureColumnResult (3)|  
|DATA_TYPE|**smallint**|Der SQL-Datentyp aus "java.sql.Types".|  
|TYPE_NAME|**String**|Der Name des Datentyps.|  
|PRECISION|**ssNoversion**|Die Gesamtanzahl von signifikanten Stellen.|  
|LENGTH|**ssNoversion**|Die Länge der Daten in Bytes.|  
|SCALE|**short**|Die Anzahl der Ziffern rechts vom Dezimaltrennzeichen.|  
|RADIX|**short**|Die Basis für numerische Typen.|  
|NULLABLE|**short**|Gibt an, ob die Spalte einen NULL-Wert enthalten kann. Mögliche Werte:<br /><br /> procedureNoNulls (0)<br /><br /> procedureNullable (1)<br /><br /> procedureNullableUnknown (2)|  
|REMARKS|**String**|Die Beschreibung der Prozedurspalte.<br /><br /> <br /><br /> **Hinweis:** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gibt für diese Spalte keinen Wert zurück.|  
|COLUMN_DEF|**String**|Der Standardwert der Spalte.|  
|SQL_DATA_TYPE|**smallint**|Diese Spalte entspricht der **DATA_TYPE**-Spalte mit Ausnahme der **datetime**- und ISO-**interval**-Datentypen.|  
|SQL_DATETIME_SUB|**smallint**|Wenn **SQL_DATA_TYPE** den Wert **SQL_DATETIME** oder **SQL_INTERVAL** aufweist, enthält diese Spalte den Subcode für **datetime** ISO **interval**. Bei allen Datentypen außer **"DateTime"** und ISO **Intervall**, diese Spalte ist NULL.|  
|CHAR_OCTET_LENGTH|**ssNoversion**|Die maximale Anzahl von Bytes in der Spalte.|  
|ORDINAL_POSITION|**ssNoversion**|Der Index der Spalte innerhalb der Tabelle.|  
|IS_NULLABLE|**String**|Gibt an, ob in der Spalte NULL-Werte zulässig sind.|  
|SS_TYPE_CATALOG_NAME|**String**|Der Name des Katalogs, der den benutzerdefinierten Typ (UDT) enthält.|  
|SS_TYPE_SCHEMA_NAME|**String**|Der Name des Schemas, der den benutzerdefinierten Typ (UDT) enthält.|  
|SS_UDT_CATALOG_NAME|**String**|Der benutzerdefinierte Typ (UDT) für den vollqualifizierten Namen.|  
|SS_UDT_SCHEMA_NAME|**String**|Der Name des Katalogs, in dem ein XML-Schemasammlungsname definiert ist. Wenn der Katalogname nicht gefunden werden kann, enthält diese Variable eine leere Zeichenfolge.|  
|SS_UDT_ASSEMBLY_TYPE_NAME|**String**|Der Name des Schemas, in dem eine XML-Schemaauflistung definiert ist. Wenn der Schemaname nicht gefunden werden kann, handelt es sich dabei um eine leere Zeichenfolge.|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|**String**|Name der XML-Schemaauflistung. Wenn der Name nicht gefunden werden kann, handelt es sich dabei um eine leere Zeichenfolge.|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|**String**|Der Name des Katalogs, der den benutzerdefinierten Typ (UDT) enthält.|  
|SS_XML_SCHEMACOLLECTION_NAME|**String**|Der Name des Schemas, der den benutzerdefinierten Typ (UDT) enthält.|  
|SS_DATA_TYPE|**tinyint**|Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentyp, der von erweiterten gespeicherten Prozeduren verwendet wird.<br /><br /> <br /><br /> **Hinweis:** Weitere Informationen zu den Datentypen, die von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zurückgegeben werden, finden Sie in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Onlinedokumentation unter „Datentypen (Transact-SQL)“.|  
  
> [!NOTE]  
>  Weitere Informationen zu den Daten, die von der getProcedureColumns-Methode zurückgegeben werden, finden Sie in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Onlinedokumentation unter „sp_sproc_columns (Transact-SQL)“.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie mithilfe der getProcedureColumns-Methode Informationen zur gespeicherten Prozedur „uspGetBillOfMaterials“ aus der [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]-Beispieldatenbank zurückgegeben werden können.  
  
```  
public static void executeGetProcedureColumns(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getProcedureColumns(null, null, "uspGetBillOfMaterials", null);  
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
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
