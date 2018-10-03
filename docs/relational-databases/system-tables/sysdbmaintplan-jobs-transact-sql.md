---
title: Sysdbmaintplan_jobs (Transact-SQL) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 0e54355cf0c7806c70f6bb80ee0463744b4c869b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47794946"
---
# <a name="sysdbmaintplanjobs-transact-sql"></a>sysdbmaintplan_jobs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Diese Tabelle ist in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enthalten, um vorhandene Informationen für Instanzen beizubehalten, für die ein Update von einer früheren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] durchgeführt wurde. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] der Inhalt dieser Tabelle wird nicht geändert werden. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  

  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**plan_id**|**uniqueidentifier**|ID des Datenbankwartungsplans.|  
|**job_id**|**uniqueidentifier**|ID eines Auftrags, der dem Datenbank-Wartungsplan zugeordnet ist.|  
  
  
