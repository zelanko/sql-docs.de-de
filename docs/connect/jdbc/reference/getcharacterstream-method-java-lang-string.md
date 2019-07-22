---
title: getcharakteristream-Methode (Java. lang. String) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getCharacterStream (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: cdddc572-05c1-480d-b3e5-28270001575c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 174deb24d78821e30d69dc899c5657909241ad3d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67953283"
---
# <a name="getcharacterstream-method-javalangstring"></a>getCharacterStream-Methode (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den Wert des angegebenen Spaltennamens in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als java.io.Reader-Objekt ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.io.Reader getCharacterStream(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnName*  
  
 Eine **Zeichenfolge**, die den Spaltennamen enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Reader-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese getcharakteristream-Methode wird von der getcharakteristream-Methode in der Java. SQL. Resultset-Schnittstelle angegeben.  
  
 Mit dieser Methode werden nur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Unicodezeichen-Datentypen wie „nchar“, „nvarchar“, „nvarchar(max)“ und „ntext“ gelesen. Alle anderen Datentypen, einschließlich der ASCII-Zeichentypen lösen eine Ausnahme aus. Verwenden Sie zum Lesen der ASCII-Datentypen die [getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlserverresultset.md)-Methode.  
  
## <a name="see-also"></a>Weitere Informationen  
 [getCharacterStream-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
