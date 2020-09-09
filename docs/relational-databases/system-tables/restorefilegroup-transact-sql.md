---
description: restorefilegroup (Transact-SQL)
title: restorefilegroup (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- restorefilegroup_TSQL
- restorefilegroup
dev_langs:
- TSQL
helpviewer_keywords:
- filegroups [SQL Server], restorefilegroup system table
- restorefilegroup system table
ms.assetid: 3aa15c55-6b72-4f76-97d7-bd88391d105c
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 52d1fb66f32d17521343c979493766f2d1ff086a
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89545325"
---
# <a name="restorefilegroup-transact-sql"></a>restorefilegroup (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Enthält eine Zeile für jede wiederhergestellte Dateigruppe. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**restore_history_id**|**int**|Eindeutiger Bezeichner, der den entsprechenden Wiederherstellungsvorgang angibt. Verweist auf **restorehistory (restore_history_id)**.|  
|**filegroup_name**|**nvarchar(128)**|Name der wiederhergestellten Dateigruppe. Kann den Wert NULL haben.<br /><br /> Wird eine Datenbankmomentaufnahme einer Datenbank wiederhergestellt, wird dieser Wert auf die gleiche Weise wie bei einer vollständigen Wiederherstellung aufgefüllt.|  
  
## <a name="remarks"></a>Hinweise  
 Führen Sie die gespeicherte Prozedur [sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md) aus, um die Anzahl der Zeilen in dieser Tabelle und in anderen Sicherungs-und Verlaufs Tabellen zu verringern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sichern und Wiederherstellen von Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [restorefile &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/restorefile-transact-sql.md)   
 [restorehistory &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/restorehistory-transact-sql.md)   
 [Systemtabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
