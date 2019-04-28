---
title: MSSQLSERVER_41342 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41342 (Database Engine error)
ms.assetid: 28270d98-c543-4e7d-b40c-2200e38dce1c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 57ce65cb8fed85eed9eacc176a371dec52145e1c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62867914"
---
# <a name="mssqlserver41342"></a>MSSQLSERVER_41342
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Ereignis-ID|41342|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|HK_HW_NOT_SUPPORTED|  
|Meldungstext|Das Modell des Prozessors im System unterstützt nicht die Erstellung von *construct*. Dieser Fehler tritt normalerweise bei älteren Prozessoren auf. Weitere Informationen zu unterstützten Modellen finden Sie in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation.|  
  
## <a name="explanation"></a>Erklärung  
 Speicheroptimierte Tabellen erfordern ein Prozessormodell, das unteilbare Vergleichs- und Austauschvorgänge für 128-Bit-Werte unterstützt. Das erfordert die Assemblyanweisung CMPXCHG16B. Bestimmte ältere AMD-Prozessormodelle unterstützen nicht die CMPXCHG16B-Anweisung. Außerdem wird diese Anweisung von bestimmten Virtualisierungsumgebungen standardmäßig nicht aktiviert.  
  
## <a name="user-action"></a>Benutzeraktion  
 Aktualisieren Sie den Prozessor. Wenn Ihr Prozessor die Anweisung unterstützt und Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf einem virtuellen Computer ausführen, ändern Sie die Konfiguration, sodass die Anweisung CMPXCHG16B unterstützt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
