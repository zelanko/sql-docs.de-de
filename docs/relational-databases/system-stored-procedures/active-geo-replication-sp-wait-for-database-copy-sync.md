---
title: sp_wait_for_database_copy_sync
titleSuffix: Azure SQL Database
ms.date: 03/03/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sp_wait_for_database_copy_sync_TSQL
- sp_wait_for_database_copy_sync
dev_langs:
- TSQL
helpviewer_keywords:
- sp_wait_for_database_copy_sync
ms.assetid: 7068da7f-cb74-47f2-b064-eb076a0d3885
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.custom: seo-dt-2019
ms.openlocfilehash: 931babcaa6e229d6114930bba5f06803aa25f59e
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82829682"
---
# <a name="active-geo-replication---sp_wait_for_database_copy_sync"></a>Aktive georeplikation-sp_wait_for_database_copy_sync
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Diese Prozedur ist auf eine [!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)] -Beziehung zwischen einer primären und sekundären Datenbank beschränkt. Wenn **sp_wait_for_database_copy_sync** aufgerufen wird, wartet die Anwendung, bis alle Transaktionen, für die ein Commit ausgeführt wurde, repliziert und durch die aktive sekundäre Datenbank bestätigt wurden. Führen Sie **sp_wait_for_database_copy_sync** nur in der primären Datenbank aus.  
  
||  
|-|  
|**Gilt für**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].|  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_wait_for_database_copy_sync [ @target_server = ] 'server_name'   
     , [ @target_database = ] 'database_name'  
```  
  
## <a name="arguments"></a>Argumente  
 [ @target_server =] ' server_name '  
 Der Name des SQL-Datenbankservers, der die aktive sekundäre Datenbank hostet. server_name ist vom Datentyp sysname und hat keinen Standardwert.  
  
 [ @target_database = ] 'database_name'  
 Der Name der aktiven sekundären Datenbank. database_name ist vom Datentyp sysname und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Gibt 0 für Erfolg oder eine Fehlernummer für Fehler zurück.  
  
 Die häufigsten Fehler sind:  
  
-   Der Servername oder der Datenbankname fehlt.  
  
-   Die Verbindung zum angegebenen Servernamen oder der angegebenen Serverdatenbank kann nicht gefunden werden.  
  
-   Interlink-Konnektivität ist unterbrochen. **sp_wait_for_database_copy_sync** wird nach dem Verbindungstimeout zurückgegeben.  
  
## <a name="permissions"></a>Berechtigungen  
 Jeder Benutzer in der primären Datenbank kann diese gespeicherte Systemprozedur aufrufen. Die Anmeldung muss einem Benutzer der primären und aktiven sekundären Datenbank entsprechen.  
  
## <a name="remarks"></a>Bemerkungen  
 Alle Transaktionen, für die vor einem Aufruf von **sp_wait_for_database_copy_sync** ein Commit ausgeführt wurde, werden an die aktive sekundäre Datenbank gesendet.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird **sp_wait_for_database_copy_sync** aufgerufen, um sicherzustellen, dass alle Transaktionen, für die ein Commit in der primären Datenbank db0 ausgeführt wurde, an die jeweilige aktive sekundäre Datenbank auf dem Zielserver ubfyu5ssyt gesendet werden.  
  
```  
USE db0;  
GO  
EXEC sys.sp_wait_for_database_copy_sync @target_server = N'ubfyu5ssyt1', @target_database = N'db0';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys. dm_continuous_copy_status &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-continuous-copy-status-azure-sql-database.md)   
 [Dynamische Verwaltungs Sichten für die georeplikation (DMVs) und Funktionen &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-dynamic-management-views/geo-replication-dynamic-management-views-and-functions-azure-sql-database.md)   
 [sys.dm_geo_replication_link_status](../system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md)
  
  
