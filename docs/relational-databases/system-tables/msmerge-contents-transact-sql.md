---
title: MSmerge_contents (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_contents
- MSmerge_contents_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_contents system table
ms.assetid: 8d68a61a-683f-4b20-92f9-c0a8d9ba0ad1
author: stevestein
ms.author: sstein
ms.openlocfilehash: a4be6cffcc7e4f13b88d8037b53d438d604b9650
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68089944"
---
# <a name="msmergecontents-transact-sql"></a>MSmerge_contents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSmerge_contents** -Tabelle enthält eine Zeile für jede Zeile in der aktuellen Datenbank geändert, seit diese veröffentlicht wurde. Diese Tabelle wird vom Mergeprozess verwendet, um die geänderten Zeilen zu ermitteln. Diese Tabelle wird in der Veröffentlichungs- und in der Abonnementdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|Der Spitzname der veröffentlichten Tabelle.|  
|**rowguid**|**uniqueidentifier**|Der Zeilenbezeichner für die angegebene Zeile.|  
|**generation**|**bigint**|Die Generierung der Zeile durch identifiziert die **Tablenick** und **Rowguid**.|  
|**partchangegen**|**bigint**|Die Generierung, die der letzten Datenänderung zugeordnet ist, bei der die Zugehörigkeit der Zeile zu einer gefilterten Veröffentlichung geändert worden sein könnte|  
|**Datenherkunft**|**varbinary(501)**|Die Paare aus Spitzname des Abonnenten und Versionsnummer, die zur Verwaltung eines Verlaufs der Änderungen an dieser Zeile verwendet werden.|  
|**colvl**|**varbinary(7489)**|Die Versionsinformationen für die Spalte.|  
|**Marker**|**uniqueidentifier**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**logical_record_parent_rowguid**|**uniqueidentifier**|Gibt die obersten übergeordneten Zeile im **MSmerge_contents** (von **Rowguid**) für jede entsprechende untergeordnete Zeile in einem logischen Datensatz.|  
|**logical_record_lineage**|**varbinary(501)**|Die Paare aus Spitzname des Abonnenten und Versionsnummer, die zur Verwaltung eines Verlaufs der Änderungen an der übergeordneten Zeile der obersten Ebene in einem logischen Datensatz verwendet werden. Für alle untergeordneten Zeilen in einem logischen Datensatz lautet dieser Wert NULL.|  
|**logical_relation_change_gen**|**bigint**|Der Generierungswert, der mit der letzten Änderung verbunden ist, die zur Neuausrichtung des logischen Datensatzes führte. Die Neuausrichtung wurde erforderlich, da eine vorhandene Zeile in den logischen Datensatz hinein oder aus diesem heraus verschoben wurde.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
