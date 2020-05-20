---
title: sp_delete_jobserver (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_jobserver
- sp_delete_jobserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_jobserver
ms.assetid: 6d63ed32-68cf-4d8f-aa40-05a3826e05b8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4499183a8cf5019fe7a4ce10bdb9ffc83726551a
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82831199"
---
# <a name="sp_delete_jobserver-transact-sql"></a>sp_delete_jobserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Entfernt den angegebenen Zielserver.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_delete_jobserver { [ @job_id = ] job_id | [ @job_name = ] 'job_name' } ,   
     [ @server_name = ] 'server'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_id = ] job_id`Die ID des Auftrags, aus dem der angegebene Zielserver entfernt wird. *job_id* ist vom Datentyp **uniqueidentifier**und hat den Standardwert NULL.  
  
`[ @job_name = ] 'job_name'`Der Name des Auftrags, aus dem der angegebene Zielserver entfernt wird. *job_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Es muss entweder *job_id* oder *job_name* angegeben werden. Beide können nicht angegeben werden.  
  
`[ @server_name = ] 'server'`Der Name des Zielservers, der aus dem angegebenen Auftrag entfernt werden soll. der *Server* ist vom Datentyp **nvarchar (30)** und hat keinen Standardwert. der *Server* kann **(local)** oder der Name eines Remote Zielservers sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="permissions"></a>Berechtigungen  
 Zum Ausführen dieser gespeicherten Prozedur müssen Benutzer Mitglieder der festen Server Rolle **sysadmin** sein.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Server `SEATTLE2` aus der Verarbeitung des `Weekly Sales Backups` Auftrags entfernt.  
  
> [!NOTE]  
>  Bei diesem Beispiel wird davon ausgegangen, dass der Auftrag `Weekly Sales Backups` bereits erstellt wurde.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_delete_jobserver  
    @job_name = N'Weekly Sales Backups',  
    @server_name = N'SEATTLE2' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_add_jobserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_help_jobserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-jobserver-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
