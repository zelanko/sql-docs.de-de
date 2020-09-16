---
description: getCharacterStream-Methode (int)
title: getCharacterStream(int)-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getCharacterStream (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4f9f230d-be4c-469a-b3dc-f24531429aae
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fae765e165eaefd67caf5f07e32c4d61f479c74a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88436862"
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
 Ein Reader-Objekt  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getCharacterStream-Methode wird von der getCharacterStream-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Mit dieser Methode werden nur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Unicodezeichen-Datentypen wie „nchar“, „nvarchar“, „nvarchar(max)“ und „ntext“ gelesen. Alle anderen Datentypen, einschließlich der ASCII-Zeichentypen lösen eine Ausnahme aus. Verwenden Sie zum Lesen der ASCII-Datentypen die [getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlserverresultset.md)-Methode.  
  
## <a name="see-also"></a>Weitere Informationen  
 [getCharacterStream-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
