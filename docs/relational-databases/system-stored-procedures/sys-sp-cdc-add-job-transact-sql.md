---
title: sys. sp_cdc_add_job (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cdc_add_job_TSQL
- sys.sp_cdc_add_job
- sys.sp_cdc_add_job_TSQL
- sp_cdc_add_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_add_job
ms.assetid: c4458738-ed25-40a6-8294-a26ca5a05bd9
author: rothja
ms.author: jroth
ms.openlocfilehash: 7dd10d28855cc4c10f5496c74f1f39a91826052f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68106546"
---
# <a name="syssp_cdc_add_job-transact-sql"></a>sys.sp_cdc_add_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Erstellt einen Cleanup- oder Aufzeichnungsauftrag für Change Data Capture in der aktuellen Datenbank.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.sp_cdc_add_job [ @job_type = ] 'job_type'  
    [ , [ @start_job = ] start_job ]   
    [ , [ @maxtrans = ] max_trans ]   
    [ , [ @maxscans = ] max_scans ]   
    [ , [ @continuous = ] continuous ]   
    [ , [ @pollinginterval = ] polling_interval ]   
    [ , [ @retention ] = retention ]   
    [ , [ @threshold ] = 'delete_threshold' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_type = ] 'job\_type'`Der Typ des hinzu zufügenden Auftrags. *job_type* ist vom Datentyp **nvarchar (20)** und darf nicht NULL sein. Gültige Eingaben sind **' Capture '** und **' Cleanup '**.  
  
`[ @start_job = ] start_job`Flag zum angeben, ob der Auftrag sofort nach dem Hinzufügen gestartet werden soll. *start_job* ist vom Typ **Bit** und hat den Standardwert 1.  
  
`[ @maxtrans ] = max_trans`Maximale Anzahl von Transaktionen, die in jedem Scanvorgang verarbeitet werden sollen. *max_trans* ist vom Datentyp **int** und hat den Standardwert 500. Wenn dieser Wert angegeben ist, muss er eine positive ganze Zahl annehmen.  
  
 *max_trans* ist nur für Aufzeichnungs Aufträge gültig.  
  
`[ @maxscans ] = max\_scans_`Maximale Anzahl der Scan Zyklen, die ausgeführt werden müssen, um alle Zeilen aus dem Protokoll zu extrahieren. *max_scans* ist vom Datentyp **int** und hat den Standardwert 10.  
  
 *max_scan* ist nur für Aufzeichnungs Aufträge gültig.  
  
`[ @continuous ] = continuous_`Gibt an, ob der Aufzeichnungs Auftrag fortlaufend (1) oder nur einmal ausgeführt werden soll (0). *Continuous* ist vom Typ **Bit** und hat den Standardwert 1.  
  
 Wenn *Continuous* = 1, scannt der [sp_cdc_scan](../../relational-databases/system-stored-procedures/sys-sp-cdc-scan-transact-sql.md) Auftrag das Protokoll und verarbeitet bis zu (*max_trans* \* *max_scans*) Transaktionen. Anschließend wird die Anzahl der Sekunden gewartet, die in *polling_interval* angegeben ist, bevor mit dem nächsten Protokoll Scan begonnen wird.  
  
 Wenn *Continuous* = 0, wird der **sp_cdc_scan** Auftrag bis zu *max_scans* Scans des Protokolls ausgeführt, während jeder Überprüfung bis zu *max_trans* Transaktion verarbeitet und dann beendet.  
  
 *Continuous* ist nur für Aufzeichnungs Aufträge gültig.  
  
`[ @pollinginterval ] = polling\_interval_`Anzahl der Sekunden zwischen Protokoll Scan Zyklen. *polling_interval* ist vom Datentyp **bigint** und hat den Standardwert 5.  
  
 *polling_interval* ist nur für Aufzeichnungs Aufträge gültig, wenn *Continuous* auf 1 festgelegt ist. Wenn angegeben, kann der Wert nicht negativ sein und 24 Stunden nicht übersteigen. Wenn der Wert 0 angegeben ist, wird zwischen den Protokollscans nicht gewartet.  
  
`[ @retention ] = retention_`Die Anzahl der Minuten, die Änderungs Daten Zeilen in Änderungs Tabellen beibehalten werden sollen. die *Beibehaltung* ist vom Datentyp **bigint** und hat den Standardwert 4320 (72 Stunden). Der Maximalwert beträgt 52494800 (100 Jahre). Wenn dieser Wert angegeben ist, muss er eine positive ganze Zahl annehmen.  
  
 die *Beibehaltung* ist nur für Cleanupaufträge gültig.  
  
`[ @threshold = ] 'delete\_threshold'`Maximale Anzahl von DELETE-Einträgen, die mit einer einzelnen Anweisung beim Cleanup gelöscht werden können. *delete_threshold* ist vom Datentyp **bigint** und hat den Standardwert 5000.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Es wird ein Cleanupauftrag mit den Standardwerten erstellt, wenn die erste Tabelle in der Datenbank für Change Data Capture aktiviert ist. Es wird ein Aufzeichnungsauftrag mit den Standardwerten erstellt, wenn die erste Tabelle in der Datenbank für Change Data Capture aktiviert ist und keine Transaktionsveröffentlichungen für diese Datenbank vorhanden sind. Wenn eine Transaktionsveröffentlichung vorhanden ist, wird der Transaktionsprotokollleser verwendet, um den Aufzeichnungsmechanismus zu ermöglichen. Ein separater Aufzeichnungsauftrag ist dann weder erforderlich noch zulässig.  
  
 Da die Cleanup- und Aufzeichnungsaufträge standardmäßig erstellt werden, ist diese gespeicherte Prozedur nur dann erforderlich, wenn ein Auftrag explizit gelöscht wurde und erneut erstellt werden muss.  
  
 Der Name des Auftrags ist **CDC.** _Datenbankname\_\>bereinigen oder cdc. \<_**\_** **cdc.** Erfassung von**\_** _Datenbanknamen\_\>, bei der<database_name>der Name der aktuellen Datenbank ist. \<_ *<database_name>* Wenn bereits ein Auftrag mit demselben Namen vorhanden ist, wird der Name mit einem Wert (**.**) gefolgt von einem eindeutigen Bezeichner (z. b. CDC) angehängt **. AdventureWorks_capture. A1ACBDED-13FC-428C-8302-10100EF74F52**.  
  
 Verwenden Sie [sp_cdc_help_jobs](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md), um die aktuelle Konfiguration eines Bereinigungs-oder Aufzeichnungs Auftrags anzuzeigen. Verwenden Sie [sp_cdc_change_job](../../relational-databases/system-stored-procedures/sys-sp-cdc-change-job-transact-sql.md), um die Konfiguration eines Auftrags zu ändern.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **db_owner** Fixed-Daten Bank Rolle.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-creating-a-capture-job"></a>A. Erstellen eines Aufzeichnungsauftrags  
 Im folgenden Beispiel wird ein Aufzeichnungsauftrag erstellt. In diesem Beispiel wird davon ausgegangen, dass der vorhandene Cleanupauftrag explizit gelöscht wurde und erneut erstellt werden muss. Der Auftrag wird mit den Standardwerten erstellt.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_cdc_add_job @job_type = N'capture';  
GO  
```  
  
### <a name="b-creating-a-cleanup-job"></a>B. Erstellen eines Cleanupauftrags  
 Im folgenden Beispiel wird ein Cleanupauftrag in der [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]-Datenbank erstellt. Der `@start_job`-Parameter wird auf 0 festgelegt, und `@retention` wird auf 5760 Minuten (96 Stunden) festgelegt. In diesem Beispiel wird davon ausgegangen, dass der vorhandene Cleanupauftrag explizit gelöscht wurde und erneut erstellt werden muss.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sys.sp_cdc_add_job  
     @job_type = N'cleanup'  
    ,@start_job = 0  
    ,@retention = 5760;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [dbo. cdc_jobs &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)   
 [sys. sp_cdc_enable_table &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)   
 [Über Change Data Capture &#40;SQL Server&#41;](../../relational-databases/track-changes/about-change-data-capture-sql-server.md)  
  
  
