---
title: sys. sysdepends (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sysdepends_TSQL
- sysdepends
- sysdepends_TSQL
- sys.sysdepends
dev_langs:
- TSQL
helpviewer_keywords:
- sysdepends system table
- sys.sysdepends compatibility view
ms.assetid: f9c182cb-386f-4e72-859f-9f1115b389f9
author: rothja
ms.author: jroth
ms.openlocfilehash: 5d928926294bb3e80f860a535a266b5c106e3f18
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68053497"
---
# <a name="syssysdepends-transact-sql"></a>sys.sysdepends (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält Informationen zu den Abhängigkeiten zwischen Objekten (Sichten, Prozeduren und Triggern) in der Datenbank und den Objekten (Tabellen, Sichten und Prozeduren), die in ihrer Definition enthalten sind.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Objekt-ID|  
|**depid**|**int**|ID des abhängigen Objekts|  
|**Zahl**|**smallint**|Prozedurnummer|  
|**depnumber**|**smallint**|Nummer der abhängigen Prozedur|  
|**status**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**deptype**|**tinyint**|Gibt den abhängigen Objekttyp an:<br /><br /> 0 = Objekt oder Spalte (nur nicht schemagebundene Verweise)<br /><br /> 1 = Objekt oder Spalte (schemagebundene Verweise)|  
|**depdbid**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**depsiteid**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**selall**|**bit**|1 = Objekt wird in einer SELECT *-Anweisung verwendet.<br /><br /> 0 = Nein.|  
|**resultobj**|**bit**|1 = Objekt wird aktualisiert.<br /><br /> 0 = Nein.|  
|**readobj**|**bit**|1 = Objekt wird gelesen.<br /><br /> 0 = Nein.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zuordnung von Systemtabellen zu System Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Kompatibilitäts Sichten &#40;Transact-SQL-&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)   
 [sp_depends &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-depends-transact-sql.md)   
 [sys. sql_dependencies &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/sys-sql-dependencies-transact-sql.md)  
  
  
