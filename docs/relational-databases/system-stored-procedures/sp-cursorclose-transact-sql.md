---
title: Sp_cursorclose (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursor_close_TSQL
- sp_cursor_close
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursorclose
ms.assetid: d9b7b44d-cdff-456e-97df-7031a3b9beb6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 56ff3e67c51be8618f0254298a7d8707e18884ff
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47740778"
---
# <a name="spcursorclose-transact-sql"></a>sp_cursorclose (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Schließt und hebt den Cursor, sowie alle zugeordneten Ressourcen frei; d. h. es zur Unterstützung von KEYSET oder STATIC verwendete temporäre Tabelle löscht **Cursor**. Sp_cursorclose wird aufgerufen, indem ID = 9 in einem tabular Data Stream (TDS)-Paket.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_cursorclose cursor  
```  
  
## <a name="arguments"></a>Argumente  
 *Cursor*  
 Ist ein Cursor *behandeln* generierter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und von der Prozedur Sp_cursoropen zurückgegeben. *Cursor* ist ein erforderlicher Parameter, die bei Aufrufen einer **Int** Eingabewert.  
  
> [!NOTE]  
>  Der Eingabewert -1 gilt für alle Cursor der aktuellen Verbindung.  
  
## <a name="remarks"></a>Hinweise  
 *Cursor* gibt Fehlermeldungen, wenn die Prozedur ausgeführt wurde, nachdem der Cursor geschlossen wurde, oder wenn ein ungültiges Handle angegeben wird.  
  
 Der RPC-Status gibt an, ob der Vorgang erfolgreich oder fehlerhaft war.  
  
 Die DONE-Zeilenanzahl beträgt immer 0.  
  
## <a name="see-also"></a>Siehe auch  
 [sp_cursoropen &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
