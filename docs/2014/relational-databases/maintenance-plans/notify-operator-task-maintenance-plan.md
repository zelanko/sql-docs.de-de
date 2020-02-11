---
title: Task 'Operator benachrichtigen' (Wartungsplan) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.notifyoperator.f1
helpviewer_keywords:
- Notify Operator Task dialog box
ms.assetid: 39c0797c-ad2b-4591-85c9-a23a7f902895
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0ef94ed9e296c588b70789ace0bbbbe79bc8008f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68205965"
---
# <a name="notify-operator-task-maintenance-plan"></a>Task 'Operator benachrichtigen' (Wartungsplan)
  Im Dialogfeld " **Operatoren benachrichtigen** " können Sie dem Wartungsplan eine automatische Benachrichtigung hinzufügen. Um diese Aufgabe verwenden zu können, muss Datenbank-E-Mail aktiviert und ordnungsgemäß mit msdb als Mailhost-Datenbank konfiguriert sein, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und es muss ein-Agent-Operator mit einer gültigen e-Mail-Adresse vorhanden sein.  
  
 Dieser Task verwendet die gespeicherte Prozedur sp_notify_operator.  
  
## <a name="options"></a>Tastatur  
 **Verbindung**  
 Wählen Sie die Serververbindung aus, die bei der Ausführung dieses Tasks verwendet werden soll.  
  
 **Neu**  
 Erstellen Sie eine neue Serververbindung, die bei der Ausführung dieses Tasks verwendet werden soll. Das Dialogfeld **Neue Verbindung** wird im Folgenden beschrieben.  
  
 **Zu benachrichtigende Operatoren**  
 Gibt den Empfänger der E-Mail an.  
  
 **Betreff der Benachrichtigungs Meldung**  
 Geben Sie den Text an, der in der Betreffzeile der Benachrichtigungsmeldung enthalten sein soll.  
  
 **Benachrichtigungs Nachrichtentext**  
 Geben Sie den Text an, der in dem Textkörper der Benachrichtigungsmeldung enthalten sein soll.  
  
 **T-SQL anzeigen**  
 Zeigt die [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen an, die für diesen Task auf dem Server auf Basis der ausgewählten Optionen ausgeführt werden.  
  
> [!NOTE]  
>  Wenn die Anzahl der betroffenen Objekte groß ist, kann die Anzeige erhebliche Zeit in Anspruch nehmen.  
  
## <a name="new-connection-dialog-box"></a>Neue Verbindung (Dialogfeld)  
 **Verbindungs Name**  
 Geben Sie einen Namen für die neue Verbindung ein.  
  
 **Servernamen auswählen oder eingeben**  
 Wählen Sie den Server aus, zu dem bei der Ausführung dieses Tasks eine Verbindung hergestellt werden soll.  
  
 **Aktualisieren**  
 Mithilfe dieser Option aktualisieren Sie die Liste der verfügbaren Server.  
  
 **Geben Sie Informationen ein, um sich beim Server anzumelden.**  
 Legt fest, wie die Authentifizierung gegenüber dem Server stattfindet.  
  
 **Integrierte Sicherheit von Windows verwenden**  
 Stellen Sie mithilfe der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Authentifizierung eine Verbindung mit einer Instanz von her.  
  
 **Einen bestimmten Benutzernamen und ein bestimmtes Kennwort verwenden**  
 Stellt mithilfe der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] -Authentifizierung eine Verbindung zu einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] her. Diese Option ist nicht verfügbar.  
  
 **Benutzername**  
 Stellt eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung für den Gebrauch bei der Authentifizierung bereit. Diese Option ist nicht verfügbar.  
  
 **Kennwort**  
 Stellt ein Kennwort für den Gebrauch bei der Authentifizierung bereit. Diese Option ist nicht verfügbar.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-E-Mail](../database-mail/database-mail.md)   
 [sp_notify_operator &#40;Transact-SQL-&#41;](/sql/relational-databases/system-stored-procedures/sp-notify-operator-transact-sql)  
  
  
