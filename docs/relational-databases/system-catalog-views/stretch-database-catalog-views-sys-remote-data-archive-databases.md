---
title: remote_data_archive_databases (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0dbf0566239b6434bb25c707ff2bb3142dbc2b15
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47607218"
---
# <a name="stretch-database-catalog-views---sysremotedataarchivedatabases"></a>Stretch Database-Katalogsichten - remote_data_archive_databases
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jede Remotedatenbank, die Daten aus einer lokalen Datenbank mit aktivierter Funktion Stretch-speichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**remote_database_id**|**int**|Der automatisch generierten lokale Bezeichner der Remotedatenbank.|  
|**remote_database_name**|**sysname**|Der Name der Remotedatenbank.|  
|**data_source_id**|**int**|Die Datenquelle, die zur Verbindung mit dem Remoteserver|  
  
## <a name="see-also"></a>Siehe auch  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
