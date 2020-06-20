---
title: MSSQLSERVER_2596 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2596 (Database Engine error)
ms.assetid: 49ab892f-8ba3-4ba1-b562-ddf205019802
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 27b2ceed40274df4ba57c4d61a83fbc60b6a7f80
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85034053"
---
# <a name="mssqlserver_2596"></a>MSSQLSERVER_2596
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|SQL Server|  
|Ereignis-ID|2596|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|DBCC_DATABASE_IN_READ_ONLY_MODE|  
|Meldungstext|Die REPAIR-Anweisung wurde nicht verarbeitet. Die Datenbank kann nicht im schreibgeschützten Modus sein.|  
  
## <a name="explanation"></a>Erklärung  
 Diese Meldung gibt an, dass sich die Datenbank im schreibgeschützten Modus befindet. Reparaturen sind nicht möglich, wenn sich eine Datenbank im schreibgeschützten Modus befindet.  
  
## <a name="user-action"></a>Benutzeraktion  
 Legen Sie die Datenbank mithilfe der ALTER DATABASE-Anweisung auf Lese-/Schreibzugriff fest, und führen Sie anschließend den DBCC-Befehl erneut aus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)  
  
  
