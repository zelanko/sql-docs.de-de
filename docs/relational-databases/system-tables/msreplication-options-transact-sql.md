---
title: MSreplication_options (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSreplication_options
- MSreplication_options_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplication_options system table
ms.assetid: 23cf10d7-8bc1-4368-b5eb-e5576421e776
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4bb4c4568c220df16f9f5592f8e38d143340f96b
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52757942"
---
# <a name="msreplicationoptions-transact-sql"></a>MSreplication_options (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSreplication_options** Tabelle speichert Metadaten, die intern von der Replikation verwendet wird. Diese Tabelle befindet sich in der **master** Datenbank.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**optname**|**sysname**|Nur interne Verwendung.|  
|**value**|**bit**|Nur interne Verwendung.|  
|**Hauptversion**|**int**|Nur interne Verwendung.|  
|**minor_version**|**int**|Nur interne Verwendung.|  
|**Revision**|**int**|Nur interne Verwendung.|  
|**install_failures**|**int**|Nur interne Verwendung.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
