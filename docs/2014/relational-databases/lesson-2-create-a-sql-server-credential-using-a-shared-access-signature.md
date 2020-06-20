---
title: 'Lektion 3: Erstellen eines SQL Server Anmelde Informationen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 29e57ebd-828f-4dff-b473-c10ab0b1c597
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 808438e544e3beb18b2e2afa9c399b5666277483
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85025057"
---
# <a name="lesson-3-create-a-sql-server-credential"></a>Lektion 3: Erstellen von SQL Server-Anmeldeinformationen
  In dieser Lektion erstellen Sie Anmelde Informationen zum Speichern der Sicherheitsinformationen, die für den Zugriff auf das Azure-Speicherkonto verwendet werden.  
  
 SQL Server-Anmeldeinformationen sind ein Objekt zum Speichern von Authentifizierungsinformationen, die für die Verbindung mit einer Ressource außerhalb von SQL Server erforderlich sind. In den Anmeldeinformationen werden der URI-Pfad des Speichercontainers und die Shared Access Signature-Schlüsselwerte gespeichert. Für jeden Speichercontainer, der von einer Daten- oder Protokolldatei verwendet wird, müssen Sie SQL Server-Anmeldeinformationen erstellen, deren Namen mit dem Containerpfad übereinstimmen.  
  
 Allgemeine Informationen zu Anmelde Informationen finden Sie unter [Anmelde Informationen &#40;Datenbank-Engine&#41;](security/authentication-access/credentials-database-engine.md).  
  
> [!IMPORTANT]  
>  Die Anforderungen zum Erstellen einer SQL Server Anmelde Informationen, die unten beschrieben werden, gelten speziell für das Feature [SQL Server Datendateien in Azure](databases/sql-server-data-files-in-microsoft-azure.md) . Informationen zum Erstellen von Anmelde Informationen für Sicherungs Prozesse in Azure Storage finden Sie unter [Lektion 2: Erstellen eines SQL Server](../tutorials/lesson-2-create-a-sql-server-credential.md)Anmelde Informationen.  
  
 Führen Sie die folgenden Schritte aus, um SQL Server-Anmeldeinformationen zu erstellen:  
  
1.  Stellen Sie eine Verbindung mit SQL Server Management Studio her.  
  
2.  Stellen Sie im Objekt-Explorer eine Verbindung mit der Instanz der installierten Datenbank-Engine her.  
  
3.  Klicken Sie auf der Standardsymbolleiste auf "Neue Abfrage".  
  
4.  Kopieren Sie das folgende Beispiel in das Abfragefenster, und ändern Sie es nach Bedarf. Mit der folgenden Anweisung wird eine SQL Server Anmelde Informationen erstellt, um das freigegebene Zugriffs Zertifikat Ihres Speicher Containers zu speichern.  
  
    ```sql  
  
    USE master  
    CREATE CREDENTIAL credentialname - this name should match the container path and it must start with https.   
       WITH IDENTITY='SHARED ACCESS SIGNATURE', -- this is a mandatory string and do not change it.   
       SECRET = 'sharedaccesssignature' -- this is the shared access signature key that you obtained in Lesson 2.   
    GO  
  
    ```  
  
     Ausführliche Informationen finden Sie unter [Create Credential &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-credential-transact-sql) in SQL Server-Onlinedokumentation.  
  
5.  Um alle verfügbaren Anmeldeinformationen anzuzeigen, können Sie im Abfragefenster die folgende Anweisung ausführen:  
  
    ```sql  
    SELECT * from sys.credentials  
    ```  
  
     Weitere Informationen zu sys. Anmelde Informationen finden Sie unter [sys. Anmelde Informationen &#40;Transact-SQL-&#41;](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql) in SQL Server-Onlinedokumentation.  
  
 **Nächste Lektion:**  
  
 [Lektion 4: Erstellen einer Datenbank in Azure Storage](lesson-3-database-backup-to-url.md)  
  
  
