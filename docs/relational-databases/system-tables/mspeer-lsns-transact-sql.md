---
title: MSpeer_lsns (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpeer_lsns
- MSpeer_lsns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_lsns system table
ms.assetid: 0ba33907-601b-4c3d-8099-2663f680a161
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 38efa38b53a089f960311e415d42972599872fcc
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82832280"
---
# <a name="mspeer_lsns-transact-sql"></a>MSpeer_lsns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSpeer_lsns** Tabelle wird verwendet, um jede Transaktion einem Abonnement in einer Peer-zu-Peer-Replikations Topologie zuzuordnen. Diese Tabelle wird in jeder Veröffentlichungsdatenbank in einer Peer-zu-Peer-Replikationstopologie sowie in der Abonnementdatenbank aller Abonnenten einer Peer-zu-Peer-Veröffentlichung gespeichert. Weitere Informationen zu dieser Art von Transaktionsreplikations Topologie finden [Sie unter Peer-to-Peer-Transaktions Replikation](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md). Diese Tabelle wird in der Veröffentlichungsdatenbank gespeichert.  
  
## <a name="definition"></a>Definition  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Identifiziert eine Peer-zu-Peer-LSN.|  
|**last_updated**|**datetime**|Der **DateTime** -Wert, zu dem das letzte Zeilen Update durchgeführt wurde.|  
|**originator**|**sysname**|Der Name des Verlegers, von dem die Transaktion stammt|  
|**originator_db**|**sysname**|Der Name der Datenbank, aus der die Transaktion stammt|  
|**originator_publication**|**sysname**|Der Name der Veröffentlichung, aus der die Transaktion stammt|  
|**originator_publication_id**|**int**|Die ID der Veröffentlichung, aus der die Transaktion stammt|  
|**originator_db_version**|**int**|Kennzeichnet die Versionsnummer der ursprünglichen Datenbank.|  
|**originator_lsn**|**int**|Identifiziert die LSN in der Ausgangsveröffentlichung|  
|**originator_version**|**int**|Kennzeichnet die Versionsnummer des Verlegers|  
|**originator_id**|**smallint**|Identifiziert jeden Knoten in der Topologie zum Zweck der Konflikterkennung. Weitere Informationen finden Sie unter [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
