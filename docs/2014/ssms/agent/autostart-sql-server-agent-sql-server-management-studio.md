---
title: Autostart SQL Server Agent (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL Server Agent, starting
- autostart SQL Server Agent
ms.assetid: 2ea332da-0ede-4d2b-b122-c4c10eaca191
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5348c17d3b481212d9b9795dfa8e9e2cc5d945fa
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36147614"
---
# <a name="autostart-sql-server-agent-sql-server-management-studio"></a>Autostart SQL Server Agent (SQL Server Management Studio)
  In diesem Thema wird beschrieben, wie der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent konfiguriert wird, um nach einem unerwarteten Abbruch in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]automatisch neu gestartet zu werden.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Einschränkungen](#Restrictions)  
  
     [Security](#Security)  
  
-   [So konfigurieren Sie den automatischen Neustart des SQL Server-Agents mithilfe von SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
  
###  <a name="Restrictions"></a> Einschränkungen  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Knoten wird nur im Objekt-Explorer angezeigt, wenn Sie die Berechtigung besitzen, ihn zu verwenden.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent muss zur Verwendung der Anmeldeinformationen eines Kontos konfiguriert werden, das Mitglied der festen Serverrolle **sysadmin** in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ist, um seine Funktionen ausführen zu können. Das Konto muss über die folgenden Windows-Berechtigungen verfügen:  
  
-   Anmelden als Dienst (SeServiceLogonRight)  
  
-   Ersetzen von Token auf Prozessebene (SeAssignPrimaryTokenPrivilege)  
  
-   Umgehen von durchsuchenden Prüfungen (SeChangeNotifyPrivilege)  
  
-   Anpassen des Arbeitsspeicherkontingents für einen Prozess (SeIncreaseQuotaPrivilege)  
  
 Weitere Informationen zu den Windows-Berechtigungen erforderlich sind, für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienstkonto, finden Sie unter [wählen Sie ein Konto für den SQL Server-Agent-Dienst](select-an-account-for-the-sql-server-agent-service.md) und [Konfigurieren von Windows-Dienstkonten und Berechtigungen](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
##  <a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-configure-sql-server-agent-to-automatically-restart"></a>So konfigurieren Sie den automatischen Neustart des SQL Server-Agents  
  
1.  Klicken Sie im **Objekt-Explorer** auf das Pluszeichen, um den Server zu erweitern, auf dem Sie den automatischen Neustart des SQL Server Agents konfigurieren möchten.  
  
2.  Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent**, und klicken Sie anschließend auf **Eigenschaften**.  
  
3.  Aktivieren Sie auf der Seite **Allgemein** das Kontrollkästchen **SQL Server-Agent nach unerwartetem Beenden automatisch neu starten**.  
  
  