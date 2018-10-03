---
title: MSSQLSERVER_5554 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5554 (Database Engine error)
ms.assetid: 7134bbe5-d240-4a98-85ce-b13cc8ae9b0e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c3b8e4690b0e0c501fee26648cd9632fdcf28b1d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48066870"
---
# <a name="mssqlserver5554"></a>MSSQLSERVER_5554
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|MSSQLSERVER|  
|Ereignis-ID|5554|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|FS_MINIVER_OVERFLOW|  
|Meldungstext|Das maximale Limit des Dateisystems an Versionen insgesamt für eine einzige Datei wurde erreicht.|  
  
## <a name="explanation"></a>Erklärung  
 In MARS (Multiple Active Result Sets) oder Triggerszenarios verwendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Miniversion des Betriebssystems.  
  
## <a name="user-action"></a>Benutzeraktion  
 Versuchen Sie, wiederholte Datenupdates in derselben Transaktion zu vermeiden.  
  
  
