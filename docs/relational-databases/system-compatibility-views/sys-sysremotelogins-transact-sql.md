---
title: sys.sysRemoteLogins (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysremotelogins
- sysremotelogins_TSQL
- sys.sysremotelogins
- sys.sysremotelogins_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysremotelogins system table
- sys.sysremotelogins compatibility view
ms.assetid: b7ffcfa6-aed8-41d4-8b70-845439ab813d
author: rothja
ms.author: jroth
ms.openlocfilehash: 520749113c3e9aeea8f2d0c3c3125965b1511a5a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85718848"
---
# <a name="syssysremotelogins-transact-sql"></a>sys.sysremotelogins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Enthält eine Zeile für jeden Remote Benutzer, dem gespeicherte Remote Prozeduren auf einer Instanz von aufgerufen werden dürfen [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**remoteserverid**|**smallint**|ID des Remoteservers.|  
|**remoteusername**|**sysname**|Anmeldename des Benutzers auf einem Remoteserver.|  
|**status**|**smallint**|Gibt 0 zurück.|  
|**sid**|**varbinary(85)**|Sicherheits-ID des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Benutzers.|  
|**changedate**|**datetime**|Datum und Uhrzeit, zu dem bzw. der der Remotebenutzer hinzugefügt wurde.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zuordnung von Systemtabellen zu System Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Kompatibilitätssichten &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
