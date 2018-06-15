---
title: Sys.sysdevices (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysdevices
- sysdevices_TSQL
- sys.sysdevices
- sys.sysdevices_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysdevices compatibility view
- sysdevices system table
ms.assetid: ac5bcaf4-8fb6-4855-8856-d7643f469361
caps.latest.revision: 24
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: bf1a22fae1c4c8f69edf843c1a126844abdd1190
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
ms.locfileid: "33219981"
---
# <a name="syssysdevices-transact-sql"></a>sys.sysdevices (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jede Sicherungsdatei auf dem Datenträger und auf Band sowie für jede Datenbankdatei.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Logischer Name der Sicherungs- oder Datenbankdatei.|  
|**size**|**int**|Größe der Datei in Seiten mit einer Größe von 2 Kilobytes (KB)|  
|**Niedrig**|**int**|Nur aus Gründen der Abwärtskompatibilität beibehalten.|  
|**Hohe**|**int**|Nur aus Gründen der Abwärtskompatibilität beibehalten.|  
|**status**|**smallint**|Bitmuster, das den Medientyp anzeigt:<br /><br /> 1 = Standarddatenträger<br /><br /> 2 = Physischer Datenträger<br /><br /> 4 = Logischer Datenträger<br /><br /> 8 = Header auslassen<br /><br /> 16 = Sicherungsdatei<br /><br /> 32 = Serielle Schreibvorgänge<br /><br /> 4096 = Schreibgeschützt|  
|**cntrltype**|**smallint**|Controllertyp:<br /><br /> 0 = Nicht-CD-ROM-Datenbankdatei<br /><br /> 2 = Sicherungsdatei auf Datenträger<br /><br /> 3 - 4 = Sicherungsdatei auf Diskette<br /><br /> 5 = Sicherungsdatei auf Band<br /><br /> 6 = Named Pipe-Datei|  
|**phyname**|**nvarchar(260)**|Name der physischen Datei|  
  
## <a name="see-also"></a>Siehe auch  
 [Zuordnen von Systemtabellen zu Systemsichten &#40;Transact-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Kompatibilitätssichten &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
