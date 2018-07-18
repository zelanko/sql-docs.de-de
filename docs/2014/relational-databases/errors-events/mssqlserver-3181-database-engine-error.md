---
title: MSSQLSERVER_3181 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 3181 (Database Engine error)
ms.assetid: e6d2e716-5263-477c-ad0e-7bcbfef4c1f3
caps.latest.revision: 13
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7fdd37c8c79abb36aea4892d55ef8346af28eedb
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37414439"
---
# <a name="mssqlserver3181"></a>MSSQLSERVER_3181
    
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
  
## <a name="see-also"></a>Siehe auch  
 [Wiederherstellen einer Datenbank an einem neuen Speicherort &#40;SQL Server&#41;](../backup-restore/restore-a-database-to-a-new-location-sql-server.md)   
 [Wiederherstellen von Dateien auf einem neuen Speicherort &#40;SQLServer&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)   
 [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)  
  
  
