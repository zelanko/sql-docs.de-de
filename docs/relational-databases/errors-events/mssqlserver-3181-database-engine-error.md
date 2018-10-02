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
manager: craigg
ms.openlocfilehash: bcab7974c7cf997c57eacf79ccb03b4551e5a3f4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47688598"
---
# <a name="mssqlserver3181"></a>MSSQLSERVER_3181
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
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
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Wiederherstellen einer Datenbank an einem neuen Speicherort &#40;SQL Server&#41;](~/relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)  
[Wiederherstellen von Dateien an einem neuen Speicherort &#40;SQL Server&#41;](~/relational-databases/backup-restore/restore-files-to-a-new-location-sql-server.md)  
[RESTORE &#40;Transact-SQL&#41;](~/t-sql/statements/restore-statements-transact-sql.md)  
[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](~/t-sql/statements/restore-statements-verifyonly-transact-sql.md)  
  
