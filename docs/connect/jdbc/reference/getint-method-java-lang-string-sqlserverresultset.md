---
title: getInt-Methode (java.lang.String) (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getInt (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 76b7054d-46dd-4d87-93a4-a7ea2ae9b7fd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 31acd78f47af77ea034e653a0857aac182804d4d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67982730"
---
# <a name="getint-method-javalangstring-sqlserverresultset"></a>getInt-Methode (java.lang.String) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den Wert des angegebenen Spaltennamens in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als Wert vom Typ **int** in der Programmiersprache Java ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public int getInt(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnName*  
  
 Eine **Zeichenfolge**, die den Spaltennamen enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **int** -Wert.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getInt-Methode wird von der getInt-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Die Methode wird nur für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentypen unterstützt, die einen ganzzahligen Wert wie „int“, „smallint“, „tinyint“ und „bit“ sicher zurückgeben. Bei Verwendung dieser Methode für andere Datentypen wird eine Ausnahme ausgelöst.  
  
## <a name="see-also"></a>Weitere Informationen  
 [getInt-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getint-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
