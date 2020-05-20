---
title: dbo. sysnotification (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 69a2c9dea5f2ce0745bf30cef9a99eb0b245c433
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82806761"
---
# <a name="dbosysnotifications-transact-sql"></a>dbo.sysnotifications (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jede Benachrichtigung.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**alert_id**|**int**|ID der Warnung.|  
|**operator_id**|**int**|ID des Operators, an den diese Benachrichtigung gesendet werden soll.|  
|**notification_method**|**tinyint**|Benachrichtigungsmethode:<br /><br /> **1** = E-Mail<br /><br /> **2** = Pager<br /><br /> **4**  =  " **nend** "<br /><br /> **7** = alle|  
  
  
