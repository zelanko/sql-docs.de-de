---
description: MSsync_states (Transact-SQL)
title: MSsync_states (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsync_states
- MSsync_states_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsync_states system table
ms.assetid: b25e17e1-7718-432e-a442-c4946741d474
author: markingmyname
ms.author: maghan
ms.openlocfilehash: bc3ef439c3d5027e64eb988730c41c3f9bea12d9
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89545484"
---
# <a name="mssync_states-transact-sql"></a>MSsync_states (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  In der **MSsync_states** Tabelle wird nachverfolgt, welche Veröffentlichung noch im gleichzeitigen Momentaufnahme Modus ist. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|Die ID des Verlegers.|  
|**publisher_db**|**sysname**|Der Name der Veröffentlichungs Datenbank.|  
|**publication_id**|**int**|Die ID der Veröffentlichung.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zuordnung von Systemtabellen zu System Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Integration Services Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/integration-services-tables-transact-sql.md)   
 [Sichern und Wiederherstellen von Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [Protokollversandtabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/log-shipping-tables-transact-sql.md)  
  
  
