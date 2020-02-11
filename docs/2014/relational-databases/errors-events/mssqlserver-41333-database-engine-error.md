---
title: MSSQLSERVER_41333 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41333 (Database Engine error)
ms.assetid: c3c3ae9a-1e4c-4de6-ba72-2f393375b053
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ab94977bcd3bf5a9b0b26ac7be76cb67d58e0755
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62913986"
---
# <a name="mssqlserver_41333"></a>MSSQLSERVER_41333
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Ereignis-ID|41333|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|CROSS_CONTAINER_ISOLATION_FAILURE|  
|Meldungstext|Die folgenden Transaktionen müssen auf speicheroptimierte Tabellen und systemintern kompilierte gespeicherte Prozeduren unter Momentaufnahmeisolation zugreifen: RepeatableRead-Transaktionen, serialisierbare Transaktionen und Transaktionen, die auf Tabellen zugreifen, die nicht in der RepeatableRead- oder serialisierbaren Isolationsstufe speicheroptimiert sind.|  
  
## <a name="explanation"></a>Erklärung  
 Es gibt Einschränkungen für den Benutzer der höheren Isolationsstufen zwischen datenträgerbasierten Transaktionen und XTP-Transaktionen.  
  
## <a name="user-action"></a>Benutzeraktion  
 Versuchen Sie nicht, Isolationsvorgänge auf hoher Ebene in speicheroptimierten Tabellen (und systemintern kompilierten Prozeduren) und datenträgerbasierten Tabellen durchzuführen.  
  
 Weitere Informationen finden Sie unter [In-Memory OLTP &#40;Arbeitsspeicheroptimierung&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
