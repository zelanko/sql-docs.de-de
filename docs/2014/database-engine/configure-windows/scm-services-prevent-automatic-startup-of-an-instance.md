---
title: Verhindern des automatischen Starts einer Instanz von SQLServer (SQL Server-Konfigurations-Manager) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: d296f9a73138dd2a93cec5f3ae6ca62d257fd2fb
ms.sourcegitcommit: 04dd0620202287869b23cc2fde998a18d3200c66
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2018
ms.locfileid: "52640061"
---
# <a name="prevent-automatic-startup-of-an-instance-of-sql-server-sql-server-configuration-manager"></a>Verhindern des automatischen Starts einer Instanz von SQL Server (SQL Server-Konfigurations-Manager)
  In diesem Thema wird beschrieben, wie Sie in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe des SQL Server-Konfigurations-Managers verhindern können, dass eine Instanz von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] automatisch gestartet wird. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist normalerweise für den automatischen Start konfiguriert. Sie können diese Einstellung ändern, indem Sie den Startmodus für die Instanz auf manuell festlegen.  
  
##  <a name="SSMSProcedure"></a> Verwenden des SQL Server-Konfigurations-Managers  
  
#### <a name="to-prevent-automatic-startup-of-an-instance-of-sql-server"></a>So verhindern Sie das automatische Starten einer Instanz von SQL Server  
  
1.  Zeigen Sie im Menü **Start** auf **Alle Programme**, zeigen Sie auf [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], zeigen Sie auf **Konfigurationstools**, und klicken Sie dann auf **SQL Server-Konfigurations-Manager**.  
  
2.  Erweitern Sie im SQL Server-Konfigurations-Manager **Dienste**, und klicken Sie dann auf **SQL Server**.  
  
3.  Klicken Sie im Detailbereich mit der rechten Maustaste auf **MSSQLServer**, und klicken Sie dann auf **Eigenschaften**.  
  
4.  In der **SQL Server \< ***Instancename***> Eigenschaften** Dialogfeld die **Eigenschaften** legen den Wert der **Startmodus**zu **manuelle**.  
  
5.  Klicken Sie auf **OK**, um das Dialogfeld **SQL Server \<***Instanzname***> Eigenschaften** zu schließen, und schließen Sie dann den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Konfigurations-Manager.  
  
## <a name="see-also"></a>Siehe auch  
 [Starten, Beenden, Anhalten, Fortsetzen und Neustarten der Datenbank-Engine, SQL Server-Agent oder des SQL Server-Browsers](start-stop-pause-resume-restart-sql-server-services.md)  
  
  
