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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7763f7406f865194743c43a6d182466767799b41
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82829834"
---
# <a name="msreplication_queue-transact-sql"></a>MSreplication_queue (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSreplication_queue** Tabelle wird vom Replikationsprozess verwendet, um die Befehle in der Warteschlange zu speichern, die von allen Abonnements mit verzögertem Update über eine Warteschlange ausgegeben werden, die SQL-basierte Warteschlangen Diese Tabelle wird in der Abonnement Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|Der Name des Verlegers.|  
|**publisher_db**|**sysname**|Der Name der Veröffentlichungs Datenbank.|  
|**ung**|**sysname**|Der Name der Veröffentlichung.|  
|**tranid**|**sysname**|Die Transaktions-ID, unter der der Befehl in der Warteschlange ausgeführt wurde|  
|**Daten**|**varbinary(8000)**|Der gepackte Bytedatenstrom, der Informationen zu dem in der Warteschlange aufgenommenen Befehl gespeichert hat.|  
|**datalen**|**int**|Die Länge der Daten in Bytes.|  
|**CommandType**|**int**|Der Typ des Befehls in der Warteschlange:<br /><br /> 1 = Benutzerbefehl in Transaktion.<br /><br /> 2 = Befehl zur Abonnementsynchronisierung.|  
|**insertdate**|**datetime**|Das Einfügedatum.|  
|**orderkey**|**bigint**|Die Identitätsspalte, deren Wert monoton ansteigt.|  
|**cmdstate**|**bit**|Der Befehlsstatus:<br /><br /> 0 = Abgeschlossen.<br /><br /> 1 = Teilweise.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
