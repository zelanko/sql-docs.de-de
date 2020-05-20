---
title: sysarticleupdates (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysarticleupdates_TSQL
- sysarticleupdates
dev_langs:
- TSQL
helpviewer_keywords:
- sysarticleupdates system table
ms.assetid: 11a53bcd-a215-4d0b-9db8-233981d3ef5d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 34a6e261665555575daf78ba31e2f6cb5257e9d0
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82833051"
---
# <a name="sysarticleupdates-transact-sql"></a>sysarticleupdates (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält eine Zeile für jeden Artikel, der sofort aktualisierte Abonnements unterstützt. Diese Tabelle wird in der replizierten Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Die Identitäts Spalte, die eine eindeutige ID für den Artikel bereitstellt.|  
|**pubid**|**int**|Die ID der Veröffentlichung, zu der der Artikel gehört.|  
|**sync_ins_proc**|**int**|Die ID der gespeicherten Prozedur, die synchrone Einfügetransaktionen verarbeitet.|  
|**sync_upd_proc**|**int**|Die ID der gespeicherten Prozedur, die synchrone Updatetransaktionen verarbeitet.|  
|**sync_del_proc**|**int**|Die ID der gespeicherten Prozedur, die synchrone Löschtransaktionen verarbeitet.|  
|**Autogen**|**bit**|Zeigt an, dass gespeicherte Prozeduren automatisch generiert werden:<br /><br /> **0** = false, nicht automatisch.<br /><br /> **1** = true, automatisch.|  
|**sync_upd_trig**|**int**|Die ID des Triggers für die automatische Versionsverwaltung für die Artikeltabelle.|  
|**conflict_tableid**|**int**|Die ID für die Konflikttabelle.|  
|**ins_conflict_proc**|**int**|Die ID der Prozedur, die zum Schreiben des Konflikts in die **conflict_table**verwendet wird.|  
|**identity_support**|**bit**|Gibt an, ob die automatische Behandlung des Identitätsbereichs aktiviert ist, wenn das verzögerte Aktualisieren über eine Warteschlange verwendet wird. **0** bedeutet, dass keine Identitäts Bereichs Unterstützung vorhanden ist.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
