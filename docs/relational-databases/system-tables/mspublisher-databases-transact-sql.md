---
title: MSpublisher_databases (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpublisher_databases
- MSpublisher_databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpublisher_databases system table
ms.assetid: 59b0166e-a64c-46b8-befc-c222fa1ccce2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5c9ceb08b4757af09cfc5eba8c4d9f26da3cf931
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52817712"
---
# <a name="mspublisherdatabases-transact-sql"></a>MSpublisher_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSpublisher_databases** Tabelle enthält eine Zeile für jede vom lokalen Verteiler bediente Verleger/Verlegerdatenbank-Paar. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|Die ID des Verlegers|  
|**publisher_db**|**sysname**|Der Name der Verlegerdatenbank.|  
|**id**|**int**|Die ID der Zeile.|  
|**publisher_engine_edition**|**int**|Die Edition des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verlegers. Diese kann einen der folgenden Werte annehmen:<br /><br /> **10** = personal Edition<br /><br /> **11** = desktop Engine (MSDE)<br /><br /> **20** = Standard<br /><br /> **21** = Arbeitsgruppe<br /><br /> **30** = Enterprise (Evaluation)<br /><br /> **31** = Developer<br /><br /> **40** = Express (Express kann kein Verleger sein. Dieser Wert ist der Vollständigkeit halber angegeben.)|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
