---
title: MSSQLSERVER_17883 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17883 (Database Engine error)
ms.assetid: adaf1c04-e397-4a69-90b8-9353a37277ea
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2f9f712ed8d37872c90eff773e81a657fb96c296
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62915269"
---
# <a name="mssqlserver_17883"></a>MSSQLSERVER_17883
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|17883|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SRV_SCHEDULER_NONYIELDING|  
|Meldungstext|Prozess %ld:%ld:%ld (0x%lx) Arbeitsthread 0x%p stellt im Zeitplanungsmodul %ld kein Ergebnis bereit. Threaderstellungszeit: %I64d. Ungefähre Thread-CPU-Belegung: Kernel %I64d Millisek., Benutzer %I64d Millisek. Prozessnutzung %d%%. Leerlauf des Systems: %d%%. Intervall: % I64d Millisek.|  
  
## <a name="explanation"></a>Erklärung  
 Kennzeichnet ein mögliches Problem mit einem Thread, der in einem Zeitplanungsmodul kein Ergebnis bereitstellt.  Die Ursache könnte ein Programmfehler in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sein. Das Problem kann auch dadurch verursacht werden, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht genug Zyklen für die Ausführung abruft.  Dieser Fehler könnte behoben werden, wenn der Thread Ergebnisse bereitstellt.  
  
## <a name="user-action"></a>Benutzeraktion  
 Bei übermäßiger Last im System reduzieren Sie die Last, wenden Sie sich andernfalls an Microsoft Support Services.  
  
  
