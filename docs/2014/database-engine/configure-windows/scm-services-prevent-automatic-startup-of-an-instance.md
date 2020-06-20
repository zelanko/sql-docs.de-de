---
title: Verhindern des automatischen Starts einer Instanz von SQL Server (SQL Server-Konfigurations-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- automatic SQL Server startup
- SQL Server, stopping
- SQL Server, automatic startup
- canceling automatic startup
- stopping SQL Server
- preventing automatic startups [SQL Server]
ms.assetid: 782663cf-f3d7-4cc6-b621-21e4550f0322
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8f93f5abc749f589ab4208b3a4c9434ca63b8769
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935036"
---
# <a name="prevent-automatic-startup-of-an-instance-of-sql-server-sql-server-configuration-manager"></a>Verhindern des automatischen Starts einer Instanz von SQL Server (SQL Server-Konfigurations-Manager)
  In diesem Thema wird beschrieben, wie Sie in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe des SQL Server-Konfigurations-Managers verhindern können, dass eine Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] automatisch gestartet wird. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist normalerweise für den automatischen Start konfiguriert. Sie können diese Einstellung ändern, indem Sie den Startmodus für die Instanz auf manuell festlegen.  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> Verwenden des SQL Server-Konfigurations-Managers  
  
#### <a name="to-prevent-automatic-startup-of-an-instance-of-sql-server"></a>So verhindern Sie das automatische Starten einer Instanz von SQL Server  
  
1.  Zeigen Sie im Menü **Start** auf **Alle Programme**, zeigen Sie auf [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], zeigen Sie auf **Konfigurationstools**, und klicken Sie dann auf **SQL Server-Konfigurations-Manager**.  
  
2.  Erweitern Sie in SQL Server-Konfigurations-Manager den Eintrag **Dienste**, und klicken Sie dann auf **SQL Server**.  
  
3.  Klicken Sie im Detailbereich mit der rechten Maustaste auf **MSSQLServer**, und klicken Sie dann auf **Eigenschaften**.  
  
4.  Legen Sie im Dialogfeld **SQL Server \<**_instancename_**> Eigenschaften** im Feld **Eigenschaften** den Wert für **Start Modus** auf **manuell**fest.  
  
5.  Klicken Sie auf **OK** , um das Dialogfeld **SQL Server \<**_instancename_**> Eigenschaften** zu schließen, und schließen Sie dann [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten, Beenden, Anhalten, Fortsetzen und Neustarten der Datenbank-Engine, SQL Server-Agent oder des SQL Server-Browsers](start-stop-pause-resume-restart-sql-server-services.md)  
  
  
