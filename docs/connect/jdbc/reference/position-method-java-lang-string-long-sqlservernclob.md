---
title: position-Methode (java.lang.String, long) (SQLServerNClob) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 46d4beec-831a-449f-98b6-322a80cc499a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fe0bf76df2f2350b76ad6f817b621d01ae2410dc
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80914336"
---
# <a name="position-method-javalangstring-long-sqlservernclob"></a>position-Methode (java.lang.String, long) (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft die Zeichenposition ab, an der sich die angegebene *searchstr*-Teilzeichenfolge im **NCLOB**-Wert befindet, der von diesem **NClob**-Objekt dargestellt wird  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public long position(java.lang.String searchstr,  
              long start)  
```  
  
#### <a name="parameters"></a>Parameter  
 *searchstr*  
  
 Die Teilzeichenfolge, nach der gesucht werden soll  
  
 *start*  
  
 Die Position, an der mit der Suche begonnen wird. Die erste Position ist "1".  
  
## <a name="return-value"></a>Rückgabewert  
 Die Position, an der sich die Teilzeichenfolge befindet, oder "-1", wenn sie nicht vorhanden ist. Die erste Position ist "1".  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese position-Methode wird von der position-Methode in der java.sql.NClob-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [position-Methode &#40;SQLServerNClob&#41;](../../../connect/jdbc/reference/position-method-sqlservernclob.md)   
 [SQLServerNClob-Methoden](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob-Elemente](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob-Klasse](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
