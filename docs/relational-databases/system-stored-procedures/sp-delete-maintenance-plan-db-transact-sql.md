---
description: sp_delete_maintenance_plan_db (Transact-SQL)
title: sp_delete_maintenance_plan_db (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9997758701897aa5fa37afb85cac053e22b0e5c0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88474372"
---
# <a name="sp_delete_maintenance_plan_db-transact-sql"></a>sp_delete_maintenance_plan_db (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Trennt den angegebenen Wartungsplan und die angegebene Datenbank.  
  
> [!NOTE]  
>  Diese gespeicherte Prozedur wird mit Datenbankwartungsplänen verwendet. Diese Funktion wurde durch Wartungspläne ersetzt, die nicht diese gespeicherte Prozedur verwenden. Verwenden Sie diese Prozedur, um Datenbankwartungspläne für Installationen bereitzustellen, die von einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]aktualisiert wurden.  
  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_delete_maintenance_plan_db [ @plan_id = ] 'plan_id' ,   
     [ @db_name = ] 'database_name'   
```  
  
## <a name="arguments"></a>Argumente  
`[ @plan_id = ] 'plan\_id'` Gibt die ID des Wartungsplans an. *plan_id* ist vom Datentyp **uniqueidentifier**.  
  
`[ @db_name = ] 'database\_name'` Gibt den Datenbanknamen an, der aus dem Wartungsplan gelöscht werden soll. *database_name* ist **sysname**  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_delete_maintenance_plan_db** müssen von der **msdb** -Datenbank aus ausgeführt werden.  
  
 Die gespeicherte Prozedur **sp_delete_maintenance_plan_db** entfernt die Zuordnung zwischen dem Wartungsplan und der angegebenen Datenbank. die Datenbank wird nicht gelöscht oder zerstört.  
  
 Wenn **sp_delete_maintenance_plan_db** die letzte Datenbank aus dem Wartungsplan entfernt, löscht die gespeicherte Prozedur auch den Wartungsplan.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_delete_maintenance_plan_db**ausführen.  
  
## <a name="examples"></a>Beispiele  
 Löscht den Wartungsplan in der **AdventureWorks2012** -Datenbank, der zuvor mit **sp_add_maintenance_plan_db**hinzugefügt wurde.  
  
```  
EXECUTE   sp_delete_maintenance_plan_db N'FAD6F2AB-3571-11D3-9D4A-00C04FB925FC', N'AdventureWorks2012';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Wartungspläne](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [Gespeicherte Prozeduren für Datenbank-Wartungspläne &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-maintenance-plan-stored-procedures-transact-sql.md)  
  
  
