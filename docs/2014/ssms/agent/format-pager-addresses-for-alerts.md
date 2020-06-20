---
title: Formatieren von Pageradressen für Warnungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- pager addresses [SQL Server]
- SQL Server Agent, alerts
- formats [SQL Server], pager addresses
- pager notifications [SQL Server]
- addresses [SQL Server]
- alerts [SQL Server], pager addresses
ms.assetid: a9797d01-1050-442c-9038-ed4bfee1e76a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3754afbc5d8f0f67dac61e785a4626c8ced4c2e9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "84995299"
---
# <a name="format-pager-addresses-for-alerts"></a>Format Pager Addresses for Alerts
  In diesem Thema wird beschrieben, wie Pager-Adressen für- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Warnungen in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] mithilfe von oder formatiert werden [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **So formatieren Sie Pageradressen mit**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Standardmäßig können nur Mitglieder der festen Serverrolle **sysadmin** Information über eine Warnung anzeigen. Andere Benutzer müssen Mitglieder der festen Datenbankrolle **SQLAgentOperatorRole** in der **msdb** -Datenbank sein.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-format-pager-addresses"></a>So formatieren Sie Pageradressen  
  
1.  Klicken Sie im **Objekt-Explorer** auf das Pluszeichen, um den Server zu erweitern, der die Warnung enthält, die Sie an einen Pager senden möchten.  
  
2.  Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent** und wählen Sie **Eigenschaften**  
  
3.  Wählen Sie unter **Seite auswählen**die Option **Warnungssystem**aus.  
  
4.  Geben Sie in die Felder **An-Zeile** und **Cc-Zeile** des Felds **Adressformatierung für Pager-E-Mails:** das Präfix oder das Suffix der Pageradresse ein. Die eigentliche Pageradresse des Operators wird beim Senden einer Benachrichtigung eingefügt.  
  
5.  Geben Sie in das Feld **Betreff** das Präfix oder Suffix der Betreffzeile ein.  
  
6.  Aktivieren Sie das Kontrollkästchen **Nachrichtenbereich der E-Mail in Benachrichtigungsseite aufnehmen** , um die vollständige E-Mail-Nachricht in die Pagernachricht einzuschließen (statt lediglich die Betreffzeile).  
  
7.  Wenn Sie fertig sind, klicken Sie auf **OK**.  
  
  
