---
description: Catalog.update_logdb_info (SSISDB-Datenbank)
title: Catalog.update_logdb_info (SSISDB-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/18/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
author: haoqian
ms.author: haoqian
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 78a720f0ac29337dd7752fc72fe93ea3a3f91018
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2020
ms.locfileid: "96129653"
---
# <a name="catalogupdate_logdb_info-ssisdb-database"></a>Catalog.update_logdb_info (SSISDB-Datenbank)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE[sqlserver2017](../../includes/applies-to-version/sqlserver2017.md)]

Aktualisieren Sie die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Scale Out-Protokollinformationen.

## <a name="syntax"></a>Syntax

```sql
catalog.update_logdb_info [ @server_name = ] server_name, [ @connection_string = ] connection_string
```

## <a name="arguments"></a>Argumente
[ @server_name = ] *server_name*  
 Die für die Scale Out-Protokollierung verwendete SQL Server-Instanz. Der *server_name* ist **nvarchar**.  

 [ @connection_string = ] *connection_string*  
 Die Verbindungszeichenfolge, die für Scale Out-Protokollierung verwendet wird. Der *connection_string* ist **nvarchar**.

 ## <a name="return-code-value"></a>Rückgabecodewert  
 0 (Erfolg)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  

## <a name="permissions"></a>Berechtigungen  
 Diese gespeicherte Prozedur erfordert eine der folgenden Berechtigungen:  
   
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
 
