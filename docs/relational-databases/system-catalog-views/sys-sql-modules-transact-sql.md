---
title: Sys. sql_modules (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/06/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sql_modules_TSQL
- sql_modules
- sql_modules_TSQL
- sys.sql_modules
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sql_modules catalog view
ms.assetid: 23d3ccd2-f356-4d89-a2cd-bee381243f99
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 59f65e8743dab760b54cec9b088f5feca8d49e0b
ms.sourcegitcommit: cb73d60db8df15bf929ca17c1576cf1c4dca1780
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2018
ms.locfileid: "51221536"
---
# <a name="syssqlmodules-transact-sql"></a>sys.sql_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Gibt eine Zeile für jedes Objekt, das ist eine SQL-Sprache definiertes Modul in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], einschließlich systemintern kompilierte benutzerdefinierte Skalarfunktion. Objekten des Typs P, RF, V, TR, FN, IF, TF und R ist ein SQL-Modul zugeordnet. Eigenständige Standards, Objekte des Typs D, haben ebenfalls eine SQL-Moduldefinition in dieser Sicht. Eine Beschreibung dieser Typen finden Sie in der **Typ** -Spalte in der [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) -Katalogsicht angezeigt.  
  
 Weitere Informationen dazu finden Sie unter [Benutzerdefinierte Skalarfunktionen für In-Memory-OLTP](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md).  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Die Objekt-ID des enthaltenen Objekts. Ist innerhalb einer Datenbank eindeutig.|  
|**definition**|**nvarchar(max)**|Der SQL-Text, der dieses Modul definiert. Dieser Wert kann auch mit abgerufen werden die [OBJECT_DEFINITION](../../t-sql/functions/object-definition-transact-sql.md) integrierte Funktion.<br /><br /> NULL = Verschlüsselt.|  
|**uses_ansi_nulls**|**bit**|Das Modul wurde mit SET ANSI_NULLS ON erstellt.<br /><br /> Ist immer = 0 für Regeln und Standardwerte.|  
|**uses_quoted_identifier**|**bit**|Das Modul wurde mit SET QUOTED_IDENTIFIER ON erstellt.|  
|**is_schema_bound**|**bit**|Das Modul wurde mit der Option SCHEMABINDING erstellt.<br /><br /> Enthält immer den Wert 1 für systemintern kompilierte gespeicherte Prozeduren.|  
|**uses_database_collation**|**bit**|1 = Die richtige Auswertung der schemagebundenen Moduldefinition ist abhängig von der Standardsortierung der Datenbank; andernfalls ist der Wert 0. Diese Abhängigkeit wird verhindert, dass die standardsortierung der Datenbank geändert wird.|  
|**is_recompiled**|**bit**|Die Prozedur wurde mit der Option WITH RECOMPILE erstellt.|  
|**null_on_null_input**|**bit**|Das Modul wurde so deklariert, dass auf eine NULL-Eingabe eine NULL-Ausgabe folgt.|  
|**execute_as_principal_id**|**Int**|Die ID des Datenbankprinzipals EXECUTE AS.<br /><br /> NULL als Standardwert oder bei Verwendung von EXECUTE AS CALLER.<br /><br /> ID des angegebenen Prinzipals bei EXECUTE AS SELF oder EXECUTE AS \<principal >.<br /><br /> -2 = EXECUTE AS OWNER.|  
|**uses_native_compilation**|**bit**|**Gilt für**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] bis [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].<br /><br /> 0 = nicht systemintern kompiliert<br /><br /> 1 = systemintern kompiliert<br /><br /> Der Standardwert ist 0.|  
|**is_inlineable**|**bit**|**Gilt für**: [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] oder höher.<br/><br />Gibt an, ob das Modul inlineable oder nicht. Inlinefähigkeit basiert darauf, dass die angegebenen Bedingungen [hier](../user-defined-functions/scalar-udf-inlining.md#inlineable-scalar-udfs-requirements).<br /><br /> 0 = nicht inlineable<br /><br /> 1 = inlineable ist. <br /><br /> Für skalare benutzerdefinierte Funktionen wird der Wert 1 sein, wenn die UDF inlineable 0, andernfalls ist. Er enthält immer den Wert 1 für Inline-Tabellenwertfunktionen und 0 für alle anderen Modultypen.<br />|  
|**inline_type**|**bit**|**Gilt für**: [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] oder höher.<br /><br />Gibt an, ob inlining ist derzeit für das Modul eingeschaltet. <br /><br />0 = inlining ist deaktiviert.<br /><br /> 1 = inlining ist aktiviert.<br /><br /> Für skalare benutzerdefinierte Funktionen, wird der Wert 1 sein, wenn inlining ist aktiviert (explizit oder implizit). Der Wert ist immer 1 für Inline-Tabellenwertfunktionen und 0 für andere Modultypen sein.<br />|  

  
## <a name="remarks"></a>Hinweise  
 Der SQL-Ausdruck für eine DEFAULT-Einschränkung, Objekt vom Typ D, befindet sich der [Sys. default_constraints](../../relational-databases/system-catalog-views/sys-default-constraints-transact-sql.md) -Katalogsicht angezeigt. Der SQL-Ausdruck für eine CHECK-Einschränkung, Objekt vom Typ C, befindet sich der [Sys. check_constraints](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md) -Katalogsicht angezeigt.  
  
 Diese Informationen finden Sie auch auf [dm_db_uncontained_entities &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-uncontained-entities-transact-sql.md).  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden der Name, der Typ und die Definition der einzelnen Module in der aktuellen Datenbank zurückgegeben.  
  
```  
SELECT sm.object_id, OBJECT_NAME(sm.object_id) AS object_name, o.type, o.type_desc, sm.definition  
FROM sys.sql_modules AS sm  
JOIN sys.objects AS o ON sm.object_id = o.object_id  
ORDER BY o.type;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Abfragen des Systemkatalogs von SQL Server – häufig gestellte Fragen](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
