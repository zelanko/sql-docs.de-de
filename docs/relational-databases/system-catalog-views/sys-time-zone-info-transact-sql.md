---
description: sys.time_zone_info (Transact-SQL)
title: sys. time_zone_info (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/06/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.time_zone_info
- sys.time_zone_info_TSQL
- time_zone_info
- time_zone_info_TSQL
helpviewer_keywords:
- sys.time_zone_info system table
ms.assetid: 3f51a9a4-75f8-4a11-9552-8bf6118b68da
author: markingmyname
ms.author: maghan
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 51f3fd600b3c2c78caf437e758ece03aa325d29a
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89544978"
---
# <a name="systime_zone_info-transact-sql"></a>sys.time_zone_info (Transact-SQL)
[!INCLUDE [sqlserver2016-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa.md)]

  Gibt Informationen zu unterstützten Zeitzonen zurück. Alle Zeitzonen, die auf dem Computer installiert sind, werden in der folgenden Registrierungs Struktur gespeichert:  
`KEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones`.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Der Name der Zeitzone im Windows-Standardformat. Beispiel: die **Australien-Standardzeit** oder die **mitteleuropäische Standardzeit**.|  
|**current_utc_offset**|**nvarchar (12)**|Aktueller Offset bis UTC. Beispielsweise **+ 01:00** oder **-07:00**.|  
|**is_currently_dst**|**bit**|True, wenn derzeit die Sommerzeit beachtet wird.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [GETUTCDATE &#40;Transact-SQL-&#41;](../../t-sql/functions/getutcdate-transact-sql.md)   
 [AT TIME ZONE &#40;Transact-SQL&#41;](../../t-sql/queries/at-time-zone-transact-sql.md)   
 [Date and Time Data Types and Functions &#40;Transact-SQL&#41; (Datums- und Uhrzeitdatentypen und zugehörige Funktionen &#40;Transact-SQL&#41;)](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)   
 [Server weite Konfigurations Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/server-wide-configuration-catalog-views-transact-sql.md)  
