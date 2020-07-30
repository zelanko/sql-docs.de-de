---
title: sp_set_session_context (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/14/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse
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
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 11a3bae7cc6cbf025370a947c8fa3194f978d419
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87394506"
---
# <a name="sp_set_session_context-transact-sql"></a>sp_set_session_context (Transact-SQL)
[!INCLUDE [sqlserver2016-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa.md)]

Legt ein Schlüssel-Wert-Paar im Sitzungs Kontext fest.  
  

 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_set_session_context [ @key= ] N'key', [ @value= ] 'value'  
    [ , [ @read_only = ] { 0 | 1 } ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @key =] N ' Schlüssel '  
 Der Schlüssel, der festgelegt wird, vom Typ **vom Datentyp sysname**. Die maximale Schlüsselgröße beträgt 128 Bytes.  
  
 [ @value =] ' Wert '  
 Der Wert für den angegebenen Schlüssel vom Typ **sql_variant**. Wenn Sie den Wert NULL festlegen, wird der Arbeitsspeicher freigegeben. Die maximale Größe beträgt 8.000 Bytes.  
  
 [ @read_only =] {0 | 1}  
 Ein Flag vom Typ **Bit**. Wenn der Wert 1 ist, kann der Wert für den angegebenen Schlüssel für diese logische Verbindung nicht erneut geändert werden. Der Standardwert 0 gibt an, dass der Wert geändert werden kann.  
  
## <a name="permissions"></a>Berechtigungen  
 Jeder Benutzer kann einen Sitzungs Kontext für seine Sitzung festlegen.  
  
## <a name="remarks"></a>Bemerkungen  
 Wie bei anderen gespeicherten Prozeduren können nur Literale und Variablen (keine Ausdrücke oder Funktionsaufrufe) als Parameter übermittelt werden.  
  
 Die Gesamtgröße des Sitzungs Kontexts ist auf 1 MB beschränkt. Wenn Sie einen Wert festlegen, der bewirkt, dass dieser Grenzwert überschritten wird, schlägt die Anweisung fehl. Sie können die Gesamtspeicher Auslastung in [sys. dm_os_memory_objects &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql.md)überwachen.  
  
 Sie können die Gesamtspeicher Auslastung überwachen, indem Sie [sys. dm_os_memory_cache_counters &#40;Transact-SQL-&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-counters-transact-sql.md) wie folgt Abfragen:`SELECT * FROM sys.dm_os_memory_cache_counters WHERE type = 'CACHESTORE_SESSION_CONTEXT';`  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird gezeigt, wie ein Sitzungs Kontext Schlüssel namens Language mit dem Wert Englisch festgelegt und dann zurückgegeben wird.  
  
```  
EXEC sys.sp_set_session_context @key = N'language', @value = 'English';  
SELECT SESSION_CONTEXT(N'language');  
```  
  
 Im folgenden Beispiel wird die Verwendung des optionalen Flag mit Leseberechtigung veranschaulicht.  
  
```  
EXEC sys.sp_set_session_context @key = N'user_id', @value = 4, @read_only = 1;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [CURRENT_TRANSACTION_ID &#40;Transact-SQL-&#41;](../../t-sql/functions/current-transaction-id-transact-sql.md)   
 [SESSION_CONTEXT &#40;Transact-SQL-&#41;](../../t-sql/functions/session-context-transact-sql.md)   
 [Sicherheit auf Zeilenebene](../../relational-databases/security/row-level-security.md)   
 [CONTEXT_INFO &#40;Transact-SQL-&#41;](../../t-sql/functions/context-info-transact-sql.md)   
 [SET CONTEXT_INFO &#40;Transact-SQL&#41;](../../t-sql/statements/set-context-info-transact-sql.md)  
  
  
