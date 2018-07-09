---
title: MSSQLSERVER_41305 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 41305 (Database Engine error)
ms.assetid: a96e5083-ff97-4003-a900-07942454151d
caps.latest.revision: 7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 499ec2d1630f74a329a5f72a1bc6a784463ec2a4
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37415879"
---
# <a name="mssqlserver41305"></a>MSSQLSERVER_41305
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Ereignis-ID|41305|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|HK_TX_COMMIT_RR_VALIDATION|  
|Meldungstext|Fehler beim Ausführen eines Commits für die aktuelle Transaktion aufgrund eines REPEATABLE READ-Überprüfungsfehlers.|  
  
## <a name="explanation"></a>Erklärung  
 Bei der Transaktion trat ein Überprüfungsfehler auf, sie kann nicht abgeschlossen werden.  
  
 Weitere Informationen finden Sie unter [In-Memory OLTP &#40;Arbeitsspeicheroptimierung&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="user-action"></a>Benutzeraktion  
 Wiederholen Sie die fehlgeschlagene Transaktion.  
  
## <a name="see-also"></a>Siehe auch  
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
