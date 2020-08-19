---
description: sp_syscollector_set_cache_directory (Transact-SQL)
title: sp_syscollector_set_cache_directory (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_set_cache_directory_TSQL
- sp_syscollector_set_cache_directory
dev_langs:
- TSQL
helpviewer_keywords:
- data collector [SQL Server], stored procedures
- sp_syscollector_set_cache_directory stored procedure
ms.assetid: df56d5a5-8961-494f-a745-d752ca63805a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: dd4f3a049a0433ed41c9ebb1f82f6f16f6222544
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88469189"
---
# <a name="sp_syscollector_set_cache_directory-transact-sql"></a>sp_syscollector_set_cache_directory (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt das Verzeichnis an, in dem die aufgelisteten Daten gespeichert werden, bevor sie in das Verwaltungs-Data Warehouse hochgeladen werden.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syscollector_set_cache_directory [ @cache_directory = ] 'cache_directory'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @cache_directory = ] 'cache_directory'` Das Verzeichnis im Dateisystem, in dem die gesammelten Daten temporär gespeichert werden. *cache_directory* ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL. Wenn kein Wert angegeben ist, wird das temporäre Verzeichnis [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 Sie müssen den Datensammler deaktivieren, bevor Sie die Konfiguration für das Cacheverzeichnis ändern. Bei dieser gespeicherten Prozedur tritt ein Fehler auf, wenn der Datensammler aktiviert ist. Weitere Informationen finden Sie unter [Aktivieren oder Deaktivieren der Datensammlung](../../relational-databases/data-collection/enable-or-disable-data-collection.md)und [Verwalten der Datensammlung](../../relational-databases/data-collection/manage-data-collection.md).  
  
 Das angegebene Verzeichnis muss zu dem Zeitpunkt, zu dem die sp_syscollector_set_cache_directory ausgeführt wird, nicht vorhanden sein. die Daten können jedoch erst erfolgreich zwischengespeichert und hochgeladen werden, wenn das Verzeichnis erstellt wurde. Sie sollten das Verzeichnis erstellen, bevor Sie diese gespeicherte Prozedur ausführen.  
  
## <a name="permissions"></a>Berechtigungen  
 Damit diese Prozedur ausgeführt werden kann, ist die Mitgliedschaft in der festen Datenbankrolle dc_admin (mit EXECUTE-Berechtigung) erforderlich.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Datensammler deaktiviert, das Cache Verzeichnis für den Datensammler auf festgelegt `D:\tempdata` und der Datensammler anschließend aktiviert.  
  
```sql  
USE msdb;  
GO  
EXECUTE dbo.sp_syscollector_disable_collector;  
GO  
EXEC dbo.sp_syscollector_set_cache_directory N'D:\tempdata';  
GO  
EXECUTE dbo.sp_syscollector_enable_collector;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren für den Datensammler &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [sp_syscollector_set_cache_window &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-set-cache-window-transact-sql.md)  
  
  
