---
title: log_shipping_monitor_alert (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- log_shipping_monitor_alert
- log_shipping_monitor_alert_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_monitor_alert system table
ms.assetid: 1c775e48-9898-4149-b9d1-04d465f23438
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 98cf21802910299e73b4839e93451080993228db
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85890205"
---
# <a name="log_shipping_monitor_alert-transact-sql"></a>log_shipping_monitor_alert (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Speichert die Warnungsauftrags-ID für den Protokollversand. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.   
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**alert_job_id**|**uniqueidentifier**|Die Auftrags-ID des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents für den Warnungsauftrag des Protokollversands.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Informationen zum Protokollversand &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_add_log_shipping_alert_job &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-alert-job-transact-sql.md)   
 [sp_delete_log_shipping_alert_job &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-alert-job-transact-sql.md)   
 [sp_help_log_shipping_alert_job &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-log-shipping-alert-job-transact-sql.md)   
 [Systemtabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
