---
title: 'Lektion 4: Ausführen einer Wiederherstellung von einer vollständigen Datenbanksicherung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 580f76e6-9802-4abc-9043-db6de592c733
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: e239526f0a5e77ad57122e8e9ddbaa163f040827
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48162920"
---
# <a name="lesson-4-perform-a-restore-from-a-full-database-backup"></a>Lektion 4: Ausführen einer Wiederherstellung von einer vollständigen Datenbanksicherung
  In dieser Lektion wird veranschaulicht, wie mithilfe einer T-SQL-Anweisung eine Wiederherstellung von einer vollständigen Datenbanksicherung ausgeführt wird, die in der vorherigen Lektion erstellt wurde.  
  
## <a name="perform-a-restore-of-a-database-backup"></a>Ausführen einer Wiederherstellung von einer Datenbanksicherung  
 Führen Sie die folgenden Schritte aus, um eine vollständige Datenbanksicherung wiederherzustellen:  
  
1.  Herstellen einer Verbindung mit [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  In der **Objekt-Explorer**, eine Verbindung mit der Instanz [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
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
 [Tutorial: SQL Server-Sicherung und-Wiederherstellung im Windows Azure Blob Storage-Dienst](../relational-databases/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md).  
  
  
