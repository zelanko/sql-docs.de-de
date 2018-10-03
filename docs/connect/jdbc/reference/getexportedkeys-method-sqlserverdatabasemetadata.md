---
title: GetExportedKeys-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getExportedKeys
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 26888e61-b243-4a1b-922c-c0a451dcff4d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 91c4b7bdcf360047cc02a53f4bc013b3e3d972e7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47839978"
---
# <a name="getexportedkeys-method-sqlserverdatabasemetadata"></a>getExportedKeys-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft eine Beschreibung der Fremdschlüsselspalten ab, von denen auf die Primärschlüsselspalten der angegebenen Tabelle verwiesen wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.ResultSet getExportedKeys(java.lang.String cat,  
                                          java.lang.String schema,  
                                          java.lang.String table)  
```  
  
#### <a name="parameters"></a>Parameter  
 *cat*  
  
 Ein **String-Objekt**, das den Katalognamen enthält.  
  
 *schema*  
  
 Ein **String-Objekt**, das den Schemanamen enthält.  
  
 *table*  
  
 Ein **String-Objekt**, das den Tabellennamen enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese GetExportedKeys-Methode wird von der GetExportedKeys-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
 Das von der getExportedKeys-Methode zurückgegebene Resultset enthält folgende Informationen:  
  
|Name|Typ|und Beschreibung|  
|----------|----------|-----------------|  
|PKTABLE_CAT|**String**|Der Name des Katalogs, der die Primärschlüsseltabelle enthält.|  
|PKTABLE_SCHEM|**String**|Der Name des Schemas der Primärschlüsseltabelle.|  
|PKTABLE_NAME|**String**|Der Name der Primärschlüsseltabelle.|  
|PKCOLUMN_NAME|**String**|Der Spaltenname des Primärschlüssels.|  
|FKTABLE_CAT|**String**|Der Name des Katalogs, der die Fremdschlüsseltabelle enthält.|  
|FKTABLE_SCHEM|**String**|Der Name des Schemas der Fremdschlüsseltabelle.|  
|FKTABLE_NAME|**String**|Der Name der Fremdschlüsseltabelle.|  
|FKCOLUMN_NAME|**String**|Der Spaltenname des Fremdschlüssels.|  
|KEY_SEQ|**short**|Die Sequenznummer der Spalte bei einem Primärschlüssel, der durch mehrere Spalten definiert wird.|  
|UPDATE_RULE|**short**|Die auf den Fremdschlüssel angewendete Aktion, wenn es sich beim SQL-Vorgang um ein Update handelt. Mögliche Werte:<br /><br /> importedKeyNoAction (3)<br /><br /> importedKeyCascade (0)<br /><br /> importedKeySetNull (2)<br /><br /> importedKeySetDefault (4)<br /><br /> importedKeyRestrict (1)|  
|DELETE_RULE|**short**|Die auf den Fremdschlüssel angewendete Aktion, wenn es sich beim SQL-Vorgang um eine Löschung handelt. Mögliche Werte:<br /><br /> importedKeyNoAction (3)<br /><br /> importedKeyCascade (0)<br /><br /> importedKeySetNull (2)<br /><br /> importedKeySetDefault (4)<br /><br /> importedKeyRestrict (1)|  
|FK_NAME|**String**|Der Name des Fremdschlüssels.|  
|PK_NAME|**String**|Der Name des Primärschlüssels.|  
|DEFERRABILITY|**short**|Zeigt an, ob die Auswertung der Fremdschlüsseleinschränkung bis zur Ausführung einer Commit-Aktion verzögert werden kann. Mögliche Werte:<br /><br /> importedKeyInitiallyDeferred (5)<br /><br /> importedKeyInitiallyImmediate (6)<br /><br /> importedKeyNotDeferrable (7)|  
  
> [!NOTE]  
>  Weitere Informationen zu den Daten, die von der getExportedKeys-Methode zurückgegeben werden, finden Sie in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Onlinedokumentation unter „sp_fkeys (Transact-SQL)“.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie mithilfe der getExportedKeys-Methode Informationen zu allen Fremdschlüsseln, die auf die Primärschlüssel der Tabelle „Person.Contac“ in der [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]-Beispieldatenbank verweisen, zurückgegeben werden.  
  
```  
public static void executeGetExportedKeys(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getExportedKeys("AdventureWorks", "Person", "Contact");  
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
  
  
