---
title: setTimestamp-Methode für timestamp- und calendar-Werte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setTimestamp (java.lang.String, java.sql.Timestamp, java.util.Calendar))
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 09dca1f9-225a-4acb-9857-9a947e0829be
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c34fb8eedd8349bcf5d86523968d7374132f2636
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80926520"
---
# <a name="settimestamp-method-javalangstring-javasqltimestamp-javautilcalendar"></a>setTimestamp-Methode (java.lang.String, java.sql.Timestamp, java.util.Calendar)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den angegebenen Parameter auf die angegebenen Zeitstempel- und Kalenderwerte fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setTimestamp(java.lang.String sCol,  
                         java.sql.Timestamp x,  
                         java.util.Calendar c)  
```  
  
#### <a name="parameters"></a>Parameter  
 *sCol*  
  
 Ein **String-Objekt**, das den Parameternamen enthält.  
  
 *x*  
  
 Ein Timestamp-Objekt  
  
 *c*  
  
 Ein Calendar-Objekt  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Bemerkungen  
 Diese setTimestamp-Methode wird von der setTimestamp-Methode in der java.sql.CallableStatement-Schnittstelle angegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [setTimestamp-Methode &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/settimestamp-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement-Elemente](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement-Klasse](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
