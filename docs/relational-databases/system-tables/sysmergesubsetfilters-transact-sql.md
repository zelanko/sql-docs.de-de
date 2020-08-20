---
description: sysmergesubsetfilters (Transact-SQL)
title: sysmergesubsetfilters (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysmergesubsetfilters
- sysmergesubsetfilters_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmergesubsetfilters system table
ms.assetid: f91d1c6c-3132-47f6-926c-88f56848cafe
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7257cd9ab4de29343015fa1050c336d3e8a69e65
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88485431"
---
# <a name="sysmergesubsetfilters-transact-sql"></a>sysmergesubsetfilters (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Enthält Informationen zu Joinfiltern für partitionierte Artikel. Diese Tabelle wird in der Veröffentlichungs- und in der Abonnementdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**Filter Name**|**sysname**|Der Name des Filters, der zum Erstellen des Artikels verwendet wurde.|  
|**join_filterid**|**int**|Die ID des Objekts, das den Joinfilter darstellt.|  
|**pubid**|**uniqueidentifier**|Die ID der Veröffentlichung.|  
|**artid**|**uniqueidentifier**|Die ID des Artikels.|  
|**art_nickname**|**int**|Der Spitzname des Artikels.|  
|**join_articlename**|**sysname**|Der Name der zu verknüpfenden Tabelle, um zu bestimmen, ob die Zeile dazugehört.|  
|**join_nickname**|**int**|Der Spitzname der zu verknüpfenden Tabelle, um zu bestimmen, ob die Zeile dazugehört.|  
|**join_unique_key**|**int**|Gibt einen Join mit einem eindeutigen Schlüssel **join_tablename**an:<br /><br /> 0 = Nicht eindeutiger Schlüssel.<br /><br /> 1 = Eindeutiger Schlüssel.|  
|**expand_proc**|**sysname**|Der Name der gespeicherten Prozedur, mit der der Merge-Agent die Zeilen identifiziert, die von einem Abonnenten gesendet oder entfernt werden müssen.|  
|**join_filterclause**|**nvarchar (1000)**|Die für den Join verwendete Filterklausel.|  
|**filter_type**|**tinyint**|Gibt den Filtertyp an. Folgende Werte sind möglich:<br /><br /> 1 = Joinfilter.<br /><br /> 2 = Logischer Datensatzlink.<br /><br /> 3 = Sowohl Joinfilter als auch logischer Datensatzlink.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
