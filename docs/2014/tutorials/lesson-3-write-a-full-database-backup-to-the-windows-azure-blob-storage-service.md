---
title: 'Lektion 3: Schreiben eine vollständigen Datenbanksicherung in den Windows Azure-Blob-Speicherdienst | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 454c8296-64e9-46ed-b141-5ebfbc8a4fe2
caps.latest.revision: 9
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 4a28465f0175be0bfc12e5c9d51a267ae6597ec6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37236080"
---
# <a name="lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service"></a>Lektion 3: Schreiben einer vollständigen Datenbanksicherung in den Windows Azure-BLOB-Speicherdienst
  In dieser Lektion wird erläutert, wie anhand der T-SQL-Anweisung eine vollständige Datenbanksicherung im Windows Azure-BLOB-Speicherdienst ausgeführt wird.  
  
## <a name="perform-a-full-database-backup-to-the-windows-azure-blob-storage-service"></a>Ausführen einer vollständigen Datenbanksicherung im Windows Azure-BLOB-Speicherdienst  
 Führen Sie die folgenden Schritte aus, um eine vollständige Datenbanksicherung zu erstellen:  
  
1.  Herstellen einer Verbindung mit [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  In der **Objekt-Explorer**, eine Verbindung mit der Instanz [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
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
  
  
