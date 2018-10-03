---
title: Sp_set_session_context (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_set_session_context
- sp_set_session_context_TSQL
- sys.sp_set_session_context
- sys.sp_set_session_context_TSQL
helpviewer_keywords:
- sp_set_session_context
ms.assetid: 7a3a3b2a-1408-4767-a376-c690e3c1fc5b
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d278e7540ef27e4c6041406bc7c4011976a5a213
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47832758"
---
# <a name="spsetsessioncontext-transact-sql"></a>Sp_set_session_context (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

Legt den Schlüssel-Wert-Paar im Sitzungskontext fest.  
  

 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_set_session_context [ @key= ] 'key', [ @value= ] 'value'  
    [ , [ @read_only = ] { 0 | 1 } ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @key=] 'Key'  
 Der Schlüssel, der festgelegt wird, vom Typ **Sysname**. Die größte gültige Schlüsselgröße ist 128 Bytes.  
  
 [ @value=] 'Value'  
 Der Wert für den angegebenen Schlüssel, der Typ **Sql_variant**. Festlegen eines Werts von NULL gibt den Arbeitsspeicher frei. Die maximale Größe beträgt 8.000 Bytes.  
  
 [ @read_only= ] { 0 | 1 }  
 Ein Flag des Typs **Bit**. Bei 1 kann nicht erneut der Wert für den angegebenen Schlüssel für die logische Verbindung geändert werden. Wenn 0 (Standard), wird der Wert geändert werden kann.  
  
## <a name="permissions"></a>Berechtigungen  
 Jeder Benutzer kann einen Sitzungskontext für seine Sitzung festlegen.  
  
## <a name="remarks"></a>Hinweise  
 Ähnlich wie andere gespeicherte Prozeduren können nur Literale und Variablen (not-Ausdrücke oder Funktionsaufrufe) als Parameter übergeben werden.  
  
 Die Gesamtgröße des Sitzungskontexts ist auf 256 kb beschränkt. Wenn festgelegt ist ein Wert, der bewirkt, dass dieser Grenzwert überschritten wird, schlägt die Anweisung fehl. Sie können überwachen, die gesamtspeicherauslastung in [Sys. dm_os_memory_objects &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql.md).  
  
 Sie können die gesamte speicherauslastung überwachen, indem Sie Abfragen [Sys. dm_os_memory_cache_counters &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-counters-transact-sql.md) wie folgt: `SELECT * FROM sys.dm_os_memory_cache_counters WHERE type = 'CACHESTORE_SESSION_CONTEXT';`  
  
## <a name="examples"></a>Beispiele  
 Das folgende Beispiel zeigt, wie Sie festlegen, und klicken Sie dann einen Sitzungen-Kontext-Schlüssel mit dem Namen Sprache mit einem Wert von Englisch zurück.  
  
```  
EXEC sp_set_session_context 'language', 'English';  
SELECT SESSION_CONTEXT(N'language');  
```  
  
 Im folgende Beispiel wird die Verwendung des optionalen Schreibschutz-Flags veranschaulicht.  
  
```  
EXEC sp_set_session_context 'user_id', 4, @read_only = 1;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [CURRENT_TRANSACTION_ID &#40;Transact-SQL&#41;](../../t-sql/functions/current-transaction-id-transact-sql.md)   
 [SESSION_CONTEXT &#40;Transact-SQL&#41;](../../t-sql/functions/session-context-transact-sql.md)   
 [Sicherheit auf Zeilenebene](../../relational-databases/security/row-level-security.md)   
 [CONTEXT_INFO  &#40;Transact-SQL&#41;](../../t-sql/functions/context-info-transact-sql.md)   
 [SET CONTEXT_INFO &#40;Transact-SQL&#41;](../../t-sql/statements/set-context-info-transact-sql.md)  
  
  
