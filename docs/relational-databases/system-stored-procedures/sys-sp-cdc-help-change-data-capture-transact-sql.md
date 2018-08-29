---
title: Sys. sp_cdc_help_change_data_capture (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f29ac764c9d948d435765abd3d11d260cbd0d59c
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43027246"
---
# <a name="sysspcdchelpchangedatacapture-transact-sql"></a>sys.sp_cdc_help_change_data_capture (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt die Change Data Capture-Konfiguration für jede Tabelle zurück, die in der aktuellen Datenbank für Change Data Capture aktiviert ist. Für jede Quelltabelle können bis zu zwei Zeilen zurückgegeben werden: eine Zeile für jede Aufzeichnungsinstanz. Change Data Capture ist nicht in jeder Edition von [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Eine Liste der Funktionen, die von den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Editionen unterstützt werden, finden Sie unter [Von den SQL Server 2016-Editionen unterstützte Funktionen](../../sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.sp_cdc_help_change_data_capture   
  [ [ @source_schema = ] 'source_schema' ]  
  [, [ @source_name = ] 'source_name' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ @source_schema =] '*Source_schema*"  
 Der Name des Schemas, zu dem die Quelltabelle gehört. *Source_schema* ist **Sysname**, hat den Standardwert NULL. Wenn *Source_schema* angegeben wird, *Source_name* muss auch angegeben werden.  
  
 Wenn ungleich NULL, *Source_schema* muss in der aktuellen Datenbank vorhanden sein.  
  
 Wenn *Source_schema* ungleich NULL, *Source_name* muss auch nicht NULL sein.  
  
 [ @source_name =] '*Source_name*"  
 Der Name der Quelltabelle. *Source_name* ist **Sysname**, hat den Standardwert NULL. Wenn *Source_name* angegeben wird, *Source_schema* muss auch angegeben werden.  
  
 Wenn ungleich NULL, *Source_name* muss in der aktuellen Datenbank vorhanden sein.  
  
 Wenn *Source_name* ungleich NULL, *Source_schema* muss auch nicht NULL sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
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
 Wenn beide *Source_schema* und *Source_name* Standardwert NULL annehmen oder explizit auf NULL, festgelegt werden diese gespeicherte Prozedur gibt Informationen für alle Datenbanken aufzeichnungsinstanzen, die der Aufrufer hat auswählen. der Zugriff auf. Wenn *Source_schema* und *Source_name* nicht NULL sind, nur Informationen zu den bestimmten benannten, aktivierten Tabelle zurückgegeben.  
  
## <a name="permissions"></a>Berechtigungen  
 Wenn *Source_schema* und *Source_name* NULL sind, die Autorisierung des Aufrufers bestimmt, welche aktivierten Tabellen im Resultset enthalten sind. Aufrufer müssen über die SELECT-Berechtigung für alle aufgezeichneten Spalten der Aufzeichnungsinstanz verfügen und zudem Mitglied aller definierten Gatingrollen für die einzubeziehenden Tabelleninformationen sein. Mitglieder der db_owner-Datenbankrolle können Informationen zu allen definierten Aufzeichnungsinstanzen anzeigen. Beim Anfordern von Informationen für eine bestimmte aktivierte Tabelle werden auf die benannte Tabelle die gleichen SELECT- und Mitgliedschaftskriterien angewendet.  
  
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
  
  
