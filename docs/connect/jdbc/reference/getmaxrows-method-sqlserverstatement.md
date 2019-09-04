---
title: getMaxRows-Methode (SQLServerStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getMaxRows
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6aece4e5-027d-434e-a8cf-a67c0484f189
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e0b9df5512466c5f12c5fda1b4e5cb4a91504499
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67982073"
---
# <a name="getmaxrows-method-sqlserverstatement"></a>getMaxRows-Methode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft die maximale Anzahl von Zeilen ab, die ein [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekt enthalten kann, das von diesem [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)-Objekt erstellt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final int getMaxRows()  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Wert vom Typ **int** zum Angeben der maximalen Zeilenanzahl oder 0 (null), wenn kein Grenzwert vorhanden ist.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getMaxRows-Methode wird von der getMaxRows-Methode in der Java. SQL. Statement-Schnittstelle angegeben.  
  
 Die getMaxRows-Methode gibt für dynamische, scrollfähige Cursor immer 0 zurück.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerStatement-Elemente](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement-Klasse](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
