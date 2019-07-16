---
title: Sys.pdw_health_alerts (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: system-objects
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 49c01e5f-ee47-41a0-871d-35a759f50851
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: c47bcc342bf8a052aed93649ca0ad8475d937608
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68127544"
---
# <a name="syspdwhealthalerts-transact-sql"></a>sys.pdw_health_alerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Speichert Eigenschaften für die verschiedenen Warnungen, die auftreten können, auf dem System. Dies ist ein Katalogtabelle für Warnungen.  
  
|Spaltenname|Datentyp|Beschreibung|Bereich|  
|-----------------|---------------|-----------------|-----------|  
|alert_id|**int**|Eindeutiger Bezeichner der Warnung.<br /><br /> Der Schlüssel für diese Sicht.|NOT NULL|  
|component_id|**int**|Die ID der Komponente, für die, der diese Warnung gilt. Die Komponente ist ein Bezeichner mit allgemeinen Komponente, z. B. "Stromversorgung,", und es ist nicht spezifisch für eine Installation. Finden Sie unter [sys.pdw_health_components &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-health-components-transact-sql.md).|NOT NULL|  
|alert_name|**nvarchar(255)**|Der Name der Warnung.|NOT NULL|  
|state|**nvarchar(32)**|Status der Warnung.|NOT NULL<br /><br /> Mögliche Werte:<br /><br /> 'Operational'<br /><br /> "Nicht mehr funktionstüchtig"<br /><br /> "Heruntergestuft"<br /><br /> "Failed"|  
|severity|**nvarchar(32)**|Schweregrad der Warnung.|NOT NULL<br /><br /> Mögliche Werte:<br /><br /> "Informational"<br /><br /> "Warnung"<br /><br /> "Error"|  
|Typ|**nvarchar(32)**|Der Typ der Warnung.|NOT NULL<br /><br /> Mögliche Werte:<br /><br /> StatusChange - wurde der Status geändert werden.<br /><br /> Schwellenwert - verfügt über ein Wert den Schwellenwert überschritten.|  
|description|**nvarchar(4000)**|Beschreibung der Warnung.|NOT NULL|  
|Bedingung|**nvarchar(255)**|Geben Sie verwendet, wenn Schwellenwert =. Definiert, wie der Schwellenwert für die berechnet wird.|NULL|  
|status|**nvarchar(32)**|Warnungsstatus|NULL|  
|Value|**bit**|Gibt an, ob die Warnung während des Systembetriebs auftreten darf.|NULL<br /><br /> Mögliche Werte<br /><br /> 0 – wird die Warnung nicht generiert.<br /><br /> 1: die Warnung wird generiert.|  
  
## <a name="see-also"></a>Siehe auch  
 [SQL Datawarehouse und Parallel Datawarehouse-Katalogsichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
