---
title: dbo. systargetservers (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.systargetservers_TSQL
- dbo.systargetservers
- systargetservers_TSQL
- systargetservers
dev_langs:
- TSQL
helpviewer_keywords:
- systargetservers system table
ms.assetid: 479d1314-be37-4d19-ac9c-419fc9110e53
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3c6304b108d75d6fe9ba00ccccdae322bf7cedde
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68095841"
---
# <a name="dbosystargetservers-transact-sql"></a>dbo.systargetservers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Zeichnet auf, welche Zielserver derzeit in dieser Domäne für Multiservervorgänge eingetragen sind.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|Server-ID.|  
|**server_name**|**sysname**|Servername.|  
|**location**|**nvarchar(200)**|Speicherort des angegebenen Zielservers.|  
|**time_zone_adjustment**|**int**|Zeitanpassungsintervall in Bezug auf die GMT (Greenwich Mean Time) in Stunden.|  
|**enlist_date**|**datetime**|Datum und Uhrzeit der Eintragung des angegebenen Zielservers.|  
|**last_poll_date**|**datetime**|Datum und Uhrzeit des Zeitpunkts, an dem der angegebene Zielserver die **sysdownloadlist** -Systemtabelle des Multiservers zuletzt abgerufen hat, um nach auszuführenden Aufträgen zu suchen.|  
|**status**|**int**|Status des Zielservers:<br /><br /> **1** = Normal<br /><br /> **2** = Neusynchronisierung ausstehend<br /><br /> **4** = Offline vermutet|  
|**local_time_at_last_poll**|**datetime**|Datum und Uhrzeit des letzten Versuchs, Auftragsvorgänge vom Zielserver abzurufen.|  
|**enlisted_by_nt_user**|**nvarchar (100)**|Benutzername der Person, die **sp_msx_enlist** auf dem Zielserver ausführt.|  
|**poll_internal**|**int**|Anzahl von Sekunden, die verstreichen müssen, bevor der Zielserver versucht, vom Masterserver neue Downloadanweisungen abzurufen.|  
  
  
