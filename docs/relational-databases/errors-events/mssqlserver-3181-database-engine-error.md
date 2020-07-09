---
title: MSSQLSERVER_3181 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3181 (Database Engine error)
ms.assetid: e6d2e716-5263-477c-ad0e-7bcbfef4c1f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2201c81cfc4d4f5f31fb3ab107262d0825274858
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85723681"
---
# <a name="mssqlserver_3181"></a>MSSQLSERVER_3181
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Details  
  
| attribute | Wert |  
| :-------- | :---- |  
|Produktname|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Ereignis-ID|3181|  
|Ereignisquelle|MSSQLSERVER|  
|Komponente|SQLEngine|  
|Symbolischer Name|LDDB_STORAGE_VERIFY|  
|Meldungstext|Beim Wiederherstellen dieser Sicherung können Speicherplatzprobleme auftreten. Nachfolgende Meldungen enthalten weitere Informationen.|  
  
## <a name="explanation"></a>Erklärung  
Mit der RESTORE VERIFYONLY-Anweisung wird der verfügbare Speicherplatz auf dem Datenträger geprüft, auf dem die Datenbank wiederhergestellt werden soll.  
  
### <a name="possible-causes"></a>Mögliche Ursachen  
Möglicherweise reicht der verfügbare Speicherplatz für die Wiederherstellung der zu prüfenden Sicherung nicht aus.  
  
## <a name="user-action"></a>Benutzeraktion  
Stellen Sie die Sicherung an einem Speicherort mit ausreichendem Speicherplatz wieder her, oder stellen Sie auf dem Datenträger mehr Speicherplatz bereit.  
  
## <a name="see-also"></a>Weitere Informationen  
[Wiederherstellen einer Datenbank an einem neuen Speicherort &#40;SQL Server&#41;](~/relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)  
[Wiederherstellen von Dateien an einem neuen Speicherort &#40;SQL Server&#41;](~/relational-databases/backup-restore/restore-files-to-a-new-location-sql-server.md)  
[RESTORE &#40;Transact-SQL&#41;](~/t-sql/statements/restore-statements-transact-sql.md)  
[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](~/t-sql/statements/restore-statements-verifyonly-transact-sql.md)  
  
