---
title: MSSQLSERVER_41365 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41365 (Database Engine error)
ms.assetid: 4fc7ec15-b722-4e3d-b7f9-3d39d171e96e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3d5120e9c02d3bbb1cae211e3deb584e982294bd
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85053921"
---
# <a name="mssqlserver_41365"></a>MSSQLSERVER_41365
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Ereignis-ID|41365|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|HK_MERGE_SCHEDULE_ERROR|  
|Meldungstext|Mergeanforderung für Transaktionsbereich [%ld, %ld] in Datenbank %.*ls wurde nicht geplant. Die Prüfpunktdateien, die den Bereich darstellen, sind entweder für Merge oder als Teil eines laufenden Mergevorgangs nicht verfügbar.|  
  
## <a name="explanation"></a>Erklärung  
 Die Prüfpunktdateien, die den Bereich darstellen, sind entweder für Merge oder als Teil eines laufenden Mergevorgangs nicht verfügbar.  
  
## <a name="user-action"></a>Benutzeraktion  
 Stellen Sie einen besseren Transaktionsbereich für den Merge-/Wartevorgang bereit, bevor Sie erneut die gleiche Anforderung ausgeben. Weitere Informationen finden Sie unter [In-Memory OLTP &#40;Arbeitsspeicheroptimierung&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
