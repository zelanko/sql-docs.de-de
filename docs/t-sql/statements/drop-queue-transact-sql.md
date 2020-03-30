---
title: DROP QUEUE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP QUEUE
- DROP_QUEUE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dropping queues
- queues [Service Broker], removing
- deleting queues
- DROP QUEUE statement
- removing queues
ms.assetid: fd866520-ca00-477d-b2e9-0110e9610ed4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2854cca3e231c479675a06857e24c3e09cfd8762
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "70745339"
---
# <a name="drop-queue-transact-sql"></a>DROP QUEUE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Löscht eine vorhandene Warteschlange.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DROP QUEUE <object>  
[ ; ]  
  
<object> ::=  
{ database_name.schema_name.queue_name | schema_name.queue_name | queue_name }
```  
  
## <a name="arguments"></a>Argumente  
 *database_name*  
 Der Name der Datenbank, die die zu löschende Warteschlange enthält. Wenn *database_name* nicht bereitgestellt wird, wird standardmäßig die aktuelle Datenbank verwendet.  
  
 *schema_name (Objekt)*  
 Der Name des Schemas, das die zu löschende Warteschlange besitzt. Wenn *schema_name* nicht angegeben wird, wird standardmäßig das Standardschema für den aktuellen Benutzer verwendet.  
  
 *queue_name*  
 Der Name der zu löschenden Warteschlange.  
  
## <a name="remarks"></a>Bemerkungen  
 Sie können eine Warteschlange nicht löschen, wenn Dienste auf sie verweisen.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig verfügen der Besitzer der Warteschlange, Mitglieder der festen Datenbankrollen **db_ddladmin** oder **db_owner** und Mitglieder der festen Datenbankrolle **sysadmin** über die Berechtigung zum Löschen einer Warteschlange.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Warteschlange **ExpenseQueue** aus der aktuellen Datenbank gelöscht.  
  
```  
DROP QUEUE ExpenseQueue ;  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE QUEUE &#40;Transact-SQL&#41;](../../t-sql/statements/create-queue-transact-sql.md)   
 [ALTER QUEUE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-queue-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
