---
title: Sichern des Diensthauptschlüssels | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- service master key [SQL Server], exporting
ms.assetid: f60b917c-6408-48be-b911-f93b05796904
author: jaszymas
ms.author: jaszymas
manager: craigg
ms.openlocfilehash: c6e67b2eacfd428bc296596699ff65939789d1e8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "74957274"
---
# <a name="back-up-the-service-master-key"></a>Sichern des Diensthauptschlüssels
  In diesem Thema wird beschrieben, wie der Diensthauptschlüssel in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[tsql](../../../includes/tsql-md.md)]gesichert wird. Der Diensthauptschlüssel ist der Stamm der Verschlüsselungshierarchie. Er sollte gesichert und an einem sicheren Ort außerhalb der Geschäftsräume aufbewahrt werden. Das Erstellen dieser Sicherung sollte eine der ersten administrativen Aktionen sein, die auf dem Server ausgeführt werden.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   [So sichern Sie den Diensthauptschlüssel](#Procedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Einschränkungen  
  
-   Der Hauptschlüssel muss geöffnet und entschlüsselt sein, bevor er gesichert wird. Wenn er mit dem Diensthauptschlüssel verschlüsselt wird, muss der Hauptschlüssel nicht explizit geöffnet werden. Wenn der Hauptschlüssel jedoch nur mit einem Kennwort verschlüsselt wird, muss er explizit geöffnet werden.  
  
-   Es wird empfohlen, dass Sie sofort nach der Erstellung eine Sicherung des Hauptschlüssels anlegen und diese an einem sicheren Ort außerhalb Ihrer Geschäftsräume aufbewahren.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Erfordert die CONTROL-Berechtigung für die Datenbank.  
  
##  <a name="using-transact-sql"></a><a name="Procedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-back-up-the-service-master-key"></a>So sichern Sie den Diensthauptschlüssel  
  
1.  Stellen Sie in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]eine Verbindung mit der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz her, die den zu sichernden Diensthauptschlüssel enthält.  
  
2.  Wählen Sie das Kennwort, das zum Verschlüsseln des Diensthauptschlüssels auf dem Sicherungsmedium verwendet werden soll. Dieses Kennwort unterliegt Komplexitätsüberprüfungen. Weitere Informationen finden Sie unter [Password Policy](../password-policy.md).  
  
3.  Verwenden Sie ein Wechselsicherungsmedium, auf dem eine Kopie des gesicherten Schlüssels gespeichert wird.  
  
4.  Ermitteln Sie ein NTFS-Verzeichnis, in dem die Sicherung des Schlüssels erstellt werden soll. In diesem Verzeichnis erstellen Sie die im nächsten Schritt beschriebene Datei. Das Verzeichnis sollte durch stark einschränkende Zugriffssteuerungslisten (Access Control Lists, ACLs) geschützt sein.  
  
5.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer [!INCLUDE[ssDE](../../../includes/ssde-md.md)]-Instanz her.  
  
6.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
7.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**.  
  
    ```  
    -- Creates a backup of the "AdventureWorks2012" master key.  
    -- Because this master key is not encrypted by the service master key, a password must be specified when it is opened.  
    USE AdventureWorks2012;  
    GO  
    BACKUP SERVICE MASTER KEY TO FILE = 'c:\temp_backups\keys\service_master_ key'   
        ENCRYPTION BY PASSWORD = '3dH85Hhk003GHk2597gheij4';  
    GO  
    ```  
  
    > [!NOTE]  
    >  Der Dateipfad zum Schlüssel und das Kennwort (sofern es vorhanden ist) des Schlüssels unterscheiden sich von den obigen Informationen. Stellen Sie sicher, dass beide für den Server und die Schlüsseleinrichtung spezifisch sind.  
  
8.  Kopieren Sie die Datei auf das Sicherungsmedium, und überprüfen Sie die Kopie.  
  
9. Verwahren Sie die Sicherung an einem sicheren Ort außerhalb der Geschäftsräume.  
  
 Weitere Informationen finden Sie unter [OPEN MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/open-master-key-transact-sql) und [BACKUP MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-master-key-transact-sql).  
  
  
