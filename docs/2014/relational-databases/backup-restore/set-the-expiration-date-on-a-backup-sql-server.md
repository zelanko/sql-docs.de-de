---
title: Festlegen des Ablaufdatums für eine Sicherung (SQL Server) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up databases [SQL Server], expiration dates
- expiration [SQL Server]
- database backups [SQL Server], expiration dates
ms.assetid: 76e814df-6487-4893-9f09-7759f1863a5c
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 30f5a68f51bf501f243bd129d11051d63a6efabd
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58533802"
---
# <a name="set-the-expiration-date-on-a-backup-sql-server"></a>Festlegen des Ablaufdatums für eine Sicherung (SQL Server)
  In diesem Thema wird beschrieben, wie Sie das Ablaufdatum für eine Sicherung in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]festlegen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **So legen Sie das Ablaufdatum für eine Sicherung fest mit**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Mitglieder der festen Serverrolle **sysadmin** und der festen Datenbankrollen **db_owner** und **db_backupoperator** verfügen standardmäßig über BACKUP DATABASE- und BACKUP LOG-Berechtigungen.  
  
 Besitz- und Berechtigungsprobleme im Zusammenhang mit der physischen Datei des Sicherungsmediums können den Sicherungsvorgang beeinträchtigen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] muss über Lese- und Schreibberechtigungen für das Medium verfügen. Das Konto, unter dem der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst ausgeführt wird, muss Schreibberechtigungen haben. Allerdings prüft die gespeicherte Prozedur [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), die den Systemtabellen einen Eintrag für ein Sicherungsmedium hinzufügt, nicht die Dateizugriffsberechtigungen. Solche Probleme mit der physischen Datei des Sicherungsmediums treten möglicherweise erst auf, wenn auf die physische Ressource zugegriffen wird, um einen Sicherungs- oder Wiederherstellungsvorgang auszuführen.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-set-the-expiration-date-on-a-backup"></a>So legen Sie das Ablaufdatum für eine Sicherung fest  
  
1.  Klicken Sie im Objekt-Explorer nach dem Herstellen einer Verbindung mit der entsprechenden Instanz von [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]auf den Servernamen, um die Serverstruktur zu erweitern.  
  
2.  Erweitern Sie **Datenbanken**, und wählen Sie je nach Datenbank eine Benutzerdatenbank aus, oder erweitern Sie **Systemdatenbanken** , und wählen Sie eine Systemdatenbank aus.  
  
3.  Klicken Sie mit der rechten Maustaste auf die Datenbank, zeigen Sie auf **Tasks**, und klicken Sie anschließend auf **Sichern**. Das Dialogfeld **Datenbank sichern** wird angezeigt.  
  
4.  Geben Sie auf der Seite **Allgemein** für **Sicherungssatz läuft ab**ein Ablaufdatum an, um anzugeben, wann der Sicherungssatz durch eine andere Sicherung überschrieben werden kann:  
  
    -   Wenn der Sicherungssatz nach einer bestimmten Anzahl von Tagen ablaufen soll, klicken Sie auf **Nach** (die Standardoption), und geben Sie an, nach wie vielen Tagen der Sicherungssatz abläuft. Dieser Wert kann zwischen 0 und 99999 Tagen liegen. Ein Wert von 0 Tagen bedeutet, dass der Sicherungssatz nicht abläuft.  
  
         Der Standardwert wird im Dialogfeld **Servereigenschaften** (Seite **Datenbankeinstellungen** ) über die Option**Standardbeibehaltung für Sicherungsmedien (in Tagen)** festgelegt. Klicken Sie hierzu mit der rechten Maustaste auf den Servernamen im Objekt-Explorer, und wählen Sie Eigenschaften aus. Wählen Sie anschließend die Seite **Datenbankeinstellungen** aus.  
  
    -   Zum Speichern des Sicherungssatzes an einem bestimmten Datum klicken Sie auf **Am**. Geben Sie das Datum ein, an dem der Sicherungssatz abläuft.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
  
#### <a name="to-set-the-expiration-date-on-a-backup"></a>So legen Sie das Ablaufdatum für eine Sicherung fest  
  
1.  Stellen Sie eine Verbindung mit dem [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Geben Sie in der [BACKUP](/sql/t-sql/statements/backup-transact-sql) -Anweisung entweder die Option EXPIREDATE oder RETAINDAYS an, um zu bestimmen, wann der die Sicherung von [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] überschrieben werden kann. Wenn keine der Optionen angegeben wird, wird das Ablaufdatum durch die Serverkonfigurationseinstellung [Medienbeibehaltung](../../database-engine/configure-windows/configure-the-media-retention-server-configuration-option.md) bestimmt. In diesem Beispiel wird die `EXPIREDATE` -Option verwendet, um das Ablaufdatum auf den 30. Juni 2015 festzulegen (`6/30/2015`).  
  
```sql  
USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
 TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.Bak'  
   WITH EXPIREDATE = '6/30/2015' ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer vollständigen Datenbanksicherung &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)   
 [Sichern von Dateien und Dateigruppen &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md)   
 [Sichern eines Transaktionsprotokolls &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)   
 [Erstellen einer differenziellen Datenbanksicherung &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md)  
  
  
