---
title: Msdistributiondsb (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdistributiondbs_TSQL
- MSdistributiondbs
dev_langs:
- TSQL
helpviewer_keywords:
- MSdistributiondbs system table
ms.assetid: d7ffa9df-bf1d-41b8-837e-b762c17c2764
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9f7fbc3827a7859cfbd4b38d90860e43560d8ad5
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85753905"
---
# <a name="msdistributiondbs-transact-sql"></a>MSdistributiondbs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Die **msdistributiondsb** -Tabelle enthält eine Zeile für jede Verteilungs Datenbank, die auf dem lokalen Verteiler definiert ist. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Der Name der Verteilungs Datenbank.|  
|**min_distretention**|**int**|Die minimale Beibehaltungs Dauer in Stunden, bevor Transaktionen gelöscht werden.|  
|**max_distretention**|**int**|Die maximale Beibehaltungsdauer in Stunden, bevor Transaktionen gelöscht werden.|  
|**history_retention**|**int**|Die Anzahl der Stunden, für die der Verlauf erhalten bleibt.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
