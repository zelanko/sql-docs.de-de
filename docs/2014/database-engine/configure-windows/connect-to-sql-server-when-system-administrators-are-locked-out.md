---
title: Herstellen einer Verbindung mit SQL Server, wenn Systemadministratoren gesperrt sind | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- sa account
- connecting when locked out [SQL Server]
- locked out [SQL Server]
ms.assetid: c0c0082e-b867-480f-a54b-79f2a94ceb67
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 156a8e765812c14da0888148505311d52c267916
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62782383"
---
# <a name="connect-to-sql-server-when-system-administrators-are-locked-out"></a>Herstellen einer Verbindung mit SQL Server, wenn Systemadministratoren gesperrt sind
  In diesem Thema wird beschrieben, wie Sie als Systemadministrator den Zugriff auf [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] wiedererlangen können. Ein Systemadministrator kann aufgrund einer der folgenden Ursachen Zugriff auf eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verlieren:  
  
-   Alle Anmeldedaten, die Mitglieder der festen Serverrolle sysadmin sind, wurden versehentlich entfernt.  
  
-   Alle Windows-Gruppen, die Mitglieder der festen Serverrolle sysadmin sind, wurden versehentlich entfernt.  
  
-   Die Anmeldedaten, die Mitglieder der festen Serverrolle sysadmin sind, gehören zu Mitarbeitern, die das Unternehmen verlassen haben oder nicht verfügbar sind.  
  
-   Das sa-Konto wurde deaktiviert, oder das Kennwort ist unbekannt.  
  
 Eine Methode zum Wiedererlangen des Zugriffs ist die Neuinstallation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und das Anfügen aller Datenbanken an die neue Instanz. Diese Lösung ist zeitaufwändig. Außerdem kann es zum Wiederherstellen der Anmeldedaten erforderlich sein, die Masterdatenbank aus einer Sicherung wiederherzustellen. Je nach Datum der Sicherung der Masterdatenbank sind möglicherweise nicht alle Informationen enthalten. Wenn die Sicherung der Masterdatenbank aktuell ist, sind möglicherweise die gleichen Anmeldedaten wie in der vorherigen Instanz enthalten und die Administratoren sind immer noch gesperrt.  
  
## <a name="resolution"></a>Lösung  
 Starten Sie die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Einzelbenutzermodus mithilfe der Option **-m** oder der Option **-f** . Ein beliebiges Mitglied der lokalen Administratorengruppe des Computers kann dann eine Verbindung mit der Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] als Mitglied der festen Serverrolle sysadmin herstellen.  
  
> [!NOTE]  
>  Wenn Sie eine Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Einzelbenutzermodus starten, müssen Sie zunächst den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst beenden. Andernfalls stellt der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent möglicherweise zuerst eine Verbindung her und verhindert, dass Sie als zweiter Benutzer eine Verbindung herstellen können.  
  
 Wenn Sie die Option **-m** mit **sqlcmd** oder [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]verwenden, können Sie die Verbindungen auf eine angegebene Clientanwendung beschränken. **-m"sqlcmd"** beschränkt Verbindungen z.B. auf eine einzelne Verbindung, und diese Verbindung muss sich als **sqlcmd** -Clientprogramm identifizieren. Verwenden Sie diese Option, wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Einzelbenutzermodus starten und eine unbekannte Clientanwendung die einzige verfügbare Verbindung belegt. Um die Verbindung über den Abfrage-Editor in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]herzustellen, verwenden Sie **-m"Microsoft SQL Server Management Studio - Query"** .  
  
> [!IMPORTANT]  
>  Verwenden Sie diese Option nicht als Sicherheitsfunktion. Die Clientanwendung gibt den Clientanwendungsnamen an und kann als Teil der Verbindungszeichenfolge einen falschen Namen angeben.  
  
 Schrittanleitungen zum Starten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Einzelbenutzermodus finden Sie unter [Konfigurieren von Serverstartoptionen &#40;SQL Server-Konfigurations-Manager&#41;](scm-services-configure-server-startup-options.md).  
  
## <a name="step-by-step-instructions"></a>Schritt-für-Schritt-Anweisungen  
 Im Folgenden wird beschrieben, wie eine Verbindung mit [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] unter Windows 8 (oder höher) hergestellt wird. Auf geringfügige Abweichungen bei früheren Versionen von SQL Server oder Windows wird ggf. hingewiesen. Diese Anweisungen müssen ausgeführt werden, während Sie als Mitglied der lokalen Administratorgruppe bei Windows angemeldet sind. Außerdem wird davon ausgegangen, dass [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] auf dem Computer installiert ist.  
  
1.  Starten Sie auf der Startseite [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Wählen Sie im Menü **Ansicht** die Option **Registrierte Server**aus. (Wenn Ihr Server noch nicht registriert ist, klicken Sie mit der rechten Maustaste auf **Lokale Servergruppen**, zeigen auf **Tasks**und klicken dann auf **Lokale Server**registrieren.)  
  
2.  Klicken Sie im Bereich „Registrierte Server“ mit der rechten Maustaste auf den Server, und klicken Sie dann auf **SQL Server-Konfigurations-Manager**. Eine Berechtigung zum Ausführen als Administrator sollte angefordert und der Konfigurations-Manager geöffnet werden.  
  
3.  Schließen Sie [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
4.  Wählen Sie im linken Bereich des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Managers die Option **SQL Server-Dienste**aus. Suchen Sie im rechten Bereich Ihre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz. (Bei der Standardinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist **(MSSQLSERVER)** nach dem Computernamen angegeben. Benannte Instanzen werden in Großbuchstaben mit demselben Namen wie unter Registrierte Server angezeigt.) Klicken Sie mit der rechten Maustaste auf die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz, und klicken Sie dann auf **Eigenschaften**.  
  
5.  Geben `-m` Sie auf der Registerkarte **Startparameter** im Feld **Startparameter angeben** den Text ein, und `Add`klicken Sie dann auf. (Der Parameter entspricht einem Bindestrich und dem Kleinbuchstaben m.)  
  
    > [!NOTE]  
    >  Bei einigen früheren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Versionen gibt es keine Registerkarte **Startparameter** . Doppelklicken Sie in diesem Fall auf der Registerkarte **Erweitert** auf **Startparameter**. Die Parameter werden in einem sehr kleinen Fenster geöffnet. Achten Sie darauf, die vorhandenen Parameter nicht zu ändern. Fügen Sie ganz unten den neuen Parameter `;-m` hinzu, und klicken Sie auf `OK`. (Der Parameter entspricht einem Semikolon, einem Bindestrich und dem Kleinbuchstaben m.)  
  
6.  Klicken `OK`Sie auf, und klicken Sie nach dem Neustart der Meldung mit der rechten Maustaste auf den Servernamen, und klicken Sie dann auf **neu starten**.  
  
7.  Nachdem [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] neu gestartet wurde, befindet sich Ihr Server im Einzelbenutzermodus. Stellen Sie sicher, dass der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent nicht ausgeführt wird. da er andernfalls Ihre einzige Verbindung belegt.  
  
8.  Klicken Sie im Startbildschirm von Windows 8 mit der rechten Maustaste auf das Symbol für [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Wählen Sie am unteren Bildschirmrand **Als Administrator ausführen**aus. (Dadurch werden Ihre Administratoranmeldeinformationen an SSMS übergeben.)  
  
    > [!NOTE]  
    >  In früheren Windows-Versionen wird die Option **Als Administrator ausführen** als Untermenü angezeigt.  
  
     In einigen Konfigurationen versucht SSMS, mehrere Verbindungen herzustellen. Mehrere Verbindungen verursachen einen Fehler, da [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im Einzelbenutzermodus ausgeführt wird. Sie können zwischen folgenden Aktionen wählen. Führen Sie einen der folgenden Schritte aus:  
  
    1.  Stellen Sie über den Objekt-Explorer unter Verwendung der Windows-Authentifizierung (die Ihre Administratoranmeldeinformationen enthält) eine Verbindung her. Erweitern Sie **Sicherheit**sowie **Anmeldungen**, und doppelklicken Sie auf Ihre eigene Anmeldung. Wählen Sie `sysadmin`auf der Seite **Server Rollen** die Option aus, `OK`und klicken Sie dann auf.  
  
    2.  Anstatt über den Objekt-Explorer stellen Sie in einem Abfragefenster unter Verwendung der Windows-Authentifizierung (die Ihre Administratoranmeldeinformationen enthält) eine Verbindung her. (Sie können diese Methode nur verbinden, wenn Sie keine Verbindung mit Objekt-Explorer hergestellt haben.) Führen Sie Code wie den folgenden aus, um einen neuen Anmelde Namen für die `sysadmin` Windows-Authentifizierung hinzuzufügen, der Mitglied der Fixed-Server Rolle ist. Im folgenden Beispiel wird ein Domänenbenutzer mit dem Namen `CONTOSO\PatK` hinzugefügt.  
  
        ```  
        CREATE LOGIN [CONTOSO\PatK] FROM WINDOWS;  
        ALTER SERVER ROLE sysadmin ADD MEMBER [CONTOSO\PatK];  
        ```  
  
    3.  Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im gemischten Authentifizierungsmodus ausgeführt wird, stellen Sie eine Verbindung in einem Abfragefenster unter Verwendung der Windows-Authentifizierung her (die Ihre Administratoranmeldeinformationen enthält). Führen Sie Code wie den folgenden aus, um einen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] neuen Anmelde Namen für die `sysadmin` Authentifizierung zu erstellen, der Mitglied der Fixed-Server Rolle ist.  
  
        ```  
        CREATE LOGIN TempLogin WITH PASSWORD = '************';  
        ALTER SERVER ROLE sysadmin ADD MEMBER TempLogin;  
        ```  
  
        > [!WARNING]  
        >  Ersetzen Sie ************ durch ein sicheres Kennwort.  
  
    4.  Wenn Ihr [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] im gemischten Authentifizierungsmodus ausgeführt wird und Sie das Kennwort des `sa` Kontos zurücksetzen möchten, stellen Sie mithilfe der Windows-Authentifizierung (die Ihre Administrator Anmelde Informationen enthält) eine Verbindung mit einem Abfragefenster her. Ändern Sie das Kennwort `sa` des Kontos mit der folgenden Syntax.  
  
        ```  
        ALTER LOGIN sa WITH PASSWORD = '************';  
        ```  
  
        > [!WARNING]  
        >  Ersetzen Sie ************ durch ein sicheres Kennwort.  
  
9. Mit den folgenden Schritten wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] jetzt wieder in den Mehrbenutzermodus zurückversetzt. Schließen Sie SSMS.  
  
10. Wählen Sie im linken Bereich des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Konfigurations-Managers die Option **SQL Server-Dienste**aus. Klicken Sie im rechten Bereich mit der rechten Maustaste auf die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], und klicken Sie dann auf **Eigenschaften**.  
  
11. Wählen Sie `-m` auf der Registerkarte **Startparameter** im Feld **vorhandene Parameter** aus, und klicken `Remove`Sie dann auf.  
  
    > [!NOTE]  
    >  Bei einigen früheren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Versionen gibt es keine Registerkarte **Startparameter** . Doppelklicken Sie in diesem Fall auf der Registerkarte **Erweitert** auf **Startparameter**. Die Parameter werden in einem sehr kleinen Fenster geöffnet. Entfernen Sie `;-m` das, das Sie zuvor hinzugefügt haben `OK`, und klicken Sie auf.  
  
12. Klicken Sie mit der rechten Maustaste auf den Servernamen, und klicken Sie dann auf **Neu starten**.  
  
 Jetzt sollten Sie in der Lage sein, mit einem der Konten, das jetzt Mitglied der Rolle " `sysadmin` fester Server" ist, eine Verbindung herzustellen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten SQL Server im Einzelbenutzermodus](start-sql-server-in-single-user-mode.md)   
 [Startoptionen für den Datenbank-Engine-Dienst](database-engine-service-startup-options.md)  
  
  
