---
title: sys. sp_rda_set_rpo_duration (Transact-SQL) | Microsoft-Dokumentation
description: Erfahren Sie mehr über sys. sp_rda_set_rpo_duration. Verwenden Sie diese gespeicherte Prozedur, um die Anzahl von Stunden für migrierte Daten festzulegen, die SQL Server in einer Stagingtabelle beibehalten.
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_set_rpo_duration
- sys.sp_rda_set_rpo_duration_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_set_rpo_duration stored procedure
ms.assetid: 95c80c5b-9252-4612-9ea7-544c48834fd2
author: markingmyname
ms.author: maghan
ms.openlocfilehash: d37717f2b2c8a3dad804538a9268e64023776422
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89540447"
---
# <a name="syssp_rda_set_rpo_duration-transact-sql"></a>sys. sp_rda_set_rpo_duration (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Legt die Anzahl von Stunden für migrierte Daten fest, die SQL Server in einer Stagingtabelle beibehalten werden, um eine vollständige Wiederherstellung der Azure-Remote Datenbank zu gewährleisten, wenn eine Zeit Punkt Wiederherstellung erforderlich ist.    
    
 Weitere Informationen finden Sie unter [Stretch Database verringert das Risiko eines Daten Verlusts für Ihre Azure-Daten, indem migrierte Zeilen vorübergehend beibehalten](../../sql-server/stretch-database/backup-stretch-enabled-databases-stretch-database.md#stretchRPO)werden.  
   
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)    
     
## <a name="syntax"></a>Syntax    
    
```    
    
sp_rda_set_rpo_duration [ @duration_hrs = ] duration_hrs    
    
```    
    
## <a name="arguments"></a>Argumente    
 [ @duration_hrs =] *duration_hrs*    
 Die Anzahl der Stunden (ein ganzzahliger Wert ungleich null) der migrierten Daten, SQL Server die für die aktuelle Stretch-aktivierte Datenbank beibehalten werden sollen. Der Standardwert und der minimale Wert sind 8 Stunden.    
 
 > [!NOTE]
 > Höhere Werte erfordern mehr Speicherplatz auf SQL Server.
    
## <a name="permissions"></a>Berechtigungen    
 Erfordert db_owner Berechtigungen.    
    
## <a name="remarks"></a>Hinweise    
 Sie erhalten den aktuellen Wert, indem Sie [sys. sp_rda_get_rpo_duration &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md)ausführen.    
    
## <a name="see-also"></a>Weitere Informationen    
 [sys. sp_rda_get_rpo_duration &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md)     
 [Wiederherstellen von Stretch-aktivierten Datenbanken (Stretch Database)](../../sql-server/stretch-database/restore-stretch-enabled-databases-stretch-database.md)     
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)    
    
  
