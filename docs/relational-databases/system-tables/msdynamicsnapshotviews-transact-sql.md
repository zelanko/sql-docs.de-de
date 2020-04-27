---
title: MSdynamicsnapshotviews (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdynamicsnapshotviews_TSQL
- MSdynamicsnapshotviews
dev_langs:
- TSQL
helpviewer_keywords:
- MSdynamicsnapshotviews system table
ms.assetid: 4fc1822a-5d6e-4034-a2e2-363210232d3b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8de7dd1571f7b9082144e97c8b35d9a39d6cabe8
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67907322"
---
# <a name="msdynamicsnapshotviews-transact-sql"></a>MSdynamicsnapshotviews (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  In der **MSdynamicsnapshotviews** -Tabelle werden alle vom Momentaufnahme-Agent erstellten temporären Sichten für die Momentaufnahme von gefilterten Daten nachverfolgt und vom System zum Bereinigen von Sichten bei einem nicht ordnungsgemäßen Herunterfahren von SQL Server-Agent oder der Momentaufnahmen-Agent verwendet. Diese Tabelle wird in der Veröffentlichungs- und in der Abonnementdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**dynamic_snapshot_view_name**|**sysname**|Der Name der gefilterten Datenmomentaufnahmesicht.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
