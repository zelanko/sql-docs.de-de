---
title: getCrossReference-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getCrossReference
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 099dd0bf-b017-479d-9696-f5b06f4c6bf9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f23da4d83217fbed39e6dddacfe92541eae0db23
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67984219"
---
# <a name="getcrossreference-method-sqlserverdatabasemetadata"></a>getCrossReference-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft eine Beschreibung der Fremdschlüsselspalten in der angegebenen Fremdschlüsseltabelle ab, von der auf die Primärschlüsselspalten der angegebenen Primärschlüsseltabelle verwiesen wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.ResultSet getCrossReference(java.lang.String cat1,  
                                            java.lang.String schem1,  
                                            java.lang.String tab1,  
                                            java.lang.String cat2,  
                                            java.lang.String schem2,  
                                            java.lang.String tab2)  
```  
  
#### <a name="parameters"></a>Parameter  
 *cat1*  
  
 Ein **String-Objekt**, das den Katalognamen der Tabelle enthält, die den Primärschlüssel enthält.  
  
 *schem1*  
  
 Ein **String-Objekt**, das den Schemanamen der Tabelle enthält, die den Primärschlüssel enthält.  
  
 *tab1*  
  
 Ein **String-Objekt**, das den Tabellennamen der Tabelle enthält, die den Primärschlüssel enthält.  
  
 *cat2*  
  
 Ein **String-Objekt**, das den Katalognamen der Tabelle enthält, die den Fremdschlüssel enthält.  
  
 *schem2*  
  
 Ein **String-Objekt**, das den Schemanamen der Tabelle enthält, die den Fremdschlüssel enthält.  
  
 *tab2*  
  
 Ein **String-Objekt**, das den Tabellennamen der Tabelle enthält, die den Fremdschlüssel enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getCrossReference-Methode wird von der getCrossReference-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
 Das von der getCrossReference-Methode zurückgegebene Resultset enthält die folgenden Informationen:  
  
|Name|type|Beschreibung|  
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
|UPDATE_RULE|**short**|Die auf den Fremdschlüssel angewendete Aktion, wenn es sich beim SQL-Vorgang um ein Update handelt. Es kann sich um einen der folgenden Werte handeln:<br /><br /> importedKeyNoAction (3)<br /><br /> importedKeyCascade (0)<br /><br /> importedKeySetNull (2)<br /><br /> importedKeySetDefault (4)<br /><br /> importedKeyRestrict (1)|  
|DELETE_RULE|**short**|Die auf den Fremdschlüssel angewendete Aktion, wenn es sich beim SQL-Vorgang um eine Löschung handelt. Es kann sich um einen der folgenden Werte handeln:<br /><br /> importedKeyNoAction (3)<br /><br /> importedKeyCascade (0)<br /><br /> importedKeySetNull (2)<br /><br /> importedKeySetDefault (4)<br /><br /> importedKeyRestrict (1)|  
|FK_NAME|**String**|Der Name des Fremdschlüssels.|  
|PK_NAME|**String**|Der Name des Primärschlüssels.|  
|DEFERRABILITY|**short**|Zeigt an, ob die Auswertung der Fremdschlüsseleinschränkung bis zur Ausführung einer Commit-Aktion verzögert werden kann. Es kann sich um einen der folgenden Werte handeln:<br /><br /> importedKeyInitiallyDeferred (5)<br /><br /> importedKeyInitiallyImmediate (6)<br /><br /> importedKeyNotDeferrable (7)|  
  
> [!NOTE]  
>  Weitere Informationen zu den Daten, die von der getCrossReference-Methode zurückgegeben werden, finden Sie in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Onlinedokumentation unter „sp_fkeys (Transact-SQL)“.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird dargestellt, wie die getCrossReference-Methode zur Rückgabe von Informationen über die Primär- und Fremdschlüsselbeziehung zwischen der Person.Contact- und der HumanResources.Employee-Tabelle in der [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]-Beispieldatenbank verwendet wird.  
  
```  
public static void executeGetCrossReference(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getCrossReference("AdventureWorks", "Person", "Contact", null, "HumanResources", "Employee");  
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
  
  
