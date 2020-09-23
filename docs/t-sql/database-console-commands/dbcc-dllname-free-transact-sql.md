---
description: DBCC dllname (FREE) (Transact-SQL)
title: DBCC dllname (FREE) (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/16/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- dbcc_dllname_(FREE)_TSQL
- dllname
- dbcc dllname (FREE)
- FREE
- dbcc_dllname(FREE)_TSQL
- FREE_TSQL
- dllname_TSQL
- dbcc dllname(FREE)
dev_langs:
- TSQL
helpviewer_keywords:
- DLL unloading [SQL Server]
- DBCC dllname (FREE)
- freeing DLLs
- unloading DLLs
ms.assetid: 1eb71c17-fe15-430b-8916-e4e312dcf9c0
author: pmasl
ms.author: umajay
ms.openlocfilehash: 0fd6d497ed6738d6ef290645df9bcad18ca6df32
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91116933"
---
# <a name="dbcc-dllname-free-transact-sql"></a>DBCC dllname (FREE) (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
Entfernt die angegebene DLL einer erweiterten gespeicherten Prozedur aus dem Arbeitsspeicher.
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
```syntaxsql
DBCC <dllname> ( FREE ) [ WITH NO_INFOMSGS ]  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 \<*dllname*>  
 Der Name der DLL, die aus dem Arbeitsspeicher gelöscht werden soll.  
  
 WITH NO_INFOMSGS  
 Alle Informationsmeldungen werden unterdrückt.  
  
## <a name="remarks"></a>Bemerkungen
Wenn eine erweiterte gespeicherte Prozedur ausgeführt wird, wird die DLL so lange von der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Arbeitsspeicher gehalten, bis der Server heruntergefahren wird. Mithilfe dieser Anweisung kann eine DLL aus dem Arbeitsspeicher entfernt werden, ohne dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] heruntergefahren werden muss. Führen Sie **sp_helpextendedproc** aus, damit alle zum aktuellen Zeitpunkt von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] geladenen DLL-Dateien angezeigt werden.
  
## <a name="result-sets"></a>Resultsets  
Wenn eine gültige DLL angegeben wird, gibt DBCC *dllname* (FREE) Folgendes zurück:
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Berechtigungen  
Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** oder der festen Datenbankrolle **db_owner** .
  
## <a name="examples"></a>Beispiele  
Bei dem folgenden Beispiel wird vorausgesetzt, dass `xp_sample` als xp_sample.dll implementiert ist und ausgeführt wurde. DBCC \<*dllname*> (FREE) entfernt die Datei xp_sample.dll, die der erweiterten Prozedur `xp_sample` zugeordnet ist, aus dem Arbeitsspeicher.
  
```sql  
DBCC xp_sample (FREE);  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[Ausführungsmerkmale erweiterter gespeicherter Prozeduren](../../relational-databases/extended-stored-procedures-programming/execution-characteristics-of-extended-stored-procedures.md)  
[sp_addextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql.md)  
[sp_dropextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)  
[sp_helpextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)  
[Entfernen der DLL einer erweiterten gespeicherten Prozedur aus dem Arbeitsspeicher](../../relational-databases/extended-stored-procedures-programming/unloading-an-extended-stored-procedure-dll.md)
  
  
