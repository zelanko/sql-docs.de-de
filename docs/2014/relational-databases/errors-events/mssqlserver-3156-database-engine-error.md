---
title: MSSQLSERVER_3156 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3156 (Database Engine error)
ms.assetid: 345d8ed4-177e-4ec3-bab3-25d30000e323
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2b1c972481b7c4cf614cf0a91b29247c643696d2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62868924"
---
# <a name="mssqlserver_3156"></a>MSSQLSERVER_3156
    
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Produktname|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Ereignis-ID|3156|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|LDDB_CANT_WRITE|  
|Meldungstext|Die Datei '%ls' kann nicht in '%ls' wiederhergestellt werden. Verwenden Sie WITH MOVE, um einen gültigen Speicherort für die Datei zu identifizieren.|  
  
## <a name="explanation"></a>Erklärung  
 Mit dieser allgemeinen Meldung werden die logischen oder physischen Dateinamen der Dateien angegeben, die aufgrund eines Problems mit dem angegebenen Speicherort nicht wiederhergestellt werden konnten.  
  
### <a name="possible-causes"></a>Mögliche Ursachen  
 Die folgenden Ursachen sind möglich:  
  
-   Möglicherweise müssen Sie auf das angegebene Windows-Verzeichnis zugreifen.  
  
-   Möglicherweise haben Sie den Pfad falsch eingegeben, oder Sie haben einen Pfad angegeben, der nicht vorhanden ist.  
  
-   Der Dateiname wird möglicherweise für eine Datei verwendet, die nicht überschrieben werden kann.  
  
## <a name="user-action"></a>Benutzeraktion  
 Suchen Sie in den Fehlerprotokollen nach anderen Meldungen, in denen weitere Details angegeben werden.  
  
 Beheben Sie das Problem mit dem angegebenen Speicherort beispielsweise durch das Gewähren von Zugriff, oder verwenden Sie die Option WITH MOVE in Ihrer RESTORE-Anweisung, um die Datei zu verschieben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Wiederherstellen einer Datenbank an einem neuen Speicherort &#40;SQL Server&#41;](../backup-restore/restore-a-database-to-a-new-location-sql-server.md)   
 [Wiederherstellen von Dateien an einem neuen Speicherort &#40;SQL Server&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
