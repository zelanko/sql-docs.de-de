---
title: GetSendTimeAsDatetime-Methode (SQLServerDataSource) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: f18836d12be9834512783f90a2d7730fcfc98798
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47845208"
---
# <a name="getsendtimeasdatetime-method-sqlserverdatasource"></a>getSendTimeAsDatetime-Methode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Diese Methode wurde im JDBC-Treiber 3.0 für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hinzugefügt.  
  
 Gibt die Einstellung der **SendTimeAsDatetime** Connection-Eigenschaft.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public boolean getSendTimeAsDatetime();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 **"true"** Wenn java.sql.Time-Werte an den Server gesendet werden, werden eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **"DateTime"** Typ. **"false"** Wenn java.sql.Time-Werte an den Server gesendet werden, werden eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **Zeit** Typ.  
  
## <a name="remarks"></a>Remarks  
 Finden Sie unter [Festlegen der Verbindungseigenschaften](../../../connect/jdbc/setting-the-connection-properties.md) für Weitere Informationen zu den **SendTimeAsDatetime** Connection-Eigenschaft.  
  
 Mit [SQLServerDataSource.setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md) können Sie die Verbindungseigenschaft **sendTimeAsDatetime** programmgesteuert festlegen.  
  
 Weitere Informationen finden Sie unter [Configuring How java.sql.Time Values are Sent to the Server (Konfigurieren der Art und Weise, wie java.sql.Time-Werte an den Server gesendet werden)](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerDataSource-Elemente](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource-Klasse](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
