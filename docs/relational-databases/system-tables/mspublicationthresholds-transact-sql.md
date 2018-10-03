---
title: MSpublicationthresholds (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- mspublicationthresholds
- mspublicationthresholds_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpublicationthresholds system table
ms.assetid: 9da3879f-b1f4-4ab4-abd4-a9a8ac395eba
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 133bdbd53cf89b9ebf20260c867e22008b460aae
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47703088"
---
# <a name="mspublicationthresholds-transact-sql"></a>MSpublicationthresholds (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSpublicationthresholds** -Tabelle dient zum Nachverfolgen des Replikationsleistungsverlaufs für eine Veröffentlichung, wobei für jeden überwachten Schwellenwert eine Zeile. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**publication_id**|**int**|Identifiziert die Veröffentlichung, für die ein Schwellenwert festgelegt wurde.|  
|**metric_id**|**int**|Identifiziert eine replikationsleistungsmetrik überwacht wird, gemäß der [MSreplmonthresholdmetrics](../../relational-databases/system-tables/msreplmonthresholdmetrics-transact-sql.md) -Systemtabelle.|  
|**Wert**|**sql_variant**|Der Schwellenwert der überwachten Eigenschaft.|  
|**shouldalert**|**bit**|Der Wert **1** gibt an, dass eine Warnung generiert werden soll, wenn die Metrik den definierten Schwellenwert überschreitet.|  
|**IsEnabled**|**bit**|Der Wert **1** gibt an, dass die Überwachung für diese Eigenschaft des Replikationsleistungsverlaufs aktiviert ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
