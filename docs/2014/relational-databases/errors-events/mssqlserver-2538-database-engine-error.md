---
title: MSSQLSERVER_2538 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 2538 (Database Engine error)
ms.assetid: 0a0f7d79-f1ba-4749-8804-fb660cca3492
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 3bd4542bc3f5288ef9fc263e693d250f5a2463c3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150384"
---
# <a name="mssqlserver2538"></a>MSSQLSERVER_2538
    
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
  
  