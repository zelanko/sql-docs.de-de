---
title: MSSQLSERVER_845 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 845 (Database Engine error)
ms.assetid: 8fff6ad4-234c-44be-b123-e25d5e1cd63e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9d98be02727582d4f9201ec7f47c3cdb8db5a56b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62761928"
---
# <a name="mssqlserver_845"></a>MSSQLSERVER_845
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|845|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|BUFLATCH_TIMEOUT|  
|Meldungstext|Timeout beim Warten auf Pufferlatchtyp %d für Seite %S_PGID, Datenbank-ID %d.|  
  
## <a name="explanation"></a>Erklärung  
 Ein Prozess hat auf die Beschaffung eines Latchs gewartet, aber für den Prozess wurde so lange gewartet, bis das Zeitlimit abgelaufen und die Beschaffung nicht mehr möglich war. Dies kann auftreten, wenn das Ausführen eines E/A-Vorgangs zu lange dauert, was normalerweise daraus resultiert, dass Systemprozesse durch andere Tasks blockiert werden. In manchen Fällen kann dieser Fehler auch das Ergebnis eines Hardwarefehlers sein.  
  
## <a name="user-action"></a>Benutzeraktion  
 Durch folgende Aktionen kann dieser Fehler verhindert werden:  
  
-   Reduzieren Sie die Arbeitsauslastung.  
  
-   Überprüfen Sie, ob zugehörige E/A-Fehler im Fehlerprotokoll oder Ereignisprotokoll vorhanden sind. E/A-Fehler werden typischerweise durch Datenträgerfehler verursacht.  
  
-   Überprüfen Sie das Fehlerprotokoll auf Tasks, die kein Ergebnis bereitstellen, sowie auf andere kritische Fehler.  
  
-   Wenn kritische Fehler, z. B. Assert-Vorgänge, häufig auftreten, beheben Sie diese Probleme.  
  
 Wenn der Fehler wiederholt auftritt, wenden Sie sich an den Microsoft-Kundendienst und -Support.  
  
  
