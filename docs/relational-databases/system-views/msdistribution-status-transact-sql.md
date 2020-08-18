---
description: MSdistribution_status (Transact-SQL)
title: MSdistribution_status (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdistribution_status_TSQL
- MSdistribution_status
dev_langs:
- TSQL
helpviewer_keywords:
- MSdistribution_status view
ms.assetid: 90d447de-3a4a-4f3e-aeab-e8fff6348361
author: stevestein
ms.author: sstein
ms.openlocfilehash: 07acca59b78290d1cab5d0c528604a8a9616ece8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473094"
---
# <a name="msdistribution_status-transact-sql"></a>MSdistribution_status (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Die **MSdistribution_status** Ansicht zeigt zusätzliche Informationen zu den Status Befehlen in der Verteilungs Datenbank an. Diese Sicht wird in der distribution-Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**article_id**|**int**|Identifiziert einen Artikel.|  
|**agent_id**|**int**|Identifiziert einen Replikations-Agent|  
|**UndelivCmdsInDistDB**|**int**|Die Anzahl der Befehle, die für die Übermittlung an Abonnenten ausstehen.|  
|**DelivCmdsInDistDB**|**int**|Die Anzahl der Befehle, die an Abonnenten übermittelt wurden|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
