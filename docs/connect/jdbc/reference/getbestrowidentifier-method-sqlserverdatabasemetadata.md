---
title: GetBestRowIdentifier-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 462de181aca55cce38d1e26f7932fe0003a0c323
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47730321"
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
  
 *table*  
  
 Ein **String-Objekt**, das den Tabellennamen enthält.  
  
 *Bereich*  
  
 Ein Wert vom Typ **int** zum Angeben des relevanten Bereichs. Die Werte können Folgendes enthalten:  
  
 bestRowTemporary (0)  
  
 bestRowTransaction (1)  
  
 bestRowSession (2)  
  
 *nullable*  
  
 **"true"** auf NULL festlegbare Spalten einbezogen werden. Andernfalls lautet der Wert **false**.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese GetBestRowIdentifier-Methode wird von der GetBestRowIdentifier-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
 Das von der getBestRowIdentifier-Methode zurückgegebene Resultset enthält die folgenden Informationen:  
  
|Name|Typ|Beschreibung|  
|----------|----------|-----------------|  
|SCOPE|short|Der Bereich der zurückgegebenen Ergebnisse. Mögliche Werte:<br /><br /> bestRowTemporary (0)<br /><br /> bestRowTransaction (1)<br /><br /> bestRowSession (2)|  
|COLUMN_NAME|Zeichenfolge|Name der Spalte.|  
|DATA_TYPE|short|Der SQL-Datentyp aus "java.sql.Types".|  
|TYPE_NAME|Zeichenfolge|Der Name des Datentyps.|  
|COLUMN_SIZE|ssNoversion|Die Genauigkeit der Spalte.|  
|BUFFER_LENGTH|ssNoversion|Die Pufferlänge.|  
|DECIMAL_DIGITS|short|Die Dezimalstellen der Spalte.|  
|PSEUDO_COLUMN|short|Gibt an, ob die Spalte eine Pseudospalte ist. Mögliche Werte:<br /><br /> bestRowUnknown (0)<br /><br /> bestRowNotPseudo (1)<br /><br /> bestRowPseudo (2)|  
  
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
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDatabaseMetaData-Methoden](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData-Elemente](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData-Klasse](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
