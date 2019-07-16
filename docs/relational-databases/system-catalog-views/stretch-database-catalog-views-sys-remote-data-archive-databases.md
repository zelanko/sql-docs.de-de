---
title: remote_data_archive_databases (Transact-SQL) | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68018198"
---
# <a name="stretch-database-catalog-views---sysremotedataarchivedatabases"></a>Stretch Database-Katalogsichten - remote_data_archive_databases
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jede Remotedatenbank, die Daten aus einer lokalen Datenbank mit aktivierter Funktion Stretch-speichert.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**remote_database_id**|**int**|Der automatisch generierten lokale Bezeichner der Remotedatenbank.|  
|**remote_database_name**|**sysname**|Der Name der Remotedatenbank.|  
|**data_source_id**|**int**|Die Datenquelle, die zur Verbindung mit dem Remoteserver|  
  
## <a name="see-also"></a>Siehe auch  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
