---
description: MSpublicationthresholds (Transact-SQL)
title: Mspublicationthreshold (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- mspublicationthresholds
- mspublicationthresholds_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpublicationthresholds system table
ms.assetid: 9da3879f-b1f4-4ab4-abd4-a9a8ac395eba
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 799c068d066fdab518a355552ead5ed5a9fde8af
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88427652"
---
# <a name="mspublicationthresholds-transact-sql"></a>MSpublicationthresholds (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Die **mspublicationthreshold** -Tabelle dient zum Nachverfolgen der Leistungsmetriken für die Replikation einer Veröffentlichung mit einer Zeile für jeden überwachten Schwellenwert. Diese Tabelle wird in der Verteilungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**publication_id**|**int**|Identifiziert die Veröffentlichung, für die ein Schwellenwert festgelegt wurde.|  
|**metric_id**|**int**|Identifiziert eine Replikations Leistungs Metrik, die gemäß der Definition in der [msreplmonationsoldmetrics](../../relational-databases/system-tables/msreplmonthresholdmetrics-transact-sql.md) -Systemtabelle überwacht wird.|  
|**value**|**sql_variant**|Der Schwellenwert der überwachten Eigenschaft.|  
|**shouldalert**|**bit**|Der Wert **1** gibt an, dass eine Warnung generiert werden soll, wenn die Metrik den definierten Schwellenwert überschreitet.|  
|**IsEnabled**|**bit**|Der Wert **1** gibt an, dass die Überwachung für diese Replikations Leistungs Metrik aktiviert ist.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
