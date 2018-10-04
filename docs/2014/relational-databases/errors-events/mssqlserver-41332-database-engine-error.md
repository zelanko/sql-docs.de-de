---
title: MSSQLSERVER_41332 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41332 (Database Engine error)
ms.assetid: d3403c3e-d178-4006-b6c9-c18609562db5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0bbd8b256145a9d91e8615aaf7d87a4b8ce7b8b7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48211560"
---
# <a name="mssqlserver41332"></a>MSSQLSERVER_41332
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Ereignis-ID|41332|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SQL_SNAPSHOT_NOT_SUPPORTED|  
|Meldungstext|Wenn der TRANSACTION ISOLATION LEVEL der Sitzung auf SNAPSHOT festgelegt ist, kann nicht auf speicheroptimierte Tabellen und systemintern kompilierte gespeicherte Prozeduren zugegriffen werden, und diese können nicht erstellt werden.|  
  
## <a name="explanation"></a>Erklärung  
 Die Transaktion wurde auf der Momentaufnahmeisolationsstufe gestartet, und anschließend wurde versucht, eine nicht kompatible Funktion zu verwenden.  
  
## <a name="user-action"></a>Benutzeraktion  
 Starten Sie die Transaktion mit einer anderen Isolationsstufe. Weitere Informationen finden Sie unter [In-Memory OLTP &#40;Arbeitsspeicheroptimierung&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Siehe auch  
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
