---
title: log_shipping_primary_secondaries (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- log_shipping_primary_secondaries_TSQL
- log_shipping_primary_secondaries
dev_langs:
- TSQL
helpviewer_keywords:
- log_shipping_primary_secondaries system table
ms.assetid: 4b315c70-7265-4acd-b35b-a4dbb7881d98
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 61a7bd0550a5f61aa8b3c1d15687aa4ba4b012b6
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82806098"
---
# <a name="log_shipping_primary_secondaries-transact-sql"></a>log_shipping_primary_secondaries (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ordnet jede primäre Datenbank ihren sekundären Datenbanken zu. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  

  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**primary_id**|**uniqueidentifier**|Die ID der primären Datenbank für die Protokollversandkonfiguration.|  
|**secondary_server**|**sysname**|Der Name der sekundären Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] in der Protokoll Versand Konfiguration.|  
|**secondary_database**|**sysname**|Der Name der sekundären Datenbank in der Protokollversandkonfiguration.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Informationen zum Protokoll Versand &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [sp_add_log_shipping_primary_secondary &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-log-shipping-primary-secondary-transact-sql.md)   
 [sp_delete_log_shipping_primary_secondary &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-log-shipping-primary-secondary-transact-sql.md)   
 [sp_help_log_shipping_primary_secondary &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-log-shipping-primary-secondary-transact-sql.md)   
 [Systemtabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
