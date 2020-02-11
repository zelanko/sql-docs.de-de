---
title: sys. destination_data_spaces (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.destination_data_spaces
- destination_data_spaces_TSQL
- destination_data_spaces
- sys.destination_data_spaces_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.destination_data_spaces catalog view
ms.assetid: 92df932b-ad5c-43f8-81f4-b158823ab189
author: stevestein
ms.author: sstein
ms.openlocfilehash: 68a9e46232246c5f3a088765f77f44a9bc018269
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68079367"
---
# <a name="sysdestination_data_spaces-transact-sql"></a>sys.destination_data_spaces (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält eine Reihe für jedes Datenbereichsziel eines Partitionsschemas.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**partition_scheme_id**|**int**|ID des Partitionsschemas, mit dem die Partitionierung für den Datenspeicher ausgeführt wird.|  
|**destination_id**|**int**|ID (1-basierte Ordnungszahl) der Zielzuordnung, die innerhalb des Partitionsschemas eindeutig ist.|  
|**data_space_id**|**int**|ID des Datenspeichers, dem Daten für das Ziel dieses Schemas zugeordnet werden.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle. Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
