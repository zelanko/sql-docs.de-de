---
title: MSSQLSERVER_41342 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 41342 (Database Engine error)
ms.assetid: 28270d98-c543-4e7d-b40c-2200e38dce1c
caps.latest.revision: 8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bdab0e9260b50b1ab9504dd7bd1455f4b8959ed8
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
ms.locfileid: "34318351"
---
# <a name="mssqlserver41342"></a>MSSQLSERVER_41342
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
