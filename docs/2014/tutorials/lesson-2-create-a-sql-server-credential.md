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
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "70154329"
---
# <a name="lesson-2-create-a-sql-server-credential"></a>Lektion 2: Erstellen von SQL Server-Anmeldeinformationen
  **Anmeldeinformationen:** [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Anmeldeinformationen sind ein Objekt zum Speichern von Authentifizierungsinformationen, die für die Verbindung mit einer Ressource außerhalb von SQL Server erforderlich sind.  Hier werden [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] von Sicherungs-und Wiederherstellungs Prozessen Anmelde Informationen für die Authentifizierung beim Azure BLOB Storage-Dienst verwendet. In den Anmeldeinformationen werden der Name des Speicherkontos und der **Zugriffsschlüssel** des Speicherkontos gespeichert. Sobald die Anmeldeinformationen erstellt wurden, müssen sie beim Ausgeben der BACKUP-/RESTORE-Anweisungen in der WITH CREDENTIAL-Option angegeben werden. Weitere Informationen zum Anzeigen, Kopieren oder erneuten Generieren von **access keys**für Speicherkonten finden Sie unter [Zugriffsschlüssel für Speicherkonten](https://msdn.microsoft.com/library/windowsazure/hh531566.aspx).  
  
 Weitere allgemeine Informationen über Anmeldeinformationen finden Sie unter [Anmeldeinformationen](../relational-databases/security/authentication-access/credentials-database-engine.md).  
  
 Informationen mit weiteren Beispielen zur Verwendung von Anmeldeinformationen finden Sie unter [Erstellen eines Proxys für den SQL Server-Agent](../ssms/agent/create-a-sql-server-agent-proxy.md).  
  
> [!IMPORTANT]  
>  Die Anforderungen für das Erstellen einer SQL Server Anmelde Informationen, die unten beschrieben werden, gelten speziell für SQL Server Sicherungs Prozesse ([SQL Server URL-Sicherung](../relational-databases/backup-restore/sql-server-backup-to-url.md)und [SQL Server verwaltete Sicherung in Azure](../relational-databases/backup-restore/sql-server-managed-backup-to-microsoft-azure.md)). SQL Server verwendet beim Zugriff auf Azure-Speicher zum Schreiben oder Lesen von Sicherungen den Namen des Speicherkontos und Informationen zu den Zugriffsschlüsseln.  Weitere Informationen zum Erstellen von Anmelde Informationen zum Speichern von Datenbankdateien in Azure [Storage finden Sie unter Lektion 3: Erstellen eines SQL Server Anmelde Informationen](../relational-databases/lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)  
  
## <a name="create-a-sql-server-credential"></a>Erstellen von SQL Server-Anmeldeinformationen  
 Führen Sie die folgenden Schritte aus, um SQL Server-Anmeldeinformationen zu erstellen:  
  
1.  Stellen Sie eine Verbindung mit SQL Server Management Studio her.  
  
2.  Stellen Sie im Objekt-Explorer eine Verbindung mit der Instanz der Datenbank-Engine her, auf der die Datenbank AdventureWorks2012 installiert ist, oder verwenden Sie Ihre eigene Datenbank für dieses Lernprogramm.  
  
3.  Klicken Sie auf der **Standardsymbolleiste** auf **Neue Abfrage**.  
  
4.  Kopieren Sie das folgende Beispiel in das Abfragefenster, und ändern Sie es nach Bedarf.  
  
    ```  
    CREATE CREDENTIAL mycredential   
    WITH IDENTITY= 'mystorageaccount' - this is the name of the storage account you specified when creating a storage account (See Lesson 1)   
    , SECRET = '<storage account access key>' - this should be either the Primary or Secondary Access Key for the storage account (See Lesson 1)  
  
    ```  
  
     ![Zuordnung von Speicherkonto zu SQL-Anmelde] Informationen (../../2014/tutorials/media/backuptocloud-storage-credential-mapping.gif "Zuordnung von Speicherkonto zu SQL-Anmelde") Informationen  
  
5.  Überprüfen Sie die T-SQL-Anweisung, und klicken Sie auf **Ausführen**.  
  
 Weitere Informationen zum Azure BLOB Storage-Dienst für Sicherungs Konzepte und-Anforderungen finden Sie unter [SQL Server sichern und Wiederherstellen mit Azure BLOB Storage Dienst](../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).  
  
### <a name="next-lesson"></a>Nächste Lektion  
 [Lektion 3: Schreiben Sie eine vollständige Datenbanksicherung in](../../2014/tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md)den Azure BLOB Storage-Dienst.  
  
  
