---
title: 'Lektion 2: Erstellen eines SQL Server Anmelde Informationen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
ms.assetid: 64f8805c-1ddc-4c96-a47c-22917d12e1ab
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: baa337d33173f292145d92b60d6192af2a716c5e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "70154329"
---
# <a name="lesson-2-create-a-sql-server-credential"></a>Lektion 2: Erstellen von SQL Server-Anmeldeinformationen
  Anmelde Informationen **:** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Anmelde Informationen sind ein Objekt zum Speichern von Authentifizierungsinformationen, die zum Herstellen einer Verbindung mit einer Ressource außerhalb von SQL Server erforderlich sind.  Hier werden [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] von Sicherungs-und Wiederherstellungs Prozessen Anmelde Informationen für die Authentifizierung beim Azure BLOB Storage-Dienst verwendet. In den Anmeldeinformationen werden der Name des Speicherkontos und der **Zugriffsschlüssel** des Speicherkontos gespeichert. Sobald die Anmeldeinformationen erstellt wurden, müssen sie beim Ausgeben der BACKUP-/RESTORE-Anweisungen in der WITH CREDENTIAL-Option angegeben werden. Weitere Informationen zum Anzeigen, Kopieren oder erneuten Generieren von **access keys**für Speicherkonten finden Sie unter [Zugriffsschlüssel für Speicherkonten](https://msdn.microsoft.com/library/windowsazure/hh531566.aspx).  
  
 Allgemeine Informationen zu Anmelde Informationen finden Sie unter [Anmelde](../relational-databases/security/authentication-access/credentials-database-engine.md)Informationen.  
  
 Informationen zu anderen Beispielen, in denen Anmelde Informationen verwendet werden, finden Sie unter [Erstellen eines SQL Server-Agent Proxys](../ssms/agent/create-a-sql-server-agent-proxy.md).  
  
> [!IMPORTANT]  
>  Die Anforderungen für das Erstellen einer SQL Server Anmelde Informationen, die unten beschrieben werden, gelten speziell für SQL Server Sicherungs Prozesse ([SQL Server URL-Sicherung](../relational-databases/backup-restore/sql-server-backup-to-url.md)und [SQL Server verwaltete Sicherung in Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)). SQL Server verwendet beim Zugriff auf Azure-Speicher zum Schreiben oder Lesen von Sicherungen den Namen des Speicherkontos und Informationen zu den Zugriffsschlüsseln.  Weitere Informationen zum Erstellen von Anmeldeinformationen für das Speichern von Datenbankdateien in Azure-Speicher finden Sie unter [Lesson 3: Create a SQL Server Credential](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)  
  
## <a name="create-a-sql-server-credential"></a>Erstellen von SQL Server-Anmeldeinformationen  
 Führen Sie die folgenden Schritte aus, um SQL Server-Anmeldeinformationen zu erstellen:  
  
1.  Stellen Sie eine Verbindung mit SQL Server Management Studio her.  
  
2.  Stellen Sie im Objekt-Explorer eine Verbindung mit der Instanz der Datenbank-Engine her, auf der die Datenbank AdventureWorks2012 installiert ist, oder verwenden Sie Ihre eigene Datenbank für dieses Lernprogramm.  
  
3.  Klicken Sie auf der **Standard** Symbolleiste auf **neue Abfrage**.  
  
4.  Kopieren Sie das folgende Beispiel in das Abfragefenster, und ändern Sie es nach Bedarf.  
  
    ```  
    CREATE CREDENTIAL mycredential   
    WITH IDENTITY= 'mystorageaccount' - this is the name of the storage account you specified when creating a storage account (See Lesson 1)   
    , SECRET = '<storage account access key>' - this should be either the Primary or Secondary Access Key for the storage account (See Lesson 1)  
  
    ```  
  
     ![Zuordnen des Speicherkontos zu SQL-Anmeldeinformationen](../../2014/tutorials/media/backuptocloud-storage-credential-mapping.gif "Zuordnen des Speicherkontos zu SQL-Anmeldeinformationen")  
  
5.  Prüfen Sie die T-SQL-Anweisung, und klicken Sie auf **Ausführen**.  
  
 Weitere Informationen zum Azure BLOB Storage-Dienst für Sicherungs Konzepte und-Anforderungen finden Sie unter [SQL Server sichern und Wiederherstellen mit Azure BLOB Storage Dienst](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
### <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 3: Schreiben einer vollständigen Datenbanksicherung in den Azure BLOB Storage-Dienst](../../2014/tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md).  
  
  
