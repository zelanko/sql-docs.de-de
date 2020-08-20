---
description: MSmerge_articlehistory (Transact-SQL)
title: MSmerge_articlehistory (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_articlehistory
- MSmerge_articlehistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_articlehistory system table
ms.assetid: 2870e7ea-dbec-4636-9171-c2cee96018ac
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b12fea643b97bda83758288459681ff98e9423cf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88454646"
---
# <a name="msmerge_articlehistory-transact-sql"></a>MSmerge_articlehistory (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  In der **MSmerge_articlehistory** Tabelle werden Änderungen nachverfolgt, die während einer Merge-Agent Synchronisierungs Sitzung an Artikeln vorgenommen wurden, mit einer Zeile für jeden Artikel, in dem Änderungen vorgenommen wurden. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|Die ID einer Merge-Agent Auftrags Sitzung in der [MSmerge_sessions](../../relational-databases/system-tables/msmerge-sessions-transact-sql.md) -Systemtabelle.|  
|**phase_id**|**int**|Die Phase der Synchronisierungssitzung, die einen der folgenden Werte haben kann:<br /><br /> **1** = hochladen.<br /><br /> **2** = herunterladen.<br /><br /> **4** = bereinigen.<br /><br /> **5** = Herunterfahren.<br /><br /> **6** = Schema Änderungen.<br /><br /> **7** = bcp.|  
|**article_name**|**sysname**|Der Name des Artikels, an dem Änderungen vorgenommen wurden.|  
|**start_time**|**datetime**|Der Zeitpunkt, an dem der Agent mit der Verarbeitung des Artikels begonnen hat.|  
|**duration**|**int**|Angabe der Dauer (in Sekunden) der Verarbeitung eines Artikels durch den Agent.|  
|**lagen**|**int**|Die Anzahl von Einfügevorgängen, die für einen bestimmten Artikel bei der Synchronisierung durchgeführt wurden. Dieser Wert wird während der Synchronisierung inkrementiert, die Gesamtzahl wird im Endwert angegeben.|  
|**Updates**|**int**|Die Anzahl von Updates, die für einen bestimmten Artikel bei der Synchronisierung vorgenommen wurden. Dieser Wert wird während der Synchronisierung inkrementiert, die Gesamtzahl wird im Endwert angegeben.|  
|**Löscht**|**int**|Die Anzahl von Löschvorgängen, die für einen bestimmten Artikel bei der Synchronisierung stattgefunden haben. Dieser Wert wird während der Synchronisierung inkrementiert, die Gesamtzahl wird im Endwert angegeben.|  
|**Conflicts**|**int**|Die Anzahl von bei der Synchronisierung aufgetretenen Konflikten. Dieser Wert wird während der Synchronisierung inkrementiert, die Gesamtzahl wird im Endwert angegeben.|  
|**conflicts_resolved**|**int**|Die Anzahl von Konflikten, die bei der Synchronisierung aufgetreten sind und gelöst wurden. Dieser Wert wird während der Synchronisierung inkrementiert, die Gesamtzahl wird im Endwert angegeben.|  
|**rows_retried**|**int**|Die Anzahl von fehlerhaften Zeilen, die bei der Synchronisierung wiederholt wurden. Dieser Wert wird während der Synchronisierung inkrementiert, die Gesamtzahl wird im Endwert angegeben.|  
|**percent_complete**|**decimal**|Der Prozentsatz an der gesamten Synchronisierungszeit, die der Merge-Agent während einer Sitzung für den Artikel aufgewendet hat. Dieser Wert ist NULL, bis die Sitzung abgeschlossen ist.|  
|**estimated_changes**|**int**|Eine Schätzung der Anzahl von Zeilenänderungen, die für den Artikel angewendet werden müssen.|  
|**relative_cost**|**decimal**|Die Zeit, die für das Anwenden von Änderungen für diesen Artikel aufgewendet werden musste, im Vergleich zur Dauer der gesamten Sitzung.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
