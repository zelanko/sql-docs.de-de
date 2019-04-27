---
title: 'Lektion 3: Eine vollständige Datenbanksicherung in den Windows Azure-Blob-Speicherdienst schreiben | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 454c8296-64e9-46ed-b141-5ebfbc8a4fe2
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 242e32b08ec6346c39e149628e773b33554c95d4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62653686"
---
# <a name="lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service"></a>Lektion 3: Schreiben Sie eine vollständige Datenbanksicherung in den Windows Azure-Blob-Speicherdienst
  In dieser Lektion wird erläutert, wie anhand der T-SQL-Anweisung eine vollständige Datenbanksicherung im Windows Azure-BLOB-Speicherdienst ausgeführt wird.  
  
## <a name="perform-a-full-database-backup-to-the-windows-azure-blob-storage-service"></a>Ausführen einer vollständigen Datenbanksicherung im Windows Azure-BLOB-Speicherdienst  
 Führen Sie die folgenden Schritte aus, um eine vollständige Datenbanksicherung zu erstellen:  
  
1.  Stellen Sie eine Verbindung mit [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]her.  
  
2.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit der [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]-Instanz her.  
  
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
  
  
