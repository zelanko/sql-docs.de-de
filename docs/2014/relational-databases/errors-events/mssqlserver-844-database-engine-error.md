---
title: MSSQLSERVER_844 | Microsoft Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 844 (Database Engine error)
ms.assetid: 2060c886-1226-4066-bc0c-de90a1cfb82b
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 78c0cd8e07097f6ca0d27bfe50c271c8661fbc98
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37421839"
---
# <a name="mssqlserver844"></a>MSSQLSERVER_844
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|844|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|BUFLATCH_TIMEOUT_CONTINUE|  
|Meldungstext|Timeout beim Warten auf einen Pufferlatch -- Typ %d, Pufferpool %p, Seite %d:%d, STAT %#x, Datenbank-ID %d, Zuordnungseinheits-ID: %I64d%ls, Task 0x%p : %d, Wartezeit %d, Flags 0x%I64x, besitzender Task 0x%p.  Der Wartevorgang wird fortgesetzt.|  
  
## <a name="explanation"></a>Erklärung  
 Ein Prozess wartet darauf, einen Latch abzurufen. Das Problem kann dadurch verursacht werden, dass ein E/A-Vorgang zu viel Zeit beansprucht, bevor er abgeschlossen wird. Normalerweise ist der Fehler das Ergebnis des Blockierens von Systemprozessen durch andere Tasks. In manchen Fällen kann dieser Fehler auch das Ergebnis eines Hardwarefehlers sein.  
  
## <a name="user-action"></a>Benutzeraktion  
 Versuchen Sie Folgendes, um zu verhindern, dass der Fehler erneut auftritt:  
  
-   Reduzieren Sie die Arbeitsauslastung.  
  
-   Führen Sie eine Überprüfung auf zugehörige E/A-Fehler im Fehlerprotokoll oder Ereignisprotokoll aus. E/A-Fehler deuten normalerweise auf eine Datenträgerfehlfunktion hin.  
  
-   Überprüfen Sie das Fehlerprotokoll auf Tasks, die kein Ergebnis bereitstellen, sowie auf andere kritische Fehler.  
  
-   Wenn kritische Fehler, z. B. Assert-Vorgänge, häufig auftreten, beheben Sie diese Probleme.  
  
 Wenn der Fehler wiederholt auftritt, wenden Sie sich an den Microsoft-Kundendienst und -Support.  
  
  
