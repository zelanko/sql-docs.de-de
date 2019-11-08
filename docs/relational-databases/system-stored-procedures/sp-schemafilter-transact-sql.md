---
title: sp_schemafilter (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 231796d1678a19106eb89f3039cd755e8385082c
ms.sourcegitcommit: 66dbc3b740f4174f3364ba6b68bc8df1e941050f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2019
ms.locfileid: "73633017"
---
# <a name="sp_schemafilter-transact-sql"></a>sp_schemafilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert Informationen im Schema, die beim Auflisten von für die Veröffentlichung in Frage kommenden Oracle-Tabellen ausgeschlossen werden, und zeigt diese an.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlink (Symbol)") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_schemafilter [ @publisher = ] 'publisher'   
   [ , [ @schema = ] 'schema' ]   
   [ , [ @operation = ] 'operation' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'` ist der Name des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verlegers, der nicht [!INCLUDE[msCoName](../../includes/msconame-md.md)] ist. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @schema = ] 'schema'` ist der Name des Schemas. *Schema* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @operation = ] 'operation'` ist die Aktion, die für dieses Schema ausgeführt werden soll. der *Vorgang* ist vom Datentyp **nvarchar (4)** . die folgenden Werte sind möglich:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**eren**|Fügt das angegebene Schema der Liste der Schemas hinzu, die für die Veröffentlichung nicht in Frage kommen.|  
|**Dropdown**|Löscht das angegebene Schema aus der Liste der Schemas, die für die Veröffentlichung nicht in Frage kommen.|  
|**Hilfe**|Gibt die Liste der Schemas zurück, die für die Veröffentlichung nicht in Frage kommen.|  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**Schema Name**|**sysname**|Der Name des Schemas, das für die Veröffentlichung nicht in Frage kommt.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_schemafilter** sollten nur für heterogene Verleger verwendet werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** auf dem Verteiler können **sp_schemafilter**ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Replikationsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
