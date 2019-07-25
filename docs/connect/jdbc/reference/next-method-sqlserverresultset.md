---
title: next-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.next
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 60248447-6908-4036-a779-a501453cd553
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c83fe6aa33d77db98fcdfc757b9bf219a45a9b15
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67976760"
---
# <a name="next-method-sqlserverresultset"></a>next-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Versetzt den Cursor von seiner aktuellen Position aus um eine Zeile nach unten.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean next()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **true** , wenn die neue aktuelle Zeile gültig ist. **false** , wenn keine weiteren zu verarbeitenden Zeilen vorhanden sind.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese next-Methode wird von der next-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Ein Resultsetcursor wird anfänglich vor dieser Zeile positioniert. Beim ersten Aufruf der next-Methode wird die erste Zeile zur aktuellen Zeile, beim zweiten Aufruf wird die zweite Zeile zur aktuellen Zeile usw.  
  
 Wenn für die aktuelle Zeile ein Eingabedatenstrom geöffnet ist, wird dieser durch einen Aufruf der next-Methode implizit geschlossen. Beim Lesen einer neuen Zeile wird eine Warnkette für das [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt gelöscht.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
