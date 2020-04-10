---
title: updateObject-Methode (java.lang.String, java.lang.Object, int) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateObject (java.lang.String, java.lang.Object, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 27283ce1-637e-4e2c-91ee-8ad379114ac5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b32c37a278c0498e23988edfb6c8461998540c95
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80919739"
---
# <a name="updateobject-method-javalangstring-javalangobject-int"></a>updateObject-Methode (java.lang.String, java.lang.Object, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aktualisiert die angegebene Spalte mit einem Wert vom Typ **Object** unter Verwendung des angegebenen Spaltennamens und der Dezimalstellen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void updateObject(java.lang.String columnName,  
                         java.lang.Object x,  
                         int scale)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnName*  
  
 Eine **Zeichenfolge**, die den Spaltennamen enthält.  
  
 *obj*  
  
 Ein **Object**-Wert.  
  
 *scale*  
  
 Gilt für java.sql.Types.DECIMAL- oder java.sql.Types.NUMERIC-Typen. Dieser Wert gibt die Anzahl der Dezimalstellen an. Bei allen anderen Typen wird dieser Wert ignoriert.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese updateObject-Methode wird von der updateObject-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [updateObject-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateobject-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
