---
title: Core. sp_create_snapshot (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_create_snapshot
- sp_create_snapshot_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- management data warehouse, data collector stored procedures
- data collector [SQL Server], stored procedures
- core.sp_create_snapshot stored procedure
- sp_create_snapshot
ms.assetid: ff297bda-0ee2-4fda-91c8-7000377775e3
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6b3ffe874615e58d276428548cb1c2ad318f111d
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85898236"
---
# <a name="coresp_create_snapshot-transact-sql"></a>core.sp_create_snapshot (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Fügt eine Zeile in die core.snapshots-Sicht des Verwaltungs-Data Warehouse ein. Diese Prozedur wird jedes Mal aufgerufen, wenn Daten durch ein Uploadpaket in das Verwaltungs-Data Warehouse hochgeladen werden.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
core.sp_create_snapshot [ @collection_set_uid = ] 'collection_set_uid'  
    , [ @collector_type_uid = ] 'collector_type_uid'  
    ,[ @machine_name = ] 'machine_name'  
    , [ @named_instance = ] 'named_instance'  
    , [ @log_id = ] log_id  
    , [ @snapshot_id = ] snapshot_id OUTPUT  
```  
  
## <a name="arguments"></a>Argumente  
 [ @collection_set_uid =] '*collection_set_uid*'  
 Die GUID für den Sammlungssatz. *collection_set_uid* ist vom Datentyp **uniqueidentifier** und hat keinen Standardwert. Um die GUID zu erhalten, fragen Sie die dbo.syscollector_collection_sets-Sicht in der MSDB-Datenbank ab.  
  
 [ @collector_type_uid =] '*collector_type_uid*'  
 Die GUID für einen Sammlertyp. *collector_type_uid* ist vom Datentyp **uniqueidentifier** und hat keinen Standardwert. Um die GUID zu erhalten, fragen Sie die dbo.syscollector_collector_types-Sicht in der MSDB-Datenbank ab.  
  
 [ @machine_name =] '*machine_name*'  
 Der Name des Servers, auf dem sich der Sammlungssatz befindet. *machine_name* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
 [ @named_instance =] '*named_instance*'  
 Der Name der Instanz für den Sammlungssatz. *named_instance* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
 [ @log_id =] *log_id*  
 Der eindeutige Bezeichner, der dem Ereignisprotokoll des Sammlungssatzes auf dem Server zugeordnet ist, der die Daten gesammelt hat. *log_id* ist vom Datentyp **bigint** und hat keinen Standardwert. Wenn Sie den Wert für *log_id*abrufen möchten, Fragen Sie die dbo.syscollector_execution_log Sicht in der msdb-Datenbank ab.  
  
 [ @snapshot_id =] *snapshot_id*  
 Der eindeutige Bezeichner für eine Zeile, die in die Core. Momentaufnahmen-Sicht eingefügt wird. *snapshot_id* ist vom Datentyp **int** und wird als Output zurückgegeben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Jedes Mal, wenn ein Uploadpaket mit dem Hochladen von Daten in das Verwaltungs-Data Warehouse startet, ruft die Laufzeitkomponente des Datensammlers core.sp_create_snapshot  auf.  
  
 Diese Prozedur führt eine Überprüfung auf Folgendes durch:  
  
-   collection_set_uid stimmt mit einem vorhandenen Eintrag in der core.source_info_internal-Tabelle überein.  
  
-   collector_type_uid stimmt mit einem vorhandenen Eintrag in der core.supported_collector_types-Sicht überein.  
  
 Schlägt eine der oben aufgeführten Überprüfungen fehl, so schlägt die Prozedur fehl und gibt einen Fehler zurück.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der Daten Bank Rolle " **mdw_writer** (mit EXECUTE-Berechtigung)".  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine Momentaufnahme für den Sammlungssatz für die Datenträgerverwendung erstellt, dem Verwaltungs-Data Warehouse hinzugefügt und der Momentaufnahmebezeichner zurückgegeben. In diesem Beispiel wird die Standardinstanz verwendet.  
  
```  
USE <management_data_warehouse>;  
DECLARE @snapshot_id int;  
EXEC core.sp_create_snapshot   
    @collection_set_uid = '7B191952-8ECF-4E12-AEB2-EF646EF79FEF',   
    @collector_type_uid = '302E93D1-3424-4BE7-AA8E-84813ECF2419',  
    @machine_name = '<computername>',  
    @named_instance = 'MSSQLSERVER',  
    @log_id = 11, -- ID of the log for the collection set  
    @snapshot_id = @snapshot_id OUTPUT;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Gespeicherte Prozeduren für den Datensammler &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Verwaltungs-Data Warehouse](../../relational-databases/data-collection/management-data-warehouse.md)  
  
  
