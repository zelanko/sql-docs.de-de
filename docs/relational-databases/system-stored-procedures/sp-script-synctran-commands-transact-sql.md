---
title: Sp_script_synctran_commands (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_script_synctran_commands
- sp_script_synctran_commands_TSQL
helpviewer_keywords:
- sp_script_synctran_commands
ms.assetid: f132694a-dd05-405b-9d84-21acce9e564a
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b86c1064eb96174243ea15cba6f5f84a77e40a1f
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43031807"
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
 [ **@publication** =] **"***Veröffentlichung***"**  
 Der Name der Veröffentlichung, für die ein Skript erstellt werden soll. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
 [ **@article** =] **"***Artikel***"**  
 Der Name des Artikels, für den ein Skript erstellt werden soll. *Artikel* ist **Sysname**, hat den Standardwert **alle**, der angibt, dass alle Artikel ein Skript erstellt werden.  
  
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
 [Sp_addsynctriggers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsynctriggers-transact-sql.md)   
 [Sp_addqueued_artinfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addqueued-artinfo-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
