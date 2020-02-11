---
title: sp_add_targetservergroup (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_targetservergroup
- sp_add_targetservergroup_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_targetservergroup
ms.assetid: acb69343-d766-46ff-b771-0c7655c5231a
author: stevestein
ms.author: sstein
ms.openlocfilehash: c268c356e41c957349f452d2f83fc4b807042d9e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67990496"
---
# <a name="sp_add_targetservergroup-transact-sql"></a>sp_add_targetservergroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fügt die angegebene Servergruppe hinzu.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_add_targetservergroup [ @name = ] 'name'   
```  
  
## <a name="arguments"></a>Argumente  
`[ @name = ] 'name'`Der Name der zu erstellenden Server Gruppe. *Name ist vom Datentyp* **vom Datentyp sysname**und hat keinen Standardwert. der *Name* darf keine Kommas enthalten.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Mit Zielservergruppen lassen sich Aufträge problemlos auf mehrere Zielservergruppen anwenden. Weitere Informationen finden Sie unter [sp_apply_job_to_targets](../../relational-databases/system-stored-procedures/sp-apply-job-to-targets-transact-sql.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können diese Prozedur ausführen.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Zielservergruppe `Servers Processing Customer Orders` erstellt.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_targetservergroup  
    'Servers Processing Customer Orders' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_apply_job_to_targets &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-apply-job-to-targets-transact-sql.md)   
 [sp_delete_targetservergroup &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-targetservergroup-transact-sql.md)   
 [sp_help_targetservergroup &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-targetservergroup-transact-sql.md)   
 [sp_update_targetservergroup &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-update-targetservergroup-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
