---
title: SetTime-Methode (SQLServerCallableStatement) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setTime
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 04ea83b2-db5e-4b46-b016-9e496363827e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e6eb67fd95f4f6383d30c8aed79d374adaccb5e0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47762200"
---
# <a name="settime-method-sqlservercallablestatement"></a>setTime-Methode (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Legt den angegebenen Parameter auf den angegebenen Zeitwert fest.  
  
 Beginnend mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0, das Verhalten dieser Methode wird geändert, indem die **SendTimeAsDatetime** Connection-Eigenschaft ([Festlegen der Verbindungseigenschaften](../../../connect/jdbc/setting-the-connection-properties.md)) und [ SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).  
  
 Weitere Informationen finden Sie unter [Configuring How java.sql.Time Values are Sent to the Server (Konfigurieren der Art und Weise, wie java.sql.Time-Werte an den Server gesendet werden)](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="overload-list"></a>Überladungsliste  
  
|Name|Beschreibung|  
|----------|-----------------|  
|[setTime (java.lang.String, java.sql.Time)](../../../connect/jdbc/reference/settime-method-java-lang-string-java-sql-time.md)|Legt den angegebenen Parameter auf den angegebenen Zeitwert fest.|  
|[setTime (java.lang.String, java.sql.Time, java.util.Calendar)](../../../connect/jdbc/reference/settime-method-java-lang-string-java-sql-time-java-util-calendar.md)|Legt den angegebenen Parameter auf die angegebenen Zeit- und Kalenderwerte fest.|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerCallableStatement-Methoden](../../../connect/jdbc/reference/sqlservercallablestatement-methods.md)   
 [SQLServerCallableStatement-Klasse](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
