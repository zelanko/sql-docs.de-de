---
title: MSSQLSERVER_7910 | Microsoft-Dokumentation
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
- 7910 (Database Engine error)
ms.assetid: 017a0113-2b17-40b3-a419-30bbc43d46b8
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 056802e0965e60963af5ec36bfc416c59cd0ff4f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150593"
---
# <a name="mssqlserver7910"></a>MSSQLSERVER_7910
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|7910|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC2_REPAIR_PAGE_ALLOCATED|  
|Meldungstext|Reparaturvorgang: Die Seite P_ID wurde der Objekt-ID O_ID, Index-ID I_ID, Partitions-ID PN_ID, Zuordnungseinheits-ID A_ID (Typ TYPE) zugeordnet.|  
  
## <a name="explanation"></a>Erklärung  
 Dies ist eine Informationsmeldung von REPAIR, die besagt, dass eine Seite dem Einzelseiten-Slotarray einer IAM-Seite (Index Allocation Map) zugeordnet wurde.  
  
## <a name="user-action"></a>Benutzeraktion  
 InclusionThresholdSetting  
  
  