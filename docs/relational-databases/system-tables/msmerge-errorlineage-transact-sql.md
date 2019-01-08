---
title: MSmerge_errorlineage (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_errorlineage_TSQL
- MSmerge_errorlineage
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_errorlineage system table
ms.assetid: 3bcbd328-c958-4cd4-a573-3c35539fa919
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d07a3fadfd2439c35b9d5255ff94d58c79bbbae5
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52794172"
---
# <a name="msmergeerrorlineage-transact-sql"></a>MSmerge_errorlineage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSmerge_errorlineage** -Tabelle enthält Zeilen, die auf dem Abonnenten gelöscht, aber deren Löschung wird nicht auf den Verleger weitergegeben. Diese Tabelle wird in der Veröffentlichungs- und in der Abonnementdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|Der ganzzahlige Wert, der der Tabelle zugewiesen ist, die für Mergereplikation veröffentlicht wird. Entspricht dem Nickname-Feld der **Sysmergearticles** Tabelle.|  
|**rowguid**|**uniqueidentifier**|Der Zeilenbezeichner.|  
|**Datenherkunft**|**varbinary(501)**|Speichert eine Verlaufsliste mit den Abonnenten und Verlegern, die eine Zeile aktualisiert haben. Er wird verwendet, um Konfliktsituationen zu entdecken und aufzulösen.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
