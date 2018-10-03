---
title: MSmerge_settingshistory (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSmerge_settingshistory
- MSmerge_settingshistory_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_settingshistory system table
ms.assetid: 0bdf2d5f-5502-44cd-aa9d-2d5006ad20ce
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c35438b1b6df4b2df3ae1af25cb9479f676d9ee5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47782918"
---
# <a name="msmergesettingshistory-transact-sql"></a>MSmerge_settingshistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSmerge_settingshistory** Tabelle dient zur Verwaltung eines Verlaufs der Änderungen an Artikel- und Veröffentlichungseigenschaften Eigenschaften für die Mergereplikation mit einer Zeile für jede Änderung an einer mergereplikationstopologie. In dieser Tabelle werden auch Informationen zu dem Zeitpunkt gespeichert, zu dem die ursprünglichen Eigenschaftseinstellungen vorgenommen wurden. Diese Tabelle wird in der Veröffentlichungs- und in der Abonnementdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**EventTime**|**datetime**|Die Uhrzeit, zu der das Ereignis aufgetreten ist|  
|**pubid**|**uniqueidentifier**|Die eindeutige ID für eine bestimmte Veröffentlichung|  
|**artid**|**uniqueidentifier**|Die eindeutige ID des angegebenen Artikels.|  
|**EventType**|**tinyint**|Gibt den Ereignistyp an, der aufgezeichnet wird. Es kann einer der folgenden Typen sein:<br /><br /> **1** -ursprüngliche veröffentlichungsebenen-eigenschaftseinstellung.<br /><br /> **2** -veröffentlichungseigenschaft ändern.<br /><br /> **101** -ursprüngliche.<br /><br /> **102** -Artikeleigenschaft ändern.|  
|**propertyname**|**sysname**|Der Name der festgelegten oder geänderten Eigenschaft|  
|**previousvalue**|**sysname**|Der vorhergehende Eigenschaftswert, falls eine Eigenschaft geändert wurde|  
|**newValue**|**sysname**|Der Wert, zu dem die Eigenschaft geändert oder mit dem die Eigenschaft erstellt wurde|  
|**eventText**|**Datentyp nvarchar(2000)**|Die Zeichenfolge, die das Ereignis beschreibt|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
