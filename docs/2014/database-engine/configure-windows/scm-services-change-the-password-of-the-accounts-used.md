---
title: Ändern des Kennworts der von SQLServer (SQL Server-Konfigurations-Manager) verwendeten Konten | Microsoft Docs
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- expired password [SQL Server], SQL Server Agent
- passwords [SQL Server], SQL Server Agent service
- passwords [SQL Server], changing
- expired password [SQL Server], Database Engine
- passwords [SQL Server], SQL Server service
- Database Engine [SQL Server], passwords
- changing passwords used by SQL Server
- modifying passwords
ms.assetid: 5b6dcc03-6cae-45d3-acef-6f85ca6d615f
caps.latest.revision: 21
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 3e1e028266d7c260652f361da13c51d81b9197fe
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049766"
---
# <a name="change-the-password-of-the-accounts-used-by-sql-server-sql-server-configuration-manager"></a>Ändern des Kennworts der von SQL Server verwendeten Konten (SQL Server-Konfigurations-Manager)
  In diesem Thema wird beschrieben, wie Sie das Kennwort der vom [!INCLUDE[ssDE](../../includes/ssde-md.md)] und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] verwendeten Konten mithilfe des SQL Server-Konfigurations-Managers ändern können. Das [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] und der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent werden auf einem Computer als Dienst ausgeführt, der Anmeldeinformationen verwendet, die während des Setups hinterlegt wurden. Wenn die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unter einem Domänenkonto ausgeführt wird und das Kennwort für dieses Konto geändert wird, muss das von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendete Kennwort auf das neue Kennwort aktualisiert werden. Wird das Kennwort nicht aktualisiert, verliert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] möglicherweise den Zugriff auf einige Domänenressourcen. Wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beendet, kann der Dienst erst wieder neu gestartet werden, wenn das Kennwort aktualisiert wurde.  
  
 Informationen zum Ändern der Kennwörter für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung finden Sie unter [Kennwort abgelaufen](../password-expired.md).  
  
##  <a name="BeforeYouBegin"></a> Vorbereitungsmaßnahmen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager ist das Tool, das zum Ändern der Einstellungen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienste entwickelt und autorisiert wurde. Wenn Sie einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst mithilfe des Dienststeuerungs-Managers von Windows (**services.msc**) ändern, ändert die Anwendung nicht immer alle erforderlichen Einstellungen und verhindert u. U., dass der Dienst einwandfrei funktioniert. Nachdem Sie in einer Clusterumgebung das Kennwort für den aktiven Knoten mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Managers geändert haben, müssen Sie das Kennwort für den passiven Knoten jedoch mithilfe des Dienststeuerungs-Managers ändern.  
  
###  <a name="Security"></a> Sicherheit  
  
####  <a name="Permissions"></a> Berechtigungen  
 Sie können nur als Administrator des Computers das von einem Dienst verwendete Konto ändern.  
  
##  <a name="SSMSProcedure"></a> Verwenden des SQL Server-Konfigurations-Managers  
  
#### <a name="to-change-the-password-used-by-the-sql-server-database-engine-service"></a>So ändern Sie das vom SQL Server-Dienst (Datenbank-Engine-Dienst) verwendete Kennwort  
  
1.  Klicken Sie auf **Start** , zeigen Sie auf **Alle Programme**, zeigen Sie auf [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], zeigen Sie auf **Konfigurationstools**, und klicken Sie dann auf **SQL Server-Konfigurations-Manager**.  
  
    > [!NOTE]  
    >  Da der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager ein Snap-In für das [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Verwaltungskonsolenprogramm und kein eigenständiges Programm ist, wird der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager in neueren Versionen von Windows nicht als Anwendung angezeigt.  
    >   
    >  -   **Windows 10**:  
    >          So öffnen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Konfigurations-Manager auf die **Startseite**, geben Sie SQLServerManager12.msc (für [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]). Für frühere Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 12 durch eine kleinere Zahl ersetzen. SQLServerManager12.msc klicken, wird der Configuration Manager geöffnet. Um den Konfigurations-Manager an die Startseite oder Taskleiste anzuheften, mit der rechten Maustaste SQLServerManager12.msc, und klicken Sie dann auf **Dateispeicherort öffnen**. Im Windows-Explorer mit der rechten Maustaste SQLServerManager12.msc, und klicken Sie dann auf **an Startmenü anheften** oder **an Taskleiste anheften**.  
    > -   **Windows 8**:  
    >          So öffnen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager in der **Suche** charm unter **Apps**, Typ **SQLServerManager\<Version > .msc** z. B. `SQLServerManager12.msc`, und drücken Sie dann die **EINGABETASTE**.  
  
2.  Klicken Sie im SQL Server-Konfigurations-Manager auf **SQL Server-Dienste**.  
  
3.  Klicken Sie im Detailbereich mit der rechten Maustaste auf **SQL Server (**\<Instanzname>**)**, und klicken Sie dann auf **Eigenschaften**.  
  
4.  Geben Sie im Dialogfeld **Eigenschaften von SQL Server (**\<Instanzname>**)** auf der Registerkarte „Anmelden“ für das im Feld **Kontoname** angegebene Konto das neue Kennwort in die Felder **Kennwort** und **Kennwort bestätigen** ein, und klicken Sie dann auf **OK**.  
  
     Das Kennwort wird sofort wirksam, ohne dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]neu gestartet werden muss.  
  
#### <a name="to-change-the-password-used-by-the-sql-server-agent-service"></a>So ändern Sie das vom SQL Server-Agent-Dienst verwendete Kennwort  
  
1.  Klicken Sie auf **Start** , zeigen Sie auf **Alle Programme**, zeigen Sie auf [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], zeigen Sie auf **Konfigurationstools**, und klicken Sie dann auf **SQL Server-Konfigurations-Manager**.  
  
2.  Klicken Sie im SQL Server-Konfigurations-Manager auf **SQL Server-Dienste**.  
  
3.  Klicken Sie im Detailbereich mit der rechten Maustaste auf **SQL Server Agent (**\<Instanzname>**)**, und klicken Sie dann auf **Eigenschaften**.  
  
4.  Geben Sie im Dialogfeld **Eigenschaften von SQL Server-Agent (**\<Instanzname>**)** auf der Registerkarte „Anmelden“ für das im Feld **Kontoname** angegebene Konto das neue Kennwort in die Felder **Kennwort** und **Kennwort bestätigen** ein, und klicken Sie dann auf **OK**.  
  
     Bei einer eigenständigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz ist das Kennwort sofort wirksam, ohne dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]neu gestartet werden muss. Auf einer gruppierten Instanz kann die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ressource von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] offline geschaltet werden und einen Neustart erfordern.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Diensten: Themen zur Vorgehensweise &#40;SQL Server-Konfigurations-Manager&#41;](../managing-services-how-to-topics-sql-server-configuration-manager.md)  
  
  