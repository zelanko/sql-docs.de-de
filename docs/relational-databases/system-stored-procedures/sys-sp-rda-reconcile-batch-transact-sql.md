---
title: sp_rda_reconcile_batch (Transact-SQL) | Microsoft-Dokumentation
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
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 54bdac5237ff190f3620bb29dabbf684868c0b75
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "65982932"
---
# <a name="syssprdareconcilebatch-transact-sql"></a>sys.sp_rda_reconcile_batch (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Gleicht die Batch-ID, die in der Stretch-aktivierten SQL Server-Tabelle gespeichert werden, mit der Batch-ID im Azure-Remotetabelle gespeichert.  
  
 In der Regel müssen Sie nur ausführen **Sp_rda_reconcile_batch** , wenn Sie die am häufigsten vor kurzem migrierten Daten manuell aus der Remotetabelle gelöscht haben. Wenn Sie manuell Remotedaten, die den aktuelle Batch enthält löschen, die Batch-IDs sind nicht synchron und Migration angehalten wird.  
 
 Zum Löschen von Daten, die bereits zu Azure migriert wurde, finden Sie unter den Hinweisen auf dieser Seite.
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
   
## <a name="syntax"></a>Syntax  
  
```  
  
sp_rda_reconcile_batch @objname = '@objname'  
  
```  
  
## <a name="arguments"></a>Argumente  
 \@objname = '*\@objname*'  
 Der Name des Stretch-aktivierten SQL Server-Tabelle.  
  
## <a name="permissions"></a>Berechtigungen  
 Benötigen Sie Db_owner-Berechtigungen.  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie möchten Daten löschen, die bereits zu Azure migriert wurde, gehen Sie folgendermaßen vor.  
  
1.  Anhalten der Datenmigration. Weitere Informationen finden Sie unter [Anhalten und Fortsetzen der Datenmigration &#40;Stretch Database&#41;](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md).  
  
2.  Löschen Sie die Daten aus der Stagingtabelle für SQL Server durch Ausführen eines DELETE-Befehls mit dem Hinweis stage_only durch. Weitere Informationen finden Sie unter [durchführen administrativer Aktualisierungs- und Löschvorgänge](../../sql-server/stretch-database/manage-and-troubleshoot-stretch-database.md#adminHints).
  
3.  Löschen Sie diese Daten aus Azure-Remotetabelle, durch Ausführen eines DELETE-Befehls mit dem REMOTE_ONLY-Hinweis.  
  
4.  Führen Sie **Sp_rda_reconcile_batch**.  
  
5.  Fortsetzen der Datenmigration. Weitere Informationen finden Sie unter [Anhalten und Fortsetzen der Datenmigration &#40;Stretch Database&#41;](../../sql-server/stretch-database/pause-and-resume-data-migration-stretch-database.md).  
  
## <a name="example"></a>Beispiel  
 Wenn der Batch-IDs abstimmen möchten, führen Sie die folgende Anweisung aus.  
  
```sql  
EXEC sp_rda_reconcile_batch @objname = N'StretchEnabledTableName';  
```  
  
  
