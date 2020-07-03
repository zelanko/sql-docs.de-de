---
title: sys. sp_cdc_scan (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sp_cdc_scan_TSQL
- sp_cdc_scan
- sys.sp_cdc_scan
- sp_cdc_scan_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cdc_scan
ms.assetid: 46e4294c-97b8-47d6-9ed9-b436a9929353
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 558a2fd9ff62baa3448609eb42e5f31883fbac53
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85891059"
---
# <a name="syssp_cdc_scan-transact-sql"></a>sys.sp_cdc_scan (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Führt den Protokollscan für Change Data Capture aus.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.sp_cdc_scan [ [ @maxtrans = ] max_trans ]   
     [ , [ @maxscans = ] max_scans ]   
     [ , [ @continuous = ] continuous ]   
     [ , [ @pollinginterval = ] polling_interval ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @maxtrans = ] max_trans`Maximale Anzahl von Transaktionen, die in jedem Scanvorgang verarbeitet werden sollen. *max_trans* ist vom Datentyp **int** und hat den Standardwert 500.  
  
`[ @maxscans = ] max_scans`Maximale Anzahl der Scan Zyklen, die ausgeführt werden müssen, um alle Zeilen aus dem Protokoll zu extrahieren. *max_scans* ist vom Datentyp **int** und hat den Standardwert 10.  
  
`[ @continuous = ] continuous`Gibt an, ob die gespeicherte Prozedur nach dem Ausführen eines einzelnen Überprüfungszyklen (0) beendet werden soll, oder ausgeführt wird, wenn die von *polling_interval* angegebene Zeit angehalten werden soll, bevor der Überprüfungszyklen erneut ausgeführt wird (1). *Continuous* ist vom Datentyp **tinyint** und hat den Standardwert 0.  
  
`[ @pollinginterval = ] polling_interval`Anzahl der Sekunden zwischen Protokoll Scan Zyklen. *polling_interval* ist vom Datentyp **bigint** und hat den Standardwert 0.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 sys. sp_cdc_scan wird intern von sys. sp_MScdc_capture_job aufgerufen, wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agenterfassungs Auftrag von Change Data Capture verwendet wird. Der Vorgang kann nicht explizit ausgeführt werden, wenn ein Protokollscan für Change Data Capture bereits aktiv ist oder wenn die Datenbank für die Transaktionsreplikation aktiviert ist. Diese gespeicherte Prozedur sollte von Administratoren verwendet werden, die das Verhalten des automatisch konfigurierten Aufzeichnungsauftrags anpassen möchten.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle "db_owner".  
  
## <a name="see-also"></a>Weitere Informationen  
 [dbo. cdc_jobs &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)  
  
  
