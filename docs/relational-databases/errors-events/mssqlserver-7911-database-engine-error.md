---
title: MSSQLSERVER_7911 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 7911 (Database Engine error)
ms.assetid: dd8390f3-0f77-4fb2-ba94-631a56e42bc6
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
robots: noindex,nofollow
ms.openlocfilehash: e26c0f199a52adeed4273e43acad52a2bc781eab
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver7911"></a>MSSQLSERVER_7911
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|7911|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC2_REPAIR_PAGE_DEALLOCATED|  
|Meldungstext|Reparaturvorgang: Die Zuordnung der Seite P_ID zu Objekt-ID O_ID, Index-ID I_ID, Partitions-ID PN_ID, Zuordnungseinheits-ID A_ID (Typ TYPE) wurde aufgehoben.|  
  
## <a name="explanation"></a>Erklärung  
Dies ist eine Informationsmeldung von REPAIR, die besagt, dass die Zuordnung einer Seite zu dem einseitigen Slotarray einer IAM-Seite (Index Allocation Map) aufgehoben wurde.  
  
## <a name="user-action"></a>Benutzeraktion  
Keine  
  
