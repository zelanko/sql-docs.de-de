---
title: 'Lektion 3: Erstellen von SQL Server-Anmeldeinformationen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 29e57ebd-828f-4dff-b473-c10ab0b1c597
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 85e60c359df2a209742b5b10693fcb72ac9cb37a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66090850"
---
# <a name="lesson-3-create-a-sql-server-credential"></a>Lektion 3: Erstellen von SQL Server-Anmeldeinformationen
  In dieser Lektion erstellen Sie Anmeldeinformationen, um die Sicherheitsinformationen für den Zugriff auf das Windows Azure-Speicherkonto zu speichern.  
  
 SQL Server-Anmeldeinformationen sind ein Objekt zum Speichern von Authentifizierungsinformationen, die für die Verbindung mit einer Ressource außerhalb von SQL Server erforderlich sind. In den Anmeldeinformationen werden der URI-Pfad des Speichercontainers und die Shared Access Signature-Schlüsselwerte gespeichert. Für jeden Speichercontainer, der von einer Daten- oder Protokolldatei verwendet wird, müssen Sie SQL Server-Anmeldeinformationen erstellen, deren Namen mit dem Containerpfad übereinstimmen.  
  
 Allgemeine Informationen zu Anmeldeinformationen finden Sie unter [Anmeldeinformationen &#40;Datenbank-Engine&#41;](security/authentication-access/credentials-database-engine.md).  
  
> [!IMPORTANT]  
>  Die Anforderungen zum Erstellen einer SQL Server-Anmeldeinformationen, die unten beschriebenen sind spezifisch für die [SQL Server-Datendateien in Windows Azure](databases/sql-server-data-files-in-microsoft-azure.md) Feature. Informationen zum Erstellen von Anmeldeinformationen für backup-Prozesse im Azure-Speicher finden Sie unter [Lektion 2: Erstellen Sie eine SQL Server-Anmeldeinformation](../tutorials/lesson-2-create-a-sql-server-credential.md).  
  
 Führen Sie die folgenden Schritte aus, um SQL Server-Anmeldeinformationen zu erstellen:  
  
1.  Stellen Sie eine Verbindung mit SQL Server Management Studio her.  
  
2.  Stellen Sie im Objekt-Explorer eine Verbindung mit der Instanz der installierten Datenbank-Engine her.  
  
3.  Klicken Sie auf der Standardsymbolleiste auf "Neue Abfrage".  
  
4.  Kopieren Sie das folgende Beispiel in das Abfragefenster, und ändern Sie es nach Bedarf. Die folgende Anweisung erstellt SQL Server-Anmeldeinformationen zum Speichern des Zertifikats für Ihren Speichercontainers freigegebenen Zugriff.  
  
    ```sql  
  
    USE master  
    CREATE CREDENTIAL credentialname - this name should match the container path and it must start with https.   
       WITH IDENTITY='SHARED ACCESS SIGNATURE', -- this is a mandatory string and do not change it.   
       SECRET = 'sharedaccesssignature' -- this is the shared access signature key that you obtained in Lesson 2.   
    GO  
  
    ```  
  
     Ausführliche Informationen finden Sie unter [CREATE CREDENTIAL &#40;Transact-SQL&#41; ](/sql/t-sql/statements/create-credential-transact-sql) in SQL Server-Onlinedokumentation.  
  
5.  Um alle verfügbaren Anmeldeinformationen anzuzeigen, können Sie im Abfragefenster die folgende Anweisung ausführen:  
  
    ```sql  
    SELECT * from sys.credentials  
    ```  
  
     Weitere Informationen zu sys.credentials finden Sie unter [sys.credentials &#40;Transact-SQL&#41; ](/sql/relational-databases/system-catalog-views/sys-credentials-transact-sql) in SQL Server-Onlinedokumentation.  
  
 **Nächste Lektion:**  
  
 [Lektion 4: Erstellen einer Datenbank in Windows Azure-Speicher](lesson-3-database-backup-to-url.md)  
  
  
