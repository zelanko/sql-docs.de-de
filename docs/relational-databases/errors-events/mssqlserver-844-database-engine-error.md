---
title: MSSQLSERVER_844 | Microsoft Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 844 (Database Engine error)
ms.assetid: 2060c886-1226-4066-bc0c-de90a1cfb82b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bdc05bbc2cf4db3875149ed35ac82dd922800484
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85767820"
---
# <a name="mssqlserver_844"></a>MSSQLSERVER_844
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|SQL Server|  
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
  
