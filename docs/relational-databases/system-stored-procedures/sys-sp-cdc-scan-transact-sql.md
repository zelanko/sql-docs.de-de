---
title: sp_cdc_scan (Transact-SQL) | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 1e7651c6df4a277d72a71c0cdb8a5910ae19ba76
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58536782"
---
# <a name="sysspcdcscan-transact-sql"></a>sys.sp_cdc_scan (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Führt den Protokollscan für Change Data Capture aus.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.sp_cdc_scan [ [ @maxtrans = ] max_trans ]   
     [ , [ @maxscans = ] max_scans ]   
     [ , [ @continuous = ] continuous ]   
     [ , [ @pollinginterval = ] polling_interval ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @maxtrans = ] max_trans` Maximale Anzahl der in jedem Scanzyklus zu verarbeitenden Transaktionen. *Max_trans* ist **Int** hat den Standardwert von 500.  
  
`[ @maxscans = ] max_scans` Maximale Anzahl der scanzyklen, ausführen, um alle Zeilen aus dem Protokoll zu extrahieren. *Max_scans* ist **Int** hat den Standardwert 10.  
  
`[ @continuous = ] continuous` Gibt an, ob die gespeicherte Prozedur sollte nach dem Ausführen eines einzelnen Scanzyklus (0) oder kontinuierlich, für die angegebene Zeit anhalten *Polling_interval* vor reexecuting der Überprüfungszyklus (1). *fortlaufende* ist **Tinyint** hat den Standardwert 0.  
  
`[ @pollinginterval = ] polling_interval` Anzahl von Sekunden zwischen den Scan des Replikationsprotokolls Prozessorzyklen. *Polling_interval* ist **Bigint** hat den Standardwert 0.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 sp_cdc_scan wird intern vom sys.sp_MScdc_capture_job aufgerufen, wenn die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-aufzeichnungsauftrag von Change Data Capture verwendet wird. Die Prozedur kann nicht explizit ausgeführt werden, wenn ein Protokollscan für Change Data Capture bereits aktiv ist oder wenn die Datenbank für die Transaktionsreplikation aktiviert ist. Diese gespeicherte Prozedur sollte von Administratoren verwendet werden, die das Verhalten für den aufzeichnungsauftrag, der automatisch konfiguriert ist, anpassen möchten.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle "db_owner".  
  
## <a name="see-also"></a>Siehe auch  
 [dbo.cdc_jobs &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-cdc-jobs-transact-sql.md)  
  
  
