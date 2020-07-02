---
title: MSdatatype_mappings (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdatatype_mappings
- MSdatatype_mappings_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdatatype_mappings view
ms.assetid: 13cdabb3-6e07-4e8d-ae80-4235022ccc7f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6e2abcb656e2f1235827bd0b348e0f288ae4c6ca
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85639369"
---
# <a name="msdatatype_mappings-transact-sql"></a>MSdatatype_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Die **MSdatatype_mappings** Ansicht ordnet SQL Server Datentypen Datentypen zu, die von nicht-SQL Server Datenbank-Managementsystemen (DBMS) verwendet werden. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**dbms_name**|**nvarchar(128)**|Der Name des DBMS. Unten sind die möglichen Werte und ihre Beschreibungen aufgeführt.<br /><br /> **MSSQLSERVER**: das Ziel ist eine SQL Server Datenbank.<br />**Oracle**: das Ziel ist eine Oracle-Datenbank.<br />**DB2**: das Ziel ist eine IBM DB2-Datenbank.<br />**Sybase**: das Ziel ist eine Sybase-Datenbank.|  
|**sql_type**|**nvarchar(128)**|Der SQL Server-Datentyp.|  
|**dest_type**|**nvarchar(128)**|Der Name des Nicht-SQL Server-Datentyps.|  
|**dest_prec**|**bigint**|Die Präzision des Nicht-SQL Server-Datentyps.|  
|**dest_create_params**|**int**|Nur interne Verwendung.|  
|**dest_nullable**|**bit**|Gibt an, ob der Nicht-SQL Server-Datentyp den Wert NULL unterstützt.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Heterogene Replikation](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Angeben von Datentyp Zuordnungen für einen Oracle-Verleger](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
