---
title: table_types (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- table_types_TSQL
- sys.table_types
- sys.table_types_TSQL
- table_types
dev_langs:
- TSQL
helpviewer_keywords:
- table types [SQL Server]
- table-valued parameters, sys.table_types
- sys.table_types
- UDTT
ms.assetid: c05fd873-aff2-4a89-9936-a54c2ea09996
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ac4898bb75623842f129e19e2e506a551f7f1f37
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47642528"
---
# <a name="systabletypes-transact-sql"></a>sys.table_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Zeigt Eigenschaften von benutzerdefinierten Tabellentypen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] an. Ein Tabellentyp ist ein Typ, von dem Tabellenvariablen oder Tabellenwertparameter deklariert werden können. Jeder Tabellentyp besitzt eine **Type_table_object_id** , einen Fremdschlüssel in der [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) -Katalogsicht angezeigt. Sie können diese ID-Spalte verschiedener Katalogsichten verwendet werden, auf eine Weise Abfragen, die ähnlich wie ein **Object_id** -Spalte einer regulären Tabelle, um die Struktur des Tabellentyps, wie z. B. die Spalten und Einschränkungen zu ermitteln.    
 
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|*\<geerbte Spalten >*||Eine Liste der Spalten, die in dieser Ansicht erbt, finden Sie unter [sys.types &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md).|  
|**type_table_object_id**|**int**|Objekt-ID. Diese Nummer ist innerhalb einer Datenbank eindeutig.|  
|**is_memory_optimized**|**bit**|**Gilt für**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Folgende Werte sind möglich:<br /><br /> 0 = ist nicht speicheroptimiert<br /><br /> 1 = ist speicheroptimiert<br /><br /> Der Wert 0 ist der Standardwert.<br /><br /> Tabellentypen werden immer mit DURABILITY = SCHEMA_ONLY erstellt. Nur das Schema wird auf dem Datenträger beibehalten.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Katalogsichten für Objekte &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Verwenden von Tabellenwertparametern &#40;Datenbank-Engine&#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)   
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
