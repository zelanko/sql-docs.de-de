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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0accd21f53a4ba1a86e4b7555be9d2ba9a087474
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80921048"
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
  
  
