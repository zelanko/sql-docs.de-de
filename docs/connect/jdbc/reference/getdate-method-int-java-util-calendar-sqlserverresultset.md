---
title: getDate-Methode (int, java.util.Calendar) (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getDate (int, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 150411f7-2a73-4380-b921-9698acd5d1f9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 17f2762975f72ccd1e6482ea7120701eacf0c4c7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67984076"
---
# <a name="getdate-method-int-javautilcalendar-sqlserverresultset"></a>getDate-Methode (int, java.util.Calendar) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft unter Verwendung des angegebenen Calendar-Objekts den Wert des angegebenen Spaltenindexes in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als java.sql.Date-Objekt in der Programmiersprache Java ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.Date getDate(int columnIndex,  
                             java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnIndex*  
  
 Ein **ganzzahliger** Wert, der den Spaltenindex angibt.  
  
 *cal*  
  
 Ein Kalender Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Date-Objekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese getDate-Methode wird von der getDate-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Von dieser Methode wird ein gültiger Datumsteil eines datetime- oder smalldatetime-Datentyps von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zurückgegeben. Der Zeitteil ist dabei in der im Kalender angegebenen Zeitzone auf die Java-Baseline 00:00 (Mitternacht) festgelegt.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [getDate-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getdate-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
