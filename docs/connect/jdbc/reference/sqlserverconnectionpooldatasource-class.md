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
ms.openlocfilehash: bb073be8ef92d44f8821078f60622341638a010d
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67971651"
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
  
## <a name="remarks"></a>Bemerkungen  
 SQLServerConnectionPoolDataSource wird üblicherweise in Java Application Server-Umgebungen verwendet, von denen integrierte Verbindungspools unterstützt werden und zum Bereitstellen physischer Verbindungen eine ConnectionPoolDataSource-Klasse benötigt wird – beispielsweise Java EE-Anwendungsserver (Java Platform Enterprise Edition), von denen Verbindungspools gemäß der Spezifikation der JDBC 3.0-API bereitgestellt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLServerConnectionPoolDataSource-Elemente](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-members.md)   
 [API-Referenz für den JDBC-Treiber](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
