---
title: MSSQLSERVER_41332 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41332 (Database Engine error)
ms.assetid: d3403c3e-d178-4006-b6c9-c18609562db5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6a0ae51ca0aea57f454446301f0e624298f146e5
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85694278"
---
# <a name="mssqlserver_41332"></a>MSSQLSERVER_41332
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Ereignis-ID|41332|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SQL_SNAPSHOT_NOT_SUPPORTED|  
|Meldungstext|Wenn der TRANSACTION ISOLATION LEVEL der Sitzung auf SNAPSHOT festgelegt ist, kann nicht auf speicheroptimierte Tabellen und systemintern kompilierte gespeicherte Prozeduren zugegriffen werden, und diese können nicht erstellt werden.|  
  
## <a name="explanation"></a>Erklärung  
Die Transaktion wurde auf der Momentaufnahmeisolationsstufe gestartet, und anschließend wurde versucht, eine nicht kompatible Funktion zu verwenden.  
  
## <a name="user-action"></a>Benutzeraktion  
Starten Sie die Transaktion mit einer anderen Isolationsstufe. Weitere Informationen finden Sie unter [In-Memory OLTP &#40;Arbeitsspeicheroptimierung&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
