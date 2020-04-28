---
title: sysdbmaintplan_jobs (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdbmaintplan_jobs
- sysdbmaintplan_jobs_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysdbmaintplan_jobs system table
ms.assetid: bc65cd70-6ef2-4c17-be11-877ecf4efe50
author: stevestein
ms.author: sstein
ms.openlocfilehash: f780199361d9e5741187dd4e5346abb2df98b9cb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68130442"
---
# <a name="sysdbmaintplan_jobs-transact-sql"></a>sysdbmaintplan_jobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Diese Tabelle ist in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enthalten, um vorhandene Informationen für Instanzen beizubehalten, für die ein Update von einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]durchgeführt wurde. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ändert den Inhalt dieser Tabelle nicht. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  

  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**plan_id**|**uniqueidentifier**|ID des Datenbankwartungsplans.|  
|**job_id**|**uniqueidentifier**|ID eines Auftrags, der dem Datenbank-Wartungsplan zugeordnet ist.|  
  
  
