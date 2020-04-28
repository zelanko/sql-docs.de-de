---
title: Mspeer_topologyrequest (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpeer_topologyrequest_TSQL
- MSpeer_topologyrequest
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_topologyrequest
ms.assetid: c644814b-4e40-44d7-b6b4-5954b0d4db7c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 29ea5e7e78d274eaf289afbd6ca73f97cd479679
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68026662"
---
# <a name="mspeer_topologyrequest-transact-sql"></a>MSpeer_topologyrequest (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Wird in der Peer-zu-Peer-Replikation verwendet, um Topologiestatusanforderungen für eine Veröffentlichung zu verfolgen. Diese Tabelle wird in der Veröffentlichungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|id|**int**|Identifiziert eine Topologiestatusanforderung. In der Spalte request_id in [MSpeer_topologyresponse](../../relational-databases/system-tables/mspeer-topologyresponse-transact-sql.md) wird dieser Wert verwendet.|  
|publication|**sysname**|Name der Veröffentlichung, aus der die Topologiestatusanforderung stammt.|  
|sent_date|**datetime**|Datum und Uhrzeit der Initiierung der Topologiestatusanforderung.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
