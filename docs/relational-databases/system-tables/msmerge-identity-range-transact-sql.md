---
description: MSmerge_identity_range (Transact-SQL)
title: MSmerge_identity_range (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_identity_range_TSQL
- MSmerge_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_identity_range system table
ms.assetid: 493a2028-88a0-4e83-ad89-ae5661d9f477
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4011fcc653e72327fbbd20b3b7d8ec1da135f4f9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88463929"
---
# <a name="msmerge_identity_range-transact-sql"></a>MSmerge_identity_range (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Die **MSmerge_identity_range** Tabelle dient zum Nachverfolgen der numerischen Bereiche, die Identitäts Spalten für Abonnements von Veröffentlichungen zugewiesen werden, für die die Replikation diese Bereichs Zuweisungen automatisch verwaltet. Diese Tabelle wird in der Veröffentlichungs- und in der Abonnementdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**subid**|**uniqueidentifier**|Die eindeutige ID für ein bestimmtes Abonnement.|  
|**artid**|**uniqueidentifier**|Die eindeutige ID des angegebenen Artikels.|  
|**range_begin**|**numerisch (38)**|Der Identitätswert am Anfang des aktuellen Bereichs.|  
|**range_end**|**numerisch (38)**|Der Identitätswert am Ende des aktuellen Bereichs.|  
|**next_range_begin**|**numerisch (38)**|Der Identitätswert am Anfang des neuen Bereichs, der zugewiesen werden soll.|  
|**next_range_end**|**numerisch (38)**|Der Identitätswert am Ende des neuen Bereichs, der zugewiesen werden soll.|  
|**is_pub_range**|**bit**|Der Wert **1** , wenn der Identitäts Bereich der Veröffentlichung zugewiesen wird.|  
|**max_used**|**numerisch (38)**|Der maximale Identitätswert, der zugewiesen werden kann.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
