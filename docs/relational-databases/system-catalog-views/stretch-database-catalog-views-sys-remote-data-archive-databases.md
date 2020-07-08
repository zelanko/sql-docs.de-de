---
title: sys. remote_data_archive_databases (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.remote_data_archive_databases
- sys.remote_data_archive_databases_TSQL
- remote_data_archive_databases
- remote_data_archive_databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.remote_data_archive_databases catalog view
ms.assetid: 25bffb0c-9821-40b4-88cf-75f854891a09
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
ms.openlocfilehash: a4d7717a6e89b156cd66ea96a44383d28cbecfb3
ms.sourcegitcommit: 703968b86a111111a82ef66bb7467dbf68126051
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2020
ms.locfileid: "86053631"
---
# <a name="stretch-database-catalog-views---sysremote_data_archive_databases"></a>Stretch Database Katalog Sichten-sys. remote_data_archive_databases
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Enthält eine Zeile für jede Remote Datenbank, in der Daten aus einer Stretch-aktivierten lokalen Datenbank gespeichert werden.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**remote_database_id**|**int**|Der automatisch generierte lokale Bezeichner der Remote Datenbank.|  
|**remote_database_name**|**sysname**|Der Name der Remote Datenbank.|  
|**data_source_id**|**int**|Die Datenquelle, mit der eine Verbindung mit dem Remote Server hergestellt wird.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
