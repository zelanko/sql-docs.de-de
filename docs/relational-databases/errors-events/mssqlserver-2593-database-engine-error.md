---
title: MSSQLSERVER_2593 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
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
ms.openlocfilehash: bb1c4cef6aa746a7d8db78d7d5c46db699207c8a
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
ms.locfileid: "34319071"
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
  
