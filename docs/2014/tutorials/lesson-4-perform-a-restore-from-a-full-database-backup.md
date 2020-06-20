---
title: 'Lektion 4: Ausführen einer Wiederherstellung aus einer vollständigen Datenbanksicherung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 580f76e6-9802-4abc-9043-db6de592c733
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 139c6ff36e37532f6704a346a44a2e1d40d91087
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85063930"
---
# <a name="lesson-4-perform-a-restore-from-a-full-database-backup"></a>Lektion 4: Ausführen einer Wiederherstellung aus einer vollständigen Datenbanksicherung
  In dieser Lektion wird veranschaulicht, wie mithilfe einer T-SQL-Anweisung eine Wiederherstellung von einer vollständigen Datenbanksicherung ausgeführt wird, die in der vorherigen Lektion erstellt wurde.  
  
## <a name="perform-a-restore-of-a-database-backup"></a>Ausführen einer Wiederherstellung von einer Datenbanksicherung  
 Führen Sie die folgenden Schritte aus, um eine vollständige Datenbanksicherung wiederherzustellen:  
  
1.  Stellen Sie eine Verbindung mit [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]her.  
  
2.  Stellen Sie im **Objekt-Explorer**eine Verbindung mit der [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]-Instanz her.  
  
3.  Klicken Sie auf der Standardmenüleiste auf **Neue Abfrage**.  
  
4.  Kopieren Sie das folgende Beispiel in das Abfragefenster, und ändern Sie es nach Bedarf.  
  
    ```  
    RESTORE DATABASE AdventureWorks2012   
    FROM URL = 'https://mystorageaccount.blob.core.windows.net/privatecontainertest/AdventureWorks2012.bak'   
    WITH CREDENTIAL = 'mycredential';  
    , STATS = 5 - use this to see monitor the progress  
    GO  
  
    ```  
  
5.  Überprüfen Sie die T-SQL-Anweisung, und klicken Sie auf **Ausführen**.  
  
### <a name="return-to-tutorials-portal"></a>Zurück zum Portal für die Lernprogramme  
 [Tutorial: SQL Server sichern und Wiederherstellen Azure BLOB Storage Dienstanbieter](../relational-databases/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md).  
  
  
