---
title: Sp_unregister_custom_scripting (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_unregister_custom_scripting_TSQL
- sp_unregister_custom_scripting
helpviewer_keywords:
- sp_unregister_custom_scripting
ms.assetid: b6e9e0d2-9144-434d-88af-4874f2582399
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e3d9af0e5eff8aff2715ff2be6caa1757702fb8b
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58529562"
---
# <a name="spunregistercustomscripting-transact-sql"></a>sp_unregister_custom_scripting (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Diese gespeicherte Prozedur entfernt eine benutzerdefinierte benutzerdefinierte gespeicherte Prozedur oder [!INCLUDE[tsql](../../includes/tsql-md.md)] -Skriptdatei, die durch Ausführen von registriert war [Sp_register_custom_scripting](../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md). Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_unregister_custom_scripting [ @type  = ] 'type'  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @type = ] 'type'` Der Typ der benutzerdefinierten gespeicherten Prozedur oder Skript entfernt wird. *Typ* ist **varchar(16)** und hat keinen Standardwert und kann die folgenden Werte sind möglich.  
  
|Wert|Description|  
|-----------|-----------------|  
|**insert**|Registrierte benutzerdefinierte gespeicherte Prozedur oder Skript wird ausgeführt, wenn eine INSERT-Anweisung repliziert wird.|  
|**update**|Registrierte benutzerdefinierte gespeicherte Prozedur oder Skript wird ausgeführt, wenn eine UPDATE-Anweisung repliziert wird.|  
|**delete**|Registrierte benutzerdefinierte gespeicherte Prozedur oder Skript wird ausgeführt, wenn eine DELETE-Anweisung repliziert wird.|  
|**custom_script**|Registrierte benutzerdefinierte gespeicherte Prozedur oder Skript wird am Ende des DDL-Triggers (Data Definition Language) ausgeführt.|  
  
`[ @publication = ] 'publication'` Der Name der Veröffentlichung, für die die benutzerdefinierte gespeicherte Prozedur oder das Skript entfernt wird. *Veröffentlichung* ist **Sysname**, hat den Standardwert NULL.  
  
`[ @article = ] 'article'` Der Name des Artikels, für die die benutzerdefinierte gespeicherte Prozedur oder das Skript entfernt wird. *Artikel* ist **Sysname**, hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_unregister_custom_scripting** wird bei der Momentaufnahme- und Transaktionsreplikation verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** festen Serverrolle die **Db_owner** feste Datenbankrolle oder der **Db_ddladmin** feste Datenbankrolle können ausführen **Sp_ Unregister_custom_scripting**.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_register_custom_scripting &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-register-custom-scripting-transact-sql.md)  
  
  
