---
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
manager: craigg
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 2df4819b14c1dec7aa1203d0a4c3416b59f292e0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47830758"
---
# <a name="catalogupdatelogdbinfo-ssisdb-database"></a>Catalog.update_logdb_info (SSISDB-Datenbank)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Aktualisieren Sie die [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Scale Out-Protokollinformationen.

## <a name="syntax"></a>Syntax

```sql
catalog.update_logdb_info [@server_name = ] server_name, [@connection_string = ] connection_string
```

## <a name="arguments"></a>Argumente
[ @server_name = ] *server_name*  
 Die für die Scale Out-Protokollierung verwendete SQL Server-Instanz. Der *server_name* ist **nvarchar**.  

 [ @connection_string = ] *connection_string*  
 Die Verbindungszeichenfolge, die für Scale Out-Protokollierung verwendet wird. Der *connection_string* ist **nvarchar**.

 ## <a name="return-code-value"></a>Rückgabecodewert  
 0 (Erfolg)  
  
## <a name="result-sets"></a>Resultsets  
 None  

## <a name="permissions"></a>Berechtigungen  
 Diese gespeicherte Prozedur erfordert eine der folgenden Berechtigungen:  
   
-   Mitgliedschaft in der Datenbankrolle **ssis_admin**  
  
-   Mitgliedschaft in der Serverrolle **sysadmin**  
 
