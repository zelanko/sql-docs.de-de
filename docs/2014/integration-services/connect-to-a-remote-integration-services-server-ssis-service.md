---
title: Verbinden mit einem Remote-Integration Services-Server (SSIS-Dienst) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- service [Integration Services], remote instance
- Integration Services service, connecting
- Integration Services service, remote instance
- service [Integration Services], connecting
ms.assetid: 9487aff1-44d8-42c1-8176-bb9891d4632d
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: eff4eb190c8225cf1d45f184515ccc5244a3a7ff
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48222770"
---
# <a name="connect-to-a-remote-integration-services-server-ssis-service"></a>Herstellen einer Verbindung mit einem Integration Services-Remoteserver (SSIS-Dienst)
    
> [!IMPORTANT] 
> In diesem Thema wird der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst beschrieben, ein Windows-Dienst zur Verwaltung von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Paketen. [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] unterstützt den Dienst für die Abwärtskompatibilität mit früheren Versionen von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Ab [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]können Sie Objekte, z. B. Pakete, auf dem Integration Services-Server verwalten.  
  
 Zum Herstellen einer Verbindung mit einer Instanz von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] auf einem Remoteserver über [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] oder eine andere Verwaltungsanwendung benötigt der Benutzer der Anwendung einen bestimmten Satz von Rechten auf dem Server.  
  
> [!IMPORTANT] 
> Zum Verwalten von Paketen auf einem Remoteserver müssen Sie keine Verbindung mit der Instanz des [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Diensts auf dem betreffenden Remoteserver herstellen. Bearbeiten Sie stattdessen die Konfigurationsdatei für den [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst, sodass die auf dem Remoteserver gespeicherten Pakete von [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] angezeigt werden. Weitere Informationen finden Sie unter [Konfigurieren des Integration Services-Diensts &#40;SSIS-Dienst&#41;](service/integration-services-service-ssis-service.md).  
  
## <a name="connecting-to-integration-services-on-a-remote-server"></a>Herstellen einer Verbindung mit Integration Services auf einem Remoteserver  
  
#### <a name="to-connect-to-integration-services-on-a-remote-server"></a>So stellen Sie eine Verbindung mit Integration Services auf einem Remoteserver her  
  
1.  Öffnen Sie [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  Wählen Sie im Menü **Datei**die Option **Objekt-Explorer verbinden** , um das Dialogfeld **Verbindung mit Server herstellen** anzuzeigen.  
  
3.  Wählen Sie in der Liste **Servertyp** den Eintrag **Integration Services** aus.  
  
4.  Geben Sie in das Textfeld [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] den **Namen eines** -Servers ein.  
  
    > [!NOTE]  
    >  Der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst ist nicht instanzspezifisch. Sie melden sich beim Dienst mit dem Namen des Computers an, auf dem der Integration Services-Dienst ausgeführt wird.  
  
5.  Klicken Sie auf **Verbinden**.  
  
> [!NOTE]  
>  Im Dialogfeld **Nach Servern suchen** werden keine Remoteinstanzen von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]angezeigt. Außerdem sind die Optionen auf der Registerkarte **Verbindungsoptionen** im Dialogfeld **Verbindung mit Server herstellen** , die durch Klicken auf die Schaltfläche **Optionen** angezeigt wird, nicht auf [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Verbindungen anwendbar.  
  
## <a name="eliminating-the-access-is-denied-error"></a>Entfernen der Fehlermeldung "Der Zugriff wurde verweigert."  
 Wenn ein Benutzer ohne ausreichende Rechte versucht, eine Verbindung mit einer Instanz von [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] auf einem Remoteserver herzustellen, antwortet der Server mit der Fehlermeldung "Der Zugriff wurde verweigert". Sie können diese Fehlermeldung vermeiden, indem Sie sicherstellen, dass der Benutzer über die erforderlichen DCOM-Berechtigungen verfügt.  
  
#### <a name="to-configure-rights-for-remote-users-on-windows-server-2003-or-windows-xp"></a>So konfigurieren Sie Rechte für Remotebenutzer unter Windows Server 2003 bzw. Windows XP  
  
1.  Wenn der Benutzer kein Mitglied der lokalen Gruppe Administratoren ist, fügen Sie den Benutzer der Gruppe Distributed COM-Benutzer hinzu. Sie können dazu das MMC-Snap-In „Computerverwaltung“ verwenden, das über das Menü **Verwaltung** aufgerufen werden kann.  
  
2.  Öffnen Sie die Systemsteuerung, doppelklicken Sie auf **Verwaltung** , und doppelklicken Sie anschließend auf **Komponentendienste** , um das MMC-Snap-In „Komponentendienste“ zu starten.  
  
3.  Erweitern Sie im linken Bereich der Konsole den Knoten **Komponentendienste** . Erweitern Sie den Knoten **Computer** , erweitern Sie **Arbeitsplatz**, und klicken Sie anschließend auf den Knoten **DCOM-Konfiguration** .  
  
4.  Wählen Sie den Knoten **DCOM-Konfiguration** aus, und wählen Sie anschließend in der Liste der Anwendungen, die konfiguriert werden können, "SQL Server Integration Services 11.0" aus.  
  
5.  Klicken Sie mit der rechten Maustaste auf „SQL Server Integration Services 11.0“, und klicken Sie anschließend auf **Eigenschaften**.  
  
6.  Wählen Sie im Dialogfeld für die **Eigenschaften von SQL Server Integration Services 11.0** die Registerkarte **Sicherheit** aus.  
  
7.  Wählen Sie unter **Start- und Aktivierungsberechtigungen**die Option **Anpassen**aus, und klicken Sie auf **Bearbeiten** , um das Dialogfeld **Startberechtigung** zu öffnen.  
  
8.  Fügen Sie im Dialogfeld **Startberechtigung** Benutzer hinzu, oder löschen Sie Benutzer, und weisen Sie die entsprechenden Berechtigungen den passenden Benutzern und Gruppen zu. Die verfügbaren Berechtigungen sind Lokaler Start, Remotestart, Lokale Aktivierung und Remoteaktivierung. Die Startrechte erteilen oder verweigern die Berechtigung zum Starten und Beenden des Diensts, während die Aktivierungsrechte die Berechtigung zum Herstellen einer Verbindung mit dem Dienst erteilen oder verweigern.  
  
9. Klicken Sie auf OK, um das Dialogfeld zu schließen.  
  
10. Wiederholen Sie die Schritte 7 und 8 unter **Zugriffsberechtigungen**, um den Benutzern und Gruppen die geeigneten Berechtigungen zuzuweisen.  
  
11. Schließen Sie das MMC-Snap-In.  
  
12. Starten Sie den [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst neu.  
  
#### <a name="to-configure-rights-for-remote-users-on-windows-2000-with-the-latest-service-packs"></a>So konfigurieren Sie Rechte für Remotebenutzer unter Windows 2000 mit den neuesten Service Packs  
  
1.  Führen Sie **dcomcnfg.exe** an der Eingabeaufforderung aus.  
  
2.  Wählen Sie auf der Seite **Anwendungen** des Dialogfelds für verteilte COM-Konfigurationseigenschaften die Option **SQL Server Integration Services 11.0** aus, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Wählen Sie die Seite **Sicherheit** aus.  
  
4.  Verwenden Sie die beiden separaten Dialogfelder zum Konfigurieren der **Zugriffsberechtigungen** und der **Startberechtigungen**. Eine Unterscheidung zwischen Remote- und lokalem Zugriff ist nicht möglich. Die Zugriffsberechtigungen umfassen lokalen und Remotezugriff, die Startberechtigungen lokalen und Remotestart.  
  
5.  Schließen Sie die Dialogfelder und **dcomcnfg.exe**.  
  
6.  Starten Sie den [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst neu.  
  
## <a name="connecting-by-using-a-local-account"></a>Herstellen einer Verbindung mithilfe eines lokalen Kontos  
 Wenn Sie ein lokales Windows-Konto auf einem Clientcomputer verwenden, können Sie nur dann eine Verbindung mit dem [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst auf einem Remotecomputer herstellen, wenn auf dem Remotecomputer ein lokales Konto mit dem gleichen Namen und Kennwort sowie ausreichenden Rechten vorhanden ist.  
  
## <a name="by-default-the-ssis-service-does-not-support-delegation"></a>Standardmäßig wird die Delegierung vom SSIS-Dienst nicht unterstützt  
Die Delegierung von Anmeldeinformationen, auch als Doppelhop bezeichnet, wird vom [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst standardmäßig nicht unterstützt. In diesem Szenario verwenden Sie einen Clientcomputer, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ist auf einem zweiten Computer und [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] auf einem dritten Computer installiert. Zunächst übergibt [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] Ihre Anmeldeinformationen erfolgreich vom Clientcomputer an den zweiten Computer, auf dem der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst ausgeführt wird. Anschließend kann der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Dienst Ihre Anmeldeinformationen jedoch nicht vom zweiten Computer an den dritten Computer delegieren, auf dem [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ausgeführt wird.

Sie können die Delegierung von Anmeldeinformationen aktivieren, indem Sie dem SQL Server-Dienstkonto, das den Integration Services-Dienst als untergeordneten Prozess startet (ISServerExec.exe), die Berechtigung **Benutzer bei Delegierungen aller Dienste vertrauen (nur Kerberos)** erteilen. Beachten Sie, dass diese Berechtigung die Sicherheitsanforderungen Ihrer Organisation erfüllt, bevor Sie sie erteilen.

Weitere Informationen finden Sie im Blogbeitrag [Getting Cross Domain Kerberos and Delegation working with SSIS Package](https://blogs.msdn.microsoft.com/psssql/2014/06/26/getting-cross-domain-kerberos-and-delegation-working-with-ssis-package/)(Erreichen, dass Kerberos (domänenübergreifend) und Delegierung in SSIS-Paketen funktionieren).
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren einer Windows-Firewall für den Zugriff auf den SSIS-Dienst](../../2014/integration-services/configure-a-windows-firewall-for-access-to-the-ssis-service.md)  
  
  
