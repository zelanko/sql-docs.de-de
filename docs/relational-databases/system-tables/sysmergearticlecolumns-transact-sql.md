---
title: sysmergearticlecolumns (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysmergearticlecolumns
- sysmergearticlecolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmergearticlecolumns system table
ms.assetid: 1ad8663f-a624-42a2-8641-fefac3433c97
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e15f6a424a4fc13b4aaf1ad8240fa43cf7708b42
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82829172"
---
# <a name="sysmergearticlecolumns-transact-sql"></a>sysmergearticlecolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **sysmergearticlecolumns** -Tabelle enthält eine Zeile für jede Tabellenspalte, die in einer Mergeveröffentlichung veröffentlicht wird, und ordnet jede Spalte dem zugehörigen Mergeartikel zu. Diese Tabelle wird in der Veröffentlichungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Identifiziert einen Artikel.|  
|**colid**|**smallint**|Identifiziert eine Spalte in einem Artikel.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
