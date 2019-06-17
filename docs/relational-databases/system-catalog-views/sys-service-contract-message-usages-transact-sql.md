---
title: Sys. service_contract_message_usages (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- service_contract_message_usages_TSQL
- sys.service_contract_message_usages
- sys.service_contract_message_usages_TSQL
- service_contract_message_usages
dev_langs:
- TSQL
helpviewer_keywords:
- sys.service_contract_message_usages catalog view
ms.assetid: f783e662-126c-4595-8e22-f9d05191f5d0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 280686087a0099fa374664eb0cbfe9d7c2b244ec
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62856044"
---
# <a name="sysservicecontractmessageusages-transact-sql"></a>sys.service_contract_message_usages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Diese Katalogsicht enthält eine Zeile pro Vertrag/Nachrichtentyp-Paar.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**service_contract_id**|**int**|Bezeichner des Vertrags, der den Nachrichtentyp verwendet. Lässt keine NULL-Werte zu.|  
|**message_type_id**|**int**|Bezeichner des Nachrichtentyps, der vom Vertrag verwendet wird. Lässt keine NULL-Werte zu.|  
|**is_sent_by_initiator**|**bit**|Der Nachrichtentyp kann vom Konversationsinitiator gesendet werden. Lässt keine NULL-Werte zu.|  
|**is_sent_by_target**|**bit**|Der Nachrichtentyp kann vom Konversationsziel gesendet werden. Lässt keine NULL-Werte zu.|  
  
## <a name="permissions"></a>Berechtigungen  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Weitere Informationen finden Sie unter [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
