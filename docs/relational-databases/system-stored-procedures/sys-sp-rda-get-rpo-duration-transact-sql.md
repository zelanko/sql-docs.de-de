---
title: sp_rda_get_rpo_duration (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_get_rpo_duration
- sys.sp_rda_get_rpo_duration_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_get_rpo_duration stored procedure
ms.assetid: 35882067-3072-47ff-9024-ca453c0f49a7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 15a188a912d9338b6e786248e9242914d5759196
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67905081"
---
# <a name="syssprdagetrpoduration-transact-sql"></a>sp_rda_get_rpo_duration (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Ruft die Anzahl der Stunden der migrierten Daten, die von SQL Server beibehalten. in einer Stagingtabelle aus, um sicherzustellen, eine vollständige Wiederherstellung von Azure-Remotedatenbank, wenn ein Punkt in der Time-Wiederherstellung erforderlich ist. 
  
  Weitere Informationen finden Sie unter [Stretch Database reduziert das Risiko eines Datenverlusts für Ihre Azure-Daten, indem migrierte Zeilen vorübergehend beibehalten werden](../../sql-server/stretch-database/backup-stretch-enabled-databases-stretch-database.md#stretchRPO).  
    
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)    
    
## <a name="syntax"></a>Syntax    
    
```    
    
sp_rda_get_rpo_duration @durationinhours output    
    
```    
    
## <a name="output-parameter"></a>Output-parameter    
 *@durationinhours*    
  Die Anzahl der Stunden (ein nicht-Null-Integer-Wert) der migrierten Daten, die von SQL Server für die aktuelle aktivierter Funktion Stretch-Datenbank beibehalten.    
    
## <a name="permissions"></a>Berechtigungen    
 Benötigen Sie Db_owner-Berechtigungen.    
    
## <a name="remarks"></a>Hinweise    
 Ändern Sie den Wert mit [Sys. sp_rda_set_rpo_duration &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-set-rpo-duration-transact-sql.md).    
    
## <a name="see-also"></a>Siehe auch    
 [sys.sp_rda_set_rpo_duration &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-set-rpo-duration-transact-sql.md)     
 [Wiederherstellen von Stretch-aktivierten Datenbanken (Stretch Database)](../../sql-server/stretch-database/restore-stretch-enabled-databases-stretch-database.md)    
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)    
    
  
