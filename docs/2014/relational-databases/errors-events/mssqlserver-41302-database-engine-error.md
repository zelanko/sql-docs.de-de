---
title: MSSQLSERVER_41302 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41302 (Database Engine error)
ms.assetid: 01e75618-afec-4232-ba68-93ab7bc31003
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2808c76867092777a50cd56b917b8431e5dabe2a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62867924"
---
# <a name="mssqlserver_41302"></a>MSSQLSERVER_41302
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Ereignis-ID|41302|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|WRITE_WRITE_CONFLICT|  
|Meldungstext|Für die aktuelle Transaktion wurde versucht, einen Datensatz zu aktualisieren, der aktualisiert wurde, nachdem diese Transaktion gestartet wurde. Die Transaktion wurde abgebrochen.|  
  
## <a name="explanation"></a>Erklärung  
 Bei der Transaktion trat ein Schreibkonflikt auf und die Anweisung wurde beendet.  
  
## <a name="user-action"></a>Benutzeraktion  
 Wiederholen Sie den Vorgang später in einer anderen Transaktion. Weitere Informationen finden Sie unter [In-Memory OLTP &#40;Arbeitsspeicheroptimierung&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
