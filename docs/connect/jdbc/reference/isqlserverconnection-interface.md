---
title: ISQLServerConnection-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 031c01e2-2c65-4fe4-9700-fdbcc7a39f30
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 0f979ef1a15a07866e5331849130a7089acb1cea
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66796433"
---
# <a name="isqlserverconnection-interface"></a>ISQLServerConnection-Schnittstelle
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Stellt eine JDBC-Verbindung mit einer [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbank dar. Diese Schnittstelle wurde im JDBC-Treiber 3.0 für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] hinzugefügt.  
  
 **Paket:** com.microsoft.sqlserver.jdbc  
  
 **Erweitert:** java.sql.Connection  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public interface ISQLServerConnection  
```  
  
## <a name="remarks"></a>Remarks  
 Diese Schnittstelle wird implementiert von [SQLServerConnection-Klasse](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
 Diese Schnittstelle macht das folgende [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-spezifische Feld verfügbar:  
  
|Feld|Weitere Informationen finden Sie unter|  
|-----------|-------------------------------|  
|öffentliches final static int TRANSACTION_SNAPSHOT|[TRANSACTION_SNAPSHOT](../../../connect/jdbc/reference/transaction-snapshot-field-sqlserverconnection.md)|  
|öffentliche UUID getClientConnectionId()|[getClientConnectionID()](../../../connect/jdbc/reference/getclientconnectionid-method-sqlserverconnection.md)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [API-Referenz für den JDBC-Treiber](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
