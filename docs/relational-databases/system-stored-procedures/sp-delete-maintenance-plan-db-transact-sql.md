---
title: Sp_delete_maintenance_plan_db (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_maintenance_plan_db_TSQL
- sp_delete_maintenance_plan_db
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_maintenance_plan_db
- maintenance plans [SQL Server], deleting
- removing maintenance plan
- disassociating maintenance plan
ms.assetid: d1e8afb5-12ee-492b-a770-ba708ed7c8a4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 81631efabd541ace5dd7296b54d806ec3750d327
ms.sourcegitcommit: fc6a6eedcea2d98c93e33d39c1cecd99fbc9a155
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49169061"
---
# <a name="spdeletemaintenanceplandb-transact-sql"></a>sp_delete_maintenance_plan_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Trennt den angegebenen Wartungsplan und die angegebene Datenbank.  
  
> [!NOTE]  
>  Diese gespeicherte Prozedur wird mit Datenbankwartungsplänen verwendet. Diese Funktion wurde durch Wartungspläne ersetzt, die nicht diese gespeicherte Prozedur verwenden. Verwenden Sie diese Prozedur, um Datenbankwartungspläne für Installationen bereitzustellen, die von einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]aktualisiert wurden.  
  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_delete_maintenance_plan_db [ @plan_id = ] 'plan_id' ,   
     [ @db_name = ] 'database_name'   
```  
  
## <a name="arguments"></a>Argumente  
 [  **@plan_id =**] **"**_Plan\_Id_**"**  
 Gibt die ID des Wartungsplans. *Plan_id* ist **Uniqueidentifier**.  
  
 [  **@db_name =**] **"**_Datenbank\_Namen_**"**  
 Gibt den Namen der Datenbank an, die aus dem Wartungsplan gelöscht werden soll. *database_name* ist **sysname**  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_delete_maintenance_plan_db** muss ausgeführt werden, aus der **Msdb** Datenbank.  
  
 Die **Sp_delete_maintenance_plan_db** gespeicherte Prozedur entfernt die Zuordnung zwischen dem Wartungsplan und der angegebenen Datenbank; nicht löschen oder zerstören die Datenbank.  
  
 Wenn **Sp_delete_maintenance_plan_db** entfernt die letzte Datenbank, aus dem Wartungsplan, der die gespeicherte Prozedur löscht auch den Wartungsplan.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Sysadmin** feste Serverrolle **Sp_delete_maintenance_plan_db**.  
  
## <a name="examples"></a>Beispiele  
 Löscht den Wartungsplan in der **AdventureWorks2012** -Datenbank mithilfe von zuvor hinzugefügte **Sp_add_maintenance_plan_db**.  
  
```  
EXECUTE   sp_delete_maintenance_plan_db N'FAD6F2AB-3571-11D3-9D4A-00C04FB925FC', N'AdventureWorks2012';  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Wartungspläne](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [Datenbank-Wartungsplans gespeicherte Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-maintenance-plan-stored-procedures-transact-sql.md)  
  
  
