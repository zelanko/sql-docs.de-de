---
title: sp_cdc_get_captured_columns (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cdc_get_captured_columns
- sys.sp_cdc_get_captured_columns
- sys.sp_cdc_get_captured_columns_TSQL
- sp_cdc_get_captured_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_cdc_get_captured_columns
- sp_cdc_get_captured_columns
- change data capture [SQL Server], querying metadata
ms.assetid: d9e680be-ab9b-4e0c-b63a-90658f241df8
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 2cffffa064bbfc5d5d1b106a06fb5429d6ca2c72
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47781748"
---
# <a name="sysspcdcgetcapturedcolumns-transact-sql"></a>sys.sp_cdc_get_captured_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Metadateninformationen von Change Data Capture für die aufgezeichneten Quellspalten zurück, die von der angegebenen Aufzeichnungsinstanz nachverfolgt wurden. Change Data Capture ist nicht in jeder Edition von [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Eine Liste der Funktionen, die von den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Editionen unterstützt werden, finden Sie unter [Von den SQL Server 2016-Editionen unterstützte Funktionen](../../sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sys.sp_cdc_get_captured_columns   
    [ @capture_instance = ] 'capture_instance'  
```  
  
## <a name="arguments"></a>Argumente  
 [ @capture_instance =] '*Capture_instance*"  
 Der Name der Aufzeichnungsinstanz, die der Quelltabelle zugeordnet ist. *Capture_instance* ist **Sysname** und darf nicht NULL sein.  
  
 Um über die aufzeichnungsinstanzen für die Tabelle zu melden, führen Sie die [Sys. sp_cdc_help_change_data_capture](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md) gespeicherte Prozedur.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|source_schema|**sysname**|Name des Quelltabellenschemas.|  
|source_table|**sysname**|Name der Quelltabelle.|  
|capture_instance|**sysname**|Name der Aufzeichnungsinstanz.|  
|column_name|**sysname**|Name der aufgezeichneten Quellspalte.|  
|column_id|**int**|ID der Spalte in der Quelltabelle.|  
|column_ordinal|**int**|Position der Spalte innerhalb der Quelltabelle.|  
|data_type|**sysname**|Datentyp der Spalte.|  
|character_maximum_length|**int**|Maximale Zeichenlänge der zeichenbasierten Spalte; andernfalls NULL.|  
|numeric_precision|**tinyint**|Genauigkeit der Spalte, wenn sie auf numerischen Werten basiert; andernfalls NULL.|  
|numeric_precision_radix|**smallint**|Basis der Genauigkeit der Spalte, wenn sie auf numerischen Werten basiert; andernfalls NULL.|  
|numeric_scale|**int**|Dezimalstellen der Spalte, wenn sie auf numerischen Werten basiert; andernfalls NULL.|  
|datetime_precision|**smallint**|Genauigkeit der Spalte, wenn sie auf datetime-Werten basiert; andernfalls NULL.|  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie sp_cdc_get_captured_columns, um Spalteninformationen zu den aufgezeichneten Spalten, die durch Abfragen der Capture-Abfragefunktionen Instanz zurückgegeben erhalten [CDC. fn_cdc_get_all_changes_ < Capture_instance >](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md) oder [CDC. fn_cdc_get_net_changes_ < Capture_instance >](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md). Die Spaltennamen, IDs und Position bleiben während der Lebensdauer der Aufzeichnungsinstanz konstant. Nur die Spaltendatentypen ändern sich, wenn sich der Datentyp der zugrunde liegenden Quellspalte in der nachverfolgten Tabelle ändert. Spalten, die hinzugefügt oder aus einer Quelltabelle gelöscht haben keine Auswirkung auf die aufgezeichneten Spalten der vorhandenen aufzeichnungsinstanzen.  
  
 Verwendung [sp_cdc_get_ddl_history](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-ddl-history-transact-sql.md) zum Abrufen von Informationen zu Data Definition Language (DDL)-Anweisungen, die auf eine Quelltabelle angewendet. Alle DDL-Änderungen, die die Struktur einer nachverfolgten Quellspalte geändert haben, werden im Resultset zurückgegeben.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Datenbankrolle "db_owner". Für alle anderen Benutzer ist die SELECT-Berechtigung für alle aufgezeichneten Spalten in der Quelltabelle und, wenn eine Gatingrolle für die Aufzeichnungsinstanz definiert wurde, eine Mitgliedschaft in dieser Datenbankrolle erforderlich. Wenn der Aufrufer über keine Berechtigungen zum Anzeigen der Quelldaten verfügt, gibt die Funktion den Fehler 22981 zurück ("Das Objekt ist nicht vorhanden oder der Zugriff wurde verweigert").  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden Informationen zu den aufgezeichneten Spalten in der `HumanResources_Employee`-Aufzeichnungsinstanz zurückgegeben.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_get_captured_columns   
    @capture_instance = N'HumanResources_Employee';  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Sys. sp_cdc_help_change_data_capture &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)  
  
  
