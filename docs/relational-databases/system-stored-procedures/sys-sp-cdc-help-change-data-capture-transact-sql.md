---
title: sys. sp_cdc_help_change_data_capture (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cdc_help_change_data_capture_TSQL
- sys.sp_cdc_help_change_data_capture_TSQL
- sp_cdc_help_change_data_capture
- sys.sp_cdc_help_change_data_capture
dev_langs:
- TSQL
helpviewer_keywords:
- change data capture [SQL Server], querying metadata
- sys.sp_cdc_help_change_data_capture
- sp_cdc_help_change_data_capture
ms.assetid: 91fd41f5-1b4d-44fe-a3b5-b73eff65a534
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 62d1fbfffeb23e823e89ecc1a22f44c54f8245a1
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85768904"
---
# <a name="syssp_cdc_help_change_data_capture-transact-sql"></a>sys.sp_cdc_help_change_data_capture (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Gibt die Change Data Capture-Konfiguration für jede Tabelle zurück, die in der aktuellen Datenbank für Change Data Capture aktiviert ist. Für jede Quelltabelle können bis zu zwei Zeilen zurückgegeben werden: eine Zeile für jede Aufzeichnungsinstanz. Change Data Capture ist nicht in jeder Edition von [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Eine Liste der Funktionen, die von den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Editionen unterstützt werden, finden Sie unter [Von den SQL Server 2016-Editionen unterstützte Funktionen](../../sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.sp_cdc_help_change_data_capture   
  [ [ @source_schema = ] 'source_schema' ]  
  [, [ @source_name = ] 'source_name' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @source_schema =] '*source_schema*'  
 Der Name des Schemas, zu dem die Quelltabelle gehört. *source_schema* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Wenn *source_schema* angegeben wird, müssen *source_name* ebenfalls angegeben werden.  
  
 Wenn der Wert nicht NULL ist, müssen *source_schema* in der aktuellen Datenbank vorhanden sein.  
  
 Wenn *source_schema* ungleich NULL ist, müssen *source_name* ebenfalls nicht NULL sein.  
  
 [ @source_name =] '*source_name*'  
 Der Name der Quelltabelle. *source_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Wenn *source_name* angegeben wird, müssen *source_schema* ebenfalls angegeben werden.  
  
 Wenn der Wert nicht NULL ist, müssen *source_name* in der aktuellen Datenbank vorhanden sein.  
  
 Wenn *source_name* ungleich NULL ist, müssen *source_schema* ebenfalls nicht NULL sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|source_schema|**sysname**|Name des Quelltabellenschemas.|  
|source_table|**sysname**|Name der Quelltabelle.|  
|capture_instance|**sysname**|Name der Aufzeichnungsinstanz.|  
|object_id|**int**|ID der Änderungstabelle, die der Quelltabelle zugeordnet ist.|  
|source_object_id|**int**|ID der Quelltabelle.|  
|start_lsn|**binary(10)**|Protokollfolgenummer (Log Sequence Number, LSN), die den unteren Endpunkt zum Abfragen der Änderungstabelle darstellt.<br /><br /> NULL = Der untere Endpunkt wurde nicht erstellt.|  
|end_lsn|**binary(10)**|LSN, die den oberen Endpunkt zum Abfragen der Änderungstabelle darstellt. In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] hat diese Spalte immer den Wert NULL.|  
|supports_net_changes|**bit**|Die Unterstützung für Nettoänderungen ist aktiviert.|  
|has_drop_pending|**bit**|Wird in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] nicht verwendet.|  
|role_name|**sysname**|Name der Datenbankrolle, mit deren Hilfe der Zugriff auf die Änderungsdaten gesteuert wird.<br /><br /> NULL = Eine Rolle wird nicht verwendet.|  
|index_name|**sysname**|Name des Indexes, mit dessen Hilfe Zeilen in der Quelltabelle eindeutig identifiziert werden.|  
|filegroup_name|**sysname**|Name der Dateigruppe, in der sich die Änderungstabelle befindet.<br /><br /> NULL = Die Änderungstabelle befindet sich in der Standarddateigruppe der Datenbank.|  
|create_date|**datetime**|Datum, an dem die Aufzeichnungsinstanz aktiviert wurde.|  
|index_column_list|**nvarchar(max)**|Liste der Indexspalten, mit deren Hilfe Zeilen in der Quelltabelle eindeutig identifiziert werden.|  
|captured_column_list|**nvarchar(max)**|Liste der aufgezeichneten Quellspalten.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn sowohl *source_schema* als auch *source_name* standardmäßig auf NULL festgelegt ist, oder explizit auf NULL festgelegt ist, gibt diese gespeicherte Prozedur Informationen für alle Daten Bank Aufzeichnungs Instanzen zurück, für die der Aufrufer über SELECT-Zugriff verfügt. Wenn *source_schema* und *source_name* ungleich NULL sind, werden nur Informationen für die jeweilige benannte aktivierte Tabelle zurückgegeben.  
  
## <a name="permissions"></a>Berechtigungen  
 Wenn *source_schema* und *source_name* NULL sind, bestimmt die Autorisierung des Aufrufers, welche aktivierten Tabellen in das Resultset eingeschlossen werden. Aufrufer müssen über die SELECT-Berechtigung für alle aufgezeichneten Spalten der Aufzeichnungsinstanz verfügen und zudem Mitglied aller definierten Gatingrollen für die einzubeziehenden Tabelleninformationen sein. Mitglieder der db_owner-Datenbankrolle können Informationen zu allen definierten Aufzeichnungsinstanzen anzeigen. Beim Anfordern von Informationen für eine bestimmte aktivierte Tabelle werden auf die benannte Tabelle die gleichen SELECT- und Mitgliedschaftskriterien angewendet.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-returning-change-data-capture-configuration-information-for-a-specified-table"></a>A. Zurückgeben von Change Data Capture-Konfigurationsinformationen für eine angegebene Tabelle  
 Im folgenden Beispiel wird die Change Data Capture-Konfiguration für die `HumanResources.Employee`-Tabelle zurückgegeben.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_help_change_data_capture   
    @source_schema = N'HumanResources',   
    @source_name = N'Employee';  
GO  
```  
  
### <a name="b-returning-change-data-capture-configuration-information-for-all-tables"></a>B. Zurückgeben von Change Data Capture-Konfigurationsinformationen für alle Tabellen  
 Im folgenden Beispiel werden Konfigurationsinformationen für alle aktivierten Tabellen in der Datenbank zurückgegeben, die Änderungsdaten enthalten, auf die der Aufrufer zugreifen darf.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_help_change_data_capture;  
GO  
```  
  
  
