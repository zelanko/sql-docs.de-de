---
title: Konfigurieren von SQL Server-Agent-Mail zum Verwenden von Datenbank-E-Mails | Microsoft Dokumentation
ms.custom: ''
ms.date: 08/05/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], SQL Server Agent Mail
- SQL Server Agent Mail
ms.assetid: 4b8b61bd-4bd1-43cd-b6e5-c6ed2e101dce
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9676d4b30323368decbd1b164b16ec731396f30c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47685908"
---
# <a name="configure-sql-server-agent-mail-to-use-database-mail"></a>Konfigurieren von SQL Server-Agent-Mail zum Verwenden von Datenbank-E-Mails
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  In diesem Thema wird beschrieben, wie der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent mithilfe von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] zur Verwendung von Datenbank-E-Mails konfiguriert wird, damit Benachrichtigungen und Warnungen in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]versendet werden.  Weitere Informationen zum Konfigurieren der Funktion für Datenbank-E-Mail finden Sie unter [Konfigurieren von Datenbank-E-Mail](../../relational-databases/database-mail/configure-database-mail.md).  Ein Beispiel zur Verwendung von [!INCLUDE[tsql](../../includes/tsql-md.md)]finden Sie unter [Erstellen eines Profils für Datenbank-E-Mail](../../relational-databases/database-mail/create-a-database-mail-profile.md).
  
-   **Vorbereitungen:**  
  
-   [Erforderliche Komponenten](#Prerequisites)  
  
-   [Security](#Security)  
  
-   [So konfigurieren Sie mithilfe von SQL Server Management Studio den SQL Server-Agent zur Verwendung von Datenbank-E-Mail](#SSMSProcedure)  
  
-   [Anschlussaufgaben](#Follow_Up)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Prerequisites"></a> Erforderliche Komponenten  
  
-   [Aktivieren von Datenbank-E-Mail](../../relational-databases/database-mail/configure-database-mail.md).  
  
-    [Erstellen Sie ein Konto für Datenbank-E-Mail](../../relational-databases/database-mail/create-a-database-mail-account.md) zur Nutzung durch das Dienstkonto des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents.  
  
-   [Erstellen Sie ein Datenbank-E-Mail-Profil](../../relational-databases/database-mail/create-a-database-mail-profile.md) für das zu verwendende Konto des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienstes, und fügen Sie den Benutzer zur **DatabaseMailUserRole** in der **msdb** -Datenbank hinzu.  
  
-   Legen Sie das Profil als Standardprofil für die **msdb** -Datenbank fest.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Der Benutzer, der die Profilkonten erstellt und gespeicherte Prozeduren ausführt, sollte Mitglied der festen Serverrolle "sysadmin" sein.  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
 **So konfigurieren Sie den SQL Server-Agent zum Verwenden von Datenbank-E-Mail**  
  
-   Erweitern Sie im Objekt-Explorer eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz.  
  
-   Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent**, und klicken Sie anschließend auf **Eigenschaften**.  
  
-   Klicken Sie auf **Warnungssystem**.  
  
-   Wählen Sie **Mailprofil aktivieren**aus.  
  
-   Wählen Sie in der Liste **Mailsystem** die Option **Datenbank-E-Mail**aus.  
  
-   Wählen Sie in der Liste **Mailprofil**ein Mailprofil für Datenbank-E-Mail aus.  
  
-   Starten Sie SQL Server-Agent neu.  
  
##  <a name="Follow_Up"></a> Anschlussaufgaben  
 Die folgenden Aufgaben sind zum Abschließen der Konfiguration des Agents zum Senden von Warnungen und Benachrichtigungen erforderlich:  
  
-   [Warnungen](../../ssms/agent/alerts.md)  
  
     Warnungen können zum Benachrichtigen eines Operators über ein bestimmtes Datenbankereignis oder eine Betriebssystembedingung konfiguriert werden.  
  
-   [Operatoren](../../ssms/agent/operators.md)  
  
     Operatoren sind Aliase für Personen oder Gruppen, die elektronische Benachrichtigung empfangen können.  
  
  
