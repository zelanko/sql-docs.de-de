---
title: Konfigurieren von Serverstartoptionen (SQL Server-Konfigurations-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- parameters [SQL Server], startup options
- SQL Server, startup options
- single-user mode [SQL Server], starting in
- startup options [SQL Server]
- SQL Server services, setting startup options
ms.assetid: 7a94643c-6460-4baf-bb31-0cb99eaf970d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 91a48d4acd771c19617bac26c1393f30334768e8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62810368"
---
# <a name="configure-server-startup-options-sql-server-configuration-manager"></a>Konfigurieren von Serverstartoptionen (SQL Server-Konfigurations-Manager)
  In diesem Thema wird beschrieben, wie Sie Startoptionen, die bei jedem Starten von [!INCLUDE[ssDE](../../includes/ssde-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] verwendet werden, mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfigurations-Managers konfigurieren. Weitere Informationen finden Sie unter [Startoptionen für den Datenbank-Engine-Dienst](database-engine-service-startup-options.md).  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungen  
  
### <a name="limitations-and-restrictions"></a>Einschränkungen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager schreibt Startparameter in die Registrierung. Diese werden beim nächsten Start von [!INCLUDE[ssDE](../../includes/ssde-md.md)]wirksam.  
  
 Bei einem Cluster müssen Änderungen auf dem aktiven Server vorgenommen werden, während [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] online ist und werden beim nächsten Start von [!INCLUDE[ssDE](../../includes/ssde-md.md)] wirksam. Die Registrierungsaktualisierung der Startoptionen auf dem anderen Knoten findet beim nächsten Failover statt.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Die Konfiguration von Serverstartoptionen ist auf Benutzer beschränkt, die die entsprechenden Einträge in der Registrierung ändern können. Dazu gehören folgende Benutzer.  
  
-   Mitglieder der lokalen Administratorgruppe.  
  
-   Das Domänenkonto, das von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]verwendet wird, wenn [!INCLUDE[ssDE](../../includes/ssde-md.md)] für die Ausführung unter einem Domänenkonto konfiguriert ist.  
  
##  <a name="SSMSProcedure"></a> Verwenden des SQL Server-Konfigurations-Managers  
  
#### <a name="to-configure-startup-options"></a>So konfigurieren Sie Startoptionen  
  
1.  Klicken Sie im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager auf **SQL Server-Dienste**.  
  
    > [!NOTE]  
    >  Da der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager ein Snap-In für das [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Verwaltungskonsolenprogramm und kein eigenständiges Programm ist, wird der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager in neueren Versionen von Windows nicht als Anwendung angezeigt.  
    >   
    >  -   **Windows 10**:  
    >          Zum Öffnen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Konfigurations-Manager auf die **Startseite**, geben Sie SQLServerManager12.msc (für [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]). Ersetzen Sie für frühere Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 12 durch eine kleinere Zahl. Wenn SQLServerManager12.msc, wird der Konfigurations-Manager geöffnet. Um den Konfigurations-Manager an die Startseite oder Taskleiste anzuheften, mit der rechten Maustaste SQLServerManager12.msc, und klicken Sie dann auf **Dateispeicherort öffnen**. In den Windows-Datei-Explorer mit der rechten Maustaste SQLServerManager12.msc, und klicken Sie dann auf **an Startmenü anheften** oder **an Taskleiste anheften**.  
    > -   **Windows 8**:  
    >          Zum Öffnen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager in der **Suche** charm **Apps**, Typ **SQLServerManager\<Version > .msc** wie z. B. `SQLServerManager12.msc`, und drücken Sie dann die **EINGABETASTE**.  
  
2.  Klicken Sie im rechten Bereich mit der rechten Maustaste auf **SQL Server (***<Instanzname>***)**, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Geben Sie auf der Registerkarte **Startparameter** im Feld **Startparameter angeben** den Parameter ein, und klicken Sie anschließend auf **Hinzufügen**.  
  
     Um im Einzelbenutzermodus starten, geben Sie z. B. `-m` in die **Startparameter angeben** ein, und klicken Sie dann auf **hinzufügen**. (Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Einzelbenutzermodus erneut starten, müssen Sie zunächst den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent beenden. Andernfalls stellt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent möglicherweise zuerst eine Verbindung her und verhindert, dass Sie als zweiter Benutzer eine Verbindung herstellen können.)  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
5.  Starten Sie [!INCLUDE[ssDE](../../includes/ssde-md.md)]neu.  
  
    > [!WARNING]  
    >  Wenn Sie nicht mehr im Einzelbenutzermodus, im Feld Startparameter im Feld arbeiten, wählen Sie die `-m` Parameter in der **vorhandene Parameter** ein, und klicken Sie dann auf **entfernen**. Starten Sie [!INCLUDE[ssDE](../../includes/ssde-md.md)] erneut, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im typischen Multibenutzermodus wiederherzustellen.  
  
## <a name="see-also"></a>Siehe auch  
 [Starten von SQL Server im Einzelbenutzermodus](start-sql-server-in-single-user-mode.md)   
 [Herstellen einer Verbindung mit SQL Server, wenn Systemadministratoren gesperrt sind](connect-to-sql-server-when-system-administrators-are-locked-out.md)   
 [Starten, Beenden oder Anhalten des SQL Server-Agent-Diensts](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  
