---
title: sp_add_maintenance_plan (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_maintenance_plan
- sp_add_maintenance_plan_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_maintenance_plan
ms.assetid: 01ab1834-6260-47cb-a1b7-20722217b062
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: aa33e418b81cb2f77a39f20d36bba7a25caffb4c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68104585"
---
# <a name="sp_add_maintenance_plan-transact-sql"></a>sp_add_maintenance_plan (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fügt einen Wartungsplan hinzu und gibt seine Plan-ID zurück.  
  
> [!NOTE]  
>  Diese gespeicherte Prozedur wird mit Datenbankwartungsplänen verwendet. Diese Funktion wurde durch Wartungspläne ersetzt, die nicht diese gespeicherte Prozedur verwenden. Verwenden Sie diese Prozedur, um Datenbankwartungspläne für Installationen bereitzustellen, die von einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]aktualisiert wurden.  
  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_add_maintenance_plan [ @plan_name = ] 'plan_name' ,   
     @plan_id = 'plan_id' OUTPUT  
```  
  
## <a name="arguments"></a>Argumente  
`[ @plan_name = ] 'plan_name'`Gibt den Namen des Wartungsplans an, der hinzugefügt werden soll. *plan_name* ist vom Datentyp **varchar (128)**.  
  
 *plan_id* ** @plan_id = '** plan_id **'**  
 Gibt die ID des Wartungsplans an. *plan_id* ist vom Datentyp **uniqueidentifier**.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_add_maintenance_plan** müssen von der **msdb** -Datenbank aus ausgeführt werden, und es wird ein neuer, aber leerer Wartungsplan erstellt. Um eine oder mehrere Datenbanken hinzuzufügen und Sie einem Auftrag oder Aufträgen zuzuordnen, führen Sie **sp_add_maintenance_plan_db** und **sp_add_maintenance_plan_job**aus.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_add_maintenance_plan**ausführen.  
  
## <a name="examples"></a>Beispiele  
 Erstellen eines Wartungsplans namens Myplan.  
  
```  
DECLARE   @myplan_id UNIQUEIDENTIFIER;  
EXECUTE   sp_add_maintenance_plan N'Myplan',@plan_id=@myplan_id OUTPUT  
PRINT   'The id for the maintenance plan "Myplan" is:'+convert(varchar(256),@myplan_id);  
GO  
```  
  
 Wenn der Wartungsplan erfolgreich erstellt wurde, wird seine Plan-ID zurückgegeben.  
  
```  
'The id for the maintenance plan "Myplan" is:' FAD6F2AB-3571-11D3-9D4A-00C04FB925FC  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Wartungspläne](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [Gespeicherte Prozeduren für Datenbank-Wartungspläne &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-maintenance-plan-stored-procedures-transact-sql.md)  
  
  
