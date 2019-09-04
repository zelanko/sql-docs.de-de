---
title: getcolumnclassname-Methode (SQLServerResultSetMetaData) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSetMetaData.getColumnClassName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2c118790-5dd2-4b10-93b6-7f065ee324ce
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 37c791c80c679afd70f4f1d2f3f2770fb0f38a16
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67952995"
---
# <a name="getcolumnclassname-method-sqlserverresultsetmetadata"></a>getColumnClassName-Methode (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Gibt den vollqualifizierten Namen der Java-Klasse zurück, deren Instanzen erstellt werden, wenn die [getObject](../../../connect/jdbc/reference/getobject-method-sqlserverresultset.md)-Methode der [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Klasse aufgerufen wird, um einen Wert aus der Spalte abzurufen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.lang.String getColumnClassName(int column)  
```  
  
#### <a name="parameters"></a>Parameter  
 *column*  
  
 Ein **ganzzahliger** Wert, der den Spaltenindex angibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine **Zeichenfolge**, die den vollqualifizierten Namen der Klasse enthält.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getcolumnclassname-Methode wird von der getcolumnclassname-Methode in der Java. SQL. ResultSetMetaData-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSetMetaData-Methoden](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [SQLServerResultSetMetaData-Elemente](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData-Klasse](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
