---
title: MSSQLSERVER_10737 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 10737 (Database Engine error)
ms.assetid: 208af6ed-b271-4ab8-803e-7666025385c8
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 14e593ef1dba6a6bed7c5d8a7a1fa42e642ee7d7
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37428369"
---
# <a name="mssqlserver10737"></a>MSSQLSERVER_10737
    
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
  
  
