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
ms.openlocfilehash: ee1a0cc83b55fc265ae2bb490fd9d5e11fd73f22
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68129621"
---
# <a name="msdatatypemappings-transact-sql"></a>MSdatatype_mappings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSdatatype_mappings** Sicht ordnet SQL Server-Datentypen in Datentypen, die von nicht - SQL Server-Datenbank-Managementsysteme (DBMS) verwendet. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**dbms_name**|**nvarchar(128)**|Ist der Name des DBMS. Im folgenden sind die möglichen Werte und deren Beschreibungen.<br /><br /> **MSSQLSERVER**: Das Ziel ist eine SQL Server-Datenbank.<br />**ORACLE**: Das Ziel ist eine Oracle-Datenbank.<br />**DB2**: Das Ziel ist eine IBM DB2-Datenbank.<br />**SYBASE**: Das Ziel ist eine Sybase-Datenbank.|  
|**sql_type**|**nvarchar(128)**|Ist der SQL Server-Datentyp.|  
|**dest_type**|**nvarchar(128)**|Ist der Name des nicht - SQL Server-Datentyps.|  
|**dest_prec**|**bigint**|Ist die Genauigkeit des Datentyps nicht - SQL-Server an.|  
|**dest_create_params**|**int**|Nur interne Verwendung.|  
|**dest_nullable**|**bit**|Ist, wenn der nicht - SQL Server-Datentyp um einen NULL-Wert unterstützt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Heterogene Datenbankreplikation](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Angeben von Datentypzuordnungen für einen Oracle-Verleger](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
