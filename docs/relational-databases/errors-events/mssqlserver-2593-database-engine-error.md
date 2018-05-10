---
title: MSSQLSERVER_2593 | Microsoft-Dokumentation
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
- 2593 (Database Engine error)
ms.assetid: 2e25bc43-606a-40de-8b87-3b55b96f4a91
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d084bae5bc5e46c4a15c01df7330467f34ec2671
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver2593"></a>MSSQLSERVER_2593
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|2593|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC_OBJECT_ROW_PAGE_SUMMARY|  
|Meldungstext|Es sind ROWCOUNT Zeilen auf PAGECOUNT Seiten für das Objekt 'OBJECT' vorhanden.|  
  
## <a name="explanation"></a>Erklärung  
Diese Meldung ist Teil der Informationsausgabe, die von allen DBCC-Überprüfungen außer von DBCC CHECKALLOC zurückgegeben wird. Sie gibt die Zeilen- und Seitenanzahl für ein bestimmtes Objekt an.  
  
## <a name="user-action"></a>Benutzeraktion  
InclusionThresholdSetting  
  
