---
title: MSdbms_datatype (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdbms_datatype
- MSdbms_datatype_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdbms_datatype system table
ms.assetid: 606168cc-79a8-442f-ab43-936f8f884d72
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bf246256471931292d6dfcee8a83386bce256e08
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52810542"
---
# <a name="msdbmsdatatype-transact-sql"></a>MSdbms_datatype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSdbms_datatype** Tabelle enthält die vollständige Liste der systemeigenen Datentypen in jeder unterstützten Datenbank-Managementsystem (DBMS) als Verleger oder Abonnenten bei der heterogenen Datenbankreplikation verwendet. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**datatype_id**|**int**|Identifiziert jeden eindeutigen Datentyp.|  
|**dbms_id**|**int**|Identifiziert das DBMS, zu dem der Typ gehört.|  
|**type**|**sysname**|Der Name des Datentyps (systemeigen).|  
|**CreateParams**|**int**|Das Bitmap, das beschreibt, welche Kombination aus Länge, Genauigkeit und Dezimalstellen für jeden Datentyp gilt:<br /><br /> **0 x 1** = mit einfacher Genauigkeit.<br /><br /> **0 x 2** = skalieren.<br /><br /> **0 x 4** = Länge.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Tabelle enthält Einträge für SQL Server-Datentypen, da es sich bei eine Instanz von SQL Server in einer nicht - SQL Server-Datenbank abonnieren und Veröffentlichen auf einen nicht - SQL Server-Abonnenten kann.  
  
## <a name="see-also"></a>Siehe auch  
 [Heterogene Datenbankreplikation](../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)   
 [Angeben von Datentypzuordnungen für einen Oracle-Verleger](../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md)   
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
