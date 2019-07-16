---
title: Sys.sysperfinfo (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysperfinfo_TSQL
- sys.sysperfinfo_TSQL
- sys.sysperfinfo
- sysperfinfo
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysperfinfo compatibility view
- sysperfinfo system table
ms.assetid: e22a81cd-27de-4690-9443-6aad6393bd3c
author: rothja
ms.author: jroth
ms.openlocfilehash: e6ce86e7be7d54e95c2336691b53ea12ff0d8575
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68076499"
---
# <a name="syssysperfinfo-transact-sql"></a>sys.sysperfinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält eine [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] -Darstellung der internen Leistungsindikatoren, die über den Windows-Systemmonitor angezeigt werden können.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**object_name**|**NCHAR(128)**|Name des Leistungsobjekts, z. B. **SQLServer:LockManager** oder **SQLServer:BufferManager**.|  
|**counter_name**|**NCHAR(128)**|Name des Leistungsindikators innerhalb des Objekts, z. B. **Seitenanforderungen** oder **Sperranforderungen**.|  
|**instance_name**|**NCHAR(128)**|Benannte Instanz des Indikators. Es sind beispielsweise Leistungsindikatoren für jeden Typ von Sperre, z. B. **Tabelle**, **Seite**, **Schlüssel**und so weiter. Durch den Instanznamen kann zwischen ähnlichen Indikatoren unterschieden werden.|  
|**cntr_value**|**bigint**|Tatsächlicher Indikatorwert. Häufig ist dies ein konstanter oder monoton wachsender Leistungsindikator, der das Auftreten des Instanzereignisses zählt.|  
|**cntr_type**|**int**|Typ des Leistungsindikators, wie von der Windows-Leistungsarchitektur definiert.|  
  
## <a name="see-also"></a>Siehe auch  
 [Zuordnen von Systemtabellen zu Systemsichten &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Kompatibilitätssichten &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
