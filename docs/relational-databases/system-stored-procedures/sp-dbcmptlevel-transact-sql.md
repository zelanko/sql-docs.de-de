---
title: Sp_dbcmptlevel (Transact-SQL) | Microsoft-Dokumentation
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
- sp_dbcmptlevel
- sp_dbcmptlevel_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dbcmptlevel
ms.assetid: 508c686d-2bd4-41ba-8602-48ebca266659
caps.latest.revision: 110
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: acd4d6a2d87d97bd31b35779a9bc605dde41db04
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43031943"
---
# <a name="spdbcmptlevel-transact-sql"></a>sp_dbcmptlevel (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Legt für bestimmte Verhalten der Datenbank fest, dass sie mit der angegebenen Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kompatibel sein müssen.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Verwendung [ALTER DATABASE Compatibility Level](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)stattdessen.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_dbcmptlevel [ [ @dbname = ] name ]   
    [ , [ @new_cmptlevel = ] version ]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@dbname=** ] *Name*  
 Der Name der Datenbank, deren Kompatibilitätsgrad geändert werden soll. Datenbanknamen müssen den Regeln für Bezeichner entsprechen. *name* ist vom Datentyp **sysname**und hat den Standardwert NULL.  
  
 [  **@new_cmptlevel=** ] *Version*  
 Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Version, mit der die Datenbank kompatibel sein soll. *Version* ist **Tinyint**, hat den Standardwert NULL. Folgende Werte sind zulässig:  
  
 **90** = [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
  
 **100** = [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
 **110** = [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
 **120** = [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
 **130** = [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Wenn keine Parameter angegeben werden, oder wenn die *Namen* Parameter nicht angegeben ist, **Sp_dbcmptlevel** gibt einen Fehler zurück.  
  
 Wenn *Namen* ohne angegeben *Version*, [!INCLUDE[ssDE](../../includes/ssde-md.md)] eine Nachricht mit den aktuellen Kompatibilitätsgrad der angegebenen Datenbank zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Eine Beschreibung der Kompatibilitätsgrade finden Sie unter [ALTER DATABASE Compatibility Level &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Nur der Datenbankbesitzer, Mitglieder der **Sysadmin** festen Serverrolle und die **Db_owner** festen Datenbankrolle "" (Wenn Sie die aktuelle Datenbank ändern), kann diese Prozedur ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine gespeicherten Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [Reserved Keywords &#40;Transact-SQL&#41;](../../t-sql/language-elements/reserved-keywords-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
