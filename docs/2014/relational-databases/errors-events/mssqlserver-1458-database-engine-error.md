---
title: MSSQLSERVER_1458 | Microsoft-Dokumentation
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
- 1458 (Database Engine error)
ms.assetid: adc78c59-a6f2-432b-9a07-fdd1dc2b9026
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8ff43b96cfe4e520972b9293d9843417b63e1683
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150381"
---
# <a name="mssqlserver1458"></a>MSSQLSERVER_1458
    
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
  
## <a name="see-also"></a>Siehe auch  
 [Überwachen der Datenbankspiegelung &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  