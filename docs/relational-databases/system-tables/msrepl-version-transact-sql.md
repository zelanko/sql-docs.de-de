---
description: MSrepl_version (Transact-SQL)
title: MSrepl_version (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSrepl_version
- MSrepl_version_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_version system table
ms.assetid: c1330f03-940b-4564-ac42-6030c6e21173
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 46ec999ebb21446d0a4973dc393460aa69f1bdc7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473165"
---
# <a name="msrepl_version-transact-sql"></a>MSrepl_version (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Die **MSrepl_version** Tabelle enthält eine Zeile, in der die aktuelle Version der Replikation installiert ist. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**major_version**|**int**|Die Hauptversionsnummer der Verteilungsdatenbank.|  
|**minor_version**|**int**|Die Nebenversionsnummer der Verteilungsdatenbank.|  
|**revision**|**int**|Die Revisionsnummer.|  
|**db_existed**|**bit**|Gibt an, ob die Verteilungs Datenbank vorhanden ist, bevor **sp_adddistributiondb** aufgerufen wird.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
