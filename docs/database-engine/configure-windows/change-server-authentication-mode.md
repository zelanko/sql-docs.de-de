---
title: Ändern des Serverauthentifizierungsmodus | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/18/2020
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- sa account
- authentication [SQL Server], changing modes
- server authentication mode [SQL Server]
- modifying server authentication mode
ms.assetid: 79babcf8-19fd-4495-b8eb-453dc575cac0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a8ffafae40991d6134925481409b5898b06c20c4
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "79288564"
---
# <a name="change-server-authentication-mode"></a>Ändern des Serverauthentifizierungsmodus

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
In diesem Thema wird beschrieben, wie Sie den Serverauthentifizierungsmodus in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder [!INCLUDE[tsql](../../includes/tsql-md.md)]ändern können. Während der Installation wird [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] entweder auf den **Windows-Authentifizierungsmodus** oder den **SQL Server- und Windows-Authentifizierungsmodus**festgelegt. Nach der Installation können Sie jederzeit den Authentifizierungsmodus ändern.

Wird während der Installation der **Windows-Authentifizierungsmodus** ausgewählt, wird die Systemadministratoranmeldung deaktiviert und ein Kennwort durch das Setup zugewiesen. Wenn Sie den Authentifizierungsmodus später zu **SQL Server- und Windows-Authentifizierungsmodus**ändern, bleibt die Systemadministratoranmeldung deaktiviert. Um die Systemadministratoranmeldung zu verwenden, nutzen Sie die ALTER LOGIN-Anweisung, um die Systemadministratoranmeldung zu aktivieren und ein neues Kennwort zuzuweisen. Die Systemadministratoranmeldung kann nur mithilfe der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung eine Verbindung mit dem Server herstellen.

## <a name="before-you-begin"></a>Voraussetzungen

Das Systemadministratorkonto ist ein bekanntes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konto und oft das Ziel böswilliger Benutzer. Aktivieren Sie das Systemadministratorkonto nur dann, wenn die Anwendung es erfordert. Es ist sehr wichtig, dass Sie für die Systemadministratoranmeldung ein sicheres Kennwort verwenden.

## <a name="change-authentication-mode-with-ssms"></a>Ändern des Authentifizierungsmodus mit SSMS

1. Klicken Sie im Objekt-Explorer von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] mit der rechten Maustaste auf den Server, und klicken Sie dann auf **Eigenschaften**.

2. Wählen Sie auf der Seite **Sicherheit** unter **Serverauthentifizierung**den neuen Serverauthentifizierungsmodus aus, und klicken Sie dann auf **OK**.

3. Klicken Sie im Dialogfeld [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] auf **OK** , um den notwendigen Neustart von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu bestätigen.

4. Klicken Sie im Objekt-Explorer mit der rechten Maustaste auf Ihren Server, und klicken Sie dann auf **Neu starten**. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent muss ebenfalls neu gestartet werden, sofern er ausgeführt wird.

## <a name="enable-sa-login"></a>Aktivieren der SA-Anmeldung

Sie können die **SA**-Anmeldung mit SSMS oder T-SQL aktivieren.

### <a name="use-ssms"></a>Verwenden Sie SSMS.

1. Erweitern Sie im Objekt-Explorer **Sicherheit**, erweitern Sie „Anmeldungen“, klicken Sie mit der rechten Maustaste auf **Systemadministrator**, und klicken Sie dann auf **Eigenschaften**.

2. Auf der Seite **Allgemein** müssen Sie eventuell ein Kennwort für die **SA**-Anmeldung erstellen und bestätigen.

3. Klicken Sie auf der Seite **Status** im Abschnitt **Anmeldung** auf **Aktiviert**, und klicken Sie dann auf **OK**.

### <a name="using-transact-sql"></a>Verwenden von Transact-SQL

Im folgenden Beispiel wird die Systemadministratoranmeldung aktiviert, und es wird ein neues Kennwort festgelegt. Ersetzen Sie `<enterStrongPasswordHere>` durch ein sicheres Kennwort, bevor Sie den Befehl ausführen.

```sql  
ALTER LOGIN sa ENABLE ;  
GO  
ALTER LOGIN sa WITH PASSWORD = '<enterStrongPasswordHere>' ;  
GO  
```

## <a name="change-authentication-mode-t-sql"></a>Ändern des Authentifizierungsmodus mit T-SQL

Im folgenden Beispiel wird die Serverauthentifizierung vom gemischten Modus (Windows und SQL) in den Nur-Windows-Modus geändert.

> [!CAUTION]
> Im folgenden Beispiel wird eine erweiterte gespeicherte Prozedur zum Ändern der Serverregistrierung verwendet. Wenn Ihnen beim Bearbeiten der Registrierung ein Fehler unterläuft, kann dies zu schwerwiegenden Problemen führen. Diese Probleme können dazu führen, dass Sie das Betriebssystem neu installieren müssen. Microsoft kann nicht garantieren, dass diese Probleme behoben werden können. Das Bearbeiten der Registrierung erfolgt auf eigenes Risiko.

```sql
USE [master]
GO
EXEC xp_instance_regwrite N'HKEY_LOCAL_MACHINE', 
     N'Software\Microsoft\MSSQLServer\MSSQLServer',
     N'LoginMode', REG_DWORD, 1
GO
```

## <a name="see-also"></a>Weitere Informationen

 [Sichere Kennwörter](../../relational-databases/security/strong-passwords.md)   
 [Überlegungen zur Sicherheit bei SQL Server-Installationen](../../sql-server/install/security-considerations-for-a-sql-server-installation.md) [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md) [Herstellen einer Verbindung mit SQL Server bei gesperrten Systemadministratoren](../../database-engine/configure-windows/connect-to-sql-server-when-system-administrators-are-locked-out.md)
