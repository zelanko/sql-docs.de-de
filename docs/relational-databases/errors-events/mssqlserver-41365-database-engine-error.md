---
title: MSSQLSERVER_41365 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 41365 (Database Engine error)
ms.assetid: 4fc7ec15-b722-4e3d-b7f9-3d39d171e96e
caps.latest.revision: 7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 119d582ed78fabbf8169b9d5db2ee93bdcbf5823
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2018
ms.locfileid: "34318947"
---
# <a name="mssqlserver41365"></a>MSSQLSERVER_41365
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
Stellen Sie einen besseren Transaktionsbereich für den Merge-/Wartevorgang bereit, bevor Sie erneut die gleiche Anforderung ausgeben. Weitere Informationen finden Sie unter [In-Memory OLTP &#40;Arbeitsspeicheroptimierung&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
