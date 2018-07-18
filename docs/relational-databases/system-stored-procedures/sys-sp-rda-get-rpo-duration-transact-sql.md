---
title: sp_rda_get_rpo_duration (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: stored-procedures
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_get_rpo_duration
- sys.sp_rda_get_rpo_duration_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_get_rpo_duration stored procedure
ms.assetid: 35882067-3072-47ff-9024-ca453c0f49a7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 50b92b70a0ea3045236c6084f046f1d2c0c88146
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37412989"
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
    
  
