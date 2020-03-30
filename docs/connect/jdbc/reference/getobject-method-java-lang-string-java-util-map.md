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
- SQLServerCallableStatement.getObject (java.lang.String, Java.util.Map)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e174eb81-d569-479e-a171-365cd6d44b6a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8803ead9f5ec779a024a0f1980b0e3dab3a746ca
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67981152"
---
# <a name="getobject-method-javalangstring-javautilmap"></a>getObject-Methode (java.lang.String, java.util.Map)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den Wert des angegebenen Parameters unter Berücksichtigung des Parameternamens und unter Verwendung des angegebenen Map-Objekts als Objekt in der Programmiersprache Java ab.  
  
> [!NOTE]  
>  Diese Methode wird von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] derzeit nicht unterstützt. Bei Verwendung dieser Methode wird immer die Standardzuordnung zurückgegeben.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.lang.Object getObject(java.lang.String sCol,  
                                  java.util.Map m)  
```  
  
#### <a name="parameters"></a>Parameter  
 *sCol*  
  
 Ein **String-Objekt**, das den Parameternamen enthält.  
  
 *m*  
  
 Ein Map-Objekt  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **Object**-Wert.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getObject-Methode wird von der getObject-Methode in der java.sql.CallableStatement-Schnittstelle angegeben.  
  
 Von dieser Methode wird der Wert der angegebenen Spalte als Java-Objekt zurückgegeben. Beim Typ des Java-Objekts handelt es sich um den standardmäßigen Java-Objekttyp, der dem SQL-Typ der Spalte entspricht. Die Grundlage hierfür bildet die in der JDBC-Spezifikation angegebene Zuordnung für integrierte Typen. Bei einem SQL-NULL-Wert wird vom Treiber ein Java-NULL-Wert zurückgegeben.  
  
 Diese Methode kann auch zum Lesen datenbankspezifischer, abstrakter Datentypen verwendet werden. In der JDBC 2.0-API wird das Verhalten der getObject-Methode erweitert, um Daten von benutzerdefinierten SQL-Typen zu materialisieren. Enthält eine Spalte einen strukturierten oder eindeutigen Wert, entspricht das Verhalten dieser Methode einem Aufruf von `getObject(columnIndex, this.getStatement().getConnection().getTypeMap())`.  
  
 Ab dem JDBC-Treiber 3.0 für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] wird folgendermaßen verfahren:  
  
-   Ein **date**-Wert wird als java.sql.Date-Objekt zurückgegeben.  
  
-   Ein **time**-Wert wird als java.sql.Time-Objekt zurückgegeben.  
  
-   Ein **datetime2**-Wert wird als java.sql.Timestamp-Objekt zurückgegeben.  
  
-   Ein **datetimeoffset**-Wert wird als microsoft.sql.DateTimeOffset-Objekt zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [getObject-Methode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getobject-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement-Klasse](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
