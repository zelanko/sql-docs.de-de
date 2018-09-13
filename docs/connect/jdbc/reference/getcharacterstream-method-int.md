---
title: GetCharacterStream-Methode (Int) | Microsoft-Dokumentation
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
- SQLServerResultSet.getCharacterStream (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4f9f230d-be4c-469a-b3dc-f24531429aae
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b11668ad05cd06fac0579f894667b286d25cfbee
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42784208"
---
# <a name="getcharacterstream-method-int"></a>getCharacterStream-Methode (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den Wert des angegebenen Spaltenindexes in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als java.io.Reader-Objekt ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.io.Reader getCharacterStream(int columnIndex)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnIndex*  
  
 Ein **ganzzahliger** Wert, der den Spaltenindex angibt.  
  
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
  
  
