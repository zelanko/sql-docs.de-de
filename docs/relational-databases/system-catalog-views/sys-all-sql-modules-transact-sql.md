---
title: sys. all_sql_modules (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- all_sql_modules_TSQL
- sys.all_sql_modules
- all_sql_modules
- sys.all_sql_modules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.all_sql_modules catalog view
ms.assetid: 7477a3fe-afb3-44c8-bb2c-c6e1d9bdee6f
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3ba511b8ef64fe1a805df604dd916fb259fe7033
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86006318"
---
# <a name="sysall_sql_modules-transact-sql"></a>sys.all_sql_modules (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Gibt die Vereinigung von **sys. sql_modules** und **sys.system_sql_modules**zurück.  
  
 Die Sicht gibt eine Zeile für jede nativ kompilierte benutzerdefinierte Skalarfunktion zurück. Weitere Informationen dazu finden Sie unter [Benutzerdefinierte Skalarfunktionen für In-Memory-OLTP](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md).  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Die Objekt-ID des enthaltenen Objekts. Ist innerhalb einer Datenbank eindeutig.|  
|**Definition**|**nvarchar(max)**|Der SQL-Text, der dieses Modul definiert.<br /><br /> NULL = Verschlüsselt|  
|**uses_ansi_nulls**|**bit**|Das Modul wurde mit SET ANSI_NULLS ON erstellt.|  
|**uses_quoted_identifier**|**bit**|Das Modul wurde mit SET QUOTED_IDENTIFIER ON erstellt.|  
|**is_schema_bound**|**bit**|Das Modul wurde mit der SCHEMABINDING-Option erstellt.|  
|**uses_database_collation**|**bit**|1 = Die richtige Auswertung der schemagebundenen Moduldefinition ist abhängig von der Standardsortierung der Datenbank; andernfalls ist der Wert 0. Diese Abhängigkeit verhindert die Änderung der Standardsortierung der Datenbank.|  
|**is_recompiled**|**bit**|Die Prozedur wurde mit der WITH RECOMPILE-Option erstellt.|  
|**null_on_null_input**|**bit**|Das Modul wurde so deklariert, dass auf eine NULL-Eingabe eine NULL-Ausgabe folgt.|  
|**execute_as_principal_id**|**int**|Die ID des Datenbankprinzipals EXECUTE AS.<br /><br /> NULL als Standardwert oder bei Verwendung von EXECUTE AS CALLER.<br /><br /> ID des angegebenen Prinzipals, wenn EXECUTE als Self oder EXECUTE AS ausgeführt wird \<principal> .<br /><br /> -2 = EXECUTE AS OWNER.|  
|**uses_native_compilation**|bit|**Gilt für**:  [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] und höher.<br /><br /> 0 = nicht systemintern kompiliert<br /><br /> 1 = systemintern kompiliert<br /><br /> Der Standardwert ist 0.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Objektkatalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.system_sql_modules &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-system-sql-modules-transact-sql.md)   
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
