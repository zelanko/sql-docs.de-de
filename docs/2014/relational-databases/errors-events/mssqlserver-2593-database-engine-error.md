---
title: MSSQLSERVER_2593 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 2593 (Database Engine error)
ms.assetid: 2e25bc43-606a-40de-8b87-3b55b96f4a91
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 316228d2dffa4cfcaba0bd3e6356999d4052d21a
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37427439"
---
# <a name="mssqlserver2593"></a>MSSQLSERVER_2593
    
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
  
  
