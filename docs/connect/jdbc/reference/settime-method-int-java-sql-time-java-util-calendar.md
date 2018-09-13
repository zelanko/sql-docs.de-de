---
title: setTime-Methode (int, java.sql.Time, java.util.Calendar) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setTime (int, java.sql.Time, java.lang.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 79ff6eef-6ad7-4e33-95be-c2d552c65546
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4aa26ba8f24ae349cddab42874b373c77b1df216
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42787387"
---
# <a name="settime-method-int-javasqltime-javautilcalendar"></a>setTime-Methode (int, java.sql.Time, java.util.Calendar)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den angegebenen Parameter auf die angegebenen Zeit- und Kalenderwerte fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public final void setTime(int n,  
                          java.sql.Time x,  
                          java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Parameter  
 *n*  
  
 Ein Wert **ganzzahliger** Wert zum Angeben der Parameternummer.  
  
 *x*  
  
 Ein Uhrzeit-Objekt.  
  
 *CAL*  
  
 Ein Kalenderobjekt.  
  
## <a name="exceptions"></a>Ausnahmen  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Diese setTime-Methode wird von der setTime-Methode in der java.sql.PreparedStatement-Schnittstelle angegeben.  
  
 Beginnend mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0, das Verhalten dieser Methode wird geändert, indem die **SendTimeAsDatetime** Connection-Eigenschaft ([Festlegen der Verbindungseigenschaften](../../../connect/jdbc/setting-the-connection-properties.md)) und [ SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).  
  
 Weitere Informationen finden Sie unter [Configuring How java.sql.Time Values are Sent to the Server (Konfigurieren der Art und Weise, wie java.sql.Time-Werte an den Server gesendet werden)](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [setTime-Methode &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/settime-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement-Elemente](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement-Klasse](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
