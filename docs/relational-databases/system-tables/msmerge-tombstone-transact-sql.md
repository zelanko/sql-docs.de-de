---
title: MSmerge_tombstone (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_tombstone_TSQL
- MSmerge_tombstone
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_tombstone system table
ms.assetid: 8b3fc7bf-729b-40f2-8a26-e7dfbe8ddb38
author: stevestein
ms.author: sstein
ms.openlocfilehash: 12caefe8b764090d46051912c876272c9efe86bd
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68092659"
---
# <a name="msmerge_tombstone-transact-sql"></a>MSmerge_tombstone (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSmerge_tombstone** Tabelle enthält Informationen zu gelöschten Zeilen und ermöglicht das Weitergeben von Lösch Vorgängen an andere Abonnenten. Diese Tabelle wird in der Veröffentlichungs- und in der Abonnementdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**rowguid**|**uniqueidentifier**|Der Zeilen Bezeichner.|  
|**tablenick**|**int**|Spitzname der Tabelle|  
|**type**|**tinyint**|Der Typ des Löschvorgangs:<br /><br /> 1 = Löschvorgang durch Benutzer.<br /><br /> 5 = Zeile gehört nicht mehr zur gefilterten Partition.<br /><br /> 6 = Löschvorgang durch System.|  
|**Leitung**|**varbinary (249)**|Zeigt die Version des Datensatzes an, der gelöscht wurde, und die Updates, die bekannt waren, als der Datensatz gelöscht wurde. Ermöglicht Regeln für eine konsistente Auflösung eines Konflikts, wenn ein Abonnent eine Zeile aktualisiert, während diese auf einem anderen Abonnenten gelöscht wird.|  
|**Stro**|**int**|Wird zugewiesen, wenn eine Zeile gelöscht wird. Wenn ein Abonnent Generation N anfordert, werden nur Tombstones mit Generation >= n gesendet.|  
|**logical_record_parent_rowguid**|**uniqueidentifier**|Identifiziert den logischen Datensatz, zu dem eine gelöschte Zeile gehört hat.|  
|**logical_record_lineage**|**Varbinary (501)**|Paare aus Spitzname des Abonnenten und Versionsnummer, die zur Verwaltung eines Verlaufs der Löschungen für den logischen Datensatz, zu dem diese Zeile gehört, verwendet werden.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
