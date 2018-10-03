---
title: MSSQLSERVER_10737 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10737 (Database Engine error)
ms.assetid: 208af6ed-b271-4ab8-803e-7666025385c8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f96a3849360cc0eb5d04c75187f505967b33baf3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47849178"
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
  
