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
ms.openlocfilehash: fde7bbf3e3db95f75606a7b735eef41b7b6abf2b
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86552306"
---
# <a name="mssqlserver_1401"></a>MSSQLSERVER_1401
    
## <a name="details"></a>Details  
  
|attribute|Wert|  
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
  
  
