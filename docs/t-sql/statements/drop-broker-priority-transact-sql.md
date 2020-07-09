---
title: DROP BROKER PRIORITY (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP_BROKER_PRIORITY_TSQL
- DROP BROKER PRIORITY
dev_langs:
- TSQL
helpviewer_keywords:
- DROP BROKER PRIORITY statement
ms.assetid: 09ee6c5b-af94-4a4b-a0e2-f9eac50e43aa
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: bb2601bb5fd85313fd66f58cdd0ab616bc8c13c4
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85893375"
---
# <a name="drop-broker-priority-transact-sql"></a>DROP BROKER PRIORITY (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Entfernt eine Konversationspriorität aus der aktuellen Datenbank.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
  
DROP BROKER PRIORITY ConversationPriorityName  
[;]  
```  
  
## <a name="arguments"></a>Argumente  
 *ConversationPriorityName*  
 Gibt den Namen der zu entfernenden Konversationspriorität an.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn Sie eine Konversationspriorität löschen, werden vorhandene Konversationen mit den Prioritätsebenen fortgesetzt, die von der Konversationspriorität zugewiesen wurden.  
  
## <a name="permissions"></a>Berechtigungen  
 Die Berechtigung zum Erstellen einer Konversationspriorität erhalten standardmäßig die Mitglieder der festen Datenbankrolle db_ddladmin oder db_owner und die feste Serverrolle sysadmin. Erfordert die ALTER-Berechtigung für die Datenbank.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Konversationspriorität mit dem Namen `InitiatorAToTargetPriority`gelöscht.  
  
```  
DROP BROKER PRIORITY InitiatorAToTargetPriority;  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER BROKER PRIORITY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-broker-priority-transact-sql.md)   
 [CREATE BROKER PRIORITY &#40;Transact-SQL&#41;](../../t-sql/statements/create-broker-priority-transact-sql.md)   
 [sys.conversation_priorities &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-conversation-priorities-transact-sql.md)  
  
  
