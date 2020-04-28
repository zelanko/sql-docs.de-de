---
title: sp_script_synctran_commands (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: d7caca72f684dfb6428361a4550860b3bea3f273
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68126412"
---
# <a name="sp_script_synctran_commands-transact-sql"></a>sp_script_synctran_commands (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Generiert ein-Skript, das die **sp_addsynctrigger** Aufrufe enthält, die auf Abonnenten für aktualisierbare Abonnements angewendet werden sollen. Für jeden Artikel in der Veröffentlichung gibt es einen **sp_addsynctrigger** . Das generierte Skript enthält auch die **sp_addqueued_artinfo** Aufrufe, mit denen die **MSsubsciption_articles** Tabelle erstellt wird, die für die Verarbeitung von Veröffentlichungen in der Warteschlange erforderlich ist. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_script_synctran_commands [@publication = ] 'publication'  
    [ , [@article = ] 'article']  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung, für die ein Skript erstellt werden soll. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @article = ] 'article'`Der Name des Artikels, für den ein Skript erstellt werden soll. der *Artikel* ist vom **Datentyp vom Datentyp sysname**. der Standardwert **all**gibt an, dass für alle Artikel skriskripten erstellt werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="results-set"></a>Resultset  
 **sp_script_synctran_commands** gibt ein Resultset zurück, das aus einer einzelnen **nvarchar (4000)** -Spalte besteht. Das Resultset bildet die gesamten Skripts, die zum Erstellen der **sp_addsynctrigger** -und **sp_addqueued_artinfo** Aufrufe erforderlich sind, die auf den Abonnenten angewendet werden sollen.  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_script_synctran_commands** wird bei der Momentaufnahme-und Transaktions Replikation verwendet.  
  
 **sp_addqueued_artinfo** wird für aktualisierbare Abonnements in der Warteschlange verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** oder der festen Daten Bank Rolle **db_owner** können **sp_script_synctran_commands**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_addsynctriggers &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addsynctriggers-transact-sql.md)   
 [sp_addqueued_artinfo &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addqueued-artinfo-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
