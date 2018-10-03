---
title: Sys. dm_pdw_network_credentials (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d4fee3ad-6285-4ea5-8513-5e6eb617abb0
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 0661b5bd203cd1bca26ed6fb5bf380d6882dc5e5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47609918"
---
# <a name="sysdmpdwnetworkcredentials-transact-sql"></a>Sys. dm_pdw_network_credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Gibt eine Liste mit allen Netzwerk-Anmeldeinformationen gespeichert werden, in der [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] Appliance für alle Zielserver. Ergebnisse werden für den Steuerelementknoten aus, und jede Compute-Knoten aufgeführt.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|pdw_node_id|**int**|Eindeutige numerische Id, die dem Knoten zugeordnet.|  
|target_server_name|**nvarchar(32)**|IP-Adresse des Zielservers, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] greift mithilfe der Benutzername und Kennwort-Anmeldeinformationen.|  
|username|**nvarchar(32)**|Benutzername für die das Kennwort gespeichert wird.|  
|last_modified|**datetime**|Datum und Uhrzeit des letzten Vorgangs, der die Anmeldeinformationen geändert.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die VIEW SERVER STATE.  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
 Der Schlüssel für diese dynamische verwaltungssicht ist *Pdw_node_id* plus *Target_server_name*.  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Data Warehouse-dynamische Verwaltungssichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
