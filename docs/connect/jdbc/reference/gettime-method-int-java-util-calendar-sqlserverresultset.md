---
title: getTime-Methode (int, java.util.Calendar) (SQLServerResultSet) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getTime (int, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d21e0c1d-9d6e-468f-8b11-cc7209b2c2e5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 31e6d09782746d72ac7073cca99f8e55736e08ef
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927468"
---
# <a name="gettime-method-int-javautilcalendar-sqlserverresultset"></a>getTime-Methode (int, java.util.Calendar) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ruft unter Verwendung des angegebenen Calendar-Objekts den Wert des angegebenen Spaltenindexes in der aktuellen Zeile dieses [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)-Objekts als java.sql.Time-Objekt in Java ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public java.sql.Time getTime(int columnIndex,  
                             java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Parameter  
 *columnIndex*  
  
 Ein **ganzzahliger** Wert, der den Spaltenindex angibt.  
  
 *cal*  
  
 Ein Calendar-Objekt  
  
## <a name="return-value"></a>Rückgabewert  
 Ein Time-Objekt  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese getTime-Methode wird von der getTime-Methode in der java.sql.ResultSet-Schnittstelle angegeben.  
  
 Von dieser Methode wird ein gültiger Uhrzeitteil eines [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-datetime- oder smalldatetime-Datentyps zurückgegeben. Der Datumsteil ist dabei in der im Kalender angegebenen Zeitzone auf die Java-Datumsbaseline 1.1.1970 festgelegt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [getTime-Methode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/gettime-method-sqlserverresultset.md)   
 [SQLServerResultSet-Elemente](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet-Klasse](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
