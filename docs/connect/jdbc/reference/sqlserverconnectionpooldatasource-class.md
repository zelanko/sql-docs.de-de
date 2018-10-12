---
title: SQLServerConnectionPoolDataSource-Klasse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b00e5a90-2af7-4d04-8ef8-256183777dcf
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 416f9dd730bd1cc085f8a48d1b748584037d1b65
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692278"
---
# <a name="sqlserverconnectionpooldatasource-class"></a>SQLServerConnectionPoolDataSource-Klasse
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Stellt die physischen Datenbankverbindungen für Verbindungspool-Manager dar.  
  
 **Paket:** com.microsoft.sqlserver.jdbc  
  
 **Erweitert:** [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
 **Implementiert:** javax.sql.ConnectionPoolDataSource  
  
## <a name="syntax"></a>Syntax  
  
```  
  
public class SQLServerConnectionPoolDataSource  
```  
  
## <a name="remarks"></a>Remarks  
 SQLServerConnectionPoolDataSource wird üblicherweise in Java Application Server-Umgebungen verwendet, von denen integrierte Verbindungspools unterstützt werden und zum Bereitstellen physischer Verbindungen eine ConnectionPoolDataSource-Klasse benötigt wird – beispielsweise Java EE-Anwendungsserver (Java Platform Enterprise Edition), von denen Verbindungspools gemäß der Spezifikation der JDBC 3.0-API bereitgestellt werden.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [SQLServerConnectionPoolDataSource-Elemente](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-members.md)   
 [API-Referenz für den JDBC-Treiber](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
