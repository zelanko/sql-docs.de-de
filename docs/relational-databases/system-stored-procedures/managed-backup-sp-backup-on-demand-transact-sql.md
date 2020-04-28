---
title: managed_backup. sp_backup_on_demand (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: e34cf20585ea7dcd3690d80ee415fc274bf852ca
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "70155401"
---
# <a name="managed_backupsp_backup_on_demand-transact-sql"></a>managed_backup. sp_backup_on_demand (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Weist [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] an, eine Sicherung der angegebenen Datenbank auszuführen.  
  
 Führen Sie mithilfe dieser gespeicherten Prozedur Ad-hoc-Sicherungen für eine mit [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] konfigurierte Datenbank aus. Dadurch wird verhindert, dass eine Unterbrechung in [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] der Sicherungs Kette erfolgt, und die Prozesse werden in demselben Azure BLOB Storage-Container gespeichert.  
  
 Nach dem erfolgreichen Abschluss der Sicherung wird der vollständige Sicherungsdateipfad zurückgegeben. Dieser schließt den Namen und den Speicherort der neuen Sicherungsdatei ein, die durch den Sichervorgang erzeugt wird.  
  
 Ein Fehler wird zurückgegeben, wenn [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] im Begriff ist, eine Sicherung eines bestimmten Typs für die angegebene Datenbank auszuführen. In diesem Fall enthält die zurückgegebene Fehlermeldung den vollständigen Sicherungsdateipfad, unter dem die aktuelle Sicherung hochgeladen wird.  
   
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```sql  
EXEC managed_backup.sp_backup_on_demand   
[@database_name  =]  'database name',[@type = ] { 'Database' | 'Log' }  
  
```  
  
##  <a name="arguments"></a><a name="Arguments"></a>Argumentation  
 @database_name  
 Der Name der Datenbank, für die die Sicherung ausgeführt werden soll. Ist @database_name vom **Datentyp sysname**.  
  
 @type  
 Der Typ der auszuführenden Sicherung: Datenbank- oder Protokollsicherung. Der @type Parameter ist vom Datentyp **nvarchar (32)**.  
  
## <a name="return-code-value"></a>Rückgabecodewert  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="security"></a>Sicherheit  
  
### <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in **db_backupoperator** Daten Bank Rolle mit **ALTER ANY CREDENTIAL** -Berechtigungen und **Execute** -Berechtigungen für die gespeicherte Prozedur **sp_delete_backuphistory**.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine Daten Bank Sicherungs Anforderung für die Datenbank "TestDB" erstellt. Für diese Datenbank ist [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] aktiviert.  
  
```  
Use MSDB  
Go  
EXEC managed_backup.sp_backup_on_demand  
 @database_name = 'TestDB'  
,@type = 'Database'  
  
```  
  
 Wählen Sie für jeden Codeausschnitt "tsql" im Sprachattributfeld aus.  
  
  
