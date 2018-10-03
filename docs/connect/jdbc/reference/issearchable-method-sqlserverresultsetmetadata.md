---
title: IsSearchable-Methode (SQLServerResultSetMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSetMetaData.isSearchable
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 10cf54f9-ef42-475e-8397-790306934573
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eccee93632d466d5799ddda6b19aebc462a68743
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47597894"
---
# <a name="issearchable-method-sqlserverresultsetmetadata"></a>isSearchable-Methode (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt an, ob die angegebene Spalte in einer SQL-Klausel vom Typ "WHERE" verwendet werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean isSearchable(int column)  
```  
  
#### <a name="parameters"></a>Parameter  
 *column*  
  
 Ein **ganzzahliger** Wert, der den Spaltenindex angibt.  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** , wenn die Spalte die Spalte in einer WHERE-Klausel verwendet werden kann. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese IsSearchable-Methode wird von der IsSearchable-Methode in der java.sql.ResultSetMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerResultSetMetaData-Methoden](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [SQLServerResultSetMetaData-Elemente](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData-Klasse](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
