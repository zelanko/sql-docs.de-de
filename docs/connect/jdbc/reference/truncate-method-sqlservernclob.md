---
title: Truncate-Methode (SQLServerNClob) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b7e8210d-a724-4bae-832a-ae4c63031c9c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f9ed19679cb1a173d015152a006f55660fe9f826
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67968465"
---
# <a name="truncate-method-sqlservernclob"></a>truncate-Methode (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Kürzt das **NCLOB** auf die angegebene Länge.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void truncate(long len)  
```  
  
#### <a name="parameters"></a>Parameter  
 *len*  
  
 Die Länge (in Zeichen), auf die der **NCLOB**-Wert gekürzt werden soll.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Truncate-Methode wird von der Truncate-Methode in der Java. SQL. NCLOB-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerNClob-Methoden](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob-Elemente](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob-Klasse](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
