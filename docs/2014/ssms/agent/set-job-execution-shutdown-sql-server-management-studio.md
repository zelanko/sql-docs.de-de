---
title: Festlegen des Herunterfahrens der Auftragsausführung (SQL Server Management Studio) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], stopping
- SQL Server Agent jobs, stopping
- stopping jobs
- SQL Server Agent jobs, execution shutdowns
ms.assetid: ac23e88f-53fc-41de-bb16-0c27c002d5a5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ca9343fe8a6f9e89ba9f26dbbbb12dd7362aff91
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63033602"
---
# <a name="set-job-execution-shutdown-sql-server-management-studio"></a>Set Job Execution Shutdown (SQL Server Management Studio)
  In diesem Thema wird beschrieben, wie Sie die [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Zeit festlegen, die der-Agent auf die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Beendigung von Ausführungs Aufträgen [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] wartet, [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]bevor der-Agent selbst in mithilfe von abgeschlossen wird  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Sicherheit](#Security)  
  
-   **So legen Sie eine Zeit für das Herunterfahren für einen SQL Server-Agent-Auftrag fest mit**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Standardmäßig können Mitglieder der festen Serverrolle **sysadmin** festlegen, wie lange der [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent auf die Beendigung von ausgeführten Aufträgen wartet, bevor der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent selbst beendet wird. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-set-job-execution-shutdown"></a>So legen Sie das Herunterfahren der Auftragsausführung fest  
  
1.  Klicken Sie im **Objekt-Explorer** auf das Pluszeichen, um den Server zu erweitern, auf dem Sie ein Intervall für das Herunterfahren der Auftragsausführung festlegen möchten.  
  
2.  Klicken Sie mit der rechten Maustaste auf **SQL Server-Agent** , und wählen Sie **Eigenschaften**aus.  
  
3.  Wählen Sie unter **Seite auswählen**die Option **Auftragssystem**aus.  
  
4.  Erhöhen oder reduzieren Sie den Wert für **Timeoutintervall beim Herunterfahren (Sekunden)** . Damit wird bestimmt, wie lange der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent auf die Beendigung von ausführenden Aufträgen wartet, bevor der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent selbst beendet wird.  
  
  
