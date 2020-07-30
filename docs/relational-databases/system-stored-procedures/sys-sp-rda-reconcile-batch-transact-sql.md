---
title: sys. sp_rda_reconcile_batch (Transact-SQL) | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie sys. sp_rda_reconcile_batch verwenden, um die Batch-ID in der Stretch-aktivierten SQL Server Tabelle mit der Batch-ID abzustimmen, die in der Azure-Remote Tabelle gespeichert ist.
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_reconcile_batch
- sys.sp_rda_reconcile_batch_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_reconcile_batch stored procedure
ms.assetid: 6d21eac3-7b6c-4fe0-8bc4-bf503f3948a6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: aa97030851e13eac020564eec7931a00595b8884
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87247089"
---
# <a name="syssp_rda_reconcile_batch-transact-sql"></a>sys. sp_rda_reconcile_batch (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Gibt die Batch-ID, die in der Stretch-aktivierten SQL Server Tabelle gespeichert ist, mit der in der Azure-Remote Tabelle gespeicherten Batch-ID aus.  
  
 In der Regel müssen Sie nur **sp_rda_reconcile_batch** ausführen, wenn Sie die zuletzt migrierten Daten manuell aus der Remote Tabelle gelöscht haben. Wenn Sie Remote Daten manuell löschen, die den letzten Batch enthalten, sind die Batch-IDs nicht synchron, und die Migration wird beendet.  
 
 Informationen zum Löschen von Daten, die bereits zu Azure migriert wurden, finden Sie in den Hinweisen auf dieser Seite.
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
   
## <a name="syntax"></a>Syntax  
  
```  
  
sp_rda_reconcile_batch @objname = '@objname'  
  
```  
  
## <a name="arguments"></a>Argumente  
 \@objname = '* \@ objname*'  
 Der Name der SQL Server Tabelle, für die Stretch aktiviert ist.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert db_owner Berechtigungen.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn Sie Daten löschen möchten, die bereits zu Azure migriert wurden, führen Sie die folgenden Schritte aus.  
  
1.  Anhalten der Datenmigration. Weitere Informationen finden Sie unter [Anhalten und Fortsetzen der Datenmigration &#40;Stretch Database&#41;](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md).  
  
2.  Löschen Sie die Daten aus der SQL Server Stagingtabelle, indem Sie einen DELETE-Befehl mit dem STAGE_ONLY-Hinweis ausführen. Weitere Informationen finden Sie unter [Erstellen von administrativen Updates und Löschungen](../../sql-server/stretch-database/manage-and-troubleshoot-stretch-database.md#adminHints).
  
3.  Löschen Sie die gleichen Daten aus der Azure-Remote Tabelle, indem Sie einen DELETE-Befehl mit dem REMOTE_ONLY-Hinweis ausführen.  
  
4.  Führen Sie **sp_rda_reconcile_batch**aus.  
  
5.  Fortsetzen der Datenmigration. Weitere Informationen finden Sie unter [Anhalten und Fortsetzen der Datenmigration &#40;Stretch Database&#41;](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md).  
  
## <a name="example"></a>Beispiel  
 Führen Sie die folgende Anweisung aus, um die Batch-IDs abzustimmen.  
  
```sql  
EXEC sp_rda_reconcile_batch @objname = N'StretchEnabledTableName';  
```  
  
  
