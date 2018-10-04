---
title: MSSQLSERVER_125 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- "125"
helpviewer_keywords:
- 125 (Database Engine error)
ms.assetid: 0f58338d-2ea0-48b8-8a20-c438b0940433
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8287572d31dc136f21717ba45b730936b4fb78ae
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48088390"
---
# <a name="mssqlserver125"></a>MSSQLSERVER_125
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|125|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name||  
|Meldungstext|CASE-Ausdrücke können nur bis zu %d Ebenen geschachtelt werden.|  
  
## <a name="explanation"></a>Erklärung  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist für CASE-Ausdrücke nur eine Schachtelung von 10 Ebenen zulässig.  
  
## <a name="user-action"></a>Benutzeraktion  
 Reduzieren Sie die Anzahl der Ebenen von CASE-Anweisungen auf 10 oder weniger.  
  
## <a name="see-also"></a>Siehe auch  
 [CASE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/case-transact-sql)  
  
  
