---
description: sp_mergemetadataretentioncleanup (Transact-SQL)
title: sp_mergemetadataretentioncleanup (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_mergemetadataretentioncleanup
- sp_mergemetadataretentioncleanup_TSQL
helpviewer_keywords:
- sp_mergemetadataretentioncleanup
ms.assetid: 4e8d6343-2a38-421d-a3f3-c37d437a0f88
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7c0a186852c704a5ab21fd31864de9aa019078df
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88464149"
---
# <a name="sp_mergemetadataretentioncleanup-transact-sql"></a>sp_mergemetadataretentioncleanup (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Führt eine manuelle Bereinigung der Metadaten in den Systemtabellen [MSmerge_genhistory](../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md), [MSmerge_contents](../../relational-databases/system-tables/msmerge-contents-transact-sql.md), [MSmerge_tombstone](../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md), [MSmerge_past_partition_mappings](../../relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql.md)und [MSmerge_current_partition_mappings](../../relational-databases/system-tables/msmerge-current-partition-mappings.md) durch. Diese gespeicherte Prozedur wird auf jedem Verleger und Abonnenten in der Topologie durchgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_mergemetadataretentioncleanup [ [ @num_genhistory_rows = ] num_genhistory_rows OUTPUT ]  
    [ , [ @num_contents_rows = ] num_contents_rows OUTPUT ]   
    [ , [ @num_tombstone_rows = ] num_tombstone_rows OUTPUT ]   
    [ , [ @aggressive_cleanup_only = ] aggressive_cleanup_only ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @num_genhistory_rows = ] num_genhistory_rows OUTPUT` Gibt die Anzahl der Zeilen zurück, die aus der [MSmerge_genhistory](../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md) Tabelle bereinigt wurden. *num_genhistory_rows* ist vom Datentyp **int**und hat den Standardwert **0**.  
  
`[ @num_contents_rows = ] num_contents_rows OUTPUT` Gibt die Anzahl der Zeilen zurück, die aus der [MSmerge_contents](../../relational-databases/system-tables/msmerge-contents-transact-sql.md) Tabelle bereinigt wurden. *num_contents_rows* ist vom Datentyp **int**und hat den Standardwert **0**.  
  
`[ @num_tombstone_rows = ] num_tombstone_rows OUTPUT` Gibt die Anzahl der Zeilen zurück, die aus der [MSmerge_tombstone](../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md) Tabelle bereinigt wurden. *num_tombstone_rows* ist vom Datentyp **int**und hat den Standardwert **0**.  
  
`[ @aggressive_cleanup_only = ] aggressive_cleanup_only` Nur interne Verwendung.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
  
> [!IMPORTANT]  
>  Wenn mehrere Veröffentlichungen in einer Datenbank vorhanden sind und eine dieser Veröffentlichungen eine unbegrenzte Beibehaltungs Dauer für die Veröffentlichung verwendet, werden durch das Ausführen von **sp_mergemetadataretentioncleanup** die Metadaten der Änderungs Nachverfolgung für die Mergereplikation für die Datenbank nicht bereinigt. Aus diesem Grund sollten Sie die unbegrenzte Aufbewahrungsdauer für Veröffentlichungen mit Vorsicht verwenden. Führen Sie [sp_helpmergepublication &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md) auf dem Verleger aus, und notieren Sie alle Veröffentlichungen im Resultset mit einem Wert von **0** für die **Beibehaltung**, um zu bestimmen, ob eine Veröffentlichung über eine unbegrenzte Beibehaltungs Dauer verfügt.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der Daten Bank Rolle **db_owner** oder Benutzer in der Veröffentlichungs Zugriffsliste für eine veröffentlichte Datenbank können **sp_mergemetadataretentioncleanup**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
