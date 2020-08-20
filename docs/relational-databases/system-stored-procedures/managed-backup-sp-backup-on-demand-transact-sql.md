---
description: managed_backup. sp_backup_on_demand (Transact-SQL)
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4357cc8cc214f610ef1f61c27dd8e05be3e3d56b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88486293"
---
# <a name="managed_backupsp_backup_on_demand-transact-sql"></a>managed_backup. sp_backup_on_demand (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Weist [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] an, eine Sicherung der angegebenen Datenbank auszuführen.  
  
 Führen Sie mithilfe dieser gespeicherten Prozedur Ad-hoc-Sicherungen für eine mit [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] konfigurierte Datenbank aus. Dadurch wird verhindert, dass eine Unterbrechung in der Sicherungs Kette erfolgt, und [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] die Prozesse werden in demselben Azure BLOB Storage-Container gespeichert.  
  
 Nach dem erfolgreichen Abschluss der Sicherung wird der vollständige Sicherungsdateipfad zurückgegeben. Dieser schließt den Namen und den Speicherort der neuen Sicherungsdatei ein, die durch den Sichervorgang erzeugt wird.  
  
 Ein Fehler wird zurückgegeben, wenn [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] im Begriff ist, eine Sicherung eines bestimmten Typs für die angegebene Datenbank auszuführen. In diesem Fall enthält die zurückgegebene Fehlermeldung den vollständigen Sicherungsdateipfad, unter dem die aktuelle Sicherung hochgeladen wird.  
   
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```sql  
EXEC managed_backup.sp_backup_on_demand   
[@database_name  =]  'database name',[@type = ] { 'Database' | 'Log' }  
  
```  
  
##  <a name="arguments"></a><a name="Arguments"></a>Argumente  
 @database_name  
 Der Name der Datenbank, für die die Sicherung ausgeführt werden soll. @database_nameIst vom **Datentyp sysname**.  
  
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
  
  
