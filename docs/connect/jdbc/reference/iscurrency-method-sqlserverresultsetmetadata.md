---
title: IsCurrency-Methode (SQLServerResultSetMetaData) | Microsoft-Dokumentation
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
manager: jroth
ms.openlocfilehash: cf38e568d723f72c673a85d31093ffe7e1bae26f
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66796547"
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
 **"true"** , wenn die Spalte einen Währungswert handelt. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese IsCurrency-Methode wird von der IsCurrency-Methode in der java.sql.ResultSetMetaData-Schnittstelle angegeben.  
  
 Von dieser Methode wird nur bei den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datentypen money und smallmoney **TRUE** zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSetMetaData-Methoden](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [SQLServerResultSetMetaData-Elemente](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData-Klasse](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
