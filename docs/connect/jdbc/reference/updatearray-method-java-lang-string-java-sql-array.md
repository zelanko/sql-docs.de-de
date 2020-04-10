---
title: updateArray-Methode (java.lang.String, java.sql.Array) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateArray (java.lang.String, java.sql.Array)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6f2ced5a-1c7d-439a-aaa5-472b9f4fdeab
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fabe48fed129a4139dc5b2873cd81a6448972a3e
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80926054"
---
# <a name="updatearray-method-javalangstring-javasqlarray"></a>updateArray-Methode (java.lang.String, java.sql.Array)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aktualisiert die angegebene Spalte mit einem Array-Objekt unter Berücksichtigung des Spaltennamens.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void updateArray(java.lang.String columnName,  
                        java.sql.Array x)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnName*  
  
 Eine **Zeichenfolge**, die den Spaltennamen enthält.  
  
 *x*  
  
 Ein Arrayobjekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese updateArray-Methode wird von der updateArray-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [updateArray-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatearray-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
