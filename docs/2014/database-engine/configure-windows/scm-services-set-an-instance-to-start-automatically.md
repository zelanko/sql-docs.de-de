---
title: Eine Instanz von SQLServer automatisch auf Start festgelegt (SQL Server-Konfigurations-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- automatic SQL Server startup
- SQL Server, automatic startup
- starting SQL Server, automatically
ms.assetid: aa2b6bde-e76d-4fea-a560-54a63745d9b1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1b1b13c560919c8538b7f83441992687d811ad1f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48155876"
---
# <a name="set-an-instance-of-sql-server-to-start-automatically-sql-server-configuration-manager"></a>Festlegen des automatischen Starts einer Instanz von SQL Server (SQL Server-Konfigurations-Manager)
  In diesem Thema wird beschrieben, wie Sie in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe des SQL Server-Konfigurations-Managers festlegen können, dass eine Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] automatisch gestartet wird. Bei der Installation wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] normalerweise für den automatischen Start konfiguriert. Diese Einstellung kann jederzeit geändert werden.  
  
##  <a name="SSMSProcedure"></a> Verwenden des SQL Server-Konfigurations-Managers  
  
#### <a name="to-set-an-instance-of-sql-server-to-start-automatically"></a>So legen Sie für eine Instanz von SQL Server den automatischen Start fest  
  
1.  Zeigen Sie im Menü **Start** auf **Alle Programme**, zeigen Sie auf [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], zeigen Sie auf **Konfigurationstools**, und klicken Sie dann auf **SQL Server-Konfigurations-Manager**.  
  
    > [!NOTE]  
    >  Da der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager ein Snap-In für die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Management Console und kein eigenständiges Programm ist, wird der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager in neueren Versionen von Windows nicht als Anwendung angezeigt.  
    >   
    >  -   **Windows 10**:  
    >          Zum Öffnen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Konfigurations-Manager auf die **Startseite**, geben Sie SQLServerManager12.msc (für [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]). Für frühere Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 12 durch eine kleinere Zahl ersetzen. Wenn SQLServerManager12.msc, wird der Konfigurations-Manager geöffnet. Um den Konfigurations-Manager an die Startseite oder Taskleiste anzuheften, mit der rechten Maustaste SQLServerManager12.msc, und klicken Sie dann auf **Dateispeicherort öffnen**. In den Windows-Datei-Explorer mit der rechten Maustaste SQLServerManager12.msc, und klicken Sie dann auf **an Startmenü anheften** oder **an Taskleiste anheften**.  
    > -   **Windows 8**:  
    >          Zum Öffnen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager in der **Suche** charm **Apps**, Typ **SQLServerManager\<Version > .msc** wie z. B. `SQLServerManager12.msc`, und drücken Sie dann die **EINGABETASTE**.  
  
2.  Erweitern Sie in **SQL Server-Konfigurations-Manager**den Ordner **Services**, und klicken Sie dann auf **SQL Server**.  
  
3.  Klicken Sie im Detailbereich mit der rechten Maustaste auf den Namen der Instanz, die automatisch gestartet werden soll, und klicken Sie dann auf **Eigenschaften**.  
  
4.  Legen Sie im Dialogfeld **SQL Server \<***Instanzname***> Eigenschaften** unter **Startmodus** die Option **Automatisch** fest.  
  
5.  Klicken Sie auf **OK**, und schließen Sie dann den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager.  
  
## <a name="see-also"></a>Siehe auch  
 [Verhindern des automatischen Starts einer Instanz von SQL Server &#40;SQL Server-Konfigurations-Manager&#41;](scm-services-prevent-automatic-startup-of-an-instance.md)   
 [Herstellen einer Verbindung mit einem anderen Computer (SQL Server-Konfigurations-Manager)](scm-services-connect-to-another-computer.md)   
 [Konfigurieren von WMI zum Anzeigen des Serverstatus in SQL Server-Tools](../../ssms/configure-wmi-to-show-server-status-in-sql-server-tools.md)  
  
  
