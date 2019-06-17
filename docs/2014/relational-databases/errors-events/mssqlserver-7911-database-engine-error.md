---
title: MSSQLSERVER_7911 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7911 (Database Engine error)
ms.assetid: dd8390f3-0f77-4fb2-ba94-631a56e42bc6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: dbb5a12fdcb3c326957d719882feec4fe948190c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62761847"
---
# <a name="mssqlserver7911"></a>MSSQLSERVER_7911
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|7911|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC2_REPAIR_PAGE_DEALLOCATED|  
|Meldungstext|Reparaturvorgang: Die Seite wurde P_ID in Objekt-ID O_ID, Index-ID I_ID, Partitions-ID PN_ID, zuordnungseinheits-ID A_ID (Typ TYPE) aufgehoben.|  
  
## <a name="explanation"></a>Erklärung  
 Dies ist eine Informationsmeldung von REPAIR, die besagt, dass die Zuordnung einer Seite zu dem einseitigen Slotarray einer IAM-Seite (Index Allocation Map) aufgehoben wurde.  
  
## <a name="user-action"></a>Benutzeraktion  
 None  
  
  
