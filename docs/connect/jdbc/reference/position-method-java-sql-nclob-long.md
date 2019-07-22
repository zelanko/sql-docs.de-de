---
title: Position-Methode (Java. SQL. NCLOB, Long) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f2354278-d128-4cf4-a170-22c05fcb763b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ea868190b635a9471bfad424d6fc74572970799b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67976361"
---
# <a name="position-method-javasqlnclob-long"></a>position-Methode (java.sql.NClob, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft die Zeichenposition ab, an der das angegebene **NCLOB** -Objekt *SearchStr* in diesem **NCLOB** -Objekt angezeigt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
long position(java.sql.NClob searchstr,  
              long start)  
```  
  
#### <a name="parameters"></a>Parameter  
 *searchstr*  
  
 Ein zu suchendes NClob-Objekt.  
  
 *start*  
  
 Die Position, an der mit der Suche begonnen wird. Die erste Position ist "1".  
  
## <a name="return-value"></a>Rückgabewert  
 Die Position, an der sich die Teilzeichenfolge befindet, oder "-1", wenn sie nicht vorhanden ist. Die erste Position ist "1".  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese Positions Methode wird von der Positions Methode in der Java. SQL. NCLOB-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Positions Methode &#40;SQLServerNClob&#41;](../../../connect/jdbc/reference/position-method-sqlservernclob.md)   
 [SQLServerNClob-Methoden](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob-Elemente](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob-Klasse](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
