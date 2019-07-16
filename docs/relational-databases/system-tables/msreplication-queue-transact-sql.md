---
title: MSreplication_queue (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSreplication_queue
- MSreplication_queue_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplication_queue system table
ms.assetid: 664bf817-8021-4417-96d6-2bb1e4baabff
author: stevestein
ms.author: sstein
ms.openlocfilehash: 914cf3ad65c881383a6d625c07d4fb5ed028b36a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68080008"
---
# <a name="msreplicationqueue-transact-sql"></a>MSreplication_queue (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSreplication_queue** Tabelle wird vom Replikationsprozess verwendet, um die Warteschlange eingereihten Befehlen ausgegeben, die von allen die Abonnements mit verzögertem Aktualisieren, die SQL-basierten verwenden, in der Warteschlange zu speichern. Diese Tabelle wird in der Abonnementdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|Der Name des Verlegers.|  
|**publisher_db**|**sysname**|Der Name der Veröffentlichungsdatenbank.|  
|**publication**|**sysname**|Der Name der Veröffentlichung.|  
|**der Standard**|**sysname**|Die Transaktions-ID, unter der der Befehl in der Warteschlange ausgeführt wurde|  
|**data**|**varbinary(8000)**|Der gepackte Bytedatenstrom, der Informationen zu dem in der Warteschlange aufgenommenen Befehl gespeichert hat.|  
|**datalen**|**int**|Die Länge der Daten in Bytes.|  
|**Befehlstyp (CommandType)**|**int**|Der Typ des Befehls in der Warteschlange:<br /><br /> 1 = Benutzerbefehl in Transaktion.<br /><br /> 2 = Befehl zur Abonnementsynchronisierung.|  
|**insertdate**|**datetime**|Das Einfügedatum.|  
|**orderkey**|**bigint**|Die Identitätsspalte, deren Wert monoton ansteigt.|  
|**cmdstate**|**bit**|Der Befehlsstatus:<br /><br /> 0 = Abgeschlossen.<br /><br /> 1 = Teilweise.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
