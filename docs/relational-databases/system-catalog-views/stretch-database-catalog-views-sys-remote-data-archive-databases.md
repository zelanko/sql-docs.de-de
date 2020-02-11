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
ms.openlocfilehash: 339d960a136e9cf939032068c21ec737f4d37ceb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68018198"
---
# <a name="stretch-database-catalog-views---sysremote_data_archive_databases"></a>Stretch Database Katalog Sichten-sys. remote_data_archive_databases
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jede Remote Datenbank, in der Daten aus einer Stretch-aktivierten lokalen Datenbank gespeichert werden.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**remote_database_id**|**int**|Der automatisch generierte lokale Bezeichner der Remote Datenbank.|  
|**remote_database_name**|**sysname**|Der Name der Remote Datenbank.|  
|**data_source_id**|**int**|Die Datenquelle, mit der eine Verbindung mit dem Remote Server hergestellt wird.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
