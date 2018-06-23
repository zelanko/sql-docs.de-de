---
title: 'Lektion 4: Ausführen einer Wiederherstellung von einer vollständigen Datenbanksicherung | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 580f76e6-9802-4abc-9043-db6de592c733
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8869fa4bba6050dd0c15b8b59b7f2d091902936f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047069"
---
# <a name="lesson-4-perform-a-restore-from-a-full-database-backup"></a>Lektion 4: Ausführen einer Wiederherstellung von einer vollständigen Datenbanksicherung
  In dieser Lektion wird veranschaulicht, wie mithilfe einer T-SQL-Anweisung eine Wiederherstellung von einer vollständigen Datenbanksicherung ausgeführt wird, die in der vorherigen Lektion erstellt wurde.  
  
## <a name="perform-a-restore-of-a-database-backup"></a>Ausführen einer Wiederherstellung von einer Datenbanksicherung  
 Führen Sie die folgenden Schritte aus, um eine vollständige Datenbanksicherung wiederherzustellen:  
  
1.  Herstellen einer Verbindung mit [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  In der **Objektexplorer**, Herstellen einer Verbindung mit der Instanz von [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
3.  Klicken Sie auf der Standardmenüleiste auf **Neue Abfrage**.  
  
4.  Kopieren Sie das folgende Beispiel in das Abfragefenster, und ändern Sie es nach Bedarf.  
  
    ```  
    RESTORE DATABASE AdventureWorks2012   
    FROM URL = 'https://mystorageaccount.blob.core.windows.net/privatecontainertest/AdventureWorks2012.bak'   
    WITH CREDENTIAL = 'mycredential';  
    , STATS = 5 – use this to see monitor the progress  
    GO  
  
    ```  
  
5.  Überprüfen Sie die T-SQL-Anweisung, und klicken Sie auf **Ausführen**.  
  
### <a name="return-to-tutorials-portal"></a>Zurück zum Portal für die Lernprogramme  
 [Lernprogramm: SQL Server-Sicherung und-Wiederherstellung im Windows Azure Blob-Speicherdienst](../relational-databases/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md).  
  
  