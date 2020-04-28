---
title: 'Lektion 3: Schreiben einer vollständigen Datenbanksicherung in den Azure BLOB Storage-Dienst | Microsoft-Dokumentation'
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
ms.openlocfilehash: 1d5a749c61a3bc97de841e1149dd1539cbc990f2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "70153473"
---
# <a name="lesson-3-write-a-full-database-backup-to-the-azure-blob-storage-service"></a>Lektion 3: Schreiben einer vollständigen Datenbanksicherung in den Azure Blob Storage-Dienst
  Diese Lektion veranschaulicht die Verwendung der TQL-Anweisung zum Ausführen einer vollständigen Datenbanksicherung im Azure-BLOB-Speicherdienst.  
  
## <a name="perform-a-full-database-backup-to-the-azure-blob-storage-service"></a>Ausführen einer vollständigen Datenbanksicherung für den Azure BLOB Storage-Dienst  
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
 [Lektion 4: Ausführen einer Wiederherstellung aus einer vollständigen Datenbanksicherung](../../2014/tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md)  
  
  
