---
title: MSSQLSERVER_8642 | Microsoft-Dokumentation
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
- 8642 (Database Engine error)
ms.assetid: fc498059-202f-4d0b-8599-4e784b47c186
caps.latest.revision: 15
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7270f28654a90ab6245845b0ea606c3dfa8a070f
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver8642"></a>MSSQLSERVER_8642
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|8642|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|EXCHNGSTART_ERR|  
|Meldungstext|Der Abfrageprozessor konnte die erforderlichen Threadressourcen für die parallele Abfrageausführung nicht starten.|  
  
## <a name="explanation"></a>Erklärung  
Auf dem Server gibt es nicht genügend Threadressourcen.  
  
## <a name="user-action"></a>Benutzeraktion  
Verringern Sie die Last auf dem Server, und führen Sie die Abfrage erneut aus.  
  
