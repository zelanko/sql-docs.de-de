---
title: MSSQLSERVER_2538 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 2538 (Database Engine error)
ms.assetid: 0a0f7d79-f1ba-4749-8804-fb660cca3492
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8bc726c6dd875c6988e905e6d720881d3e0be6c8
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver2538"></a>MSSQLSERVER_2538
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|2538|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC_ALLOCATION_SUMMARY_PER_FILE|  
|Meldungstext|Datei FILE. Blockanzahl = EXTENTS, verwendete Seiten = USED_PAGES, reservierte Seiten = RESERVED_PAGES.|  
  
## <a name="explanation"></a>Erklärung  
Diese Informationen sind Teil der Ausgabe des Befehls DBCC CHECKALLOC. Bei diesen Informationen handelt es sich um die Zusammenfassung von zugeordneten Blöcken, verwendeten Seiten und reservierten Seiten pro Datei für die angegebene Datenbank.  
  
## <a name="user-action"></a>Benutzeraktion  
InclusionThresholdSetting  
  
