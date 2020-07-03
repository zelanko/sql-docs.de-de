---
title: sys. sp_cdc_get_ddl_history (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cdc_get_ddl_history
- sp_cdc_get_ddl_history_TSQL
- sys.sp_cdc_get_ddl_history_TSQL
- sys.sp_cdc_get_ddl_history
dev_langs:
- TSQL
helpviewer_keywords:
- change data capture [SQL Server], querying metadata
- sp_cdc_get_ddl_history
- sys.sp_cdc_get_ddl_history
ms.assetid: 4dee5e2e-d7e5-4fea-8037-a4c05c969b3a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c72e4a325c8374c3d08ae00cc5af6898d5e206f2
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85891100"
---
# <a name="syssp_cdc_get_ddl_history-transact-sql"></a>sys.sp_cdc_get_ddl_history (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Gibt den Änderungsverlauf der Datendefinitionssprache (DDL, Data Definition Language), die der angegebenen Aufzeichnungsinstanz zugeordnet ist, zurück. Dabei werden alle Daten ab dem Zeitpunkt berücksichtigt, ab dem Change Data Capture für die entsprechende Aufzeichnungsinstanz aktiviert wurde. Change Data Capture ist nicht in jeder Edition von [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Eine Liste der Funktionen, die von den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Editionen unterstützt werden, finden Sie unter [Von den SQL Server 2016-Editionen unterstützte Funktionen](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.sp_cdc_get_ddl_history [ @capture_instance = ] 'capture_instance'  
```  
  
## <a name="arguments"></a>Argumente  
 [ @capture_instance =] '*capture_instance*'  
 Der Name der Aufzeichnungsinstanz, die der Quelltabelle zugeordnet ist. *capture_instance* ist vom **Datentyp vom Datentyp sysname** und darf nicht NULL sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|source_schema|**sysname**|Name des Quelltabellenschemas.|  
|source_table|**sysname**|Name der Quelltabelle.|  
|capture_instance|**sysname**|Name der Aufzeichnungsinstanz.|  
|required_column_update|**bit**|Weist darauf hin, dass die DDL-Änderung eine Spaltenänderung in der Änderungstabelle erfordert, um die Datentypänderung widerzuspiegeln, die in der Quellspalte durchgeführt wurde.|  
|ddl_command|**nvarchar(max)**|Die DDL-Anweisung, die auf die Quelltabelle angewendet wurde.|  
|ddl_lsn|**binary(10)**|Protokollfolgenummer (Log Sequence Number, LSN), die der DDL-Änderung zugeordnet wurde.|  
|ddl_time|**datetime**|Der mit der DDL-Änderung verknüpfte Zeitpunkt.|  
  
## <a name="remarks"></a>Hinweise  
 DDL-Änderungen an der Quell Tabelle, die die Spalten Struktur der Quell Tabelle ändern, z. b. das Hinzufügen oder Löschen einer Spalte oder das Ändern des Datentyps einer vorhandenen Spalte, werden in der Tabelle [CDC. ddl_history](../../relational-databases/system-tables/cdc-ddl-history-transact-sql.md) beibehalten. Diese Änderungen können mithilfe dieser gespeicherten Prozedur gemeldet werden. Die Einträge in cdc.ddl_history erfolgen zu dem Zeitpunkt, zu dem der Aufzeichnungsprozess die DDL-Transaktion im Protokoll vorfindet.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle db_owner, damit Zeilen für alle Aufzeichnungsinstanzen in der Datenbank zurückgegeben werden. Für alle anderen Benutzer ist die SELECT-Berechtigung für alle aufgezeichneten Spalten in der Quelltabelle und, wenn eine Gatingrolle für die Aufzeichnungsinstanz definiert wurde, eine Mitgliedschaft in dieser Datenbankrolle erforderlich.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine Spalte in der `HumanResources.Employee`-Quelltabelle hinzugefügt und anschließend die gespeicherte Prozedur `sys.sp_cdc_get_ddl_history` ausgeführt, um die DDL-Änderungen zu melden, die sich auf die Quelltabelle beziehen, die der Aufzeichnungsinstanz `HumanResources_Employee` zugeordnet ist.  
  
```  
USE AdventureWorks2012;  
GO  
ALTER TABLE HumanResources.Employee  
ADD Test_Column int NULL;  
GO  
-- Pause 10 seconds to allow the event to be logged.   
WAITFOR DELAY '00:00:10';  
GO   
EXECUTE sys.sp_cdc_get_ddl_history   
    @capture_instance = 'HumanResources_Employee';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys.sp_cdc_help_change_data_capture &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)  
  
  
