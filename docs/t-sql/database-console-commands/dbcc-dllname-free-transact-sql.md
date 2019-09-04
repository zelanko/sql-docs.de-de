---
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
ms.openlocfilehash: cc9716cbd1e27c6589b964c3c3d6208105f4863c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68101948"
---
# <a name="dbcc-dllname-free-transact-sql"></a>DBCC dllname (FREE) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
Entfernt die angegebene DLL einer erweiterten gespeicherten Prozedur aus dem Arbeitsspeicher.
  
![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
```sql
DBCC <dllname> ( FREE ) [ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Argumente  
 \<*dllname*>  
 Der Name der DLL, die aus dem Arbeitsspeicher gelöscht werden soll.  
  
 WITH NO_INFOMSGS  
 Alle Informationsmeldungen werden unterdrückt.  
  
## <a name="remarks"></a>Bemerkungen
Wenn eine erweiterte gespeicherte Prozedur ausgeführt wird, wird die DLL so lange von der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Arbeitsspeicher gehalten, bis der Server heruntergefahren wird. Mithilfe dieser Anweisung kann eine DLL aus dem Arbeitsspeicher entfernt werden, ohne dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] heruntergefahren werden muss. Führen Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]aus, um die zurzeit von **aus, um die zurzeit von**geladenen DLL-Dateien anzuzeigen.
  
## <a name="result-sets"></a>Resultsets  
Wenn eine gültige DLL angegeben wird, gibt DBCC *dllname* (FREE) Folgendes zurück:
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Berechtigungen  
Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** oder der festen Datenbankrolle **db_owner** .
  
## <a name="examples"></a>Beispiele  
Bei dem folgenden Beispiel wird vorausgesetzt, dass `xp_sample` als xp_sample.dll implementiert ist und ausgeführt wurde. DBCC \<*dllname*> (FREE) entfernt die Datei „xp_sample.dll“ aus dem Arbeitsspeicher, die der erweiterten Prozedur `xp_sample` zugeordnet ist.
  
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
  
  
