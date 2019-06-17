---
title: dbo.sysoperators (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysoperators
- dbo.sysoperators
- dbo.sysoperators_TSQL
- sysoperators_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysoperators system table
ms.assetid: c2afa20c-b15f-46ca-ae74-2eb65909409e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3796714cbdfb55900447bf23904136ac5abefa9c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62470657"
---
# <a name="dbosysoperators-transact-sql"></a>dbo.sysoperators (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jeden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agentoperator.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|ID des Operators.|  
|**name**|**sysname**|Name des Operators.|  
|**enabled**|**tinyint**|Status der Warnbenachrichtigungen (Boolesch). Beträgt der Wert **1**, kann dieser Operator Benachrichtigungen erhalten, wenn eine Warnung auftritt.|  
|**email_address**|**nvarchar(100)**|E-Mail-Adresse für diesen Operator.|  
|**last_email_date**|**int**|Datum, an dem dieser Operator zuletzt eine Warnbenachrichtigung per E-Mail erhalten hat.|  
|**last_email_time**|**int**|Tageszeit, zu der dieser Operator zuletzt eine Warnbenachrichtigung per E-Mail erhalten hat.|  
|**pager_address**|**nvarchar(100)**|Pageradresse für diesen Operator.|  
|**last_pager_date**|**int**|Datum, an dem dieser Operator zuletzt eine Warnbenachrichtigung per Pager erhalten hat.|  
|**last_pager_time**|**int**|Tageszeit, zu der dieser Operator zuletzt eine Warnbenachrichtigung per Pager erhalten hat.|  
|**weekday_pager_start_time**|**int**|Tageszeit an einem Arbeitstag (Montag bis Freitag), von der an dieser Operator zur Verfügung steht, um eine Warnbenachrichtigung per Pager zu erhalten.|  
|**weekday_pager_end_time**|**int**|Tageszeit an einem Arbeitstag (Montag bis Freitag), von der an dieser Operator nicht zur Verfügung steht, um eine Warnbenachrichtigung per Pager zu erhalten.|  
|**saturday_pager_start_time**|**int**|Tageszeit an einem Samstag, von der an dieser Operator zur Verfügung steht, um eine Warnbenachrichtigung per Pager zu erhalten.|  
|**saturday_pager_end_time**|**int**|Tageszeit an einem Samstag, von der an dieser Operator nicht zur Verfügung steht, um eine Warnbenachrichtigung per Pager zu erhalten.|  
|**sunday_pager_start_time**|**int**|Tageszeit an einem Sonntag, von der an dieser Operator zur Verfügung steht, um eine Warnbenachrichtigung per Pager zu erhalten.|  
|**sunday_pager_end_time**|**int**|Tageszeit an einem Sonntag, von der an dieser Operator nicht zur Verfügung steht, um eine Warnbenachrichtigung per Pager zu erhalten.|  
|**pager_days**|**tinyint**|Bitmaske, die die Arbeitstage darstellt, an denen dieser Operator zur Verfügung steht, um eine Warnbenachrichtigung per Pager zu erhalten.|  
|**netsend_address**|**nvarchar(100)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**last_netsend_date**|**int**|Datum, an dem die neueste Netzwerkmeldung zuletzt an die angegebene Operator-ID gesendet wurde.|  
|**last_netsend_time**|**int**|Uhrzeit, zu der die neueste Netzwerkmeldung zuletzt an die angegebene Operator-ID gesendet wurde.|  
|**category_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Server-Agent-Tabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)  
  
  
