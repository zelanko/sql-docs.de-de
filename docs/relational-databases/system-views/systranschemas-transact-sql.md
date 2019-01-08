---
title: "' systranschemas ' (Transact-SQL) | Microsoft-Dokumentation"
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- systranschemas
- systranschemas_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- systranschemas system table
ms.assetid: 864c3966-cb61-4f2b-8939-ccda112de853
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3339cf1731c712cdfee7145390d5cc955c748a98
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52760702"
---
# <a name="systranschemas-transact-sql"></a>systranschemas (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Die **Systranschemas** -Tabelle dient zum Nachverfolgen von schemaänderungen in Artikeln, die in Transaktions- und momentaufnahmeveröffentlichungen veröffentlicht. Diese Tabelle wird sowohl in Veröffentlichungs- als auch in Abonnementdatenbanken gespeichert.  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**tabid**|**int**|Identifiziert den Tabellenartikel, in dem die Schemaänderung stattgefunden hat.|  
|**startlsn**|**binary**|LSN-Wert zu Beginn der Schemaänderung|  
|**endlsn**|**binary**|LSN-Wert am Ende der Schemaänderung|  
|**typeid**|**int**|Art der Schemaänderung|  
  
## <a name="see-also"></a>Siehe auch  
 [Replikationstabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
