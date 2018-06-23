---
title: 'Lektion 3: Schreiben eine vollständigen Datenbanksicherung im Windows Azure-Blob-Speicherdienst | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 454c8296-64e9-46ed-b141-5ebfbc8a4fe2
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cec916094b297baa648b743b2c5649ee4fced1c8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151024"
---
# <a name="lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service"></a>Lektion 3: Schreiben einer vollständigen Datenbanksicherung in den Windows Azure-BLOB-Speicherdienst
  In dieser Lektion wird erläutert, wie anhand der T-SQL-Anweisung eine vollständige Datenbanksicherung im Windows Azure-BLOB-Speicherdienst ausgeführt wird.  
  
## <a name="perform-a-full-database-backup-to-the-windows-azure-blob-storage-service"></a>Ausführen einer vollständigen Datenbanksicherung im Windows Azure-BLOB-Speicherdienst  
 Führen Sie die folgenden Schritte aus, um eine vollständige Datenbanksicherung zu erstellen:  
  
1.  Herstellen einer Verbindung mit [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  In der **Objektexplorer**, Herstellen einer Verbindung mit der Instanz von [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
3.  Klicken Sie auf der Standardmenüleiste auf **Neue Abfrage**.  
  
4.  Kopieren Sie das folgende Beispiel, und fügen Sie es in das Abfragefenster ein, ändern Sie das Beispiel ggf., und klicken Sie auf **Ausführen**.  
  
    ```  
    BACKUP DATABASE[AdventureWorks2012]   
    TO URL = 'https://mystorageaccount.blob.core.windows.net/privatecontainertest/AdventureWorks2012.bak'   
    /* URL includes the endpoint for the BLOB service, followed by the container name, and the name of the backup file*/   
    WITH CREDENTIAL = 'mycredential';  
    /* name of the credential you created in the previous step */   
    GO  
  
    ```  
  
5.  Stellen Sie im Objekt-Explorer eine Verbindung mit dem Azure-Speicher her. Navigieren Sie zum Container und den neu erstellten Sicherungsdateien.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 4: Ausführen einer Wiederherstellung von einer vollständigen Datenbanksicherung](../../2014/tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md).  
  
  