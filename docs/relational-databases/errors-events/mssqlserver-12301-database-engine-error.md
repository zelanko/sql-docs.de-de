---
title: MSSQLSERVER_12301 | Microsoft-Dokumentation
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
- 12301 (Database Engine error)
ms.assetid: 69455df4-4ce9-4a6f-af5a-8bbc93e21245
caps.latest.revision: 4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 14c7818688d5fe2ab39bfd9a03dd0269fb524445
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver12301"></a>MSSQLSERVER_12301
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|12301|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|HK_UNSUPPORTED_NULLABLE_COLUMNS|  
|Meldungstext|Im Indexschlüssel enthaltene Spalten, die NULL zulassen, werden bei *construct* nicht unterstützt.|  
  
## <a name="user-action"></a>Benutzeraktion  
Verwenden Sie im Indexschlüssel keine Spalten, die NULL zulassen.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
