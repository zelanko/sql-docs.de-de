---
title: isCurrency-Methode (SQLServerResultSetMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSetMetaData.isCurrency
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7fe25d90-693c-4d3b-9dd2-0f8351c5a9ed
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 33d21e8bfe8a774d8b5b21584ba9fd3f02246f4e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67977685"
---
# <a name="iscurrency-method-sqlserverresultsetmetadata"></a>isCurrency-Methode (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt an, ob es sich bei der angegebenen Spalte um einen Währungswert handelt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean isCurrency(int column)  
```  
  
#### <a name="parameters"></a>Parameter  
 *column*  
  
 Ein **ganzzahliger** Wert, der den Spaltenindex angibt.  
  
## <a name="return-value"></a>Rückgabewert  
 **true** , wenn die Spalte ein Bargeld Wert ist. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese isCurrency-Methode wird von der isCurrency-Methode in der Java. SQL. ResultSetMetaData-Schnittstelle angegeben.  
  
 Von dieser Methode wird nur bei den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentypen money und smallmoney **TRUE** zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSetMetaData-Methoden](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [SQLServerResultSetMetaData-Elemente](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData-Klasse](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
