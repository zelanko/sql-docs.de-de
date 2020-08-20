---
description: sysopentapes (Transact-SQL)
title: sysopentapes (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysopentapes
- sysopentapes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- backup media [SQL Server], sysopentapes system table
- sysopentapes system table
ms.assetid: c066ca9b-9cfd-46b1-90a3-5c8dc9e7b6ae
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d97f19143a2d1128f6164543847cfbc27b275877
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473142"
---
# <a name="sysopentapes-transact-sql"></a>sysopentapes (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Enthält eine Zeile für jedes aktuell geöffnete Bandmedium. Diese Sicht wird in der **Master** -Datenbank gespeichert.  
  
> [!IMPORTANT]  
>  Diese Systemtabelle wird aus Gründen der Abwärtskompatibilität als Sicht bereitgestellt. Verwenden Sie stattdessen die dynamische Verwaltungs Sicht [sys. dm_io_backup_tapes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql.md) .  
  
> [!NOTE]  
>  Die **sysopentapes** -Sicht kann nicht gelöscht werden.  

  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**openTape**|**nvarchar (64)**|Physischer Dateiname des geöffneten Bandmediums. Weitere Informationen zum Öffnen und Freigeben von Band Geräten finden Sie unter [Backup &#40;Transact-SQL-&#41;](../../t-sql/statements/backup-transact-sql.md) und [Restore &#40;Transact-SQL-&#41;](../../t-sql/statements/restore-statements-transact-sql.md).|  
  
## <a name="permissions"></a>Berechtigungen  
 Der Benutzer benötigt die View Server State-Berechtigung auf dem Server.  
  
  
