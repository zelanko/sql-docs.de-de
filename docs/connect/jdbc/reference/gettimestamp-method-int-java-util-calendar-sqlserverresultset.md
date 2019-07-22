---
title: getTimestamp-Methode (int, java.util.Calendar) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getTimestamp (int, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f2dd5688-7344-437a-8716-7024fb8e9c31
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c4022d3a90e81ba3d4de73aab88b740108584c5f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67978892"
---
# <a name="gettimestamp-method-int-javautilcalendar-sqlserverresultset"></a>getTimestamp-Methode (int, java.util.Calendar) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft unter Verwendung eines Calendar-Objekts den Wert des angegebenen Spaltenindexes in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als java.sql.Timestamp-Objekt in der Programmiersprache Java ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.Timestamp getTimestamp(int columnIndex,  
                                       java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnIndex*  
  
 Ein **ganzzahliger** Wert, der den Spaltenindex angibt.  
  
 *cal*  
  
 Ein Kalender Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Timestamp-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese getTimestamp-Methode wird von der getTimestamp-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Von dieser Methode werden nur Werte aus datetime- und smalldatetime-Spalten von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [getTimestamp-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/gettimestamp-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
