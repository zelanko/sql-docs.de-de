---
title: MSSQLSERVER_3431 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3431 (Database Engine error)
ms.assetid: 9541217f-e5c6-4a12-a19a-006058f1d3f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9b62047a25d71ca05dc3ab03651e5672353bc0a0
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85033551"
---
# <a name="mssqlserver_3431"></a>MSSQLSERVER_3431
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|3431|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|UNRESOLVED_XACT|  
|Meldungstext|Die '%.*ls'-Datenbank (Datenbank-ID %d) konnte aufgrund von nicht aufgelösten Transaktionsergebnissen nicht wiederhergestellt werden. MS DTC-Transaktionen (Microsoft Distributed Transaction Coordinator) wurden vorbereitet, aber MS DTC konnte die Auflösung nicht bestimmen. Zum Auflösen müssen Sie MS DTC reparieren, eine Wiederherstellung von einer vollständigen Sicherung ausführen oder die Datenbank reparieren.|  
  
## <a name="explanation"></a>Erklärung  
 Eine oder mehrere verteilte Transaktionen, für die MS DTC ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator) verwendet wurde, waren nicht abgeschlossen, als die Datenbank beendet wurde. Bei der Wiederherstellung dieser Datenbank sind Fehler aufgetreten, da die Transaktionen in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht abgeschlossen werden können bzw. ohne weitere Informationen von MS DTC kein Rollback für die Transaktionen ausgeführt werden kann.  
  
## <a name="user-action"></a>Benutzeraktion  
 Zum Wiederherstellen dieser Datenbank müssen Sie zunächst das Problem mit MS DTC lösen. Weitere Informationen zu diesem Problem mit MS DTC finden Sie in den Windows-Ereignisprotokollen. Wenn das Problem mit MS DTC nicht gelöst und die Datenbank nicht wiederhergestellt werden kann, führen Sie die Wiederherstellung einer Sicherungskopie der Datenbank aus.  
  
  
