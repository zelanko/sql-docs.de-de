---
title: SQL Server-Agent-Eigenschaften (Seite Warnungssystem)|Microsoft-Dokumente
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.alert.f1
ms.assetid: 3e6d3bfd-20ee-4593-86cc-f65b1c08c69d
caps.latest.revision: 31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1d8edb6696adee4d3b3873e01194f746c1dfcafe
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37238290"
---
# <a name="sql-server-agent-properties-alert-system-page"></a>SQL Server-Agent-Eigenschaften (Seite Warnungssystem)
  Auf dieser Seite können Sie die Einstellungen für die vom [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent versandten Warnmeldungen anzeigen und ändern.  
  
## <a name="options"></a>Tastatur  
 **Mailsitzung**  
 Mithilfe der Optionen in diesem Abschnitt wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Mail konfiguriert.  
  
 **Mailprofil aktivieren**  
 Aktiviert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Mail. Standardmäßig ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Mail nicht aktiviert.  
  
 **Mailsystem**  
 Legt das von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent zu verwendende Mailsystem fest. Datenbank-E-Mail  
  
> [!NOTE]  
>  Nach der Änderung des E-Mail-Systems müssen Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst neu starten, damit die Änderung wirksam wird.  
  
 **Mailprofil**  
 Legt das von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent zu verwendende Profil fest. Sie können auch **\< neues Profil für Datenbank-E-Mail...>** wählen, um ein neues Profil zu erstellen.  
  
 **Pager-E-Mails**  
 Mithilfe der Optionen in diesem Abschnitt können Sie die an Pageradressen zu versendenden E-Mail-Nachrichten so konfigurieren, dass eine Kommunikation mit Ihrem Pagingsystem möglich ist.  
  
 **Adressformatierung für Pager-E-Mails**  
 In diesem Abschnitt können Sie das in Pager-E-Mails verwendete Format für Adressen und Betreffzeile angeben.  
  
 **An-Zeile**  
 Bestimmt die Optionen für die Zeile **An** der Nachricht.  
  
 **Prfix**  
 Geben Sie einen beliebigen festgelegten Text ein, den das System bei Nachrichten, die an Pager gesendet werden, am Anfang der Zeile **An** verlangt.  
  
 **Pager**  
 Enthält die E-Mail-Adresse der Nachricht zwischen Präfix und Suffix.  
  
 **Suffix**  
 Geben Sie einen beliebigen festgelegten Text ein, den das Pagingsystem bei Nachrichten, die an Pager gesendet werden, am Ende der Zeile **An** verlangt.  
  
 **Cc-Zeile**  
 Bestimmt Optionen für die Zeile **Cc** der Nachricht.  
  
 **Prfix**  
 Geben Sie einen beliebigen festgelegten Text ein, den das System bei Nachrichten, die an Pager gesendet werden, am Anfang der Zeile **Cc** verlangt.  
  
 **Pager**  
 Enthält die E-Mail-Adresse der Nachricht zwischen Präfix und Suffix.  
  
 **Suffix**  
 Geben Sie einen beliebigen festgelegten Text ein, den das Pagingsystem bei Nachrichten, die an Pager gesendet werden, am Ende der Zeile **Cc** verlangt.  
  
 **Betreff**  
 Bestimmt die Optionen für den Betreff der Nachricht.  
  
 **Prefix**  
 Geben Sie einen beliebigen festgelegten Text ein, den das Pagingsystem bei Nachrichten, die an Pager gesendet werden, am Anfang der Zeile **Betreff** verlangt.  
  
 **Suffix**  
 Geben Sie einen beliebigen festgelegten Text ein, den das Pagingsystem bei Nachrichten, die an Pager gesendet werden, am Ende der Zeile **Betreff** verlangt.  
  
 **E-Mail-Textkörper in Benachrichtigungsmeldung einschließen**  
 Schließt den Textkörper der E-Mail-Nachricht in die an den Pager versendete Nachricht ein.  
  
 **Ausfallsicherheitsoperator**  
 In diesem Abschnitt können Sie die Optionen für den Ausfallsicherheitsoperator angeben.  
  
 **Ausfallsicherheitsoperator aktivieren**  
 Legt einen Ausfallsicherheitsoperator fest.  
  
 **Ist gleich**  
 Legt den Namen des Operators fest, der die Ausfallsicherheitsbenachrichtigungen empfängt.  
  
 **Benachrichtigen durch**  
 Legt die Methode zur Benachrichtigung des Ausfallsicherheitsoperators fest.  
  
 **Tokenersetzung**  
 In diesem Abschnitt können Sie Tokens für Auftragsschritte aktivieren, die in von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Warnungen ausgeführten Aufträgen verwendet werden können. Weitere Informationen zu Auftragsschritttokens finden Sie unter [Verwenden von Token in Auftragsschritten](use-tokens-in-job-steps.md).  
  
> [!IMPORTANT]  
>  Jeder Windows-Benutzer mit Schreibberechtigungen für das Windows-Ereignisprotokoll hat u. U. die Möglichkeit, auf Auftragsschritte zuzugreifen, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Warnungen aktiviert werden. Zur Vermeidung dieses Sicherheitsrisikos sind [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Tokens, die in von Warnungen aktivierten Aufträgen verwendet werden können, standardmäßig deaktiviert. Hierbei handelt es sich um folgende Token: **$(A-DBN)**, **$(A-SVR)**, **$(A-ERR)**, **$(A-SEV)** und **$(A-MSG)**.  
>   
>  Wenn Sie diese Tokens verwenden müssen, können Sie sie aktivieren. Stellen Sie zuvor jedoch sicher, dass nur Mitglieder von vertrauenswürdigen Windows-Sicherheitsgruppen, wie z. B. die Gruppe Administratoren, über Schreibberechtigungen für das Ereignisprotokoll des Computers verfügen, auf dem sich [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] befindet.  
  
 **Token für alle Auftragsantworten auf Warnungen ersetzen**  
 Aktivieren Sie dieses Kontrollkästchen, um die Tokenersetzung für Aufträge zu aktivieren, die von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Warnungen aktiviert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Operatoren](operators.md)   
 [Konfigurieren von SQL Server-Agent-Mail zum Datenbank-e-Mail](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)   
 [Datenbank-E-Mail](../../relational-databases/database-mail/database-mail.md)  
  
  
