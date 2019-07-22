---
title: getBytes-Methode (java.lang.String) (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getBytes (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ff617165-47f8-41c1-9c51-37ffc7714923
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4591a91d1adb924801a39a132a0f20c68579e31b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67953383"
---
# <a name="getbytes-method-javalangstring-sqlserverresultset"></a>getBytes-Methode (java.lang.String) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den Wert des angegebenen Spaltennamens in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als Array vom Typ **byte** in der Programmiersprache Java ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public byte[] getBytes(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnName*  
  
 Eine **Zeichenfolge**, die den Spaltennamen enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Array von **Byte** Werten.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese getBytes-Methode wird von der getBytes-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Von dieser Methode wird das Abrufen aller Spalten als unaufbereitete Bytes vom Server unterstützt. Sie gibt ein Bytearray direkt vom Server in einem Format wieder, das auf dem Server gespeichert ist.  
  
 In einer früheren Version von [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] konnten Sie mithilfe von „SQLServerResultSet.getBytes“ Werte zwischen Bytearrays und dem [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentyp **date**, **time**, **datetime2** oder **datetimeoffset** konvertieren. Nun wird durch Verwendung der Methode mit diesen Datentypen eine Ausnahme ausgelöst, die angibt, dass die Konvertierung nicht unterstützt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [getBytes-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getbytes-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
