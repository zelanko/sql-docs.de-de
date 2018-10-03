---
title: Installieren von Distributed Replay (Setup) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 64479cdc-661a-4e32-a381-8f8b5a238337
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0f9d81920e9e14dc745813795bcf98eb1d9ebdf9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48051403"
---
# <a name="install-distributed-replay-setup"></a>Installieren von Distributed Replay (Setup)
  Installieren Sie die [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay-Features mit dem [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Installations-Assistenten. Beachten Sie Folgendes, bevor Sie sich für ein Verzeichnis für die Installation der Funktionen entscheiden:  
  
-   Sie können das Verwaltungstool auf demselben Computer wie den Distributed Replay-Controller oder auf anderen Computern installieren.  
  
-   Es kann in jeder Distributed Replay-Umgebung jeweils nur einen Controller geben.  
  
-   Sie können den Clientdienst auf bis zu 16 (physischen oder virtuellen) Computern installieren.  
  
-   Nur eine Instanz des Clientdiensts kann auf dem Distributed Replay Controller-Computer installiert werden. Wenn die Distributed Replay-Umgebung mehr als einen Client umfasst, wird davon abgeraten, den Clientdienst auf demselben Computer wie den Controller zu installieren. Dadurch könnte sich die Gesamtgeschwindigkeit der verteilten Wiedergabe verringern.  
  
-   Für Leistungstestszenarien sollten das Verwaltungstool, der Distributed Replay Controller-Dienst oder Client-Dienst auf der Zielinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]nicht installiert werden. Das Installieren aller dieser Features auf dem Zielserver sollte auf Funktionstests für die Anwendungskompatibilität beschränkt werden.  
  
-   Nach der Installation muss der Controllerdienst, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller, ausgeführt werden, bevor Sie den Distributed Replay Client-Dienst auf den Clients starten.  
  
> [!NOTE]  
>  Um die Distributed Replay-Funktionen zu entfernen oder zu ändern, verwenden Sie das Fenster **Programme und Funktionen** in der **Systemsteuerung**. Wählen Sie im **Programm deinstallieren oder ändern** [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] aus, und klicken Sie anschließend auf **Entfernen** , um den [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Installations-Assistenten zu öffnen. Kontrollieren Sie auf der Seite **Funktionen auswählen** die Distributed Replay-Funktionen, die Sie entfernen möchten.  
  
 **Voraussetzungen:**  
  
-   Stellen Sie sicher, dass die Computer, die Sie verwenden möchten, die im Thema [Distributed Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md)beschriebenen Anforderungen erfüllen.  
  
-   Erstellen Sie zuvor die Domänenbenutzerkonten, unter denen die Controller- und Clientdienste ausgeführt werden. Diese Konten sollten keine Mitglieder der Windows-Gruppe "Administratoren" sein. Weitere Informationen finden Sie im Abschnitt "Benutzer- und Dienstkonten" im Thema [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md) .  
  
    > [!NOTE]  
    >  Sie können lokale Benutzerkonten verwenden, wenn Sie das Verwaltungstool, den Controllerdienst und den Clientdienst auf dem gleichen Computer ausführen.  
  
 **Installationsorte:**  
  
 Angenommen, Sie verwenden die Standardorte und eine Standardinstallation, dann befindet sich das Basisverzeichnis in "C:\Programme\Microsoft SQL Server". Innerhalb des Verzeichnisses werden die Binärdateien und Assemblys in folgenden Unterverzeichnissen installiert:  
  
-   Auf einem 32-Bit-System:  
  
     [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]Tools  
  
     \- - ODER -  
  
     \<Freigabefeatureverzeichnis>\Tools\\(alternatives freigegebenes Featureverzeichnis, das vom Benutzer angegeben wird)  
  
-   Auf einem 64-Bit-System:  
  
     C:\Program Files\\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (x86) \120\Tools  
  
     \- - ODER -  
  
     \<Freigabefeatureverzeichnis (x86)>\Tools\\(alternatives freigegebenes x86-Featureverzeichnis, das vom Benutzer angegeben wird)  
  
### <a name="to-install-distributed-replay-features"></a>So installieren Sie Distributed Replay-Funktionen  
  
1.  Um die Installation einer der Distributed Replay-Funktionen zu starten, öffnen Sie den [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] -Installations-Assistenten.  
  
2.  Auf der Seite **Setupunterstützungsregeln** werden Probleme erkannt, die auftreten können, wenn die SQL Server-Setupunterstützungsdateien installiert werden. Sie müssen vor dem Fortfahren mit Setup alle Setupunterstützungsfehler korrigieren.  
  
3.  Wählen Sie auf der Seite **Product Key** ein Optionsfeld aus, um anzugeben, ob Sie eine kostenlose Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]installieren oder ob Sie über eine Produktionsversion des Produkts mit einem PID-Schlüssel verfügen. Weitere Informationen finden Sie unter [Editionen und Komponenten von SQL Server 2014](../editions-and-components-of-sql-server-2016.md).  
  
4.  Lesen Sie auf der Seite **Lizenzbedingungen** den Lizenzvertrag, und aktivieren Sie dann das Kontrollkästchen, um den Lizenzbestimmungen zuzustimmen. Falls Sie zur Verbesserung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]beitragen möchten, können Sie auch die Option zur Funktionsverwendung aktivieren und Berichte an [!INCLUDE[msCoName](../../includes/msconame-md.md)]senden.  
  
5.  Klicken Sie auf der Seite **Setup-Unterstützungsdateien** auf **Installieren** , um die Setup-Unterstützungsdateien für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]zu installieren oder zu aktualisieren.  
  
6.  Wählen Sie auf der Seite **Setuprolle** die **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktionsinstallation**aus, und klicken Sie dann auf **Weiter** , um mit der Seite für die **Funktionsauswahl** fortzufahren.  
  
7.  Konfigurieren Sie auf der Seite **Funktionsauswahl** , welche Funktionen Sie installieren möchten.  
  
    -   Wählen Sie zum Installieren des Verwaltungstools **Verwaltungstools - Einfach**aus.  
  
    -   Wählen Sie **Distributed Replay Controller**aus, um den Controllerdienst zu installieren.  
  
    -   Wählen Sie **Distributed Replay Client**aus, um den Clientdienst zu installieren.  
  
     **Wichtig**: Wenn Sie den Distributed Replay Controller konfigurieren, können Sie mindestens ein Benutzerkonto angeben, das zum Ausführen der Distributed Replay Client-Dienste verwendet wird. Die folgenden Kontotypen werden unterstützt:  
  
    -   Domänenbenutzerkonto  
  
    -   Vom Benutzer erstelltes lokales Benutzerkonto  
  
    -   Administrator  
  
    -   Virtuelles Konto und verwaltetes Dienstkonto (Managed Service Account, MSA)  
  
    -   Netzwerkdienste, lokale Dienste und System  
  
     Gruppenkonten (lokales oder Domänenbenutzerkonto) und andere integrierte Konten (wie "Jeder") werden nicht akzeptiert.  
  
8.  Klicken Sie optional auf die Schaltfläche mit den Auslassungspunkten (…), um den Pfad des freigegebenen Funktionsverzeichnisses zu ändern.  
  
    1.  Auf 32-Bit-Computern ist der Standardinstallationspfad **C:\Programme\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\**  
  
    2.  Auf 64-Bit-Computern ist der Standardinstallationspfad **C:\Programme (x86)\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\**.  
  
9. Wenn Sie fertig sind, klicken Sie auf **Weiter**.  
  
10. Auf der Seite **Installationsregeln** überprüft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup Ihre Computerkonfiguration. Sobald der Überprüfungsprozess abgeschlossen wurde, klicken Sie auf **Weiter**.  
  
11. Auf der Seite **Erforderlicher Speicherplatz** wird der für die angegebenen Funktionen erforderliche Speicherplatz berechnet. Der erforderliche Speicherplatz wird dann mit dem verfügbaren Speicherplatz auf dem Computer verglichen.  
  
12. Geben Sie auf der Seite **Fehlerberichterstellung** die Informationen an, die Sie an [!INCLUDE[msCoName](../../includes/msconame-md.md)] senden möchten, um zur Verbesserung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]beizutragen. Die Option für Fehlerberichte ist standardmäßig aktiviert.  
  
13. Auf der Seite **Konfigurationsregeln für die Installation** führt die Systemkonfigurationsprüfung einen weiteren Regelsatz aus, um die Konfiguration des Computers anhand der angegebenen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Funktionen zu überprüfen.  
  
14. Klicken Sie auf der Seite **Das Programm kann jetzt installiert werden** auf **Installieren**.  
  
    > [!IMPORTANT]  
    >  Nachdem Sie Distributed Replay installiert haben, müssen Sie auf dem Controller und den Clientcomputern Firewallregeln erstellen und jedem Clientcomputer Berechtigungen für den Zielserver gewähren. Weitere Informationen finden Sie unter [Ausführen der Schritte nach der Installation](../../tools/distributed-replay/complete-the-post-installation-steps.md).  
  
 Diese zusätzlichen Themen dokumentieren weitere Möglichkeiten, Distributed Replay zu installieren:  
  
-   [Installieren von Distributed Replay von der Eingabeaufforderung](../../tools/distributed-replay/install-distributed-replay-overview.md)  
  
-   [Installieren von Distributed Replay mithilfe einer Konfigurationsdatei](../../../2014/sql-server/install/install-distributed-replay-using-a-configuration-file.md)  
  
## <a name="net-framework-security"></a>.NET Framework-Sicherheit  
 Sie müssen über Administratorberechtigungen verfügen, um eine der Distributed Replay-Funktionen zu installieren. Nur bei einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Anmeldung mit sysadmin-Berechtigungen können der sysadmin-Serverrolle des Testservers die Clientdienstkonten hinzugefügt werden. Weitere Informationen zu Sicherheitsüberlegungen für Distributed Replay finden Sie unter [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Von den Editionen von SQLServer 2014 unterstützte Funktionen](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)   
 [Distributed Replay: Anforderungen](../../tools/sql-server-profiler/replay-requirements.md)   
 [Befehlszeilenoptionen für das Verwaltungstool &#40;Distributed Replay Utility&#41;](../../tools/distributed-replay/administration-tool-command-line-options-distributed-replay-utility.md)   
 [Konfigurieren von Distributed Replay](../../tools/distributed-replay/configure-distributed-replay.md)  
  
  
