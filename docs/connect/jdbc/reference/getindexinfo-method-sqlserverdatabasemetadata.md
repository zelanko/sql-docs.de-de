---
title: getIndexInfo-Methode (SQLServerDatabaseMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getIndexInfo
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8a677cc6-8e33-4e57-8678-0849345aa8d0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8dd512236aa3070ce299756d4e4294c79ac2e94a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67982793"
---
# <a name="getindexinfo-method-sqlserverdatabasemetadata"></a>getIndexInfo-Methode (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft eine Beschreibung der Indizes und der Statistik für die angegebene Tabelle ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.ResultSet getIndexInfo(java.lang.String cat,  
                                       java.lang.String schema,  
                                       java.lang.String table,  
                                       boolean unique,  
                                       boolean approximate)  
```  
  
#### <a name="parameters"></a>Parameter  
 *cat*  
  
 Ein **String-Objekt**, das den Katalognamen enthält.  
  
 *schema*  
  
 Ein **String-Objekt**, das den Schemanamen enthält.  
  
 *table*  
  
 Ein **String-Objekt**, das den Tabellennamen enthält.  
  
 *unique*  
  
 **true** , wenn nur Indizes für eindeutige Werte zurückgegeben werden. **false** , wenn alle Indizes zurückgegeben werden.  
  
 *approximate*  
  
 **true** , wenn die Ergebnisse ungefähre oder veraltete Werte widerspiegeln. **false** , wenn die Ergebnisse korrekt sind.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese getIndexInfo-Methode wird von der getIndexInfo-Methode in der java.sql.DatabaseMetaData-Schnittstelle angegeben.  
  
 Das von der getIndexInfo-Methode zurückgegebene Resultset enthält folgende Informationen:  
  
|Name|Typ|und Beschreibung|  
|----------|----------|-----------------|  
|TABLE_CAT|**String**|Der Name der Datenbank, in der sich die angegebene Tabelle befindet.|  
|TABLE_SCHEM|**String**|Das Schema der Tabelle.|  
|table_name|**String**|Der Name der Tabelle.|  
|NON_UNIQUE|**boolean**|Gibt an, ob die Indexwerte nicht eindeutig sein können.|  
|INDEX_QUALIFIER|**String**|Der Name des Indexbesitzers. Wenn für TYPE das tableIndexStatistic-Objekt eingetragen wird, entspricht er NULL.|  
|INDEX_NAME|**String**|Der Name des Index.|  
|TYPE|**short**|Der Typ des Indexes. Mögliche Werte:<br /><br /> tableIndexStatistic (0)<br /><br /> tableIndexClustered (1)<br /><br /> tableIndexHashed (2)<br /><br /> tableIndexOther (3)|  
|ORDINAL_POSITION|**short**|Die Ordinalposition der Spalte innerhalb des Indexes. Die erste Spalte im Index hat den Wert 1.|  
|COLUMN_NAME|**String**|Name der Spalte.|  
|ASC_OR_DESC|**String**|Der in der Indexsortierung verwendete Befehl. Mögliche Werte:<br /><br /> A (aufsteigend)<br /><br /> D (absteigend)<br /><br /> NULL (nicht anwendbar)<br /><br /> **Hinweis:** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gibt immer A zurück.|  
|CARDINALITY|**int**|Die Anzahl der Zeilen in der Tabelle oder der eindeutigen Werte im Index|  
|PAGES|**int**|Die Anzahl der Seiten, die zum Speichern des Indexes oder der Tabelle verwendet werden.|  
|FILTER_CONDITION|**String**|Die Filter-Bedingung.<br /><br /> **Hinweis:** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] gibt immer NULL zurück.|  
  
> [!NOTE]  
>  Weitere Informationen zu den Daten, die von der getIndexInfo-Methode zurückgegeben werden, finden Sie in der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Onlinedokumentation unter „sp_indexes (Transact-SQL)“.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie mithilfe der getIndexInfo-Methode Informationen über die Indizes und Statistiken der Tabelle „Person.Contact“ aus der [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]-Beispieldatenbank zurückgegeben werden können.  
  
```  
public static void executeGetIndexInfo(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getIndexInfo("AdventureWorks", "Person", "Contact", false, true);  
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
  
  
