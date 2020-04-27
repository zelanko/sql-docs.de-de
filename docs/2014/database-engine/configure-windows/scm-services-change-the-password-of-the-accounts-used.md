---
title: Ändern des Kennworts für die von SQL Server verwendeten Konten (SQL Server-Konfigurations-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/07/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
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
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 865c23dc88571e0c9ee317eca280286a6c37118f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62810435"
---
# <a name="change-the-password-of-the-accounts-used-by-sql-server-sql-server-configuration-manager"></a>Ändern des Kennworts der von SQL Server verwendeten Konten (SQL Server-Konfigurations-Manager)
  In diesem Thema wird beschrieben, wie Sie das Kennwort der vom [!INCLUDE[ssDE](../../includes/ssde-md.md)] und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] verwendeten Konten mithilfe des SQL Server-Konfigurations-Managers ändern können. Das [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] und der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent werden auf einem Computer als Dienst ausgeführt, der Anmeldeinformationen verwendet, die während des Setups hinterlegt wurden. Wenn die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unter einem Domänenkonto ausgeführt wird und das Kennwort für dieses Konto geändert wird, muss das von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendete Kennwort auf das neue Kennwort aktualisiert werden. Wird das Kennwort nicht aktualisiert, verliert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] möglicherweise den Zugriff auf einige Domänenressourcen. Wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beendet, kann der Dienst erst wieder neu gestartet werden, wenn das Kennwort aktualisiert wurde.  
  
 Informationen zum Ändern der Kennwörter für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Authentifizierung finden Sie unter [Kennwort abgelaufen](../password-expired.md).  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Vorbereitungen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager ist das Tool, das zum Ändern der Einstellungen der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienste entwickelt und autorisiert wurde. Wenn Sie einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst mithilfe des Dienststeuerungs-Managers von Windows (**services.msc**) ändern, ändert die Anwendung nicht immer alle erforderlichen Einstellungen und verhindert u. U., dass der Dienst einwandfrei funktioniert. Nachdem Sie in einer Clusterumgebung das Kennwort für den aktiven Knoten mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Managers geändert haben, müssen Sie das Kennwort für den passiven Knoten jedoch mithilfe des Dienststeuerungs-Managers ändern.  
  
###  <a name="security"></a><a name="Security"></a> Sicherheit  
  
####  <a name="permissions"></a><a name="Permissions"></a> Berechtigungen  
 Sie können nur als Administrator des Computers das von einem Dienst verwendete Konto ändern.  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> Verwenden des SQL Server-Konfigurations-Managers  
  
#### <a name="to-change-the-password-used-by-the-sql-server-database-engine-service"></a>So ändern Sie das vom SQL Server-Dienst (Datenbank-Engine-Dienst) verwendete Kennwort  
  
1.  Klicken Sie auf **Start** , zeigen Sie auf **Alle Programme**, zeigen Sie auf [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], zeigen Sie auf **Konfigurationstools**, und klicken Sie dann auf **SQL Server-Konfigurations-Manager**.  
  
    > [!NOTE]  
    >  Da der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager ein Snap-In für das [!INCLUDE[msCoName](../../includes/msconame-md.md)] -Verwaltungskonsolenprogramm und kein eigenständiges Programm ist, wird der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager in neueren Versionen von Windows nicht als Anwendung angezeigt.  
    >   
    >  -   **Windows 10**:  
    >          Um Configuration Manager [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu öffnen, geben Sie auf der **Start Seite**SQLServerManager12. msc ( [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]für) ein. Ersetzen Sie für frühere Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 12 durch eine kleinere Zahl. Durch Klicken auf SQLServerManager12.msc wird der Konfigurations-Manager geöffnet. Um die Configuration Manager an die Start Seite oder Task Leiste anzuheften, klicken Sie mit der rechten Maustaste auf SQLServerManager12. msc, und klicken Sie dann auf **Datei Speicherort öffnen**. Klicken Sie im Windows-Datei-Explorer mit der rechten Maustaste auf SQLServerManager12. msc, und klicken Sie dann auf am **Anfang anheften** oder **an Taskleiste**anheften  
    > -   **Windows 8**:  
    >          Um Configuration Manager [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Charm **Suchen** unter **apps**zu öffnen, geben Sie **\<SQLServerManager Version>. msc** ein, z `SQLServerManager12.msc`. b., und drücken Sie dann die **Eingabe**Taste.  
  
2.  Klicken Sie im SQL Server-Konfigurations-Manager auf **SQL Server-Dienste**.  
  
3.  Klicken Sie im Detailbereich mit der rechten Maustaste auf **SQL Server (** \<Instanzname> **)** , und klicken Sie dann auf **Eigenschaften**.  
  
4.  Geben Sie im Dialogfeld **Eigenschaften von SQL Server (** \<Instanzname> **)** auf der Registerkarte „Anmelden“ für das im Feld **Kontoname** angegebene Konto das neue Kennwort in die Felder **Kennwort** und **Kennwort bestätigen** ein, und klicken Sie dann auf **OK**.  
  
     Das Kennwort wird sofort wirksam, ohne dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]neu gestartet werden muss.  
  
#### <a name="to-change-the-password-used-by-the-sql-server-agent-service"></a>So ändern Sie das vom SQL Server-Agent-Dienst verwendete Kennwort  
  
1.  Klicken Sie auf **Start** , zeigen Sie auf **Alle Programme**, zeigen Sie auf [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], zeigen Sie auf **Konfigurationstools**, und klicken Sie dann auf **SQL Server-Konfigurations-Manager**.  
  
2.  Klicken Sie im SQL Server-Konfigurations-Manager auf **SQL Server-Dienste**.  
  
3.  Klicken Sie im Detailbereich mit der rechten Maustaste auf **SQL Server Agent (** \<Instanzname> **)** , und klicken Sie dann auf **Eigenschaften**.  
  
4.  Geben Sie im Dialogfeld **Eigenschaften von SQL Server-Agent (** \<Instanzname> **)** auf der Registerkarte „Anmelden“ für das im Feld **Kontoname** angegebene Konto das neue Kennwort in die Felder **Kennwort** und **Kennwort bestätigen** ein, und klicken Sie dann auf **OK**.  
  
     Bei einer eigenständigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz ist das Kennwort sofort wirksam, ohne dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]neu gestartet werden muss. Auf einer gruppierten Instanz kann die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ressource von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] offline geschaltet werden und einen Neustart erfordern.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Diensten: Themen zur Vorgehensweise &#40;SQL Server-Konfigurations-Manager&#41;](../managing-services-how-to-topics-sql-server-configuration-manager.md)  
  
  
