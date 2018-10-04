---
title: 'Lektion 3: Schreiben eine vollständigen Datenbanksicherung in den Windows Azure-Blob-Speicherdienst | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 454c8296-64e9-46ed-b141-5ebfbc8a4fe2
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: f0de77c43dc2a18bbbb4496f6c1d1c3aab21de96
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48172270"
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
  
  
