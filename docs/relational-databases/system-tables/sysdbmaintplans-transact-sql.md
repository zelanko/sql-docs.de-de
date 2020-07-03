---
title: sysdbmaintplans übereinstimmen (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdbmaintplans_TSQL
- sysdbmaintplans
dev_langs:
- TSQL
helpviewer_keywords:
- sysdbmaintplans system table
ms.assetid: 0363296a-3082-48a9-9eb5-a1020b2f541a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7eb84e9d50a797e52aca749cf590ca95b4f3e835
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85881402"
---
# <a name="sysdbmaintplans-transact-sql"></a>sysdbmaintplans (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Diese Tabelle ist in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enthalten, um vorhandene Informationen für Instanzen beizubehalten, für die ein Update von einer früheren Version von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]durchgeführt wurde. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ändert den Inhalt dieser Tabelle nicht. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  

  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**plan_id**|**uniqueidentifier**|ID des Datenbankwartungsplans.|  
|**plan_name**|**sysname**|Name des Datenbankwartungsplans.|  
|**date_created**|**datetime**|Erstellungsdatum des Datenbankwartungsplans.|  
|**Eigentor**|**sysname**|Besitzer des Datenbankwartungsplans.|  
|**max_history_rows**|**int**|Maximale Anzahl von Zeilen, die für das Aufzeichnen des Verlaufs für den Datenbankwartungsplan in der Systemtabelle zugeteilt werden.|  
|**remote_history_server**|**sysname**|Der Name des Remoteservers, auf den der Verlaufsbericht geschrieben werden konnte.|  
|**max_remote_history_rows**|**int**|Maximale Anzahl von Zeilen, die in der Systemtabelle auf einem Remoteserver zugeteilt wurden und in die der Verlaufsbericht geschrieben werden konnte.|  
|**user_defined_1**|**int**|Der Standardwert ist NULL.|  
|**user_defined_2**|**nvarchar (100)**|Der Standardwert ist NULL.|  
|**user_defined_3**|**datetime**|Der Standardwert ist NULL.|  
|**user_defined_4**|**uniqueidentifier**|Der Standardwert ist NULL.|  
|**log_shipping**|**bit**|Protokollversandstatus:<br /><br /> **0** = Deaktiviert **1** = Aktiviert|  
  
  
