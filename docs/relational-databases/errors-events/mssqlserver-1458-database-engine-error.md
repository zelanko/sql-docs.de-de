---
title: MSSQLSERVER_1458 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 1458 (Database Engine error)
ms.assetid: adc78c59-a6f2-432b-9a07-fdd1dc2b9026
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0585f1167083a6b2126ad98d3c6f3b8d81478de2
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
ms.locfileid: "34321521"
---
# <a name="mssqlserver1458"></a>MSSQLSERVER_1458
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|1458|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBM_FAILREDO_ON_PRIMARY|  
|Meldungstext|Bei der Prinzipalkopie der %.*ls-Datenbank ist der Fehler %d, Status %d, Schweregrad %d, aufgetreten. Die Datenbankspiegelung wurde angehalten. Beheben Sie den Fehler, und setzen Sie die Spiegelung fort.|  
  
## <a name="explanation"></a>Erklärung  
In dieser Meldung wird angegeben, dass in der Prinzipaldatenbank ein Fehler aufgetreten ist, durch den die Datenbankspiegelung angehalten wurde.  
  
## <a name="user-action"></a>Benutzeraktion  
Dieser Fehler wird in den meisten Fällen automatisch behoben. Wenn das Problem weiterhin besteht, kann das Problem normalerweise durch einen Neustart der Datenbank- oder Serverinstanz behoben werden. Weitere Informationen finden Sie im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlerprotokoll auf jedem Partner für den zugeordneten Fehler, der dieser Meldung vorausging.  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Überwachen der Datenbankspiegelung &#40;SQL Server&#41;](~/database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)  
  
