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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: cab5283d83079f3a9a17dbf6f23dde1228019473
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82805333"
---
# <a name="msmerge_errorlineage-transact-sql"></a>MSmerge_errorlineage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSmerge_errorlineage** Tabelle enthält Zeilen, die auf dem Abonnenten gelöscht wurden, deren Löschung aber nicht an den Verleger weitergegeben wurde. Diese Tabelle wird in der Veröffentlichungs- und in der Abonnementdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|Der ganzzahlige Wert, der der Tabelle zugewiesen ist, die für Mergereplikation veröffentlicht wird. Entspricht dem Feld Spitzname in der **sysmergearticles** -Tabelle.|  
|**rowguid**|**uniqueidentifier**|Der Zeilen Bezeichner.|  
|**Leitung**|**varbinary (501)**|Speichert eine Verlaufsliste mit den Abonnenten und Verlegern, die eine Zeile aktualisiert haben. Er wird verwendet, um Konfliktsituationen zu entdecken und aufzulösen.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
