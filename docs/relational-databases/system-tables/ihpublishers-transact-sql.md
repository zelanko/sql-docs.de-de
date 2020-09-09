---
description: IHpublishers (Transact-SQL)
title: IHpublishers (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- IHpublishers
- IHpublishers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublishers system table
ms.assetid: 77007246-f10b-4b87-8edf-7afc3c2096af
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 03d8633b8e859df67d60e8b535cb18c01d031a1e
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89551032"
---
# <a name="ihpublishers-transact-sql"></a>IHpublishers (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Die **IHpublishers** -Systemtabelle enthält eine Zeile für jeden nicht-SQL Server-Verleger, der den aktuellen Verteiler verwendet. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
## <a name="definition"></a>Definition  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|Identifiziert einen Nicht-SQL Server-Verleger.|  
|**Verkäufern**|**sysname**|Der Name des Herstellers für die Nicht-SQL Server-Datenbank.|  
|**publisher_guid**|**uniqueidentifier**|Ein GUID, der einen Nicht-SQL Server-Verleger identifiziert.|  
|**flush_request_time**|**datetime**|Gibt das Datum und die Uhrzeit der letzten Änderung an Artikelmetadaten an, für die der Protokolllese-Agent den Metadatencache aktualisieren musste.|  
|**version**|**sysname**|Eine Textzeichenfolge für die Version eines Nicht-SQL Server-Verlegers.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Heterogene Datenbankreplikation](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikations Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_adddistpublisher &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_changedistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [sp_helpdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md)  
  
  
