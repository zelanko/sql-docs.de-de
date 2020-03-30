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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4dd9e30039b0d5ef429b8e729ce36f7b085e5cfc
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "67976467"
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
  
  
