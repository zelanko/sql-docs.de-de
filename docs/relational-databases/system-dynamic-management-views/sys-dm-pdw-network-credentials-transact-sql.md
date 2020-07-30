---
title: sys. dm_pdw_network_credentials (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d4fee3ad-6285-4ea5-8513-5e6eb617abb0
author: CarlRabeler
ms.author: carlrab
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 8be0dde15dea7c02cda9fb59cdc71680ec494178
ms.sourcegitcommit: df1f0f2dfb9452f16471e740273cd1478ff3100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87395954"
---
# <a name="sysdm_pdw_network_credentials-transact-sql"></a>sys. dm_pdw_network_credentials (Transact-SQL)
[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

  Gibt eine Liste aller im [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] Gerät für alle Zielserver gespeicherten Netzwerk Anmelde Informationen zurück. Die Ergebnisse werden für den Knoten "Steuerelement" und alle Computeknoten aufgeführt.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|pdw_node_id|**int**|Eindeutige numerische ID, die dem Knoten zugeordnet ist.|  
|target_server_name|**nvarchar(32)**|Die IP-Adresse des Zielservers, [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] auf den mithilfe der Anmelde Informationen für Benutzername und Kennwort zugegriffen werden soll.|  
|username|**nvarchar(32)**|Der Benutzername, für den das Kennwort gespeichert wird.|  
|last_modified|**datetime**|Der DateTime-Wert des letzten Vorgangs, der die Anmelde Informationen geändert hat.|  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert den View Server State.  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
 Der Schlüssel für diese dynamische Verwaltungs Sicht ist *pdw_node_id* Plus *target_server_name*.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Data Warehouse und parallele Data Warehouse dynamischen Verwaltungs Sichten &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
