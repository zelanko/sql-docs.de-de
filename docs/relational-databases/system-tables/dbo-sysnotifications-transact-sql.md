---
title: dbo.sysnotifications (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysnotifications_TSQL
- sysnotifications
- sysnotifications_TSQL
- dbo.sysnotifications
dev_langs:
- TSQL
helpviewer_keywords:
- sysnotifications system table
ms.assetid: c5150d18-e8b7-48a7-ada7-77c583af6e41
author: stevestein
ms.author: sstein
ms.openlocfilehash: ef7a5456f0bae470bcbf1f12f37843aa6c311d78
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67984919"
---
# <a name="dbosysnotifications-transact-sql"></a>dbo.sysnotifications (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jede Benachrichtigung.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**alert_id**|**int**|ID der Warnung.|  
|**operator_id**|**int**|ID des Operators, an den diese Benachrichtigung gesendet werden soll.|  
|**notification_method**|**tinyint**|Benachrichtigungsmethode:<br /><br /> **1** = E-mail<br /><br /> **2** = Pager<br /><br /> **4** = **NET SEND**<br /><br /> **7** = all|  
  
  
