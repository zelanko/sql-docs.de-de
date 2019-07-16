---
title: Sp_helparticledts (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helparticledts
- sp_helparticledts_TSQL
helpviewer_keywords:
- sp_helparticledts
ms.assetid: cd1aed60-e056-4ff3-86ee-62b19433d890
author: stevestein
ms.author: sstein
ms.openlocfilehash: 153b7736f126a09765eaac4c364b322fffc96c48
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68084946"
---
# <a name="sphelparticledts-transact-sql"></a>sp_helparticledts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ruft Informationen zu den benutzerdefinierten Tasknamen ab, die beim Erstellen eines Transformationsabonnements mithilfe von [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic verwendet werden sollen. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helparticledts [ @publication = ] 'publication', [ @article = ] 'article'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat keinen Standardwert.  
  
`[ @article = ] 'article'` Ist der Name eines Artikels in der Veröffentlichung. *Artikel* ist **Sysname**, hat keinen Standardwert.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**pre_script_ignore_error_task_name**|**sysname**|Taskname für den Programmiertask, der auftritt, bevor die Momentaufnahmedaten kopiert werden. Die Programmausführung soll beim Auftreten eines Skriptfehlers fortgesetzt werden.|  
|**pre_script_task_name**|**sysname**|Taskname für den Programmiertask, der auftritt, bevor die Momentaufnahmedaten kopiert werden. Die Programmausführung wird beim Auftreten eines Fehlers beendet.|  
|**transformation_task_name**|**sysname**|Taskname für den Programmiertask, wenn der Task Datengesteuerte Abfrage verwendet wird.|  
|**post_script_ignore_error_task_name**|**sysname**|Taskname für den Programmiertask, der auftritt, nachdem die Momentaufnahmedaten kopiert wurden. Die Programmausführung soll beim Auftreten eines Skriptfehlers fortgesetzt werden.|  
|**post_script_task_name**|**sysname**|Taskname für den Programmiertask, der auftritt, nachdem die Momentaufnahmedaten kopiert wurden. Die Programmausführung wird beim Auftreten eines Fehlers beendet.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_helparticledts** wird bei Momentaufnahme- und Transaktionsreplikation verwendet.  
  
 Beim Benennen von Tasks in einem Replikations-DTS-Programm (Data Transformation Services) müssen für die Replikations-Agents bestimmte Namenskonventionen eingehalten werden. Für benutzerdefinierte Tasks, wie z. B. den Task SQL ausführen, stellt der Name eine verkettete Zeichenfolge dar, die aus dem Artikelnamen, einem Präfix und einem optionalen Teil besteht. Wenn Sie den Code schreiben und sich nicht sicher sind, wie die Tasknamen lauten sollen, dann weist das Resultset die zu verwendenden Tasknamen zu.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der der **Sysadmin** Serverrolle und die **Db_owner** feste Datenbankrolle können ausführen **Sp_helparticledts**.  
  
  
