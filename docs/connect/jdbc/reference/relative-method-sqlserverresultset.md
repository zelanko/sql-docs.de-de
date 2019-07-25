---
title: relative-Methode (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.relative
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2bcdbb69-95fd-4ae8-8488-1a75a91fe2e0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5b2e644feff3cd2787cc6bd80bce54562ad20794
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67975782"
---
# <a name="relative-method-sqlserverresultset"></a>relative-Methode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Versetzt den Cursor relativ zur aktuellen Zeile um die angegebene (positive oder negative) Anzahl von Zeilen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean relative(int nRows)  
```  
  
#### <a name="parameters"></a>Parameter  
 *nRows*  
  
 Ein Wert vom Typ **int**, der die Anzahl der zu verschiebenden Zeilen angibt.  
  
## <a name="return-value"></a>Rückgabewert  
 **true** , wenn sich der Cursor in einer Zeile befindet. Andernfalls lautet der Wert **false**.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese relative Methode wird durch die relative Methode in der Java. SQL. Resultset-Schnittstelle angegeben.  
  
 Wenn versucht wird, den Cursor über die erste oder letzte Zeile im Resultset hinaus zu verschieben, wird er vor oder hinter der ersten bzw. letzten Reihe positioniert. Der Aufruf von `relative(0)` ist gültig, hat jedoch keine Auswirkungen auf die Position des Cursors.  
  
 Der Aufruf der Methode `relative(1)` ist mit dem Aufruf der [next](../../../connect/jdbc/reference/next-method-sqlserverresultset.md)-Methode identisch. Der Aufruf der Methode `relative(-1)` ist mit dem Aufruf der [previous](../../../connect/jdbc/reference/previous-method-sqlserverresultset.md)-Methode identisch.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
