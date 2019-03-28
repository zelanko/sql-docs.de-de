---
title: Sp_script_synctran_commands (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_script_synctran_commands
- sp_script_synctran_commands_TSQL
helpviewer_keywords:
- sp_script_synctran_commands
ms.assetid: f132694a-dd05-405b-9d84-21acce9e564a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a9ee35eb4c5d67ff50f4f08c1cfa29596e27aec2
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58536175"
---
# <a name="spscriptsynctrancommands-transact-sql"></a>sp_script_synctran_commands (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Generiert ein Skript, enthält die **Sp_addsynctrigger** Aufrufe, die auf dem Abonnenten für aktualisierbare Abonnements angewendet werden. Es gibt ein **Sp_addsynctrigger** rufen Sie für jeden Artikel in der Veröffentlichung. Das generierte Skript enthält auch die **Sp_addqueued_artinfo** aufrufen, das Erstellen der **MSsubsciption_articles** Tabelle, die Verarbeitung der Veröffentlichungen erforderlich ist. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_script_synctran_commands [@publication = ] 'publication'  
    [ , [@article = ] 'article']  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung, die ein Skript erstellt werden. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
`[ @article = ] 'article'` Ist der Name des Artikels geschrieben werden sollen. *Artikel* ist **Sysname**, hat den Standardwert **alle**, der angibt, dass alle Artikel ein Skript erstellt werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="results-set"></a>Resultset  
 **Sp_script_synctran_commands** gibt ein Resultset besteht aus einer **nvarchar(4000)** Spalte. Das Resultset enthält sämtliche Skripts zum Erstellen der **Sp_addsynctrigger** und **Sp_addqueued_artinfo** Aufrufe, die auf den Abonnenten angewendet werden.  
  
## <a name="remarks"></a>Hinweise  
 **Sp_script_synctran_commands** wird bei der Momentaufnahme- und Transaktionsreplikation verwendet.  
  
 **Sp_addqueued_artinfo** wird für aktualisierbare Abonnements in Warteschlangen verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_script_synctran_commands**.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_addsynctriggers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsynctriggers-transact-sql.md)   
 [sp_addqueued_artinfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addqueued-artinfo-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
