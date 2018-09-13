---
title: GetCharacterStream-Methode (java.lang.String) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerResultSet.getCharacterStream (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: cdddc572-05c1-480d-b3e5-28270001575c
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f8d1df393d88348a8645a78ecd11a170c8d9d746
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42785945"
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
 Ein Readerobjekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese GetCharacterStream-Methode wird von der GetCharacterStream-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Mit dieser Methode werden nur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Unicodezeichen-Datentypen wie „nchar“, „nvarchar“, „nvarchar(max)“ und „ntext“ gelesen. Alle anderen Datentypen, einschließlich der ASCII-Zeichentypen lösen eine Ausnahme aus. Verwenden Sie zum Lesen der ASCII-Datentypen die [getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlserverresultset.md)-Methode.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [getCharacterStream-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
