---
title: Core. sp_update_data_source (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_data_source
- sp_update_data_source_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_data_source
- management data warehouse, data collector stored procedures
- core.sp_update_data_source stored procedure
- data collector [SQL Server], stored procedures
ms.assetid: 66b95f96-6df7-4657-9b3c-86a58c788ca5
author: stevestein
ms.author: sstein
ms.openlocfilehash: a840c749222cc7c01fa1b1ff5a27489e0e9d322a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67942466"
---
# <a name="coresp_update_data_source-transact-sql"></a>core.sp_update_data_source (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aktualisiert eine vorhandene Zeile oder fügt eine neue Zeile in der core.source_info_internal-Tabelle des Verwaltungs-Data Warehouse ein. Diese Prozedur wird von der Laufzeitkomponente des Datensammlers bei jedem Hochladen von Daten in das Verwaltungs-Data Warehouse durch ein Uploadpaket aufgerufen.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
core.sp_update_data_source [ @collection_set_uid = ] 'collection_set_uid'  
    ,[ @machine_name = ] 'machine_name'  
    , [ @named_instance = ] 'named_instance'  
    , [ @days_until_expiration = ] days_until_expiration  
    , [ @source_id = ] source_id OUTPUT  
```  
  
## <a name="arguments"></a>Argumente  
 [ @collection_set_uid = ] "*collection_set_uid*"  
 Die GUID für den Sammlungssatz. *collection_set_uid* ist vom Datentyp **uniqueidentifier**und hat keinen Standardwert. Um die GUID zu erhalten, fragen Sie die dbo.syscollector_collection_sets-Sicht in der MSDB-Datenbank ab.  
  
 [ @machine_name = ] "*machine_name*"  
 Der Name des Servers, auf dem sich der Sammlungssatz befindet. *machine_name* ist vom **Datentyp vom Datentyp sysname** und hat keinen Standardwert.  
  
 [ @named_instance = ] "*named_instance*"  
 Der Name der Instanz für den Sammlungssatz. *named_instance* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
> [!NOTE]  
>  *named_instance* muss der voll qualifizierte Instanzname sein, der aus dem Computernamen und dem Instanznamen im Format *Computername*\\*instanceName*besteht.  
  
 [ @days_until_expiration = ] *days_until_expiration*  
 Die Anzahl der Tage, die in der Beibehaltungsdauer für Momentaufnahmedaten verbleiben. *days_until_expiration* ist vom Datentyp **smallint**.  
  
 [ @source_id = ] *source_id*  
 Der eindeutige Bezeichner für die Quelle des Updates. *source_id* ist vom Datentyp **int** und wird als Output zurückgegeben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 Jedes Mal, wenn ein Uploadpaket mit dem Hochladen von Daten in das Verwaltungs-Data Warehouse beginnt, ruft die Laufzeitkomponente des Datensammlers core.sp_update_data_source auf. Die core.source_info_internal-Tabelle wird aktualisiert, wenn nach dem letzten Hochladen eine der folgenden Änderungen durchgeführt wurde:  
  
-   Ein neuer Sammlungssatz wurde hinzugefügt.  
  
-   Der Wert für days_until_expiration wurde geändert.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der Daten Bank Rolle " **mdw_writer** (mit EXECUTE-Berechtigung)".  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Datenquelle aktualisiert (in diesem Fall der Sammlungssatz für die Datenträgerverwendung), die Anzahl der Tage bis zum Ablaufdatum festgelegt und der Bezeichner für die Quelle zurückgegeben. In diesem Beispiel wird die Standardinstanz verwendet.  
  
```  
USE <management_data_warehouse>;  
GO  
DECLARE @source_id int;  
EXEC core.sp_update_data_source   
@collection_set_uid = '7B191952-8ECF-4E12-AEB2-EF646EF79FEF',   
@machine_name = '<computername>',  
@named_instance = 'MSSQLSERVER',  
@days_until_expiration = 10,  
@source_id = @source_id OUTPUT;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Gespeicherte Prozeduren für den Datensammler &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Verwaltungs-Data Warehouse](../../relational-databases/data-collection/management-data-warehouse.md)  
  
  
