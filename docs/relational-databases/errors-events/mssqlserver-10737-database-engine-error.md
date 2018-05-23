---
title: MSSQLSERVER_10737 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 10737 (Database Engine error)
ms.assetid: 208af6ed-b271-4ab8-803e-7666025385c8
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3591d2aad2f8e7b62ef738adfdeca145f379913b
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver10737"></a>MSSQLSERVER_10737
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|MSSQLSERVER|  
|Ereignis-ID|10737|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|REBUILD_PARTITION_ALL_NOT_SPECIFIED|  
|Meldungstext|In einer ALTER TABLE REBUILD-Anweisung oder einer ALTER INDEX REBUILD-Anweisung muss PARTITION=ALL angegeben werden, wenn in einer DATA_COMPRESSION-Klausel eine Partition angegeben ist. Mit der PARTITION=ALL-Klausel wird erzwungen, dass alle Partitionen der Tabelle oder des Indexes auch dann neu erstellt werden, wenn nur eine Teilmenge in der DATA_COMPRESSION-Klausel angegeben ist.|  
  
## <a name="user-action"></a>Benutzeraktion  
Fügen Sie die PARTITION=ALL-Klausel der ALTER TABLE-Anweisung oder der ALTER INDEX-Anweisung hinzu. Alternativ können Sie REBUILD PARTITION = \<partition-number-expr> WITH (DATA_COMPRESSION={ON | OFF}) verwenden, um eine bestimmte Partition neu zu erstellen.  
  
