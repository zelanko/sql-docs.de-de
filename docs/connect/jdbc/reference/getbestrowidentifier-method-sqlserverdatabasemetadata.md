---
title: getBestRowIdentifier-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getBestRowIdentifier
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c19e9ca6-2a53-4a0c-91ab-80090c3f7229
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9a19bd01a8ebf54eb3e819bd4a82400b8107e382
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67954029"
---
# <a name="getbestrowidentifier-method-sqlserverdatabasemetadata"></a>getBestRowIdentifier-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft eine Beschreibung der optimalen Gruppe von Spalten einer Tabelle ab, durch die eine Zeile eindeutig identifiziert wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.ResultSet getBestRowIdentifier(java.lang.String catalog,  
                                               java.lang.String schema,  
                                               java.lang.String table,  
                                               int scope,  
                                               boolean nullable)  
```  
  
#### <a name="parameters"></a>Parameter  
 *catalog*  
  
 Ein **String-Objekt**, das den Katalognamen enthält.  
  
 *schema*  
  
 Ein **String-Objekt**, das den Schemanamen enthält.  
  
 *Tabelle*  
  
 Ein **String-Objekt**, das den Tabellennamen enthält.  
  
 *scope*  
  
 Ein Wert vom Typ **int** zum Angeben des relevanten Bereichs. Die Werte können Folgendes enthalten:  
  
 bestRowTemporary (0)  
  
 bestRowTransaction (1)  
  
 bestRowSession (2)  
  
 *nullable*  
  
 **TRUE**, um Spalten einzufügen, die NULL-Werte zulassen. Andernfalls lautet der Wert **false**.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getBestRowIdentifier-Methode wird von der getBestRowIdentifier-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
 Das von der getBestRowIdentifier-Methode zurückgegebene Resultset enthält die folgenden Informationen:  
  
|Name|type|Beschreibung|  
|----------|----------|-----------------|  
|SCOPE|short|Der Bereich der zurückgegebenen Ergebnisse. Es kann sich um einen der folgenden Werte handeln:<br /><br /> bestRowTemporary (0)<br /><br /> bestRowTransaction (1)<br /><br /> bestRowSession (2)|  
|COLUMN_NAME|String|Name der Spalte.|  
|DATA_TYPE|short|Der SQL-Datentyp aus "java.sql.Types".|  
|TYPE_NAME|String|Der Name des Datentyps.|  
|COLUMN_SIZE|INT|Die Genauigkeit der Spalte.|  
|BUFFER_LENGTH|INT|Die Pufferlänge.|  
|DECIMAL_DIGITS|short|Die Dezimalstellen der Spalte.|  
|PSEUDO_COLUMN|short|Gibt an, ob die Spalte eine Pseudospalte ist. Es kann sich um einen der folgenden Werte handeln:<br /><br /> bestRowUnknown (0)<br /><br /> bestRowNotPseudo (1)<br /><br /> bestRowPseudo (2)|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie mithilfe der getBestRowIdentifier-Methode Informationen zum geeignetsten Zeilenidentifizierer für die Tabelle „Person.Contact“ aus der [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]-Beispieldatenbank zurückgegeben werden können.  
  
```  
public static void executeGetBestRowIdentifier(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getBestRowIdentifier(null, "Person", "Contact", 0, true);  
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
  
  
