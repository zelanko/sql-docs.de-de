---
title: 'Lektion 2: Erstellen von SQL Server-Anmeldeinformationen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 64f8805c-1ddc-4c96-a47c-22917d12e1ab
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 9bac1f166472fa6f4285779f2054d7121133693f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48194570"
---
# <a name="lesson-2-create-a-sql-server-credential"></a>Lektion 2: Erstellen von SQL Server-Anmeldeinformationen
  **Anmeldeinformationen:** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Anmeldeinformationen sind ein Objekt zum Speichern von Authentifizierungsinformationen, die für die Verbindung mit einer Ressource außerhalb von SQL Server erforderlich sind.  Hier [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -sicherungs-und Wiederherstellungsvorgängen Anmeldeinformationen verwenden, um in den Windows Azure-Blob-Speicherdienst zu authentifizieren. In den Anmeldeinformationen werden der Name des Speicherkontos und der **Zugriffsschlüssel** des Speicherkontos gespeichert. Sobald die Anmeldeinformationen erstellt wurden, müssen sie beim Ausgeben der BACKUP-/RESTORE-Anweisungen in der WITH CREDENTIAL-Option angegeben werden. Weitere Informationen zum Anzeigen, Kopieren oder erneuten Generieren von **access keys**für Speicherkonten finden Sie unter [Zugriffsschlüssel für Speicherkonten](http://msdn.microsoft.com/library/windowsazure/hh531566.aspx).  
  
 Allgemeine Informationen zu Anmeldeinformationen finden Sie unter [Anmeldeinformationen](../relational-databases/security/authentication-access/credentials-database-engine.md).  
  
 Informationen für andere Beispiele, wo Anmeldeinformationen verwendet werden, finden Sie unter [Erstellen eines SQL Server-Agent-Proxys](../ssms/agent/create-a-sql-server-agent-proxy.md).  
  
> [!IMPORTANT]  
>  Die Anforderungen zum Erstellen einer SQL Server-Anmeldeinformationen, die unten beschriebenen sind spezifisch für SQL Server Sicherungsprozesse ([SQL Server Backup to URL](../relational-databases/backup-restore/sql-server-backup-to-url.md), und [SQL Server Managed Backup to Windows Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)). SQL Server verwendet beim Zugriff auf Azure-Speicher zum Schreiben oder Lesen von Sicherungen den Namen des Speicherkontos und Informationen zu den Zugriffsschlüsseln.  Weitere Informationen zum Erstellen von Anmeldeinformationen für das Speichern von Datenbankdateien im Azure-Speicher finden Sie unter [Lektion 3: Erstellen von SQL Server-Anmeldeinformationen](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)  
  
## <a name="create-a-sql-server-credential"></a>Erstellen von SQL Server-Anmeldeinformationen  
 Führen Sie die folgenden Schritte aus, um SQL Server-Anmeldeinformationen zu erstellen:  
  
1.  Stellen Sie eine Verbindung mit SQL Server Management Studio her.  
  
2.  Stellen Sie im Objekt-Explorer eine Verbindung mit der Instanz der Datenbank-Engine her, auf der die Datenbank AdventureWorks2012 installiert ist, oder verwenden Sie Ihre eigene Datenbank für dieses Lernprogramm.  
  
3.  Klicken Sie auf der **Standardsymbolleiste** auf **Neue Abfrage**.  
  
4.  Kopieren Sie das folgende Beispiel in das Abfragefenster, und ändern Sie es nach Bedarf.  
  
    ```  
    CREATE CREDENTIAL mycredential   
    WITH IDENTITY= 'mystorageaccount' – this is the name of the storage account you specified when creating a storage account (See Lesson 1)   
    , SECRET = '<storage account access key>' – this should be either the Primary or Secondary Access Key for the storage account (See Lesson 1)  
  
    ```  
  
     ![Zuordnen des Speicherkontos zu Sql-Anmeldeinformationen](../../2014/tutorials/media/backuptocloud-storage-credential-mapping.gif "Zuordnen des Speicherkontos zu Sql-Anmeldeinformationen")  
  
5.  Überprüfen Sie die T-SQL-Anweisung, und klicken Sie auf **Ausführen**.  
  
 Weitere Informationen zu den Windows Azure-Blob-Speicherdienst und sicherungskonzepten und Anforderungen, finden Sie unter [SQL Server-Sicherung und-Wiederherstellung mit dem Windows Azure-Blob-Speicherdienst](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
### <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 3: Schreiben eine vollständigen Datenbanksicherung in den Windows Azure-Blob-Speicherdienst](../../2014/tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md).  
  
  
