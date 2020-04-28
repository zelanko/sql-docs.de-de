---
title: sp_syscollector_delete_collection_set (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_delete_collection_set_TSQL
- sp_syscollector_delete_collection_set
dev_langs:
- TSQL
helpviewer_keywords:
- data collector [SQL Server], stored procedures
- sp_syscollector_delete_collecton_set
ms.assetid: 29c63a74-4db4-4068-bd57-9fb519b0c598
author: stevestein
ms.author: sstein
ms.openlocfilehash: e60fb13244d6740b7d52c568835e54155eeb8c46
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68000875"
---
# <a name="sp_syscollector_delete_collection_set-transact-sql"></a>sp_syscollector_delete_collection_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht einen benutzerdefinierten Auflistsatz und all seine Sammlungselemente.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_syscollector_delete_collection_set [[ @collection_set_id = ] collection_set_id OUTPUT ]  
    , [[ @name = ] 'name' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @collection_set_id = ] *collection_set_id*  
 Der eindeutige Bezeichner für den Sammlungssatz. *collection_set_id* ist vom *Datentyp* **int** und muss über einen Wert verfügen, wenn Name NULL ist.  
  
 [ @name = ] "*Name*"  
 Der Name des Sammlungs Satzes. *Name ist vom Datentyp* **vom Datentyp sysname** und muss über einen Wert verfügen, wenn *collection_set_id* NULL ist.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 sp_syscollector_delete_collection_set müssen im Kontext der msdb-Systemdatenbank ausgeführt werden.  
  
 Entweder *collection_set_id* oder *Name* muss einen Wert aufweisen, beide dürfen nicht NULL sein. Um diese Werte zu erhalten, Fragen Sie die syscollector_collection_set Systemsicht ab.  
  
 Vom System definierte Sammlungssätze können nicht gelöscht werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Damit diese Prozedur ausgeführt werden kann, ist die Mitgliedschaft in der festen Datenbankrolle dc_admin (mit EXECUTE-Berechtigung) erforderlich.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird ein benutzerdefinierter Sammlungs Satz gelöscht, der die *collection_set_id*angibt.  
  
```  
USE msdb;  
GO  
EXEC dbo.sp_syscollector_delete_collection_set  
    @collection_set_id = 4;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren für den Datensammler &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Datensammlung](../../relational-databases/data-collection/data-collection.md)   
 [syscollector_collection_sets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql.md)  
  
  
