---
description: MSreplication_options (Transact-SQL)
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 096eb8379363e3a193ecea12593638e033c3b1ec
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89538235"
---
# <a name="msreplication_options-transact-sql"></a>MSreplication_options (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  In der **MSreplication_options** Tabelle werden Metadaten gespeichert, die intern von der Replikation verwendet werden. Diese Tabelle wird in der **Master** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**optname**|**sysname**|Nur interne Verwendung.|  
|**value**|**bit**|Nur interne Verwendung.|  
|**major_version**|**int**|Nur interne Verwendung.|  
|**minor_version**|**int**|Nur interne Verwendung.|  
|**Novel**|**int**|Nur interne Verwendung.|  
|**install_failures**|**int**|Nur interne Verwendung.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
