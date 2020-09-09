---
description: logmarkhistory (Transact-SQL)
title: logmarkhistory (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- logmarkhistory
- logmarkhistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- logmarkhistory system table
ms.assetid: 5c1becc5-f34e-4869-bf69-dfafab684540
author: markingmyname
ms.author: maghan
ms.openlocfilehash: e5b7a952735485c85c4763937a6448c164e3823b
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89538286"
---
# <a name="logmarkhistory-transact-sql"></a>logmarkhistory (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Enthält eine Zeile für jede markierte Transaktion, für die ein Commit ausgeführt wurde. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  

|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**database_name**|**nvarchar(128)**|Lokale Datenbank, in der die markierte Transaktion aufgetreten ist|  
|**mark_name**|**nvarchar(128)**|Vom Benutzer bereitgestellter Name für die markierte Transaktion|  
|**description**|**nvarchar(255)**|Vom Benutzer bereitgestellte Beschreibung für die markierte Transaktion Kann den Wert NULL haben.|  
|**user_name**|**nvarchar(128)**|Datenbank-Benutzername, der die markierte Transaktion durchgeführt hat. Kann den Wert NULL haben.|  
|**LSN**|**numeric(25,0)**|Protokollsequenznummer des Transaktionsdatensatzes, in dem die Markierung auftrat|  
|**mark_time**|**datetime**|Bestätigungszeitpunkt der markierten Transaktion (lokale Zeit)|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Wiederherstellen einer Datenbank bis zu einer markierten Transaktion &#40;SQL Server Management Studio&#41;](../../relational-databases/backup-restore/restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)   
 [Wiederherstellen von verwandten Datenbanken mithilfe von markierten Transaktionen &#40;vollständiges Wiederherstellungsmodell&#41;](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md)   
 [Systemtabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
