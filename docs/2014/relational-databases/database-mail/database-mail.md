---
title: Datenbank-E-Mail | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- architecture [SQL Server], Database Mail
- Database Mail [SQL Server], architecture
- Database Mail [SQL Server], components
ms.assetid: 9e4563dd-4799-4b32-a78a-048ea44a44c1
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8c763c6db472f52df320d0c89dc47483636bf9f5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917965"
---
# <a name="database-mail"></a>Datenbank-E-Mail
  Datenbank-E-Mail bietet eine Unternehmenslösung, die zum Senden von E-Mail-Nachrichten mit [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] verwendet werden kann. Mit Datenbank-E-Mail können Datenbankanwendungen E-Mail-Nachrichten an Benutzer senden. Diese Nachrichten können neben Abfrageergebnissen auch Dateien von anderen Ressourcen im Netzwerk enthalten.  
  
 
  
##  <a name="Benefits"></a> Vorteile der Verwendung von Datenbank-E-Mail  
 Datenbank-E-Mail zeichnet sich durch Zuverlässigkeit, Skalierbarkeit, Sicherheit sowie Unterstützbarkeit aus.  
  
### <a name="reliability"></a>Zuverlässigkeit  
  
-   Datenbank-E-Mail verwendet zum Senden von E-Mail das standardmäßige SMTP (Simple Mail Transfer Protocol). Sie können Datenbank-E-Mail auch dann verwenden, wenn auf dem Computer mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]kein Client für erweitertes MAPI installiert ist.  
  
-   Prozessisolierung. Zur Verringerung der Auswirkungen auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]wird die Komponente zur Übermittlung von E-Mail in einem separaten Prozess, außerhalb von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ausgeführt. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fügt E-Mail-Nachrichten auch dann weiter in die Warteschlange ein, wenn der externe Prozess beendet wird oder einen Fehler erzeugt. Die Nachrichten in der Warteschlange werden gesendet, sobald der externe Prozess oder der SMTP-Server online geschaltet werden.  
  
-   Failoverkonten. Mit den Profilen von Datenbank-E-Mail können Sie mehrere SMTP-Server angeben. Falls ein SMTP-Server nicht verfügbar ist, können die E-Mail-Nachrichten an einen anderen SMTP-Server übermittelt werden.  
  
-   Clusterunterstützung. Datenbank-E-Mail ist clusterabhängig und wird auf einem Cluster vollständig unterstützt.  
  
### <a name="scalability"></a>Skalierbarkeit  
  
-   Übermittlung im Hintergrund: Datenbank-e-Mails enthält Hintergrund bzw. asynchrone Übermittlung. Wenn Sie zum Senden einer Nachricht **sp_send_dbmail** aufrufen, fügt Datenbank-E-Mail eine Anforderung zu einer [!INCLUDE[ssSB](../../includes/sssb-md.md)] -Warteschlange hinzu. Die gespeicherte Prozedur liefert sofort eine Rückgabe. Die externe E-Mail-Komponente empfängt die Anforderung und übermittelt die E-Mail-Nachricht.  
  
-   Mehrere Profile: Datenbank-e-Mails können Sie mehrere Profile im Erstellen einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz. Wahlweise können Sie auch das Profil auswählen, mit dem Datenbank-E-Mail Nachrichten senden soll.  
  
-   Mehrere Konten: Jedes Profil kann mehrere Failoverkonten enthalten. Sie können verschiedene Profile mit verschiedenen Konten konfigurieren, um E-Mail-Nachrichten über mehrere E-Mail-Server zu verteilen.  
  
-   64-Bit-Kompatibilität: Datenbank-e-Mails wird vollständig unterstützt, auf 64-Bit-Installationen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="security"></a>Sicherheit  
  
-   Standardmäßig deaktiviert: Um die Oberfläche zu reduzieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], gespeicherte Prozeduren sind standardmäßig deaktiviert.  
  
-   E-Mail-Sicherheit: Zum Senden von Datenbank-E-Mail müssen Sie Mitglied der **DatabaseMailUserRole** -Datenbankrolle in der **msdb** -Datenbank sein.  
  
-   Profilsicherheit: Datenbank-e-Mails erzwingt die Sicherheit von Mailprofilen. Wählen Sie die Benutzer oder Gruppen der **msdb** -Datenbank aus, die Zugriff auf ein Profil von Datenbank-E-Mail besitzen. Sie können entweder nur bestimmten oder allen Benutzern von **msdb**Zugriff erteilen. Durch private Profile wird der Zugriff auf eine bestimmte Liste von Benutzern eingeschränkt. Öffentliche Profile sind für alle Benutzer einer Datenbank verfügbar.  
  
-   Kontrolle der Anlagengröße: Datenbank-e-Mails erzwingt ein konfigurierbares Limit für die Größe von Anlagendateien. Sie können dieses Limit mithilfe der gespeicherten Prozedur [sysmail_configure_sp](/sql/relational-databases/system-stored-procedures/sysmail-configure-sp-transact-sql) ändern.  
  
-   Unzulässige Dateierweiterungen: Datenbank-e-Mails verwaltet eine Liste der unzulässigen Dateierweiterungen. Dateien, die eine in der Liste aufgeführte Erweiterung besitzen, können nicht angefügt werden. Sie können diese Liste mithilfe von sysmail_configure_sp ändern.  
  
-   Datenbank-E-Mail wird im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Engine-Dienstkonto ausgeführt. Um eine Datei aus einem Ordner einer E-Mail anhängen zu können, muss das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Engine-Konto über die Berechtigungen zum Zugriff auf den Ordner mit der Datei verfügen.  
  
### <a name="supportability"></a>Unterstützbarkeit  
  
-   Integrierte Konfiguration: Datenbank-e-Mails verwaltet die Informationen für e-Mail-Konten in [!INCLUDE[ssDEnoversion](../../includes/tsql-md.md)].  
  
-   Anmeldung. Datenbank-E-Mail protokolliert die E-Mail-Aktivität in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], dem Microsoft Windows-Anwendungsereignisprotokoll und in Tabellen in der **msdb** -Datenbank.  
  
-   Überwachung: Datenbank-Mail speichert Kopien von Nachrichten und Anlagen gesendet werden, der **Msdb** Datenbank. Sie können die Verwendung von Datenbank-E-Mail auf einfache Weise überwachen und die gespeicherten Nachrichten überprüfen.  
  
-   Unterstützung für HTML-Code: Datenbank-e-Mails können Sie zum Senden von E-mail im HTML-Format.  
  

  
##  <a name="VisualElement"></a> Architektur der Datenbank-E-Mail  
 Datenbank-E-Mail wurde basierend auf einer Warteschlangenarchitektur entwickelt, in der Service Broker-Technologien zum Einsatz kommen. Wenn Benutzer **sp_send_dbmail**ausführen, fügt die gespeicherte Prozedur ein Element in die E-Mail-Warteschlange ein und erstellt einen Datensatz, in dem die E-Mail-Nachricht enthalten ist. Durch das Einfügen des neuen Eintrags in die E-Mail-Warteschlange wird der externe Prozess von Datenbank-E-Mail (DatabaseMail.exe) gestartet. Der externe Prozess liest die E-Mail-Informationen und sendet die E-Mail-Nachricht an den entsprechenden E-Mail-Server bzw. an mehrere E-Mail-Server. Der externe Prozess fügt für das Ergebnis des Sendevorgangs ein Element in die Statuswarteschlange ein. Durch das Einfügen des neuen Eintrags in die Statuswarteschlange wird eine interne gespeicherte Prozedur gestartet, mit der der Status der E-Mail-Nachricht aktualisiert wird. Zusätzlich zum Speichern der gesendeten (oder nicht gesendeten) E-Mail-Nachricht werden von Datenbank-E-Mail auch alle E-Mail-Anhänge in den Systemtabellen gespeichert. In den Sichten von Datenbank-E-Mail wird der Status der Nachrichten zur Problembehandlung gezeigt. Die Warteschlange von Datenbank-E-Mail kann mithilfe gespeicherter Prozeduren verwaltet werden.  
  
 ![Von der msdb-Datenbank werden Nachrichten an einen SMTP-Mailserver gesendet](../../database-engine/media/databasemail.gif "msdb sends messages to an SMTP mail server")  
  

  
##  <a name="ComponentsAndConcepts"></a> Einführung in Datenbank-E-Mail-Komponenten  
 In Datenbank-E-Mail sind die folgenden Hauptkomponenten enthalten:  
  
-   Konfigurations- und Sicherheitskomponenten  
  
     Datenbank-E-Mail speichert die Konfigurations- und Sicherheitsinformationen in der **msdb** -Datenbank. Konfigurations- und Sicherheitsobjekte erstellen Profile und Konten, die von Datenbank-E-Mail verwendet werden.  
  
-   Messagingkomponenten  
  
     Die **msdb** -Datenbank fungiert als Mailhost-Datenbank, in der die Messagingobjekte enthalten sind, mit denen Datenbank-E-Mail Nachrichten sendet. Zu diesen Objekten zählen die gespeicherte Prozedur **sp_send_dbmail** und die Datenstrukturen mit Informationen zu den Nachrichten.  
  
-   Ausführbare Datei von Datenbank-E-Mail  
  
     Die ausführbare Datei von Datenbank-E-Mail ist ein externes Programm, das Nachrichten aus einer Warteschlange in der **msdb** -Datenbank liest und an E-Mail-Server sendet.  
  
-   Protokollierungs- und Überwachungskomponenten  
  
     Datenbank-E-Mail zeichnet die Protokollinformationen in der **msdb** -Datenbank und im [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows Anwendungsereignisprotokoll auf.  
  
 **Konfigurieren des Agents zur Verwendung von Datenbank-E-Mail:**  
  
 Der SQL Server-Agent kann zur Verwendung von Datenbank-E-Mail konfiguriert werden. Dies ist für Warnbenachrichtigungen und die automatische Benachrichtigung über den Abschluss von Aufträgen erforderlich.  
  
> [!WARNING]  
>  Einzelne Auftragsschritte innerhalb eines Auftrags können ebenfalls E-Mails senden, ohne dass dazu der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent zur Verwendung von Datenbank-E-Mail konfiguriert werden muss. Ein [!INCLUDE[tsql](../../../includes/tsql-md.md)] -Auftragsschritt kann beispielsweise Datenbank-E-Mail verwenden, um die Ergebnisse einer Abfrage an eine Reihe von Empfängern zu senden.  
  
 Sie können den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent so konfigurieren, dass E-Mail-Nachrichten in folgenden Fällen an vordefinierte Operatoren gesendet werden:  
  
-   Eine Warnung wird ausgelöst. Warnungen können so konfiguriert werden, dass Benachrichtigungen über bestimmte Ereignisse per E-Mail gesendet werden. Warnungen können beispielsweise so konfiguriert werden, dass ein Operator über bestimmte Datenbankereignisse oder Betriebssystemzustände benachrichtigt wird, die umgehende Maßnahmen erfordern. Weitere Informationen zum Konfigurieren von Warnungen finden Sie unter [Warnungen](../../ssms/agent/alerts.md).  
  
-   Ein geplanter Task, z. B. eine Datenbanksicherung oder ein Replikationsereignis, wird erfolgreich durchgeführt oder erzeugt einen Fehler. Sie können mithilfe von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Mail beispielsweise Operatoren benachrichtigen, wenn ein Fehler bei der Verarbeitung am Monatsende auftritt.  
  
 
  
##  <a name="RelatedContent"></a> Themen zu Datenbank-E-Mail-Komponenten  
  
-   [Konfigurationsobjekte für Datenbank-E-Mail](database-mail-configuration-objects.md)  
  
-   [Messagingobjekte für Datenbank-E-Mail](database-mail-messaging-objects.md)  
  
-   [Externes Datenbank-E-Mail-Programm](database-mail-external-program.md)  
  
-   [Datenbank-E-Mail-Protokoll und -Überwachung](database-mail-log-and-audits.md)  
  
-   [Konfigurieren von SQL Server-Agent-Mail zum Verwenden von Datenbank-E-Mails](configure-sql-server-agent-mail-to-use-database-mail.md)  
  

  
  
