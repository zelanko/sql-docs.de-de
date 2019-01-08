---
title: Sp_schemafilter (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_schemafilter_TSQL
- sp_schemafilter
helpviewer_keywords:
- sp_schemafilter
ms.assetid: 199e869b-2cd2-44ee-b2ee-69edb06a1bc4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3018d23247a8f4d127d09878cb20c5f48f76c4ff
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53206946"
---
# <a name="spschemafilter-transact-sql"></a>sp_schemafilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert Informationen im Schema, die beim Auflisten von für die Veröffentlichung in Frage kommenden Oracle-Tabellen ausgeschlossen werden, und zeigt diese an.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_schemafilter [ @publisher = ] 'publisher'   
   [ , [ @schema = ] 'schema' ]   
   [ , [ @operation = ] 'operation' ]   
```  
  
## <a name="arguments"></a>Argumente  
 [**@publisher** =] **"***Verleger***"**  
 Der Name des nicht- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger. *Publisher* ist **Sysname**, hat keinen Standardwert.  
  
 [**@schema** =] **"***Schema***"**  
 Der Name des Schemas. *Schema* ist **Sysname**, hat den Standardwert NULL.  
  
 [**@operation** =] **"***Vorgang***"**  
 Die Aktion, die für dieses Schema ausgeführt werden soll. *Vorgang* ist **nvarchar(4)**, und kann einen der folgenden Werte.  
  
|Wert|Description|  
|-----------|-----------------|  
|**add**|Fügt das angegebene Schema der Liste der Schemas hinzu, die für die Veröffentlichung nicht in Frage kommen.|  
|**Löschen**|Löscht das angegebene Schema aus der Liste der Schemas, die für die Veröffentlichung nicht in Frage kommen.|  
|**Hilfe**|Gibt die Liste der Schemas zurück, die für die Veröffentlichung nicht in Frage kommen.|  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**Schemaname**|**sysname**|Der Name des Schemas, das für die Veröffentlichung nicht in Frage kommt.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_schemafilter** sollte nur für heterogene Verleger verwendet werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle auf dem Verteiler **Sp_schemafilter**.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
