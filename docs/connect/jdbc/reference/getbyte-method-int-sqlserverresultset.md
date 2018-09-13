---
title: GetByte-Methode (Int) (SQLServerResultSet) | Microsoft-Dokumentation
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
- SQLServerResultSet.getByte (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b22ba097-6cb8-4c5d-916b-6360dd01d2c5
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 984c18407995e577bcafac596e8a7ef94ec7eb1d
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42784916"
---
# <a name="getbyte-method-int-sqlserverresultset"></a>getByte-Methode (int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft den Wert des angegebenen Spaltenindexes in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als Wert vom Typ **byte** in der Programmiersprache Java ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public byte getByte(int columnIndex)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnIndex*  
  
 Ein **ganzzahliger** Wert, der den Spaltenindex angibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Typ **byte**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese GetByte-Methode wird von der GetByte-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Die Methode wird nur unter [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentypen unterstützt, die einen Bytewert wie „tinyint“ oder „bit“ sicher zurückgeben. Bei allen anderen Datentypen wird eine Ausnahme ausgelöst.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [GetByte-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getbyte-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
