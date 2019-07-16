---
title: IHcolumns (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHcolumns_TSQL
- IHcolumns
dev_langs:
- TSQL
helpviewer_keywords:
- IHcolumns system table
ms.assetid: 5bb027e5-5279-487b-9c33-5f402987253c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9985b0587316641955219eb5179ffd6ed07916d3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67990390"
---
# <a name="ihcolumns-transact-sql"></a>IHcolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **IHcolumns** -Systemtabelle enthält eine Zeile für jede Spalte veröffentlichte. Diese Tabelle dient zum definieren, wie Spaltendatentypen von nicht - SQL Server-Verlegers dargestellt werden, wenn veröffentlicht, das entspricht im Wesentlichen Datentypen zwischen einer nicht - SQL Server-Datenbank-Managementsysteme (DBMS) und SQL Server. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
## <a name="definition"></a>Definition  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**column_id**|**int**|Identifiziert eine veröffentlichte Spalte.|  
|**publishercolumn_id**|**int**|Ordnet eine veröffentlichte Spalte Spaltenmetadaten gespeichert, der [IHpublishercolumns](../../relational-databases/system-tables/ihpublishercolumns-transact-sql.md) -Systemtabelle.|  
|**name**|**sysname**|Gibt den Spaltennamen an.|  
|**article_id**|**int**|Identifiziert den Artikel, zu dem die Spalte gehört.|  
|**column_ordinal**|**int**|Identifiziert die Spalte nach Reihenfolge.|  
|**mapped_type**|**tinyint**|Der Spaltendatentyp der Zielspalte auf dem Abonnenten.|  
|**mapped_length**|**bigint**|Die Länge der Spalte auf dem Abonnenten.|  
|**mapped_prec**|**int**|Die Genauigkeit der Spalte auf dem Abonnenten.|  
|**mapped_scale**|**int**|Die Dezimalstellen der Spalte auf dem Abonnenten.|  
|**mapped_nullable**|**bit**|Gibt an, ob die Spalte auf dem Abonnenten NULL-Werte zulässt, in denen **1** bedeutet, dass NULL-Werte akzeptiert werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Heterogene Datenbankreplikation](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_articlecolumn &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [Sysarticlecolumns &#40;Systemsicht&#41; &#40;Transact-SQL&#41;](../../relational-databases/system-views/sysarticlecolumns-system-view-transact-sql.md)   
 [sysarticlecolumns &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysarticlecolumns-transact-sql.md)  
  
  
