---
description: DROP MESSAGE TYPE (Transact-SQL)
title: DROP MESSAGE TYPE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP_MESSAGE_TYPE_TSQL
- DROP MESSAGE TYPE
dev_langs:
- TSQL
helpviewer_keywords:
- message types [Service Broker], removing
- deleting message types
- dropping message types
- DROP MESSAGE TYPE statement
- removing message types
ms.assetid: 805e8ad5-8a93-49f0-88e5-e6fca8814dd5
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b93b022ed1937b3923a44d5c13b62ff2038df958
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88478828"
---
# <a name="drop-message-type-transact-sql"></a>DROP MESSAGE TYPE (Transact-SQL)
[!INCLUDE [SQL Server - ASDBMI](../../includes/applies-to-version/sql-asdbmi.md)]

  Löscht einen vorhandenen Nachrichtentyp.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
  
DROP MESSAGE TYPE message_type_name  
[ ; ]  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *message_type_name*  
 Der Name des Nachrichtentyps, der gelöscht werden soll. Server-, Datenbank- und Schemaname können nicht angegeben werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig verfügen Mitglieder der festen Datenbankrollen db_ddladmin oder db_owner sowie Mitglieder der festen Serverrolle sysadmin über die Berechtigung zum Löschen eines Nachrichtentyps.  
  
## <a name="remarks"></a>Hinweise  
 Sie können einen Nachrichtentyp nicht löschen, wenn sich Verträge auf diesen Nachrichtentyp beziehen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Nachrichtentyp `//Adventure-Works.com/Expenses/SubmitExpense` aus der Datenbank gelöscht.  
  
```  
DROP MESSAGE TYPE [//Adventure-Works.com/Expenses/SubmitExpense] ;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER MESSAGE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-message-type-transact-sql.md)   
 [CREATE MESSAGE TYPE &#40;Transact-SQL&#41;](../../t-sql/statements/create-message-type-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
