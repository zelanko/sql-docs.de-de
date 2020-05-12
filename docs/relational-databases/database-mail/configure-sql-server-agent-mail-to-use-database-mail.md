---
title: Konfigurieren von SQL Server-Agent-Mail zum Verwenden von Datenbank-E-Mails
ms.date: 08/05/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], SQL Server Agent Mail
- SQL Server Agent Mail
ms.assetid: 4b8b61bd-4bd1-43cd-b6e5-c6ed2e101dce
author: stevestein
ms.author: sstein
ms.custom: seo-dt-2019
ms.openlocfilehash: 1e449c95c6dd087eaa70de48b1fb79ac8d7b6f6c
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763201"
---
# <a name="configure-sql-server-agent-mail-to-use-database-mail"></a>Konfigurieren von SQL Server-Agent-Mail zum Verwenden von Datenbank-E-Mails
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In diesem Thema wird beschrieben, wie der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent mithilfe von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] zur Verwendung von Datenbank-E-Mails konfiguriert wird, damit Benachrichtigungen und Warnungen in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]versendet werden.  Weitere Informationen zum Konfigurieren der Funktion für Datenbank-E-Mail finden Sie unter [Konfigurieren von Datenbank-E-Mail](../../relational-databases/database-mail/configure-database-mail.md).  Ein Beispiel zur Verwendung von [!INCLUDE[tsql](../../includes/tsql-md.md)]finden Sie unter [Erstellen eines Profils für Datenbank-E-Mail](../../relational-databases/database-mail/create-a-database-mail-profile.md).
  
-   **Vorbereitungen:**  
  
-   [Voraussetzungen](#Prerequisites)  
  
-   [Sicherheit](#Security)  
  
-   [So konfigurieren Sie mithilfe von SQL Server Management Studio den SQL Server-Agent zur Verwendung von Datenbank-E-Mail](#SSMSProcedure)  
  
-   [Anschlussaufgaben](#Follow_Up)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
  > [!NOTE]
  > In einer verwalteten Instanz ist der SQL-Agent immer so konfiguriert, dass Datenbank-E-Mail verwendet wird. Daher gilt dieser Artikel nicht für verwaltete Instanzen. In einer verwalteten Instanz benötigen Sie ein Profil mit dem Namen **[AzureManagedInstance_dbmail_profile](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)** , um den SQL-Agent an Datenbank-E-Mail zu binden. 
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Voraussetzungen  
  
-   [Aktivieren von Datenbank-E-Mail](../../relational-databases/database-mail/configure-database-mail.md).  
  
-    [Erstellen Sie ein Konto für Datenbank-E-Mail](../../relational-databases/database-mail/create-a-database-mail-account.md) zur Nutzung durch das Dienstkonto des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents.  
  
-   [Erstellen Sie ein Datenbank-E-Mail-Profil](../../relational-databases/database-mail/create-a-database-mail-profile.md) für das zu verwendende Konto des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienstes, und fügen Sie den Benutzer zur **DatabaseMailUserRole** in der **msdb** -Datenbank hinzu.
  
-   Legen Sie das Profil als Standardprofil für die **msdb** -Datenbank fest.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Der Benutzer, der die Profilkonten erstellt und gespeicherte Prozeduren ausführt, sollte Mitglied der festen Serverrolle "sysadmin" sein.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 **So konfigurieren Sie den SQL Server-Agent zum Verwenden von Datenbank-E-Mail**  
  
-   Erweitern Sie im Objekt-Explorer eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz.  
  
-   Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent**, und klicken Sie anschließend auf **Eigenschaften**.  
  
-   Klicken Sie auf **Warnungssystem**.  
  
-   Wählen Sie **Mailprofil aktivieren**aus.  
  
-   Wählen Sie in der Liste **Mailsystem** die Option **Datenbank-E-Mail**aus.  
  
-   Wählen Sie in der Liste **Mailprofil**ein Mailprofil für Datenbank-E-Mail aus. 
  
-   Starten Sie den SQL Server-Agent neu.  
  
##  <a name="follow-up-tasks"></a><a name="Follow_Up"></a> Anschlussaufgaben  
 Die folgenden Aufgaben sind zum Abschließen der Konfiguration des Agents zum Senden von Warnungen und Benachrichtigungen erforderlich:  
  
-   [Warnungen](../../ssms/agent/alerts.md)  
  
     Warnungen können zum Benachrichtigen eines Operators über ein bestimmtes Datenbankereignis oder eine Betriebssystembedingung konfiguriert werden.  
  
-   [Operatoren](../../ssms/agent/operators.md)  
  
     Operatoren sind Aliase für Personen oder Gruppen, die elektronische Benachrichtigung empfangen können.  
  
  
