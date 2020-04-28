---
title: sys. sp_cdc_change_job (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sp_cdc_change_job_TSQL
- sys.sp_cdc_change_job
- sp_cdc_change_job_TSQL
- sp_cdc_change_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_change_job
ms.assetid: ea918888-0fc5-4cc1-b301-26b2a9fbb20d
author: rothja
ms.author: jroth
ms.openlocfilehash: 0c2c39363ca1b0824b27645df8c8501931b674a2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "74056757"
---
# <a name="syssp_cdc_change_job-transact-sql"></a>sys.sp_cdc_change_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert die Konfiguration eines Cleanup- oder Aufzeichnungsauftrags für Change Data Capture in der aktuellen Datenbank. Um die aktuelle Konfiguration eines Auftrags anzuzeigen, Fragen Sie die Tabelle [dbo. cdc_jobs](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md) ab, oder verwenden Sie [sp_cdc_help_jobs](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-jobs-transact-sql.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.sp_cdc_change_job [ [ @job_type = ] 'job_type' ]  
    [ , [ @maxtrans = ] max_trans ]   
    [ , [ @maxscans = ] max_scans ]   
    [ , [ @continuous = ] continuous ]   
    [ , [ @pollinginterval = ] polling_interval ]   
    [ , [ @retention ] = retention ]   
    [ @threshold = ] 'delete threshold'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_type = ] 'job_type'`Der Typ des Auftrags, der geändert werden soll. *job_type* ist vom Datentyp **nvarchar (20)** und hat den Standardwert ' Capture '. Gültige Eingaben sind 'capture' und 'cleanup'.  
  
`[ @maxtrans ] = max_trans_`Maximale Anzahl von Transaktionen, die in jedem Scanvorgang verarbeitet werden sollen. *max_trans* ist vom Datentyp **int** und hat den Standardwert NULL, der angibt, dass für diesen Parameter keine Änderung vorgenommen wurde Wenn dieser Wert angegeben ist, muss er eine positive ganze Zahl annehmen.  
  
 *max_trans* ist nur für Aufzeichnungs Aufträge gültig.  
  
`[ @maxscans ] = max_scans_`Maximale Anzahl der Scan Zyklen, die ausgeführt werden müssen, um alle Zeilen aus dem Protokoll zu extrahieren. *max_scans* ist vom Datentyp **int** und hat den Standardwert NULL, der angibt, dass für diesen Parameter keine Änderung vorgenommen wurde  
  
 *max_scan* ist nur für Aufzeichnungs Aufträge gültig.  
  
`[ @continuous ] = continuous_`Gibt an, ob der Aufzeichnungs Auftrag fortlaufend (1) oder nur einmal ausgeführt werden soll (0). *Continuous* ist vom Typ **Bit** und hat den Standardwert NULL, der angibt, dass für diesen Parameter keine Änderung vorgenommen wird.  
  
 Wenn *Continuous* = 1, scannt der [sp_cdc_scan](../../relational-databases/system-stored-procedures/sys-sp-cdc-scan-transact-sql.md) Auftrag das Protokoll und verarbeitet bis zu (*max_trans* \* *max_scans*) Transaktionen. Anschließend wird die Anzahl der Sekunden gewartet, die in *polling_interval* angegeben ist, bevor mit dem nächsten Protokoll Scan begonnen wird.  
  
 Wenn *Continuous* = 0, wird der **sp_cdc_scan** Auftrag bis zu *max_scans* Scans des Protokolls ausgeführt, während jeder Überprüfung bis zu *max_trans* Transaktionen verarbeitet und dann beendet.  
  
 Wenn ** \@Continuous** von 1 in 0 geändert wird, ** \@wird PollingInterval** automatisch auf 0 festgelegt. Ein Wert, der für ** \@das PollingInterval** -Wert ungleich 0 angegeben ist, wird ignoriert.  
  
 Wenn ** \@Continuous** ausgelassen wird oder explizit auf NULL und ** \@PollingInterval** explizit auf einen Wert größer als 0 festgelegt ist, ** \@wird Continuous** automatisch auf 1 festgelegt.  
  
 *Continuous* ist nur für Aufzeichnungs Aufträge gültig.  
  
`[ @pollinginterval ] = polling_interval_`Anzahl der Sekunden zwischen Protokoll Scan Zyklen. *polling_interval* ist vom Datentyp **bigint** und hat den Standardwert NULL, der angibt, dass für diesen Parameter keine Änderung vorgenommen wird.  
  
 *polling_interval* ist nur für Aufzeichnungs Aufträge gültig, wenn *Continuous* auf 1 festgelegt ist.  
  
`[ @retention ] = retention_`Die Anzahl der Minuten, die Änderungs Zeilen in Änderungs Tabellen beibehalten werden sollen. die *Beibehaltung* ist vom Datentyp **bigint** und hat den Standardwert NULL, der angibt, dass für diesen Parameter keine Änderung erfolgt. Der Maximalwert beträgt 52494800 (100 Jahre). Wenn dieser Wert angegeben ist, muss er eine positive ganze Zahl annehmen.  
  
 die *Beibehaltung* ist nur für Cleanupaufträge gültig.  
  
`[ @threshold = ] 'delete threshold'`Maximale Anzahl von DELETE-Einträgen, die mit einer einzelnen Anweisung beim Cleanup gelöscht werden können. der *Lösch Schwellenwert* ist vom Datentyp **bigint** und hat den Standardwert NULL der *Lösch Schwellenwert* ist nur für Cleanupaufträge gültig.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn ein Parameter weggelassen wird, wird der zugehörige Wert in der [dbo. cdc_jobs](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md) -Tabelle nicht aktualisiert. Ein explizit auf NULL festgelegter Parameter wird so behandelt, als ob der Parameter weggelassen wird.  
  
 Die Angabe eines für den Auftragstyp ungültigen Parameters führt dazu, dass die Anweisung fehlschlägt.  
  
 Änderungen an einem Auftrag treten erst in Kraft, wenn der Auftrag mithilfe von [sp_cdc_stop_job](../../relational-databases/system-stored-procedures/sys-sp-cdc-stop-job-transact-sql.md) beendet und mithilfe [sp_cdc_start_job](../../relational-databases/system-stored-procedures/sys-sp-cdc-start-job-transact-sql.md)neu gestartet wird.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **db_owner** Fixed-Daten Bank Rolle.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-changing-a-capture-job"></a>A. Ändern eines Aufzeichnungsauftrags  
 Im folgenden Beispiel werden die `@job_type`Parameter `@maxscans`, und `@maxtrans` eines Aufzeichnungs Auftrags in der `AdventureWorks2012` -Datenbank aktualisiert. Die anderen gültigen Parameter für einen Aufzeichnungsauftrag, `@continuous` und `@pollinginterval`, werden weggelassen. Deren Werte werden nicht geändert.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_change_job   
    @job_type = N'capture',  
    @maxscans = 1000,  
    @maxtrans = 15;  
GO  
```  
  
### <a name="b-changing-a-cleanup-job"></a>B. Ändern eines Cleanupauftrags  
 Im folgenden Beispiel wird ein Cleanupauftrag in der `AdventureWorks2012`-Datenbank aktualisiert. Alle gültigen Parameter für diesen Auftragstyp, außer ** \@Schwellenwert**, werden angegeben. Der Wert für ** \@Schwellen** Wert wird nicht geändert.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_change_job   
    @job_type = N'cleanup',  
    @retention = 2880;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [dbo. cdc_jobs &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)   
 [sys. sp_cdc_enable_table &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-table-transact-sql.md)   
 [sys.sp_cdc_add_job (Transact-SQL)](../../relational-databases/system-stored-procedures/sys-sp-cdc-add-job-transact-sql.md)  
  
  
