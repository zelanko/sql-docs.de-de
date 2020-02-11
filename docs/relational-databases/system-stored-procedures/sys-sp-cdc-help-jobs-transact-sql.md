---
title: sys. sp_cdc_help_jobs (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cdc_help_jobs
- sys.sp_cdc_help_jobs_TSQL
- sp_cdc_help_jobs_TSQL
- sys.sp_cdc_help_jobs
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_help_jobs
ms.assetid: 9399b4bc-8293-408f-b3cb-f904e0657fb5
author: rothja
ms.author: jroth
ms.openlocfilehash: 9820476ecdee25551d09c8206595b637421b9efd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68083726"
---
# <a name="syssp_cdc_help_jobs-transact-sql"></a>sys.sp_cdc_help_jobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Stellt Informationen über alle Cleanup- oder Aufzeichnungsaufträge für Change Data Capture in der aktuellen Datenbank bereit.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.sp_cdc_help_jobs  
```  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**job_id**|**uniqueidentifier**|Die ID des Auftrags.|  
|**job_type**|**nvarchar (20)**|Typ des Auftrags.|  
|**maxtrans**|**int**|Die maximale Anzahl von Transaktionen, die in jedem Scanvorgang verarbeitet werden sollen.<br /><br /> **maxtrans** ist nur für Aufzeichnungs Aufträge gültig.|  
|**maxscans**|**int**|Die maximale Anzahl der Scan Zyklen, die ausgeführt werden müssen, um alle Zeilen aus dem Protokoll zu extrahieren.<br /><br /> **maxscans** ist nur für Aufzeichnungs Aufträge gültig.|  
|**Continuous**|**bit**|Flag, das angibt, ob der Aufzeichnungsauftrag fortlaufend (1) oder einmalig (0) ausgeführt werden soll. Weitere Informationen finden Sie unter [sys. sp_cdc_add_job &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md).<br /><br /> **Continuous** ist nur für Aufzeichnungs Aufträge gültig.|  
|**PollingInterval**|**BIGINT**|Anzahl der Sekunden zwischen Protokollscanzyklen.<br /><br /> **PollingInterval** ist nur für Aufzeichnungs Aufträge gültig.|  
|**zurück**|**BIGINT**|Anzahl der Minuten, die Änderungszeilen in Änderungstabellen beibehalten werden sollen.<br /><br /> die **Beibehaltung** ist nur für Cleanupaufträge gültig.|  
|**Mindest**|**BIGINT**|Die maximale Anzahl von Einträgen für Löschvorgänge, die mit einer einzelnen Anweisung beim Cleanup gelöscht werden können.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **db_owner** Fixed-Daten Bank Rolle.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden Informationen zu den definierten Aufzeichnungs- und Cleanupaufträgen für die `AdventureWorks2012`-Datenbank zurückgegeben.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_cdc_help_jobs;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [dbo. cdc_jobs &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)   
 [sys. sp_cdc_add_job &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)  
  
  
