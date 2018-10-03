---
title: Sysopentapes (Transact-SQL) | Microsoft-Dokumentation
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7ebbaef020fe1bc45b625d255523769bb1c54a4a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47677838"
---
# <a name="sysopentapes-transact-sql"></a>sysopentapes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jedes aktuell geöffnete Bandmedium. Diese Ansicht befindet sich in der **master** Datenbank.  
  
> [!IMPORTANT]  
>  Diese Systemtabelle wird aus Gründen der Abwärtskompatibilität als Sicht bereitgestellt. Verwenden Sie stattdessen die [Sys. dm_io_backup_tapes &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-io-backup-tapes-transact-sql.md) dynamische verwaltungssicht.  
  
> [!NOTE]  
>  Sie können nicht gelöscht werden die **Sysopentapes** anzeigen.  

  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**openTape**|**Nvarchar(64)**|Physischer Dateiname des geöffneten Bandmediums. Weitere Informationen zum Öffnen und Freigeben von Bandmedien finden Sie unter [Sicherung &#40;Transact-SQL&#41; ](../../t-sql/statements/backup-transact-sql.md) und [wiederherstellen &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md).|  
  
## <a name="permissions"></a>Berechtigungen  
 Der Benutzer benötigt die VIEW SERVER STATE-Berechtigung auf dem Server.  
  
  
