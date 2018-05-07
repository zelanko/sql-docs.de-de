---
title: Sp_db_increased_partitions | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_db_increased_partitions_TSQL
- sp_db_increased_partitions
dev_langs:
- TSQL
helpviewer_keywords:
- sp_db_increased_partitions
ms.assetid: a8c043ec-b504-4929-ac0e-8babaa99d989
caps.latest.revision: 9
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: b63255e4f15505dc75dfdf92f550a1d6d4149028
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="spdbincreasedpartitions"></a>sp_db_increased_partitions
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aktiviert oder deaktiviert die Unterstützung für bis zu 15.000 Partitionen für die angegebene Datenbank.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_dp_increased_partitions   
[ @dbname ] = 'database_name'   
[ , [ @increased_partitions = ] 'increased_partitions' ] [;]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @dbname=] '*Database_name*"  
 Der Name der Datenbank. *Dbname* ist **Sysname** hat den Standardwert NULL. Wenn *Dbname* nicht angegeben wird, wird die aktuelle Datenbank verwendet.  
  
 [ @increased_partitions=] '*Increased_partitions*"  
 Aktiviert oder deaktiviert die Unterstützung für bis zu 15.000 Partitionen in der angegebenen Datenbank. *Increased_partitions* ist **varchar(6)** hat den Standardwert NULL. Zulässige Werte sind 'ON' bzw. 'TRUE', um die Unterstützung zu aktivieren, und 'OFF' bzw. 'FALSE', um die Unterstützung zu deaktivieren. Wenn *Increased_partitions* nicht angegeben ist, wird die Prozedur zurückgibt, 1, um anzugeben, Unterstützung für die angegebene Datenbank aktiviert ist, oder 0, um Unterstützung anzugeben ist deaktiviert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER DATABASE-Berechtigung für die angegebene Datenbank.  
  
  
