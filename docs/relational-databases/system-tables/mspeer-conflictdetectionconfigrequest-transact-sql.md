---
title: MSpeer_conflictdetectionconfigrequest (T-SQL)
description: Beschreibt die MSPeer_conflictdetectionconfigurerequest gespeicherte Prozedur, die zum Nachverfolgen von topologieweiten Konfigurations Anforderungen für eine Peer-zu-Peer-Veröffentlichung verwendet wird.
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpeer_conflictdetectionconfigrequest_TSQL
- MSpeer_conflictdetectionconfigrequest
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_conflictdetectionconfigurerequest
ms.assetid: 83afa0ca-707e-4468-a888-228268ed4e10
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 2ad027934c2ff0a0009512334c0d7d1a89a7bcb7
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89540329"
---
# <a name="mspeer_conflictdetectionconfigrequest-transact-sql"></a>MSpeer_conflictdetectionconfigrequest (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Wird in der Peer-zu-Peer-Replikation verwendet, um topologieübergreifende Konfigurationsanforderungen für eine Veröffentlichung zu verfolgen. Diese Tabelle wird in der Veröffentlichungsdatenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|id|**int**|Identifiziert eine Konfliktkonfigurationsanforderung. In der Spalte request_id in [MSpeer_conflictdetectionconfigresponse](../../relational-databases/system-tables/mspeer-conflictdetectionconfigresponse-transact-sql.md) wird dieser Wert verwendet.|  
|publication|**sysname**|Name der Veröffentlichung, aus der die Konfliktkonfigurationsanforderung stammt.|  
|sent_date|**datetime**|Datum und Uhrzeit der Initiierung der Konfliktkonfigurationsanforderung.|  
|timeout|**int**|Zeitraum, den eine Prozedur verstreichen lassen sollte, bis alle Peers Konfliktinformationen zurückgeben.|  
|modified_date|**datetime**|Datum und Uhrzeit, zu der eine Phase abgeschlossen wurde.|  
|progress_phase|**nvarchar(32)**|Identifiziert die aktuelle Phase der Verarbeitung mit einem der folgenden Werte:<br /><br /> Gestartet<br /><br /> Topologie wird durchsucht<br /><br /> Status wird erfasst<br /><br /> Status erfasst|  
|phase_timed_out|**bit**|Gibt an, ob für die aktuelle Phase ein Timeout eingetreten ist.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikationssichten &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
