---
title: MSSQLSERVER_8710 | Microsoft-Dokumentation
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
- 8710 (Database Engine error)
ms.assetid: 78b9f9da-5489-4be0-94df-f065d86ed18c
caps.latest.revision: 8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 28b8eb71cc0e50925788596d1b23572a51064423
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver8710"></a>MSSQLSERVER_8710
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|MSSQLSERVER|  
|Ereignis-ID|8710|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|QUERY2_CUBE_ILLEGAL_AGG_FUNC|  
|Meldungstext|Aggregatfunktionen, die mit CUBE-, ROLLUP- oder GROUPING SET-Abfragen verwendet werden, müssen das Zusammenführen von Unteraggregaten bereitstellen. Entfernen Sie die Aggregatfunktion, oder schreiben Sie die Abfrage mit UNION ALL über GROUP BY-Klauseln, um das Problem zu beheben.|  
  
## <a name="explanation"></a>Erklärung  
Es wurde eine Aggregatfunktion mit CUBE, ROLLUP oder GROUPING SETS verwendet, die keine Methode zum Zusammenführen von Unteraggregaten zur Verfügung stellt.  
  
## <a name="user-action"></a>Benutzeraktion  
Entfernen Sie die Aggregatfunktion, oder schreiben Sie die Abfrage mit UNION ALL über GROUP BY-Klauseln, um das Problem zu beheben.  
  
