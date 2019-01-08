---
title: Sp_ivindexhasnullcols (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_ivindexhasnullcols
- sp_ivindexhasnullcols_TSQL
helpviewer_keywords:
- sp_ivindexhasnullcols
ms.assetid: ed2cde63-37e1-43cf-b6ba-3b6114a0f797
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5e9ab98dc5beb4f2e07ac7fa62386f9fd44703ab
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52823328"
---
# <a name="spivindexhasnullcols-transact-sql"></a>sp_ivindexhasnullcols (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Überprüft, ob der gruppierte Index der indizierten Sicht eindeutig ist und keine Spalten enthält, die NULL-Werte zulassen, wenn die indizierte Sicht verwendet wird, um eine Transaktionsveröffentlichung zu erstellen. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_ivindexhasnullcols [ @viewname = ] 'view_name'  
        , [ @fhasnullcols= ] field_has_null_columns OUTPUT  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@viewname**=] **"***View_name***"**  
 Der Name der Sicht, die überprüft werden soll. *View_name* ist **Sysname**, hat keinen Standardwert.  
  
 [ **@fhasnullcols**=] *Field_has_null_columns* Ausgabe  
 Das Flag, das angibt, ob der Sichtindex Spalten enthält, die NULL zulassen. *View_name* ist **Sysname**, hat keinen Standardwert. Gibt einen Wert von **1** , wenn der Sichtindex über Spalten verfügt, die NULL zulassen. Gibt einen Wert von **0** , wenn die Sicht keine Spalten enthält, die NULL-Werte zulassen.  
  
> [!NOTE]  
>  Wenn die gespeicherte Prozedur selbst einen Rückgabecode zurückgibt **1**, d. h. die Ausführung der gespeicherten Prozedur fehl, ist dieser Wert ist **0** und sollte ignoriert werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_ivindexhasnullcols** wird von der Transaktionsreplikation verwendet.  
  
 Standardmäßig werden Artikel für indizierte Sichten in einer Veröffentlichung als Tabellen bei den Abonnenten erstellt. Wenn die indizierte Spalte jedoch NULL-Werte zulässt, wird die indizierte Sicht auf dem Abonnenten als indizierte Sicht erstellt und nicht als Tabelle. Durch die Ausführung dieser gespeicherten Prozedur kann der Benutzer gewarnt werden, wenn dieses Problem mit der aktuellen indizierten Sicht besteht.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder die **Db_owner** feste Datenbankrolle können ausführen **Sp_ivindexhasnullcols**.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
