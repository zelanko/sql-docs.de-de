---
title: MSSQLSERVER_1401 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1401 (Database Engine error)
ms.assetid: 02928770-aa63-4509-8713-406c73e4cedc
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 821a0bdcef41ce6691497e691f5350c0357a6693
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62915924"
---
# <a name="mssqlserver_1401"></a>MSSQLSERVER_1401
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|1401|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBM_MASTERSTARTUP|  
|Meldungstext|Fehler beim Starten der Masterthreadroutine für die Datenbankspiegelung mit folgender Ursache: %ls. Beheben Sie die Fehlerursache, und starten Sie den SQL Server-Dienst erneut.|  
  
## <a name="explanation"></a>Erklärung  
 Beim Starten des Spiegelungssteuerungsthreads ist ein Fehler aufgetreten.  
  
## <a name="user-action"></a>Benutzeraktion  
 Suchen Sie im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Fehlerprotokoll nach dem entsprechenden Fehler, der vor dieser Meldung angezeigt wurde. Beheben Sie die Fehlerursache, und starten Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienst (MSSQLSERVER) anschließend erneut.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten, Beenden, Anhalten, Fortsetzen und Neustarten der Datenbank-Engine, SQL Server-Agent oder des SQL Server-Browsers](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
  
