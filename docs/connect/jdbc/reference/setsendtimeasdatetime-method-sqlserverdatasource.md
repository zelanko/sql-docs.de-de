---
title: setsendtimeasdatetime-Methode (SQLServerDataSource) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 705a0494-b5e2-43db-940a-1b8cec550cdb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 293667d8e3e06fb5eda7a74fdeed58c89fb0f1ae
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67972960"
---
# <a name="setsendtimeasdatetime-method-sqlserverdatasource"></a>setSendTimeAsDatetime-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Diese Methode wurde im JDBC-Treiber 3.0 für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hinzugefügt.  
  
 Ändert die Einstellung der **sendtimeasdatetime** -Verbindungs Eigenschaft.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public void setSendTimeAsDatetime(boolean sendTimeAsDateTime)  
```  
  
#### <a name="parameters"></a>Parameter  
 *sendTimeAsDateTime*  
  
 Ein boolescher Wert. Wenn TRUE, werden java.sql.Time-Werte als **datetime**-Typen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] an den Server zurückgegeben. Wenn FALSE, werden java.sql.Time-Werte als **time**-Typen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] an den Server zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 [SQLServerDataSource.getSendTimeAsDatetime](../../../connect/jdbc/reference/getsendtimeasdatetime-method-sqlserverdatasource.md) gibt die Einstellung der Verbindungseigenschaft **sendTimeAsDatetime** zurück.  
  
 Weitere Informationen zur **sendtimeasdatetime** -Verbindungs Eigenschaft finden Sie unter [Festlegen der Verbindungs Eigenschaften](../../../connect/jdbc/setting-the-connection-properties.md).  
  
 Weitere Informationen finden Sie unter [Configuring How java.sql.Time Values are Sent to the Server (Konfigurieren der Art und Weise, wie java.sql.Time-Werte an den Server gesendet werden)](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
