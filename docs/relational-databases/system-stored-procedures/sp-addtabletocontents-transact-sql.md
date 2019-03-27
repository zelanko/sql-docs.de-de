---
title: Sp_addtabletocontents (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addtabletocontents_TSQL
- sp_addtabletocontents
helpviewer_keywords:
- sp_addtabletocontents
ms.assetid: 2ea27001-74f4-463e-bf1b-b6b5a86b9219
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 991ee7139ae4a323a1d426d1882e4f6b3a4df871
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58493512"
---
# <a name="spaddtabletocontents-transact-sql"></a>sp_addtabletocontents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fügt in die Mergenachverfolgungstabellen Verweise auf alle Zeilen in einer Quelltabelle ein, die derzeit nicht in den Nachverfolgungstabellen eingeschlossen sind. Verwenden Sie diese Option aus, wenn Sie Bulk-eine große Menge an Daten geladen haben **Bcp**, die Mergenachverfolgungstabellen Trigger nicht ausgelöst. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addtabletocontents [ @table_name = ] 'table_name'  
    [ , [ @owner_name = ] 'owner_name' ]  
    [ , [ @filter_clause = ] 'filter_clause' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @table_name = ] 'table_name'` Ist der Name der Tabelle. *TABLE_NAME* ist **Sysname**, hat keinen Standardwert.  
  
`[ @owner_name = ] 'owner_name'` Ist der Name des Besitzers der Tabelle. *Owner_name* ist **Sysname**, hat den Standardwert NULL.  
  
`[ @filter_clause = ] 'filter_clause'` Gibt eine Filterklausel, die steuert, welche Zeilen der neu geladenen Daten den Mergenachverfolgungstabellen hinzugefügt werden sollen. *Filter_clause* ist **nvarchar(4000)**, hat den Standardwert NULL. Wenn *Filter_clause* ist **null**, alle in einem Massenvorgang geladenen Zeilen hinzugefügt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_addtabletocontents** wird nur bei der Mergereplikation verwendet.  
  
 Die Zeilen in der *Table_name* zu verdanken ihre **Rowguidcol** und die Verweise werden den Mergenachverfolgungstabellen hinzugefügt. **Sp_addtabletocontents** sollte verwendet werden, nach dem Massenkopieren von Daten in eine Tabelle, die mithilfe der Mergereplikation veröffentlicht wird. Die gespeicherte Prozedur veranlasst die Nachverfolgung der kopierten Zeilen und gewährleistet, dass die neuen Zeilen bei der nächsten Synchronisation berücksichtigt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** -Serverrolle sein oder **Db_owner** feste Datenbankrolle können ausführen **Sp_addtabletocontents**.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
