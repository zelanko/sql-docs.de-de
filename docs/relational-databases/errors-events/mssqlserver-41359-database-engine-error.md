---
title: MSSQLSERVER_41359 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41359 (Database Engine error)
ms.assetid: 02b717c7-9170-4676-b0f6-4dec9eb5b5d4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b5372ffbeed279bf8c2c2f3adc8ad00dd8436fe3
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85765322"
---
# <a name="mssqlserver_41359"></a>MSSQLSERVER_41359
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Ereignis-ID|41359|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|SQL_READ_COMMITTED_SNAPSHOT_NOT_SUPPORTED|  
|Meldungstext|Eine Abfrage, die auf speicheroptimierte Tabellen mit der READ COMMITTED-Isolationsstufe zugreift, kann auf datenträgerbasierte Tabellen nicht zugreifen, wenn die Datenbankoption READ_COMMITTED_SNAPSHOT auf ON gesetzt ist. Geben Sie eine unterstützte Isolationsstufe für die speicheroptimierte Tabelle mithilfe eines Tabellentipps wie WITH (SNAPSHOT) an.|  
  
## <a name="explanation"></a>Erklärung  
Die Datenbank mit READ_COMMITTED_SNAPSHOT=ON unterstützt nicht die Transaktionen, die sowohl auf speicheroptimierte Tabellen als auch auf datenträgerbasierte Tabellen zugreifen.  
  
## <a name="user-action"></a>Benutzeraktion  
Setzen Sie READ_COMMITTED_SNAPSHOT auf OFF oder stellen Sie eine unterstützte Isolationsstufe für die speicheroptimierte Tabelle mithilfe eines Tipps auf Tabellenebene wie WITH (SNAPSHOT) bereit. Weitere Informationen finden Sie unter [In-Memory OLTP &#40;Arbeitsspeicheroptimierung&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>Weitere Informationen  
[In-Memory-OLTP &#40;Arbeitsspeicheroptimierung&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
