---
title: Sp_mergedummyupdate (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_mergedummyupdate_TSQL
- sp_mergedummyupdate
helpviewer_keywords:
- sp_mergedummyupdate
ms.assetid: b834f7f6-9588-4d59-a3e2-83d8e8e722e1
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bf771f02ec63260dcda1f8b7fa633f9fb6bf9a07
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52817772"
---
# <a name="spmergedummyupdate-transact-sql"></a>sp_mergedummyupdate (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Diese Prozedur führt für die angegebene Zeile ein Pseudoupdate durch, sodass sie beim nächsten Mergevorgang erneut gesendet wird. Diese gespeicherte Prozedur kann auf dem Verleger für die Veröffentlichungsdatenbank oder auf dem Abonnenten für die Abonnementdatenbank ausgeführt werden.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_mergedummyupdate [ @source_object =] 'source_object', [ @rowguid =] 'rowguid'  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@source_object=**] **"***Source_object***"**  
 Der Name des Quellobjekts. *Source_object*ist **nvarchar(386)**, hat keinen Standardwert.  
  
 [  **@rowguid=**] **"***Rowguid***"**  
 Die Zeilen-ID. *ROWGUID* ist **Uniqueidentifier**, hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_mergedummyupdate** wird bei der Mergereplikation verwendet.  
  
 **Sp_mergedummyupdate** ist nützlich, wenn Sie Ihre eigene Alternative zum Replikationskonflikt-Viewer (Wzcnflct.exe) schreiben.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Db_owner** feste Datenbankrolle können ausführen **Sp_mergedummyupdate**.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
