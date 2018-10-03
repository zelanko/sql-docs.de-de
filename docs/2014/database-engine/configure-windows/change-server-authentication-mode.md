---
title: Ändern des Serverauthentifizierungsmodus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- sa account
- authentication [SQL Server], changing modes
- server authentication mode [SQL Server]
- modifying server authentication mode
ms.assetid: 79babcf8-19fd-4495-b8eb-453dc575cac0
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6dec6d868a1eb568b20794d35774712eb98f6677
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48175652"
---
# <a name="change-server-authentication-mode"></a>Ändern des Serverauthentifizierungsmodus
  In diesem Thema wird beschrieben, wie Sie den Serverauthentifizierungsmodus in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]ändern können. Während der Installation wird [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] entweder auf den **Windows-Authentifizierungsmodus** oder den **SQL Server- und Windows-Authentifizierungsmodus**festgelegt. Nach der Installation können Sie jederzeit den Authentifizierungsmodus ändern.  
  
 Wird während der Installation der **Windows-Authentifizierungsmodus** ausgewählt, wird die Systemadministratoranmeldung deaktiviert und ein Kennwort durch das Setup zugewiesen. Wenn Sie den Authentifizierungsmodus später zu **SQL Server- und Windows-Authentifizierungsmodus**ändern, bleibt die Systemadministratoranmeldung deaktiviert. Um die Systemadministratoranmeldung zu verwenden, nutzen Sie die ALTER LOGIN-Anweisung, um die Systemadministratoranmeldung zu aktivieren und ein neues Kennwort zuzuweisen. Die Systemadministratoranmeldung kann nur mithilfe der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung eine Verbindung mit dem Server herstellen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **So ändern Sie den Serverauthentifizierungsmodus mit**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Security"></a> Sicherheit  
 Das Systemadministratorkonto ist ein bekanntes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konto und oft das Ziel böswilliger Benutzer. Aktivieren Sie das Systemadministratorkonto nur dann, wenn die Anwendung es erfordert. Es ist sehr wichtig, dass Sie für die Systemadministratoranmeldung ein sicheres Kennwort verwenden.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-change-security-authentication-mode"></a>So ändern Sie den Authentifizierungsmodus  
  
1.  Klicken Sie im Objekt-Explorer von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] mit der rechten Maustaste auf den Server, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Wählen Sie auf der Seite **Sicherheit** unter **Serverauthentifizierung**den neuen Serverauthentifizierungsmodus aus, und klicken Sie dann auf **OK**.  
  
3.  Klicken Sie im Dialogfeld [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] auf **OK** , um den notwendigen Neustart von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu bestätigen.  
  
4.  Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf Ihren Server, und klicken Sie dann auf **Neu starten**. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent muss ebenfalls neu gestartet werden, sofern er ausgeführt wird.  
  
#### <a name="to-enable-the-sa-login"></a>Informationen zum Aktivieren des Anmeldenamens "sa"  
  
1.  Erweitern Sie im Objekt-Explorer **Sicherheit**, erweitern Sie Anmeldungen, mit der rechten Maustaste `sa`, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Auf der Seite **Allgemein** müssen Sie möglicherweise ein Kennwort für die Anmeldung erstellen und bestätigen.  
  
3.  Klicken Sie auf der Seite **Status** im Abschnitt **Anmeldung** auf **Aktiviert**, und klicken Sie dann auf **OK**.  
  
##  <a name="TsqlProcedure"></a> Verwenden von Transact-SQL  
 **Informationen zum Aktivieren des Anmeldenamens "sa"**  
  
1.  Stellen Sie mithilfe des Objekt-Explorers eine Verbindung mit einer Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)]her.  
  
2.  Klicken Sie in der Standardleiste auf **Neue Abfrage**.  
  
3.  Kopieren Sie das folgende Beispiel, fügen Sie es in das Abfragefenster ein, und klicken Sie auf **Ausführen**. Im folgenden Beispiel wird die Systemadministratoranmeldung aktiviert, und es wird ein neues Kennwort festgelegt.  
  
    ```  
    ALTER LOGIN sa ENABLE ;  
    GO  
    ALTER LOGIN sa WITH PASSWORD = '<enterStrongPasswordHere>' ;  
    GO  
  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Sichere Kennwörter](../../relational-databases/security/strong-passwords.md)   
 [Überlegungen zur Sicherheit bei SQL Server-Installationen](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql)   
 [Herstellen einer Verbindung mit SQL Server, wenn Systemadministratoren gesperrt sind](connect-to-sql-server-when-system-administrators-are-locked-out.md)  
  
  
