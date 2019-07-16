---
title: Sys.database_automatic_tuning_options (Transact-SQL) | Microsoft-Dokumentation
description: Informationen Sie zum Anzeigen der Optionen für die automatischer Optimierung für eine SQL-Datenbank
ms.custom: ''
ms.date: 07/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- database_automatic_tuning_options_tsql
- database_automatic_tuning_options
- sys.database_automatic_tuning_options_tsql
- sys.database_automatic_tuning_options
dev_langs:
- TSQL
helpviewer_keywords:
- database_automatic_tuning_options catalog view
- sys.database_automatic_tuning_options catalog view
ms.assetid: 16b47d55-8019-41ff-ad34-1e0112178067
author: jovanpop-msft
ms.author: jovanpop
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 437dbbc4ea7deb32a9723febb443cc67941fdc5e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67940226"
---
# <a name="sysdatabaseautomatictuningoptions-transact-sql"></a>Sys.Database\_automatische\_Tuning_options (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

  Die automatische Optimierung von Optionen für diese Datenbank zurückgegeben.  

|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar(128)**|Der Name der Option "Automatische Optimierung". Finden Sie unter [ALTER DATABASE festgelegt AUTOMATIC_TUNING &#40;Transact-SQL&#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md) für die verfügbaren Optionen.|  
|**desired_state**|**smallint**|Gibt an, den gewünschten Betriebsmodus für die automatische Optimierung-Option, die explizit vom Benutzer festgelegt.<br />0 = OFF<br />1 = ON|  
|**desired_state_desc**|**nvarchar(60)**|Textbeschreibung für den gewünschten Betriebsmodus des automatischen Optimierungsoption.<br />OFF<br />ON|  
|**actual_state**|**smallint**|Gibt an, den Betriebsmodus des automatischen Optimierungsoption.<br />0 = OFF<br />1 = ON|  
|**actual_state_desc**|**nvarchar(60)**|Die textbeschreibung der tatsächlichen Betriebsmodus des automatischen Optimierungsoption.<br />OFF<br />ON|  
|**reason**|**smallint**|Gibt an, warum die tatsächlichen und den gewünschten Status unterschiedlich sind.<br />2 = DEAKTIVIERT<br />11 = QUERY_STORE_OFF<br />12 = QUERY_STORE_READ_ONLY<br />13 = NOT_SUPPORTED|   
|**reason_desc**|**nvarchar(60)**|Die textbeschreibung der Grund, warum die tatsächlichen und den gewünschten Status unterschiedlich sind.<br />DEAKTIVIERT = Option ist deaktiviert, vom System<br />QUERY_STORE_OFF = Query Store ist deaktiviert.<br />QUERY_STORE_READ_ONLY = Query Store befindet sich im schreibgeschützten Modus<br />NOT_SUPPORTED = verfügbar nur in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise Edition| 
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die `VIEW DATABASE STATE`-Berechtigung.  
  
## <a name="see-also"></a>Siehe auch  
 [Die automatische Optimierung](../../relational-databases/automatic-tuning/automatic-tuning.md)   
 [ALTER DATABASE SET AUTOMATIC_TUNING &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [sys.database_query_store_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-query-store-options-transact-sql.md)   
 [dm_db_tuning_recommendations &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-tuning-recommendations-transact-sql.md)   
 
