---
title: UpdateRef-Methode (java.lang.String, java.sql.Ref) | Microsoft Docs
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
- SQLServerResultSet.updateRef (java.lang.String, java.sql.Ref)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7740d17d-282f-4f1d-91f9-c68a873b069a
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5d58ec2c5fd5a6e1826058e26bdfb295cac818e6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
ms.locfileid: "32852105"
---
# <a name="updateref-method-javalangstring-javasqlref"></a>updateRef-Methode (java.lang.String, java.sql.Ref)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Aktualisiert die angegebene Spalte unter Berücksichtigung des Spaltennamens mit einem java.sql.Ref-Wert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void updateRef(java.lang.String columnName,  
                      java.sql.Ref x)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnName*  
  
 Ein **Zeichenfolge** , die den Namen der Spalte enthält.  
  
 *x*  
  
 Ein Ref-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Hinweise  
 Diese UpdateRef-Methode wird von der UpdateRef-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [UpdateRef-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateref-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
