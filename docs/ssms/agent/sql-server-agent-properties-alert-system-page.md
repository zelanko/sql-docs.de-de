---
description: SQL Server-Agent-Eigenschaften (Seite Warnungssystem)
title: SQL Server-Agent-Eigenschaften (Seite Warnungssystem)
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.agent.alert.f1
ms.assetid: 3e6d3bfd-20ee-4593-86cc-f65b1c08c69d
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 827b8319e0e0f071ee9f1d1cb4b53838ea3613c8
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92038204"
---
# <a name="sql-server-agent-properties-alert-system-page"></a>SQL Server-Agent-Eigenschaften (Seite Warnungssystem)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> In [Azure SQL Managed Instance](/azure/sql-database/sql-database-managed-instance) werden derzeit die meisten, aber nicht alle, SQL Server-Agent-Features unterstützt. Details dazu finden Sie unter [T-SQL-Unterschiede zwischen Azure SQL Managed Instance und SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Auf dieser Seite können Sie die Einstellungen für die vom [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent versendeten Warnmeldungen abrufen und bearbeiten.  
  
## <a name="options"></a>Tastatur  
**Mailsitzung**  
Mithilfe der Optionen in diesem Abschnitt wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Mail konfiguriert.  
  
**Mailprofil aktivieren**  
Aktiviert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Mail. Standardmäßig ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Mail nicht aktiviert.  
  
**Mailsystem**  
Legt das von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent zu verwendende Mailsystem fest. Datenbank-E-Mail  
  
> [!NOTE]  
> Nach der Änderung des E-Mail-Systems müssen Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst neu starten, damit die Änderung wirksam wird.  
  
**Mailprofil**  
Legt das von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent zu verwendende Profil fest. Sie können auch ein **\<new Database Mail profile...>** auswählen, um ein neues Profil zu erstellen.  
  
**Pager-E-Mails**  
Mithilfe der Optionen in diesem Abschnitt können Sie die an Pageradressen zu versendenden E-Mail-Nachrichten so konfigurieren, dass eine Kommunikation mit Ihrem Pagingsystem möglich ist.  
  
**Adressformatierung für Pager-E-Mails**  
In diesem Abschnitt können Sie das in Pager-E-Mails verwendete Format für Adressen und Betreffzeile angeben.  
  
**An-Zeile**  
Bestimmt die Optionen für die Zeile **An** der Nachricht.  
  
**Präfix**  
Geben Sie einen beliebigen festgelegten Text ein, den das System bei Nachrichten, die an Pager gesendet werden, am Anfang der Zeile **An** verlangt.  
  
**Pager**  
Enthält die E-Mail-Adresse der Nachricht zwischen Präfix und Suffix.  
  
**Suffix**  
Geben Sie einen beliebigen festgelegten Text ein, den das Pagingsystem bei Nachrichten, die an Pager gesendet werden, am Ende der Zeile **An** verlangt.  
  
**Cc-Zeile**  
Bestimmt Optionen für die Zeile **Cc** der Nachricht.  
  
**Präfix**  
Geben Sie einen beliebigen festgelegten Text ein, den das System bei Nachrichten, die an Pager gesendet werden, am Anfang der Zeile **Cc** verlangt.  
  
**Pager**  
Enthält die E-Mail-Adresse der Nachricht zwischen Präfix und Suffix.  
  
**Suffix**  
Geben Sie einen beliebigen festgelegten Text ein, den das Pagingsystem bei Nachrichten, die an Pager gesendet werden, am Ende der Zeile **Cc** verlangt.  
  
**Subject**  
Bestimmt die Optionen für den Betreff der Nachricht.  
  
**Präfix**  
Geben Sie einen beliebigen festgelegten Text ein, den das Pagingsystem bei Nachrichten, die an Pager gesendet werden, am Anfang der Zeile **Betreff** verlangt.  
  
**Suffix**  
Geben Sie einen beliebigen festgelegten Text ein, den das Pagingsystem bei Nachrichten, die an Pager gesendet werden, am Ende der Zeile **Betreff** verlangt.  
  
**E-Mail-Textkörper in Benachrichtigungsmeldung einschließen**  
Schließt den Textkörper der E-Mail-Nachricht in die an den Pager versendete Nachricht ein.  
  
**Ausfallsicherheitsoperator**  
In diesem Abschnitt können Sie die Optionen für den Ausfallsicherheitsoperator angeben.  
  
**Ausfallsicherheitsoperator aktivieren**  
Legt einen Ausfallsicherheitsoperator fest.  
  
**Operator**  
Legt den Namen des Operators fest, der die Ausfallsicherheitsbenachrichtigungen empfängt.  
  
**Benachrichtigen durch**  
Legt die Methode zur Benachrichtigung des Ausfallsicherheitsoperators fest.  
  
**Tokenersetzung**  
In diesem Abschnitt können Sie Tokens für Auftragsschritte aktivieren, die in von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Warnungen ausgeführten Aufträgen verwendet werden können. Weitere Informationen zu Auftragsschritttokens finden Sie unter [Verwenden von Token in Auftragsschritten](../../ssms/agent/use-tokens-in-job-steps.md).  
  
> [!IMPORTANT]  
> Jeder Windows-Benutzer mit Schreibberechtigungen für das Windows-Ereignisprotokoll hat u. U. die Möglichkeit, auf Auftragsschritte zuzugreifen, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Warnungen aktiviert werden. Zur Vermeidung dieses Sicherheitsrisikos sind [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Tokens, die in von Warnungen aktivierten Aufträgen verwendet werden können, standardmäßig deaktiviert. Hierbei handelt es sich um folgende Token: **$(A-DBN)** , **$(A-SVR)** , **$(A-ERR)** , **$(A-SEV)** und **$(A-MSG)** .  
>   
> Wenn Sie diese Tokens verwenden müssen, können Sie sie aktivieren. Stellen Sie zuvor jedoch sicher, dass nur Mitglieder von vertrauenswürdigen Windows-Sicherheitsgruppen, wie z. B. die Gruppe Administratoren, über Schreibberechtigungen für das Ereignisprotokoll des Computers verfügen, auf dem sich [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] befindet.  
  
**Token für alle Auftragsantworten auf Warnungen ersetzen**  
Aktivieren Sie dieses Kontrollkästchen, um die Tokenersetzung für Aufträge zu aktivieren, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Warnungen aktiviert werden.  
  
## <a name="see-also"></a>Weitere Informationen  
[Operatoren](../../ssms/agent/operators.md)  
[Konfigurieren von SQL Server-Agent-Mail zum Verwenden von Datenbank-E-Mails](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)  
[Datenbank-E-Mail](../../relational-databases/database-mail/database-mail.md)  
