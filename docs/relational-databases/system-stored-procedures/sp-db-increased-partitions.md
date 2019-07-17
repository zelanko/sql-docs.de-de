---
title: Sp_db_increased_partitions | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_db_increased_partitions_TSQL
- sp_db_increased_partitions
dev_langs:
- TSQL
helpviewer_keywords:
- sp_db_increased_partitions
ms.assetid: a8c043ec-b504-4929-ac0e-8babaa99d989
author: stevestein
ms.author: sstein
ms.openlocfilehash: 83a40c9070db1c997f30db71a6cff226cd0430d6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68108259"
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
 Der Name der Datenbank. *Dbname* ist **Sysname** hat den Standardwert NULL. Wenn *Dbname* nicht angegeben ist, wird die aktuelle Datenbank verwendet wird.  
  
 [ @increased_partitions=] '*Increased_partitions*"  
 Aktiviert oder deaktiviert die Unterstützung für bis zu 15.000 Partitionen in der angegebenen Datenbank. *Increased_partitions* ist **varchar(6)** hat den Standardwert NULL. Zulässige Werte sind 'ON' bzw. 'TRUE', um die Unterstützung zu aktivieren, und 'OFF' bzw. 'FALSE', um die Unterstützung zu deaktivieren. Wenn *Increased_partitions* nicht angegeben ist, wird die Prozedur zurückgibt, 1, um anzugeben, Unterstützung für die angegebene Datenbank aktiviert ist, oder 0, um die Unterstützung ist deaktiviert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER DATABASE-Berechtigung für die angegebene Datenbank.  
  
  
