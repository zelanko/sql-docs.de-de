---
title: getsendtimeasdatetime-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 02287122-5dc1-455d-987f-95fd9a69d503
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e1396ac28a7e41dbf530f7e4a251876f6c340871
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67979945"
---
# <a name="getsendtimeasdatetime-method-sqlserverdatasource"></a>getSendTimeAsDatetime-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Diese Methode wurde im JDBC-Treiber 3.0 für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hinzugefügt.  
  
 Gibt die Einstellung der **sendtimeasdatetime** -Verbindungs Eigenschaft zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean getSendTimeAsDatetime();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **true** , wenn die Java. SQL. Time-Werte als [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **DateTime** -Typ an den Server gesendet werden. **false** , wenn die Java. SQL. Time-Werte als [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **Zeittyp** an den Server gesendet werden.  
  
## <a name="remarks"></a>Remarks  
 Weitere Informationen zur **sendtimeasdatetime** -Verbindungs Eigenschaft finden Sie [unter Festlegen der Verbindungs Eigenschaften](../../../connect/jdbc/setting-the-connection-properties.md) .  
  
 Mit [SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md) können Sie die Verbindungseigenschaft **sendTimeAsDatetime** programmgesteuert festlegen.  
  
 Weitere Informationen finden Sie unter [Configuring How java.sql.Time Values are Sent to the Server (Konfigurieren der Art und Weise, wie java.sql.Time-Werte an den Server gesendet werden)](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
