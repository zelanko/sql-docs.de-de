---
title: Installieren von SQL Server 2016 vom Installations-Assistenten aus (Setup) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/26/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- installing SQL Server, steps
- Setup [SQL Server], steps
- SQL Server, installing
ms.assetid: 6ad23de1-2bab-4933-9122-c09f5565028d
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: bdfa96839b92150fde8b6954ffd96f8f34eb7508
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67991098"
---
# <a name="install-sql-server-from-the-installation-wizard-setup"></a>Installieren von SQL Server über den Installations-Assistenten (Setup)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel wird erläutert, wie SQL Server mit dem Installations-Assistenten installiert wird. Dies gilt für [!INCLUDE[SQLServer2016](../../includes/sssql15-md.md)] und [!INCLUDE[SQLServer2017](../../includes/sssqlv14-md.md)].

Dieser Artikel stellt Ihnen schrittweise die Installation einer neuen Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unter Verwendung des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setup-Installations-Assistenten vor. Der Installations-Assistent für enthält eine einzelne Funktionsstruktur für die Installation sämtlicher [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponenten, sodass Sie diese nicht einzeln installieren müssen. Informationen zur Installation der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponenten finden Sie unter [Installieren von SQL Server](../../database-engine/install-windows/install-sql-server.md#how-to-install-individual-components).  

Weitere Möglichkeiten zum Installieren von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] finden Sie unter:  

* [Install SQL Server from the command prompt (Installieren von SQL Server über die Eingabeaufforderung)](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)  
* [Install SQL Server by using a configuration file (Installieren von SQL Server mithilfe einer Konfigurationsdatei)](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md)  
* [Installieren von SQL Server mit SysPrep](../../database-engine/install-windows/install-sql-server-using-sysprep.md)  
* [Erstellen eines neuen SQL Server-Failoverclusters (Setup)](../../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md)  
* [Upgrade von SQL Server mithilfe des Installations-Assistenten (Setup)](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)

## <a name="get-the-installation-media"></a>Abrufen der Installationsmedien

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]
  
## <a name="prerequisites"></a>Voraussetzungen

Bevor Sie die Installation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]durchführen, lesen Sie das Thema [Planen einer SQL Server-Installation](../../sql-server/install/planning-a-sql-server-installation.md).  
  
> [!NOTE]  
> Bei lokalen Installationen müssen Sie das Setup als Administrator ausführen. Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von einer Remotefreigabe installieren, müssen Sie ein Domänenkonto verwenden, das Lese- und Ausführungsberechtigungen auf der Remotefreigabe hat.  

###  <a name="bkmk_ga_instalpatch"></a> Installieren einer Patchanforderung

Microsoft hat ein Problem erkannt, das die Runtime-Binärdateien von Microsoft Visual C++ 2013 betrifft, die von SQL Server als erforderliche Komponente installiert werden. Ein Update ist verfügbar, um dieses Problem zu beheben. Wenn dieses Update der Runtime-Binärdateien von Visual C++ nicht installiert wird, können bei SQL Server in bestimmten Szenarios Stabilitätsprobleme auftreten. Bevor Sie SQL Server installieren, sollten Sie entsprechend den Anweisungen unter [Versionsanmerkungen zu SQL Server](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch) vorgehen, um festzustellen, ob Ihr Computer einen Patch für die Runtime-Binärdateien von Visual C++ benötigt.  
  
## <a name="to-install-includessnoversionincludesssnoversion-mdmd"></a>So installieren Sie [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)]  
  
1. Legen Sie das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Installationsmedium ein. Doppelklicken Sie im Stammordner auf **Setup.exe**. Wenn Sie eine Installation über eine Netzwerkfreigabe vornehmen möchten, suchen Sie den Stammordner in der Freigabe, und doppelklicken Sie auf **Setup.exe**.  
  
2. Das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Installationscenter wird vom Installations-Assistenten ausgeführt. Um eine neue Installation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu erstellen, klicken Sie im linken Navigationsbereich auf **Installation** und anschließend auf **Neue eigenständige [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Installation oder Hinzufügen von Funktionen zu einer vorhandenen Installation**.  

3. Wählen Sie auf der Seite **Product Key** ein Optionsfeld aus, um anzugeben, ob Sie eine kostenlose Edition von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installieren oder ob Sie über eine Produktionsversion mit einem PID-Schlüssel verfügen. Weitere Informationen finden Sie unter [Editionen und unterstützte Funktionen von SQL Server 2017](../../sql-server/editions-and-components-of-sql-server-2017.md).  
  
   Wählen Sie zum Fortsetzen des Vorgangs **Weiter** aus.

<!--
The following item is for SQL Server 2019 or later
-->
  
::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"

4. Lesen Sie auf der Seite **Lizenzbedingungen** die Lizenzbedingungen. Wenn Sie zustimmen, aktivieren Sie das Kontrollkästchen **Ich akzeptiere die Lizenzbedingungen und [Datenschutzbestimmungen](https://privacy.microsoft.com/privacystatement)** , und klicken Sie auf **Weiter**.  

::: moniker-end

<!--
The following item is for SQL Server 2016-2017
-->

::: moniker range=">=sql-server-2016 <=sql-server-2017||=sqlallproducts-allversions"

4. Lesen Sie auf der Seite **Lizenzbedingungen** die Lizenzbedingungen. Wenn Sie zustimmen, aktivieren Sie das Kontrollkästchen **Ich akzeptiere die Lizenzbedingungen**, und klicken Sie auf **Weiter**.  

::: moniker-end

   >[!NOTE]
   > SQL Server übermittelt Informationen zu Ihrer Installationserfahrung und andere Nutzungs- sowie Leistungsdaten, die Microsoft bei der Produktoptimierung unterstützen. Weitere Informationen zur Datenverarbeitung und zu Datenschutzmaßnahmen in SQL Server finden Sie in den [Datenschutzbestimmungen](https://privacy.microsoft.com/privacystatement) und unter [Konfigurieren von SQL Server zum Senden von Feedback an Microsoft](https://docs.microsoft.com/sql/sql-server/sql-server-customer-feedback?view=sql-server-2016).

5. Auf der Seite **Globale Regeln** wechselt das Setup automatisch zur Seite **Produktupdates**, wenn keine Regelfehler vorliegen.  
  
6. Wenn das Kontrollkästchen **Microsoft Update** in **Systemsteuerung** > **Systemsteuerungselemente** > **Windows Update** >  **Einstellungen ändern** nicht ausgewählt ist, wird die Seite **Microsoft Update** als nächstes angezeigt. Wenn Sie das Kontrollkästchen **Microsoft Update** aktivieren, werden die Computereinstellungen so geändert, dass sie die neuesten Updates für alle Microsoft-Produkte enthalten, wenn Sie nach Windows Updates suchen.  

7. Auf der Seite für **Produktupdates** werden die neuesten verfügbaren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Produktupdates angezeigt. Wenn keine Produktupdates ermittelt wurden, zeigt Setup diese Seite nicht an und geht automatisch zur Seite **Setupdateien installieren** über.  

8. Auf der Seite **Setupdateien installieren** wird der Status angezeigt, während die Setupdateien heruntergeladen, extrahiert und installiert werden. Wenn ein Update für Setup gefunden und angegeben wird, dass das Update eingeschlossen werden soll, wird dieses Update ebenfalls installiert. Wenn kein Update gefunden wird, wird das Setup automatisch fortgefahren.
  
9. Unter **Installationsregeln** überprüft Setup hinsichtlich potenzieller Probleme, die beim Ausführen des Setups auftreten können. Wenn Fehler auftreten, klicken Sie für weitere Informationen auf ein Element in der Spalte **Status**. Wählen Sie andernfalls **Weiter** aus.

10. Ist dies die erste [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Installation auf dem Computer, überspringt Setup die Seite **Installationstyp**, und die Installation wechselt direkt zur Seite **Funktionsauswahl**. Wenn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bereits auf dem System installiert ist, legen Sie auf der Seite **Installationstyp** entweder fest, dass eine Neuinstallation durchgeführt werden soll oder dass Funktionen zu einer vorhandenen Installation hinzugefügt werden sollen. Wählen Sie zum Fortsetzen des Vorgangs **Weiter** aus.
  
11. Wählen Sie auf der Seite **Funktionsauswahl** die Komponenten für die Installation aus. Um eine neue Instanz der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] zu installieren, wählen Sie die **Datenbank-Engine-Dienste** aus.

    Nach Auswahl des Funktionsnamens wird im Abschnitt **Funktionsbeschreibung** eine Beschreibung für die einzelnen Komponentengruppen angezeigt. Sie können jede beliebige Kombination von Kontrollkästchen aktivieren. Weitere Informationen finden Sie unter [Editionen und Komponenten von SQL Server 2016](../../sql-server/editions-and-components-of-sql-server-2016.md) oder unter [Editionen und Komponenten für SQL Server 2017](../../sql-server/editions-and-components-of-sql-server-2017.md).
  
     Die erforderlichen Komponenten für die ausgewählten Funktionen werden im Abschnitt **Voraussetzungen für ausgewählte Funktionen** angezeigt. Setup installiert die erforderlichen Komponenten, die nicht bereits während des Installationsschritts installiert werden, der im weiteren Verlauf dieser Prozedur beschrieben wird.  
  
     Sie können auch ein benutzerdefiniertes Verzeichnis für freigegebene Komponenten angeben. Verwenden Sie dazu das Feld unten auf der Seite **Funktionsauswahl**. Um den Installationspfad für freigegebene Komponenten zu ändern, aktualisieren Sie den Pfadnamen im Feld unten im Dialogfeld, oder klicken Sie auf **Durchsuchen**, um zu einem Installationsverzeichnis zu wechseln. Der Standardinstallationspfad lautet [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)].  
  
     > [!NOTE]
     > Der Pfad für die freigegebenen Komponenten muss ein absoluter Pfad sein. Der Ordner darf nicht komprimiert oder verschlüsselt werden. Zugeordnete Laufwerke werden nicht unterstützt.  
  
     SQL Server verwendet zwei Verzeichnisse für freigegebene Funktionen:
  
     * Freigegebenes Funktionsverzeichnis  
     * Freigegebenes Funktionsverzeichnis (x86)  
  
     > [!NOTE]
     > Für jeden der oben erwähnten Optionen muss ein anderer Pfad angegeben werden.  
  
12. Auf der Seite **Funktionsregeln** wird automatisch fortgefahren, wenn alle Regeln gültig sind.  
  
13. Geben Sie auf der Seite **Instanzkonfiguration** an, ob Sie eine Standardinstanz oder eine benannte Instanz installieren möchten. Weitere Informationen finden Sie unter [Instanzkonfiguration](../../sql-server/install/instance-configuration.md#instance-configuration-page).  
  
     * **Instanz-ID**: In der Standardeinstellung wird der Instanzname als Instanz-ID verwendet. Mit der ID werden Installationsverzeichnisse und Registrierungsschlüssel für die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identifiziert. Dasselbe Verhalten tritt für Standardinstanzen und benannte Instanzen auf. Bei einer Standardinstanz lauten Instanzname und Instanz-ID MSSQLSERVER. Um eine nicht standardmäßige Instanz-ID zu verwenden, geben Sie einen anderen Wert in das Feld **Instanz-ID** ein.  
  
       > [!NOTE]  
       > Typische eigenständige [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)]-Instanzen – sowohl Standardinstanzen als auch benannte Instanzen – verwenden keine Nicht-Standardwerte für die Instanz-ID.  
  
       Alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Service Packs und Updates werden für jede Komponente einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] übernommen.  
  
     * **Installierte Instanzen**: Im Raster werden die Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] angezeigt, die sich auf dem Computer befinden, auf dem Setup ausgeführt wird. Wenn bereits eine Standardinstanz auf dem Computer installiert ist, muss eine benannte Instanz von [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)]installiert werden.  
  
     Der Workflow für die weitere Installation ist von den Funktionen abhängig, die Sie für die Installation angegeben haben. Je nach Auswahl werden möglicherweise nicht alle Seiten angezeigt.  
  
14. Geben Sie auf der Seite **Serverkonfiguration – Dienstkonten** Anmeldekonten für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Dienste an. Welche Dienste tatsächlich auf dieser Seite konfiguriert werden, ist von den Funktionen abhängig, die Sie für die Installation ausgewählt haben. Weitere Informationen zu den Konfigurationseinstellungen finden Sie unter [Hilfe zum Installations-Assistenten](../../sql-server/install/instance-configuration.md#serverconfig).
  
     Sie können allen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Diensten dasselbe Anmeldekonto zuweisen, oder Sie können jedes Dienstkonto einzeln konfigurieren. Außerdem können Sie angeben, ob Dienste automatisch starten sollen, manuell gestartet werden oder deaktiviert sind. Es wird empfohlen, die Dienstkonten einzeln zu konfigurieren, um die niedrigsten Berechtigungen für jeden Dienst bereitzustellen. Stellen Sie sicher, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Diensten die Mindestberechtigungen gewährt werden, die sie zum Ausführen ihre Aufgaben benötigen. Weitere Informationen finden Sie unter [Konfigurieren von Windows-Dienstkonten und -Berechtigungen](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
     Um für alle Dienstkonten in dieser Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dasselbe Anmeldekonto anzugeben, geben Sie in den Feldern unten auf dieser Seite die entsprechenden Anmeldeinformationen ein.  
  
    > [!IMPORTANT]  
    > [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  

    > [!NOTE]
    > Für Versionen ab [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]: Aktivieren Sie das Kontrollkästchen **SQL Server Database Engine Services Berechtigung zum Ausführen von Volumewartungstasks zuweisen**, um dem Dienstkonto [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] die Verwendung der [schnellen Dateiinitialisierung für Datenbanken](../../relational-databases/databases/database-instant-file-initialization.md) zu ermöglichen.
  
     Verwenden Sie die Seite **Serverkonfiguration – Sortierung**, um nicht standardmäßige Sortierungen für [!INCLUDE[ssDE](../../includes/ssde-md.md)] und [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] anzugeben. Weitere Informationen finden Sie unter [Sortierungen und Unicode-Unterstützung](../../relational-databases/collations/collation-and-unicode-support.md).  
  
15. Geben Sie auf der Seite für die **Konfiguration der Datenbank-Engine – Serverkonfiguration** folgende Optionen an:  
  
    * **Sicherheitsmodus**: Wählen Sie für die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die **Windows-Authentifizierung** oder die **Authentifizierung im gemischten Modus** aus. Bei Auswahl der **Authentifizierung im gemischten Modus** müssen Sie ein sicheres Kennwort für das integrierte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Systemadministratorkonto angeben.  
  
       Nachdem ein Gerät erfolgreich eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hergestellt hat, wird für die Windows-Authentifizierung und die Authentifizierung im gemischten Modus derselbe Sicherheitsmechanismus verwendet. Weitere Informationen finden Sie unter [Konfiguration der Datenbank-Engine – Serverkonfiguration](../../sql-server/install/instance-configuration.md#serverconfig).
  
    * **SQL Server-Administratoren**: Sie müssen wenigstens einen Systemadministrator für die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] angeben. Um das Konto hinzuzufügen, unter dem das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup ausgeführt werden soll, klicken Sie auf **Aktuellen Benutzer hinzufügen**. Um Konten zur Liste der Systemadministratoren hinzuzufügen bzw. daraus zu entfernen, klicken Sie auf **Hinzufügen** bzw. **Entfernen**, und bearbeiten Sie anschließend die Liste der Benutzer, Gruppen bzw. Computer, die Administratorrechte für die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz haben sollen.  
  
     Geben Sie ggf. auf der Seite **Konfiguration der Datenbank-Engine – Datenverzeichnisse** andere Installationsverzeichnisse als das Standardinstallationsverzeichnis an. Wenn die Installation in Standardverzeichnissen erfolgen soll, wählen Sie **Weiter** aus.  
  
    > [!IMPORTANT]  
    > Wenn Sie andere Installationsverzeichnisse als die Standardverzeichnisse angeben, müssen Sie sicherstellen, dass die Installationsordner nur für diese Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet werden. Keines der Verzeichnisse in diesem Dialogfeld sollte gemeinsam mit Verzeichnissen anderer Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]genutzt werden.  
  
     Weitere Informationen finden Sie unter [Konfiguration der Datenbank-Engine – Serverkonfiguration](../../sql-server/install/instance-configuration.md#datadir).

     Verwenden Sie die Seite **Konfiguration der Datenbank-Engine – TempDB**, um die Dateigröße, Anzahl der Dateien, nicht standardmäßige Installationsverzeichnisse und Dateiwachstumseinstellungen für **tempdb** zu konfigurieren. Weitere Informationen finden Sie unter [Konfiguration der Datenbank-Engine – TempDB](../../sql-server/install/instance-configuration.md#tempdb).  

     ::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"

     Geben Sie auf der Registerkarte für die **Konfiguration der [!INCLUDE[ssDE](../../includes/ssde-md.md)] – MaxDOP** den maximalen Grad an Parallelität an. Diese Einstellung bestimmt, wie viele Prozessoren eine einzelne Anweisung während der Ausführung verwenden kann. Der empfohlene Wert wird während der Installation automatisch berechnet. Weitere Informationen finden Sie unter den [Richtlinien für den max. Grad an Parallelität](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md#Guidelines). Diese Option ist nur ab SQL Server 2019 verfügbar. 

     Verwenden Sie die Registerkarte **Konfiguration der Datenbank-Engine – Speicher**, um die MIN- und MAX-Speicherwerte anzugeben, die diese Instanz von SQL Server nach dem Start verwenden soll. Sie können die Standardwerte oder die berechneten empfohlenen Werte verwenden oder Ihre eigenen Werte manuell angeben, nachdem Sie die Option **Empfohlen** gewählt haben. Diese Funktion ist nur in Setup ab SQL Server 2019 verfügbar. 

     ::: moniker-end

     Aktivieren Sie auf der Seite **Konfiguration der Datenbank-Engine – FILESTREAM** den FILESTREAM für Ihre Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Weitere Informationen finden Sie unter [Konfiguration der Datenbank-Engine – FILESTREAM](../../sql-server/install/instance-configuration.md#database-engine-configuration---filestream-page).  
  
16. Verwenden Sie die Seite **Analysis Services-Konfiguration – Kontenbereitstellung**, um den Servermodus und die Benutzer oder Konten anzugeben, die über Administratorberechtigungen für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] verfügen sollen. Durch den Servermodus wird bestimmt, welcher Arbeitsspeicher und welche Speichersubsysteme auf dem Server verwendet werden. Die unterschiedlichen Projektmappentypen werden in verschiedenen Servermodi ausgeführt. Wenn Sie beabsichtigen, mehrdimensionale Cubedatenbanken auf dem Server auszuführen, wählen Sie die Standardoption für den Servermodus **Mehrdimensionales und Data Mining** aus.

    Sie müssen wenigstens einen Systemadministrator für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] angeben:

    * Um das Konto hinzuzufügen, unter dem das SQL Server-Setup ausgeführt wird, klicken Sie auf **Aktuellen Benutzer hinzufügen**.

    * Um Konten zur Liste der Systemadministratoren hinzuzufügen bzw. daraus zu entfernen, klicken Sie auf **Hinzufügen** bzw. **Entfernen**, und bearbeiten Sie anschließend die Liste der Benutzer, Gruppen bzw. Computer, die Administratorrechte für [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] haben sollen.

    Weitere Informationen zu Servermodus und Administratorberechtigungen finden Sie unter [Analysis Services-Konfiguration – Kontobereitstellung](../../sql-server/install/instance-configuration.md#analysis-services-configuration---account-provisioning-page).

    Wenn Sie die Bearbeitung der Liste abgeschlossen haben, klicken Sie auf **OK**. Überprüfen Sie die Liste der Administratoren im Konfigurationsdialogfeld. Wenn die Liste vollständig ist, wählen Sie **Weiter** aus.

    Geben Sie ggf. auf der Seite **Analysis Services-Konfiguration – Datenverzeichnisse andere Installationsverzeichnisse** als das Standardinstallationsverzeichnis an. Wenn die Installation in Standardverzeichnissen erfolgen soll, wählen Sie **Weiter** aus.  

    > [!IMPORTANT]  
    > Wenn Sie bei der Installation von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] für INSTANCEDIR und SQLUSERDBDIR denselben Verzeichnispfad angeben, starten SQL Server-Agent und die Volltextsuche aufgrund fehlender Berechtigungen nicht.  
    >  
    > Wenn Sie andere Installationsverzeichnisse als die Standardverzeichnisse angeben, müssen Sie sicherstellen, dass die Installationsordner nur für diese Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet werden. Keines der Verzeichnisse in diesem Dialogfeld sollte gemeinsam mit Verzeichnissen anderer Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]genutzt werden.  

    Weitere Informationen finden Sie unter [Analysis Services-Konfiguration – Datenverzeichnisse](../../sql-server/install/instance-configuration.md#analysis-services-configuration---data-directories-page).  

17. Verwenden Sie die Seite für die **Distributed Replay Controller-Konfiguration**, um die Benutzer anzugeben, denen Sie Administratorberechtigungen für den Distributed Replay Controller-Dienst erteilen möchten. Benutzer, die über Administratorberechtigungen verfügen, besitzen unbeschränkten Zugriff auf den Distributed Replay Controller-Dienst.  
  
     * Klicken Sie auf die Schaltfläche **Aktuellen Benutzer hinzufügen**, um die Benutzer hinzuzufügen, denen Sie Zugriffsberechtigungen für den Distributed Replay Controller-Dienst erteilen möchten.

     * Klicken Sie auf die Schaltfläche **Hinzufügen**, um andere Benutzer hinzuzufügen, denen Sie Zugriffsberechtigungen für den Distributed Replay Controller-Dienst erteilen möchten.

     * Klicken Sie auf die Schaltfläche **Entfernen**, um Zugriffsberechtigungen für den Distributed Replay Controller-Dienst zu entfernen.

     * Wählen Sie zum Fortsetzen des Vorgangs **Weiter** aus.  
  
18. Verwenden Sie die Seite für die **Distributed Replay Client-Konfiguration**, um die Benutzer anzugeben, denen Sie Administratorberechtigungen für den Distributed Replay Client-Dienst erteilen möchten. Benutzer, die über Administratorberechtigungen verfügen, besitzen unbeschränkten Zugriff auf den Distributed Replay Client-Dienst.  
  
     * **Controllername** ist optional. Der Standardwert ist \<*leer*>. Geben Sie den Namen des Controllers ein, mit dem der Clientcomputer für den Distributed Replay Client-Dienst kommuniziert:  
  
       * Wenn Sie bereits einen Controller eingerichtet haben, geben Sie den Namen des Controllers beim Konfigurieren jedes Clients ein.  
  
       * Wenn Sie noch keinen Controller eingerichtet haben, können Sie das Feld für den Controllernamen leer lassen. Sie müssen den Controllernamen jedoch in der **Clientkonfigurationsdatei** manuell eingeben.  
  
     * Geben Sie das **Arbeitsverzeichnis** für den Distributed Replay Client-Dienst an. Das Standardarbeitsverzeichnis ist \<*Laufwerkbuchstabe*>:\Programme\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\WorkingDir\\.  
  
     * Geben Sie das **Ergebnisverzeichnis** für den Distributed Replay Client-Dienst an. Das Standardergebnisverzeichnis ist \<*Laufwerkbuchstabe*>:\Programme\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\ResultDir\\.  
  
     * Wählen Sie zum Fortsetzen des Vorgangs **Weiter** aus.  
  
19. Auf der Seite **Installationsbereit** wird eine Strukturansicht der Installationsoptionen angezeigt, die während des Setups angegeben wurden. Auf dieser Setupseite ist neben der letzten Updateversion auch angegeben, ob die **Produktupdatefunktion** aktiviert oder deaktiviert ist.  
  
     Klicken Sie auf **Installieren**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup installiert zuerst die erforderlichen Komponenten für die ausgewählten Funktionen und dann die ausgewählten Funktionen.  
  
20. Während der Installation wird auf der Seite **Installationsstatus** der Status der Updates angezeigt, sodass Sie während der Installation den Installationsstatus überwachen können.  
  
21. Nach der Installation bietet die Seite **Abgeschlossen** einen Link zur zusammenfassenden Protokolldatei für die Installation und andere wichtige Hinweise.
  
    > [!IMPORTANT]
    > Wenn Sie den Setupvorgang abgeschlossen haben, lesen Sie die vom Installations-Assistenten angezeigte Meldung. Weitere Informationen finden Sie unter [Lesen und Anzeigen der Setupprotokolldateien von SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).

    Klicken Sie auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Schließen **, um die Installation von**  abzuschließen.  
  
22. Starten Sie den Computer neu, falls Sie dazu aufgefordert werden.

## <a name="next-steps"></a>Nächste Schritte

[Konfigurieren Sie die neue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Installation](https://docs.microsoft.com/sql/database-engine/configure-windows/database-engine-instances-sql-server?view=sql-server-2017).  
  
Zum Reduzieren der Angriffsfläche eines Systems werden zentrale Dienste und Funktionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] selektiv installiert und aktiviert. Weitere Informationen finden Sie unter [Oberflächenkonfiguration](../../relational-databases/security/surface-area-configuration.md).  
  
## <a name="see-also"></a>Siehe auch
  
* [Überprüfen einer SQL Server-Installation](../../database-engine/install-windows/validate-a-sql-server-installation.md)  
* [Reparieren von Fehlern bei einer SQL Server-Installation](../../database-engine/install-windows/repair-a-failed-sql-server-installation.md)
* [Lesen und Anzeigen der Setupprotokolldateien von SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)
* [Upgrade von SQL Server mithilfe des Installations-Assistenten (Setup)](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)
* [Install SQL Server from the command prompt (Installieren von SQL Server über die Eingabeaufforderung)](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md) 
