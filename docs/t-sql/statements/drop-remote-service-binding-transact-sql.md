---
title: DROP REMOTE SERVICE BINDING (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP REMOTE SERVICE BINDING
- DROP_REMOTE_SERVICE_BINDING_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dropping remote service bindings
- removing remote service bindings
- deleting remote service bindings
- remote service bindings [Service Broker], dropping
- DROP REMOTE SERVICE BINDING statement
ms.assetid: 377789b4-bf94-488f-8c20-687d0bae447a
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 6abe725d180b36de3eeea53c59666da1322214bf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63033542"
---
# <a name="drop-remote-service-binding-transact-sql"></a>DROP REMOTE SERVICE BINDING (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht eine Remotedienstbindung.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
DROP REMOTE SERVICE BINDING binding_name  
[ ; ]  
```  
  
## <a name="arguments"></a>Argumente  
 *binding_name*  
 Der Name der zu löschenden Remotedienstbindung. Server-, Datenbank- und Schemaname können nicht angegeben werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Die Berechtigung zum Löschen einer Remotedienstbindung erhalten standardmäßig Besitzer der Remotedienstbindung, Mitglieder der festen Datenbankrolle db_owner und Mitglieder der festen Serverrolle sysadmin.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Remotedienstbindung `APBinding` aus der Datenbank gelöscht.  
  
```  
DROP REMOTE SERVICE BINDING APBinding ;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE REMOTE SERVICE BINDING &#40;Transact-SQL&#41;](../../t-sql/statements/create-remote-service-binding-transact-sql.md)   
 [ALTER REMOTE SERVICE BINDING &#40;Transact-SQL&#41;](../../t-sql/statements/alter-remote-service-binding-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
