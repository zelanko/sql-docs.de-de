---
title: MSmerge_metadataaction_request (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_metadataaction_request
- MSmerge_metadataaction_request_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_metadataaction_request system table
ms.assetid: cd31a114-900a-4218-ab58-d959e547c647
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 73fe0094b77c730f496dc0650c1169824018d00f
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82829865"
---
# <a name="msmerge_metadataaction_request-transact-sql"></a>MSmerge_metadataaction_request (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **MSmerge_metadataaction_request** Tabelle speichert eine Zeile für jede erforderliche kompensierende Aktion. Wenn bei der Websynchronisierung ein Fehler auftritt und die Synchronisierung erneut versucht werden muss, wird ein Eintrag in **MSmerge_metadataaction_request**erstellt. Während der Uploadphase der nachfolgenden Zusammenführung werden Anforderungen zum Synchronisieren aller zur Veröffentlichung gehörenden Artikel von dieser Tabelle abgerufen und hochgeladen. Wenn die Synchronisierung erfolgreich abgeschlossen wurde, wird die entsprechende Zeile in der **MSmerge_metadataaction_request** Tabelle gelöscht. Diese Tabelle wird auf dem Verleger in der Veröffentlichungsdatenbank und auf dem Abonnenten in der Abonnementdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**tablenick**|**int**|Der Spitzname der veröffentlichten Tabelle.|  
|**rowguid**|**uniqueidentifier**|Der Zeilenbezeichner für die angegebene Zeile.|  
|**action**|**tinyint**|Bezeichnet die erforderliche kompensierende Aktion.|  
|**Stro**|**bigint**|Der Wert der Generierung, für die die kompensierende Aktion benötigt wird.|  
|**tes**|**int**|Nur intern verwendet.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikations Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [Websynchronisierung für die Mergereplikation](../../relational-databases/replication/web-synchronization-for-merge-replication.md)  
  
  
