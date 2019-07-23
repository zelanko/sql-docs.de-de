---
title: MSSQLSERVER_8710 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 8710 (Database Engine error)
ms.assetid: 78b9f9da-5489-4be0-94df-f065d86ed18c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8b88b9212cec193e86de72b70c126df3e3d0d92e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68120489"
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
  
