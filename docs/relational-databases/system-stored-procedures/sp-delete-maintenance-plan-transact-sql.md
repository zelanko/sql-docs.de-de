---
title: sp_delete_maintenance_plan (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_maintenance_plan
- sp_delete_maintenance_plan_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_maintenance_plan
ms.assetid: 6f36b63f-3d18-4d42-9469-2febb6926530
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5d878c1ece7139cd582aeaca39100c0719005ac5
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830334"
---
# <a name="sp_delete_maintenance_plan-transact-sql"></a>sp_delete_maintenance_plan (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht den angegebenen Wartungsplan.  
  
> [!NOTE]  
>  Diese gespeicherte Prozedur wird mit Datenbankwartungsplänen verwendet. Diese Funktion wurde durch Wartungspläne ersetzt, die nicht diese gespeicherte Prozedur verwenden. Verwenden Sie diese Prozedur, um Datenbankwartungspläne für Installationen bereitzustellen, die von einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]aktualisiert wurden.  
  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_delete_maintenance_plan [ @plan_id = ] 'plan_id'   
```  
  
## <a name="arguments"></a>Argumente  
`[ @plan_id = ] 'plan\_id'`Gibt die ID des zu löschenden Wartungsplans an. *plan_id* ist vom Datentyp **uniqueidentifier**und muss eine gültige ID sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_delete_maintenance_plan** muss von der **msdb** -Datenbank ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Serverrolle **sysadmin** können **sp_delete_maintenance_plan**ausführen.  
  
## <a name="examples"></a>Beispiele  
 In diesem Beispiel wird der erstellte Wartungsplan mithilfe von **sp_add_maintenance_plan**gelöscht.  
  
```  
EXECUTE sp_delete_maintenance_plan 'FAD6F2AB-3571-11D3-9D4A-00C04FB925FC';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Wartungspläne](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [Gespeicherte Prozeduren für Datenbank-Wartungspläne &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-maintenance-plan-stored-procedures-transact-sql.md)  
  
  
