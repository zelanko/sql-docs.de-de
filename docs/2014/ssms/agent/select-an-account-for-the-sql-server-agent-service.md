---
title: Auswählen eines Kontos für den SQL Server-Agent-Dienst | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- roles [SQL Server], SQL Server Agent
- SQL Server Agent, accounts
- startup accounts [SQL Server]
- SQL Server Agent service, accounts
- accounts [SQL Server], SQL Server Agent
- Windows groups [SQL Server Agent]
- SQL Server Agent, permissions
- members [SQL Server], SQL Server Agent service
- Windows domain accounts [SQL Server]
- security [SQL Server], SQL Server Agent
ms.assetid: fe658e32-9e6b-4147-a189-7adc3bd28fe7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9b2fd7a22c202b1210b17f86903fce32ec8d4b5b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68811079"
---
# <a name="select-an-account-for-the-sql-server-agent-service"></a>Auswählen eines Kontos für den SQL Server-Agent-Dienst
  Das Dienststartkonto definiert das [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Konto, in dem der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent ausgeführt wird, und legt dessen Netzwerkberechtigungen fest. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent wird als angegebenes Benutzerkonto ausgeführt. Sie wählen ein Konto für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst mithilfe des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Managers aus. Dort können Sie zwischen folgenden Optionen wählen:  
  
-   **Integriertes Konto**. Sie können aus einer Liste der folgenden integrierten Windows-Dienstkonten auswählen:  
  
    -   **Lokales System** Konto. Der Name dieses Kontos lautet NT-AUTORITÄT\System. Hierbei handelt es sich um ein Konto mit weit reichenden Befugnissen, das über unbeschränkten Zugriff auf alle lokalen Systemressourcen verfügt. Es ist ein Mitglied der Windows-Gruppe **Administratoren** auf dem lokalen Computer und somit Mitglied der festen Serverrolle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **in** .  
  
        > [!IMPORTANT]  
        >  Die Option **Lokales Systemkonto** wird nur aus Gründen der Abwärtskompatibilität bereitgestellt. Ein lokales Systemkonto verfügt über Berechtigungen, die für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent nicht erforderlich sind. Vermeiden Sie die Ausführung des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents als lokales Systemkonto. Zur Verbesserung der Sicherheit sollten Sie ein Windows-Domänenkonto zusammen mit den im folgenden Abschnitt "Berechtigungen für Windows-Domänenkonten" aufgelisteten Berechtigungen verwenden.  
  
-   **Dieses Konto**. Hier können Sie das Windows-Domänenkonto angeben, unter dem der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst ausgeführt wird. Das von Ihnen ausgewählte Windows-Benutzerkonto sollte kein Mitglied der Windows-Gruppe **Administratoren** sein. Es bestehen jedoch Einschränkungen für die Verwendung der Multiserveradministration, wenn das Konto des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Diensts kein Mitglied der lokalen Gruppe **Administratoren** ist. Weitere Informationen finden Sie unter "Unterstützte Dienstkontotypen" weiter unten in diesem Thema.  
  
## <a name="windows-domain-account-permissions"></a>Berechtigungen für Windows-Domänenkonten  
 Zur Verbesserung der Sicherheit sollten Sie die Option **Dieses Konto**auswählen, um ein Windows-Domänenkonto anzugeben. Das von Ihnen angegebene Windows-Domänenkonto muss folgende Berechtigungen haben:  
  
-   Berechtigung zum Anmelden als Dienst für alle Windows-Versionen (SeServiceLogonRight)  
  
> [!NOTE]  
>  Das Konto des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Diensts muss Teil der Gruppe Prä-Windows 2000 kompatibler Zugriff auf dem Domänencontroller sein. Andernfalls führen Aufträge im Besitz von Domänenbenutzern, die keine Mitglieder der Windows-Gruppe Administratoren sind, zu Fehlern.  
  
-   Auf Servern unter Windows erfordert das vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst ausgeführte Konto folgende Berechtigungen, um Proxys für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent unterstützen zu können.  
  
    -   Berechtigung zum Umgehen von durchsuchenden Prüfungen (SeChangeNotifyPrivilege)  
  
    -   Berechtigung zum Ersetzen von Token auf Prozessebene (SeAssignPrimaryTokenPrivilege)  
  
    -   Berechtigung zum Anpassen des Arbeitsspeicherkontingents für einen Prozess (SeIncreaseQuotaPrivilege)  
  
    -   Berechtigung zum Anmelden mithilfe der Batchanmeldung (SeBatchLogonRight)  
  
> [!NOTE]  
>  Wenn das Konto nicht über die Berechtigungen verfügt, die zur Unterstützung von Proxys erforderlich sind, können Aufträge nur von Mitgliedern der festen Serverrolle **sysadmin** erstellt werden.  
  
> [!NOTE]  
>  Um WMI-Warnbenachrichtigungen zu empfangen, muss das Dienstkonto des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents über die Berechtigung für den Namespace verfügen, der die WMI-Ereignisse enthält. Außerdem muss es dazu berechtigt sein, EREIGNISBERECHTIGUNGEN ZU ÄNDERN.  
  
## <a name="sql-server-role-membership"></a>SQL Server-Rollenmitgliedschaft  
 Das Konto, als das der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst ausgeführt wird, muss Mitglied der folgenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Rollen sein:  
  
-   Das Konto muss ein Mitglied der festen Serverrolle **sysadmin** sein.  
  
-   Um die Multiserver-Auftragsverarbeitung verwenden zu können, muss das Konto Mitglied der **msdb** -Datenbankrolle **TargetServersRole** auf dem Masterserver sein.  
  
## <a name="supported-service-account-types"></a>Unterstützte Dienstkontotypen  
 In der folgenden Tabelle werden die Windows-Kontotypen aufgelistet, die für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst verwendet werden können.  
  
|Dienstkontotyp|Nicht gruppierter Server|Gruppierter Server|Domänencontroller (nicht gruppiert)|  
|--------------------------|---------------------------|----------------------|------------------------------------------|  
|
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Domänenkonto (Mitglied der Windows-Administratorengruppe)|Unterstützt|Unterstützt|Unterstützt|  
|Windows-Domänenkonto (kein Administratorkonto)|Unterstützt<sup>1</sup>|Unterstützt<sup>1</sup>|Unterstützt<sup>1</sup>|  
|Netzwerkdienstkonto (NT AUTHORITY\NetworkService)|Unterstützt<sup>1, 3, 4</sup>|Nicht unterstützt|Nicht unterstützt|  
|Lokales Benutzerkonto (kein Administratorkonto)|Unterstützt<sup>1</sup>|Nicht unterstützt|Nicht verfügbar|  
|Lokales Systemkonto (NT AUTHORITY\System)|Unterstützt<sup>2</sup>|Nicht unterstützt|Unterstützt<sup>2</sup>|  
|Lokales Dienstkonto (NT AUTHORITY\LocalService)|Nicht unterstützt|Nicht unterstützt|Nicht unterstützt|  
  
 <sup>1</sup> siehe Einschränkung 1 unten.  
  
 <sup>2</sup> siehe Einschränkung 2 weiter unten.  
  
 <sup>3</sup> siehe Einschränkung 3 unten.  
  
 <sup>4</sup> siehe Einschränkung 4 unten.  
  
### <a name="limitation-1-using-non-administrative-accounts-for-multiserver-administration"></a>Einschränkung 1: Verwenden von Nichtadministratorkonten für die Multiserververwaltung  
 Beim Eintragen von Zielservern auf einem Masterserver kann ein Fehler mit einer Fehlermeldung, die der folgenden ähnlich ist, auftreten: "Fehler beim Eintragen."  
  
 Starten Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienste neu, um diesen Fehler zu beheben. Weitere Informationen finden Sie unter [Starten, Beenden, Anhalten, Fortsetzen und Neustarten von SQL Server-Diensten](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md).  
  
### <a name="limitation-2-using-the-local-system-account-for-multiserver-administration"></a>Einschränkung 2: Verwenden des lokalen Systemkontos für die Multiserververwaltung  
 Die Multiserververwaltung wird bei Ausführung des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Diensts unter dem lokalen Systemkonto nur dann unterstützt, wenn sich der Masterserver und der Zielserver auf demselben Computer befinden. Wenn Sie diese Konfiguration verwenden, wird beim Eintragen der Zielserver auf dem Masterserver etwa die folgende Meldung zurückgegeben:  
  
 „Stellen Sie sicher, dass das Agentstartkonto für *<Zielserver-Computername>* Rechte zur Anmeldung als Zielserver besitzt.“  
  
 Sie können diese zu Informationszwecken ausgegebene Meldung ignorieren. Der Eintragungsvorgang wird dennoch erfolgreich abgeschlossen. Weitere Informationen finden Sie unter [Erstellen einer Multiserverumgebung](create-a-multiserver-environment.md).  
  
### <a name="limitation-3-using-the-network-service-account-when-it-is-a-sql-server-user"></a>Einschränkung 3: Verwenden des Netzwerkdienstkontos als SQL Server-Benutzer  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent wird möglicherweise nicht gestartet, wenn Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst unter dem Netzwerkdienstkonto ausführen und dem Netzwerkdienstkonto explizit der Zugriff auf eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz als [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Benutzer erteilt wurde.  
  
 Starten Sie den Computer, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird, neu, um diesen Fehler zu beheben. Dies muss nur einmal erfolgen.  
  
### <a name="limitation-4-using-the-network-service-account-when-sql-server-reporting-services-is-running-on-the-same-computer"></a>Einschränkung 4: Verwenden des Netzwerkdienstkontos bei Ausführung von SQL Server Reporting Services auf demselben Computer  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent wird möglicherweise nicht gestartet, wenn Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst unter dem Netzwerkdienstkonto ausführen und [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ebenfalls auf demselben Computer ausgeführt wird.  
  
 Starten Sie den Computer, auf dem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird, neu, um diesen Fehler zu beheben. Starten Sie anschließend [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienste neu. Dies muss nur einmal erfolgen.  
  
## <a name="common-tasks"></a>Allgemeine Aufgaben  
 **So geben Sie das Start Konto für den SQL Server-Agent-Dienst an**  
  
-   [Legen Sie das Dienst Start Konto für SQL Server-Agent &#40;SQL Server-Konfigurations-Manager fest&#41;](set-service-startup-account-sql-server-agent-sql-server-configuration-manager.md)  
  
 **So geben Sie das Mail Profil für SQL Server-Agent an**  
  
-   [Konfigurieren von SQL Server-Agent-Mail zum Verwenden von Datenbank-E-Mails](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)  
  
> [!NOTE]  
>  Verwenden Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Manager, um anzugeben, dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent beim Start des Betriebssystems starten soll.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Windows-Dienst Konten und-Berechtigungen](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)   
 [Verwalten von Diensten: Themen zur Vorgehensweise &#40;SQL Server-Konfigurations-Manager&#41;](../../database-engine/managing-services-how-to-topics-sql-server-configuration-manager.md)   
 [Implementieren der SQL Server-Agent-Sicherheit](implement-sql-server-agent-security.md)  
  
  
