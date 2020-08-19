---
description: MSSQLSERVER_2596
title: MSSQLSERVER_2596 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2596 (Database Engine error)
ms.assetid: 49ab892f-8ba3-4ba1-b562-ddf205019802
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ce3ed3f225671a762ba6e39f958c6347f813076f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88410856"
---
# <a name="mssqlserver_2596"></a>MSSQLSERVER_2596
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
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
[ALTER DATABASE &#40;Transact-SQL&#41;](~/t-sql/statements/alter-database-transact-sql-set-options.md)  
  
