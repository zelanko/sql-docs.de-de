---
title: MSpeer_originatorid_history (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpeer_originatorid_history_TSQL
- MSpeer_originatorid_history
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_originatorid_history
ms.assetid: c1f53d0f-4080-43ff-be38-2b10395c68c9
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4f3e81b10ae8805161db6067d4363317a5c93fcb
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85751627"
---
# <a name="mspeer_originatorid_history-transact-sql"></a>MSpeer_originatorid_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Enthält eine Zeile für jede Absender-ID, die in der Topologie definiert wurde. Dies beinhaltet IDs für Knoten, die nicht mehr aktiv sind. Die Tabelle wird verwendet, wenn Sie einen neuen Knoten für die Konflikterkennung konfigurieren, um sicherzustellen, dass die angegebene Absender-ID noch nicht verwendet wurde. Diese Tabelle wird in der Veröffentlichungsdatenbank gespeichert. Weitere Informationen zur Konflikterkennung finden Sie unter [Konflikterkennung in der Peer-zu-Peer-Replikation](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|originator_publication|**sysname**|Veröffentlichung, für welche die Absender-ID angegeben wurde|  
|originator_id|**int**|Nummer, die jeden Knoten in der Topologie zum Zweck der Konflikterkennung kennzeichnet|  
|originator_node|**sysname**|Serverinstanz, für welche die Absender-ID angegeben wurde|  
|originator_db|**sysname**|Veröffentlichungsdatenbank, für welche die Absender-ID angegeben wurde|  
|originator_db_version|**int**|Kennzeichnet die Versionsnummer der ursprünglichen Datenbank.|  
|originator_version|**int**|Kennzeichnet die Versionsnummer des Verlegers|  
|inserted_date|**datetime**|Datum und Zeit, zu der die Zeile für die Absender-ID in diese Tabelle eingefügt wurde|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
