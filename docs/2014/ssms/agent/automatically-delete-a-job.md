---
title: Automatisches Löschen eines Auftrags | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- dropping jobs
- SQL Server Agent jobs, removing
- automatic job removal
- jobs [SQL Server Agent], deleting
- deleting jobs
- removing jobs
ms.assetid: 92dbb6da-5919-4bde-9354-d454e9ea3da0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7c5e165380c0f920ebf1366855e7801b6bb9089a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62472991"
---
# <a name="automatically-delete-a-job"></a>Automatically Delete a Job
  In diesem Thema wird beschrieben, wie Sie den [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] konfigurieren können, um Aufträge mithilfe von [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder SQL Server Management Objects automatisch zu löschen, wenn sie erfolgreich, fehlerhaft oder abgeschlossen sind.  
  
 Sie stellen sicher, dass Datenbankadministratoren wissen, wann Aufträge fertig gestellt sind und wie oft diese ausgeführt werden. Zu den typischen Auftragsantworten gehören folgende:  
  
-   Benachrichtigen des Operators per E-Mail, Pager oder **NET SEND** -Nachricht.  
  
     Verwenden Sie eine dieser Auftragsantworten vor allem dann, wenn der Operator weitere Schritte ausführen muss. Wenn beispielsweise ein Sicherungsauftrag erfolgreich ausgeführt wurde, muss der Operator darüber informiert werden, um das Sicherungsband entfernen zu können und an einem sicheren Standort aufbewahren zu lassen.  
  
-   Schreiben einer Ereignismeldung in das Windows-Anwendungsprotokoll.  
  
     Diese Art der Antwort können Sie nur bei fehlgeschlagenen Aufträgen verwenden.  
  
-   Automatisches Löschen des Auftrags.  
  
     Verwenden Sie diese Auftragsantwort, wenn Sie sicher sind, dass Sie diesen Auftrag nicht erneut ausführen müssen.  
  
 **In diesem Thema**  
  
-   **Vorbereitungen:**  
  
     [Security](#Security)  
  
-   **So geben Sie Auftragsantworten an mit**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
###  <a name="Security"></a> Sicherheit  
 Ausführliche Informationen finden Sie unter [Implementieren der SQL Server-Agent-Sicherheit](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Verwenden von SQL Server Management Studio  
  
#### <a name="to-automatically-delete-a-job"></a>So löschen Sie einen Auftrag automatisch  
  
1.  Stellen Sie im **Objekt-Explorer** eine Verbindung mit einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]her, und erweitern Sie dann diese Instanz.  
  
2.  Erweitern Sie **SQL Server-Agent**, erweitern Sie **Aufträge**, klicken Sie mit der rechten Maustaste auf den Auftrag, den Sie bearbeiten möchten, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Wählen Sie die Seite **Benachrichtigungen** aus.  
  
4.  Aktivieren Sie **Auftrag automatisch löschen**, und führen Sie eine der folgenden Handlungen aus:  
  
    -   Klicken Sie auf **Bei erfolgreicher Ausführung des Auftrags** , um den Auftragsstatus zu löschen, wenn der Auftrag erfolgreich abgeschlossen wurde.  
  
    -   Klicken Sie auf **Bei Auftragsfehler** , um den Auftrag zu löschen, wenn er nicht erfolgreich abgeschlossen wurde.  
  
    -   Klicken Sie auf **Beim Abschluss des Auftrags** , um den Auftrag unabhängig vom Abschlussstatus zu löschen.  
  
##  <a name="SMO"></a> Verwendung von SQL Server Management Objects  
 **So löschen Sie einen Auftrag automatisch**  
  
 Verwenden Sie die `DeleteLevel`-Eigenschaft der `Job`-Klasse in einer Programmiersprache Ihrer Wahl, z. B. Visual Basic, Visual C# oder PowerShell. Weitere Informationen finden Sie unter [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).  
  
  
