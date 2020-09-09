---
description: IHpublishercolumnconstraints (Transact-SQL)
title: Ihpublishercolumneinschränkungen (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHpublishercolumnconstraints
- IHpublishercolumnconstraints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublishercolumnconstraints system table
ms.assetid: d7a41da6-e067-430a-8da2-3f6745b8a4f3
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 5fd48949931767dde0873ac95c7184544850e842
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89547186"
---
# <a name="ihpublishercolumnconstraints-transact-sql"></a>IHpublishercolumnconstraints (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Die **ihpublishercolumneinschränkungs** -Systemtabelle ordnet Spalten einer nicht SQL Server Veröffentlichung in der [IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) -Systemtabelle Einschränkungen in der [IHpublishercolumns](../../relational-databases/system-tables/ihpublisherconstraints-transact-sql.md) -Systemtabelle zu. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
## <a name="definition"></a>Definition  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**publishercolumn_id**|**int**|Identifiziert die Spalte aus [IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) mit einer zugeordneten Einschränkung.|  
|**publisherconstraint_id**|**int**|Identifiziert eine Einschränkung von [ihpublisherschränkt](../../relational-databases/system-tables/ihpublisherconstraints-transact-sql.md) , die der Spalte zugeordnet ist.|  
|**indid**|**int**|Gibt die Position einer Spalte innerhalb der veröffentlichten Tabelle an.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Heterogene Datenbankreplikation](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
