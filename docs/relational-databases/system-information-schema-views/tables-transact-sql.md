---
description: TABLES (Transact-SQL)
title: Tabellen (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/20/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- TABLES_TSQL
- TABLES
dev_langs:
- TSQL
helpviewer_keywords:
- TABLES view
- INFORMATION_SCHEMA.TABLES view
ms.assetid: 723a9e63-8f6e-4d6e-b570-468cfaf03201
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7e94fe84e47f40cfc85af1cc002fced981c01706
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97440581"
---
# <a name="tables-transact-sql"></a>TABLES (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Gibt eine Zeile für jede Tabelle oder Sicht in der aktuellen Datenbank zurück, für die der aktuelle Benutzer über Berechtigungen verfügt.  
  
 Zum Abrufen von Informationen aus diesen Sichten geben Sie den voll qualifizierten Namen **INFORMATION_SCHEMA an.** _view_name_.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**TABLE_CATALOG**|**nvarchar (** 128 **)**|Tabellenqualifizierer|  
|**TABLE_SCHEMA**|**nvarchar (** 128 **)**|Der Name des Schemas, das die Tabelle enthält.<br /><br /> Wichtig nur eine zuverlässige Möglichkeit, das Schema eines Objekts zu finden, besteht darin, die sys. Objects-Katalog Sicht abzufragen. <strong> \* \* \* \* </strong> INFORMATION_SCHEMA-Sichten sind möglicherweise unvollständig, da sie nicht für alle neuen Funktionen aktualisiert werden.|  
|**TABLE_NAME**|**sysname**|Der Name der Tabelle oder Sicht.|  
|**TABLE_TYPE**|**varchar (** 10 **)**|Tabellentyp. VIEW oder BASE TABLE|  
  
## <a name="see-also"></a>Weitere Informationen  
 [System Sichten &#40;Transact-SQL-&#41;](../../t-sql/language-reference.md)   
 [Informations Schema Sichten &#40;Transact-SQL-&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)  
  
