---
title: MSSQLSERVER_3156 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3156 (Database Engine error)
ms.assetid: 345d8ed4-177e-4ec3-bab3-25d30000e323
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5480f60c6bb47f5e2c0a03236da30a7dada30209
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85723732"
---
# <a name="mssqlserver_3156"></a>MSSQLSERVER_3156
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
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
[Wiederherstellen einer Datenbank an einem neuen Speicherort &#40;SQL Server&#41;](~/relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)  
[Wiederherstellen von Dateien an einem neuen Speicherort &#40;SQL Server&#41;](~/relational-databases/backup-restore/restore-files-to-a-new-location-sql-server.md)  
[RESTORE &#40;Transact-SQL&#41;](~/t-sql/statements/restore-statements-transact-sql.md)  
  
