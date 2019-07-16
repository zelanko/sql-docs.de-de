---
title: managed_backup.sp_backup_on_demand (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- smart_admin.sp_backup_on_demand
- smart_admin.sp_backup_on_demand_TSQL
- sp_backup_on_demand_TSQL
- sp_backup_on_demand
dev_langs:
- TSQL
helpviewer_keywords:
- smart_admin.sp_backup_on_demand
- sp_backup_on_demand
ms.assetid: 638f809f-27fa-4c44-a549-9cf37ecc920c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 980fb3006819e5727033376beae1f8156d26e0fc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67942051"
---
# <a name="managedbackupspbackupondemand-transact-sql"></a>managed_backup.sp_backup_on_demand (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Weist [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] an, eine Sicherung der angegebenen Datenbank auszuführen.  
  
 Führen Sie mithilfe dieser gespeicherten Prozedur Ad-hoc-Sicherungen für eine mit [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] konfigurierte Datenbank aus. Auf diese Weise ist gewährleistet, dass die Sicherungskette nicht unterbrochen wird, Prozesse von [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] erkannt werden und die Sicherung im selben Windows Azure-BLOB-Speichercontainer gespeichert wird.  
  
 Nach dem erfolgreichen Abschluss der Sicherung wird der vollständige Sicherungsdateipfad zurückgegeben. Dieser schließt den Namen und den Speicherort der neuen Sicherungsdatei ein, die durch den Sichervorgang erzeugt wird.  
  
 Ein Fehler wird zurückgegeben, wenn [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] im Begriff ist, eine Sicherung eines bestimmten Typs für die angegebene Datenbank auszuführen. In diesem Fall enthält die zurückgegebene Fehlermeldung den vollständigen Sicherungsdateipfad, unter dem die aktuelle Sicherung hochgeladen wird.  
   
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```sql  
EXEC managed_backup.sp_backup_on_demand   
[@database_name  =]  'database name',[@type = ] { 'Database' | 'Log' }  
  
```  
  
##  <a name="Arguments"></a> Argumente  
 @database_name  
 Der Name der Datenbank, für die die Sicherung ausgeführt werden soll. Die @database_name ist **SYSNAME**.  
  
 @type  
 Der Typ des auszuführenden Sicherungsvorgangs:  Datenbank- oder protokollsicherung. Die @type Parameter **NVARCHAR(32)** .  
  
## <a name="return-code-value"></a>Rückgabecodewert  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in **Db_backupoperator** -Datenbankrolle mit **ALTER ANY CREDENTIAL** Berechtigungen und **EXECUTE** Berechtigungen für **Sp_delete_ Backuphistory**gespeicherte Prozedur.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine datenbanksicherungsanforderung für die Datenbank "TestDB". Für diese Datenbank ist [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] aktiviert.  
  
```  
Use MSDB  
Go  
EXEC managed_backup.sp_backup_on_demand  
 @database_name = 'TestDB'  
,@type = 'Database'  
  
```  
  
 Wählen Sie für jeden Codeausschnitt "tsql" im Sprachattributfeld aus.  
  
  
