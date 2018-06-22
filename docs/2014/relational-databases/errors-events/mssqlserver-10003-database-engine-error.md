---
title: MSSQLSERVER_10003 | Microsoft-Dokumentation
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
- 10003 (Database Engine error)
ms.assetid: 9e2cb199-f077-4d88-8117-1b7550afc696
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 3f93a6fcdb5b5d5ac98d834f96e6d2689a5765f1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36148620"
---
# <a name="mssqlserver10003"></a>MSSQLSERVER_10003
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|10003|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|HR_E_OUTOFMEMORY|  
|Meldungstext|Dem Anbieter steht nicht genügend Arbeitsspeicher zur Verfügung.|  
  
## <a name="explanation"></a>Erklärung  
 Zu geringer Systemspeicher hat bewirkt, dass der OLE DB-Anbieter nicht mehr über genügend Speicher verfügt.  
  
## <a name="user-action"></a>Benutzeraktion  
 Starten Sie die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]neu. Falls der Fehler dadurch nicht behoben wird, starten Sie den Computer neu. Wenn das Problem weiterhin auftritt, listen Sie OLE DB-Ablaufverfolgungsereignisse mit [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] auf, und stellen Sie diese Daten für den Produktsupport des OLE DB-Anbieters bereit.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorlagen und Berechtigungen in SQL Server Profiler](../../tools/sql-server-profiler/sql-server-profiler-templates-and-permissions.md)   
 [SQL Server Native Client &#40;OLE DB&#41;](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  