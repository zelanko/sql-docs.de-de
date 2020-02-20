---
title: getObject-Methode (java.lang.String, java.util.Map) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getObject (java.lang.String, java.util.Map)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8104406b-417d-4ff5-9aca-183ee0f76762
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1e806db63799d57ae935f2288c11b70ff35d20a7
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67981216"
---
# <a name="getobject-method-javalangstring-javautilmap-sqlserverresultset"></a>getObject-Methode (java.lang.String, java.util.Map) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft unter Verwendung des Map-Objekts den Wert des angegebenen Spaltennamens in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als Objekt in der Programmiersprache Java ab.  
  
> [!NOTE]  
>  Diese Methode wird von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] derzeit nicht unterstützt. Bei Verwendung dieser Methode wird immer die Standardzuordnung zurückgegeben.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.lang.Object getObject(java.lang.String colName,  
                                  java.util.Map map)  
```  
  
#### <a name="parameters"></a>Parameter  
 *colName*  
  
 Eine **Zeichenfolge**, die den Spaltennamen enthält.  
  
 *map*  
  
 Ein Map-Objekt  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **Object**-Wert.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getObject-Methode wird von der getObject-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Von dieser Methode wird der Wert der angegebenen Spalte als Java-Objekt zurückgegeben. Beim Typ des Java-Objekts handelt es sich um den standardmäßigen Java-Objekttyp, der dem SQL-Typ der Spalte entspricht. Die Grundlage hierfür bildet die in der JDBC-Spezifikation angegebene Zuordnung für integrierte Typen. Bei einem SQL-NULL-Wert wird vom Treiber ein Java-NULL-Wert zurückgegeben.  
  
 Diese Methode kann auch zum Lesen datenbankspezifischer, abstrakter Datentypen verwendet werden. In der JDBC 2.0-API wird das Verhalten der getObject-Methode erweitert, um Daten von benutzerdefinierten SQL-Typen zu materialisieren. Enthält eine Spalte einen strukturierten oder eindeutigen Wert, entspricht das Verhalten dieser Methode einem Aufruf von `getObject(columnIndex, this.getStatement().getConnection().getTypeMap())`.  
  
 Ab dem JDBC-Treiber 3.0 für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] wird folgendermaßen verfahren:  
  
-   Ein Date-Wert wird als java.sql.Date-Objekt zurückgegeben.  
  
-   Ein Time-Wert wird als java.sql.Time-Objekt zurückgegeben.  
  
-   Ein Datetime2-Wert wird als java.sql.Timestamp-Objekt zurückgegeben.  
  
-   Ein Datetimeoffset-Wert wird als microsoft.sql.DateTimeOffset-Objekt zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [getObject-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getobject-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
