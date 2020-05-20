---
title: sp_delete_schedule (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_schedule
- sp_delete_schedule_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_schedule
ms.assetid: 18b2c985-47b8-49c8-82d1-8a4af3d7d33a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 57dea8c65cf1541030b87e965591b98c64c9b261
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82833334"
---
# <a name="sp_delete_schedule-transact-sql"></a>sp_delete_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Löscht einen Zeitplan.  
 
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_delete_schedule { [ @schedule_id = ] schedule_id | [ @schedule_name = ] 'schedule_name' } ,  
     [ @force_delete = ] force_delete  
```  
  
## <a name="arguments"></a>Argumente  
`[ @schedule_id = ] schedule_id`Die Zeitplan-ID des zu löschenden Zeitplans. *schedule_id* ist vom Datentyp **int**und hat den Standardwert NULL.  
  
> **Hinweis:** Es muss entweder *schedule_id* oder *schedule_name* angegeben werden, beide Angaben können jedoch nicht angegeben werden.  
  
`[ @schedule_name = ] 'schedule_name'`Der Name des zu löschenden Zeitplans. *schedule_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> **Hinweis:** Es muss entweder *schedule_id* oder *schedule_name* angegeben werden, beide Angaben können jedoch nicht angegeben werden.  
  
`[ @force_delete = ] force_delete`Gibt an, ob die Prozedur fehlschlagen soll, wenn der Zeitplan einem Auftrag angefügt ist. *Force_delete* ist vom Typ Bit. der Standardwert ist **0**. Wenn *force_delete* **0**ist, schlägt die gespeicherte Prozedur fehl, wenn der Zeitplan an einen Auftrag angefügt ist. Wenn *force_delete* **1**ist, wird der Zeitplan gelöscht, unabhängig davon, ob der Zeitplan an einen Auftrag angefügt ist.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Standardmäßig kann ein Zeitplan nicht gelöscht werden, wenn der Zeitplan einem Auftrag angefügt ist. Um einen Zeitplan zu löschen, der einem Auftrag zugeordnet ist, geben Sie für *force_delete*den Wert **1** an. Durch das Löschen eines Zeitplans werden derzeit ausgeführte Aufträge nicht beendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können Mitglieder der festen Server Rolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Hinweis: Der Auftragsbesitzer kann einem Zeitplan einen Auftrag anfügen oder diesen von ihm trennen, und zwar ohne der Zeitplanbesitzer sein zu müssen. Ein Zeitplan kann jedoch nicht gelöscht werden, wenn der Trennvorgang keine Aufträge hat, es sei denn, der Aufrufer ist der Zeit Plan Besitzer.  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Nur Mitglieder der **sysadmin** -Rolle können einen Auftrags Zeitplan löschen, der im Besitz eines anderen Benutzers ist.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-deleting-a-schedule"></a>A. Löschen eines Zeitplans  
 Im folgenden Beispiel wird der Zeitplan `NightlyJobs` gelöscht. Wenn der Zeitplan einem Auftrag angefügt ist, kann der Zeitplan im Rahmen des Beispiels nicht gelöscht werden.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_schedule  
    @schedule_name = N'NightlyJobs' ;  
GO  
```  
  
### <a name="b-deleting-a-schedule-attached-to-a-job"></a>B. Löschen eines an einen Auftrag angefügten Zeitplans  
 Im folgenden Beispiel wird der Zeitplan `RunOnce` gelöscht, unabhängig davon, ob der Zeitplan einem Auftrag angefügt ist.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_schedule  
    @schedule_name = 'RunOnce',  
    @force_delete = 1;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Implementieren von Aufträgen](../../ssms/agent/implement-jobs.md)   
 [sp_add_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-schedule-transact-sql.md)  
  
  
