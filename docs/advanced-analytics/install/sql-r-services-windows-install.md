---
title: Installieren Sie SQL Server 2016 R Services (Datenbankintern) – SQLServer Machine Learning
description: Hinzufügen von R-sprachunterstützung mit einer Datenbank-Engine auf SQL Server 2016 R Services auf Windows-Programmierung.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/01/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 787b26c401f825c6c74298a803a16d59f1a37d04
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58511007"
---
# <a name="install-sql-server-2016-r-services"></a>Installieren von SQL Server 2016 R Services
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel wird erläutert, wie zum Installieren und konfigurieren **SQL Server 2016 R Services**. Wenn Sie SQL Server 2016 verfügen, installieren Sie dieses Feature, um die Ausführung von R-Code in SQL Server zu ermöglichen.

In SQL Server 2017 wird die Integration von R in Angeboten [Machine Learning Services](../r/r-server-standalone.md), das Hinzufügen von Python zu reflektieren. Wenn Sie möchten die Integration von R und SQL Server 2017-Installationsmedien, finden Sie unter [installieren Sie SQL Server 2017 Machine Learning Services](sql-machine-learning-services-windows-install.md) zum Hinzufügen der Funktion. 

<a name="bkmk_prereqs"> </a> 

## <a name="pre-install-checklist"></a>Checkliste für die vor der Installation

+ Eine Instanz der Datenbank-Engine ist erforderlich. Sie können nicht nur R installieren, obwohl Sie es schrittweise zu einer vorhandenen Instanz hinzufügen können.

+ Für die Geschäftskontinuität [Always On Availabilty Groups](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server) für R Services verwendet werden. Sie müssen R Services installieren und Konfigurieren von Paketen, auf den einzelnen Knoten.

+ Installieren Sie R Services nicht auf einem Failovercluster. Der Sicherheitsmechanismus, der zum Isolieren von R-Prozessen verwendet, ist nicht mit einer Windows Server-Failoverclusterumgebung kompatibel.

+ Installieren Sie R Services nicht auf einem Domänencontroller. Der R Services-Teil der Installation schlägt fehl.

+ Installieren Sie nicht **gemeinsam genutzte Funktionen** > **R Server (eigenständig)** auf demselben Computer eine in der Datenbank-Instanz ausführen. 

  Seite-an-Seite-Installation mit anderen Versionen von R und Python sind möglich, da SQL Server-Instanz eine eigene Kopien der Open-Source-R "und" Anaconda Verteilungen verwendet. Ausführen von Code, die R- und Python auf dem SQL Server-Computer außerhalb von SQL Server verwendet, kann jedoch zu verschiedenen Problemen führen:
    
  + Sie verwenden eine andere Bibliothek und andere ausführbare Datei, und unterschiedliche Ergebnisse zu erhalten, als Sie tun, wenn Sie in SQL Server ausgeführt werden.
  + R und Python-Skripts in externen Bibliotheken können nicht von SQL Server, vorangestellte zu Ressourcenkonflikten verwaltet werden.
  
Wenn Sie alle vorherigen Versionen der Revolution Analytics Development Environment oder der RevoScaleR-Pakete verwendet, oder wenn Sie alle Vorabversionen von SQL Server 2016 installiert haben, müssen Sie sie deinstallieren. Mit älteren und neueren Versionen von RevoScaleR und anderen proprietären Pakete wird nicht unterstützt. Hilfe beim Entfernen von früheren Versions, finden Sie unter [Upgrade und Installation – häufig gestellte Fragen für SQL Server Machine Learning Services](../r/upgrade-and-installation-faq-sql-server-r-services.md).

> [!IMPORTANT]
> Nachdem Setup abgeschlossen ist, achten Sie darauf, dass Sie für die zusätzliche Aufgaben nach der Konfiguration in diesem Artikel beschriebenen Schritte. Diese Schritte umfassen SQL Server zur Verwendung externer Skripts aktivieren und Hinzufügen von Konten, die für SQL Server zum Ausführen von R-Aufträge in Ihrem Namen erforderlich sind. Konfigurationsänderungen erfordern in der Regel ein Neustart der Instanz oder einen Neustart des Launchpad-Diensts.

## <a name="get-the-installation-media"></a>Abrufen der Installationsmedien

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

<a name="bkmk_ga_instalpatch"></a>

 ### <a name="install-patch-requirement"></a>Installieren einer patchanforderung 

Microsoft hat ein Problem bei der speziellen Version von Microsoft VC++ 2013 Runtime-Binärdateien erkannt, die von SQL Server als vorausgesetzte Komponenten installiert werden. Wenn dieses Update an den VC++ Runtime-Binärdateien nicht installiert wird, können bei SQL Server in bestimmten Szenarios Stabilitätsprobleme auftreten. Bevor Sie SQL Server installieren, sollten Sie entsprechend den Anweisungen unter [Versionsanmerkungen zu SQL Server](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch) vorgehen, um festzustellen, ob Ihr Computer einen Patch für die VC-Runtime-Binärdateien benötigt.  

<a name="bkmk2016top"></a>

## <a name="run-setup"></a>Ausführen von 'Setup'

Bei lokalen Installationen müssen Sie das Setup als Administrator ausführen. Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von einer Remotefreigabe installieren, müssen Sie ein Domänenkonto verwenden, das Lese- und Ausführungsberechtigungen auf der Remotefreigabe hat.

1. Starten Sie den Setup-Assistenten für SQL Server 2016.

2. Auf der **Installation** Registerkarte **eigenständige neue SQL Server-Installation oder Hinzufügen von Funktionen zu einer vorhandenen Installation**.
    
   ![Installieren von R Services (Datenbankintern)](media/2016-setup-installation-rsvcs.png "Starten der Installation der Datenbank-Engine mit R Services")
   
3. Auf der **Funktionsauswahl** Seite, wählen Sie die folgenden Optionen:

   - Wählen Sie **Datenbankmoduldienste**. Die Datenbank-Engine ist in den einzelnen Instanzen erforderlich, das Machine Learning verwendet.
   - Wählen Sie **R Services (Datenbankintern)**. Installiert die Unterstützung für in der Datenbank mithilfe von R.
    
     ![R Services Funktionsauswahl](media/2016setup-rsvcs-features.png "wählen Sie diese Funktionen für R Services In der Datenbank")

    > [!IMPORTANT]
    > Installieren Sie R-Server und R Services nicht zur gleichen Zeit. Sie würden normalerweise installieren R Server (eigenständig) zum Erstellen einer Umgebung, die ein Data Scientist oder Entwickler verwendet werden, die Verbindung mit SQL Server und R-Lösungen bereitzustellen. Daher besteht keine Notwendigkeit beide auf demselben Computer zu installieren.

4.  Auf der **zustimmen, installieren Sie Microsoft R Open** auf **Accept**.
  
    Die Lizenzbedingungen ist erforderlich, um Microsoft R Open, enthält eine Verteilung der Open-Source-R-Basispakete und zusammen mit verbesserten R-Pakete und konnektivitätsanbieter von den Entwicklungsteams von Microsoft R-Tools herunterzuladen.
  
5. Nachdem Sie die Lizenzbedingungen akzeptiert haben, ist eine kurze Pause, während der Installer vorbereitet wird. Klicken Sie auf **Weiter** Wenn die Schaltfläche verfügbar wird.

6. Auf der **Installationsbereit** Seite, stellen Sie sicher, dass die folgenden Elemente enthalten, und Sie dann wählen **installieren**.

   + -Datenbank-Engine-Dienste
   + R Services (In-Database)

    Notieren Sie sich den Speicherort des Ordners, unter dem Pfad `..\Setup Bootstrap\Log` , in dem die Konfigurationsdateien gespeichert werden. Wenn Setup abgeschlossen ist, können Sie in der Datei für die Zusammenfassung der installierten Komponenten überprüfen.

7. Nachdem Setup abgeschlossen ist, wenn Sie aufgefordert werden, den Computer neu starten, tun Sie dies jetzt. Wenn Sie den Setupvorgang abgeschlossen haben, sollten Sie unbedingt die vom Installations-Assistenten angezeigte Meldung lesen. Weitere Informationen finden Sie unter [View and Read SQL Server Setup Log Files](https://docs.microsoft.com/sql/database-engine/install-windows/view-and-read-sql-server-setup-log-files).

## <a name="set-environment-variables"></a>Festlegen von Umgebungsvariablen

Sie sollten für die R-Funktionsintegration nur Festlegen der **MKL_CBWR** -Umgebungsvariable so fest, [sicherstellen von konsistenten Ausgabe](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr) von Intel Math Kernel Library (MKL) Berechnungen.

1. Klicken Sie in der Systemsteuerung auf **System und Sicherheit** > **System** > **Erweiterte Systemeinstellungen**  >   **Umgebungsvariablen**.

2. Erstellen Sie eine neue Variable für Benutzer- oder Systemkonto. 

  + Set-Variablennamen, um `MKL_CBWR`
  + Legen Sie den Wert den Variablen auf `AUTO`

Dieser Schritt erfordert einen Neustart des Servers. Wenn Sie sind im Begriff, die Ausführung des Skripts zu aktivieren, können Sie beim Neustart halten deaktiviert, bis alle Aufgaben Konfiguration erfolgt.

<a name="bkmk_enableFeature"></a>

##  <a name="enable-script-execution"></a>Skriptausführung aktivieren

1. Öffnen Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. 

    > [!TIP]
    > Sie können die herunterladen und installieren die entsprechende Version von dieser Seite: [Herunterladen von SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)
    > 
    > Sie können auch versuchen, sich die Preview-Version von [Studio für Azure Data](../../azure-data-studio/what-is.md), administrative Aufgaben und Abfragen für SQL Server unterstützt.
  
2. Verbinden mit der Instanz, in denen Sie Machine Learning-Dienste installiert haben, klicken Sie auf **neue Abfrage** , öffnen ein Abfragefenster, und führen den folgenden Befehl aus:

   ```sql
   sp_configure
   ```
    Der Wert für die Eigenschaft `external scripts enabled` sollte an diesem Punkt **0** betragen. Der Grund ist die Funktion standardmäßig deaktiviert ist. Die Funktion muss explizit von einem Administrator aktiviert werden, bevor Sie R- oder Python-Skripts ausführen können.
     
3. Um die Skripterstellung Feature "external" zu aktivieren, führen Sie die folgende Anweisung aus:
  
    ```sql
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
## <a name="restart-the-service"></a>Starten Sie den Dienst neu.

Wenn die Installation abgeschlossen ist, die Datenbank-Engine neu starten, vor dem Fortfahren mit der nächsten Ausführung des Skripts zu aktivieren.

Neustarten des Diensts auch automatisch neu gestartet wird das zugehörige [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] Service.

Können Sie den Dienst, mit der rechten Maustaste neu starten **neu starten** Befehl für die Instanz in SSMS oder mithilfe der **Services** Bereich in der Systemsteuerung oder mithilfe von [SQL Server-Konfigurations-Manager ](../../relational-databases/sql-server-configuration-manager.md).

## <a name="verify-installation"></a>Überprüfen der Installation

Überprüfen Sie den Installationsstatus der Instanz mit [benutzerdefinierte Berichte](../r/monitor-r-services-using-custom-reports-in-management-studio.md).

Verwenden Sie die folgenden Schritte aus, um sicherzustellen, dass alle Komponenten, die zum Starten von externen Skripts ausgeführt werden.

1. Öffnen Sie in SQL Server Management Studio ein neues Abfragefenster, und führen Sie den folgenden Befehl aus:
    
    ```sql
    EXEC sp_configure  'external scripts enabled'
    ```

    Der Wert **Run_value** sollte jetzt auf 1 festgelegt werden.

2. Öffnen der **Services** Panel oder SQL Server-Konfigurations-Manager, und vergewissern Sie sich **SQL Server Launchpad-Dienst** ausgeführt wird. Sie sollten einen Dienst für jede Datenbank-Engine-Instanz, die R oder Python installiert sein. Weitere Informationen zum Dienst finden Sie unter [Erweiterungsframework](../concepts/extensibility-framework.md).

7. Wenn Launchpad ausgeführt wird, sollten Sie in der Lage, führen Sie einfache R, um sicherzustellen, dass externe Laufzeiten, die Skripts mit SQL Server kommunizieren können. 

    Öffnen Sie ein neues **Abfrage** -Fensters im [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], und klicken Sie dann ein Skript wie dem folgenden ausführen:
    
    ```sql
    EXEC sp_execute_external_script  @language =N'R',
    @script=N'
    OutputDataSet <- InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

    Das Skript kann etwas dauern, während der erstmaligen Ausführung der externen Skript-Laufzeit geladen wird. Die Ergebnisse sollten in etwa wie folgt aussehen:

    | Hello |
    |----|
    | 1|

<a name="apply-cu"></a>

## <a name="apply-updates"></a>Anwenden von updates

Es wird empfohlen, dass Sie das neueste kumulative Update für die Datenbank-Engine und Machine learning-Komponenten anwenden.

Auf dem Internet verbundene Geräte kumulative Updates werden in der Regel über Windows Update angewendet, aber Sie können auch die unten beschriebenen Schritte verwenden, für kontrollierte Updates. Bei der Installation des Updates für die Datenbank-Engine ruft Setup den kumulativen Updates für R-Bibliotheken, die auf derselben Instanz installiert. 

Auf getrennten Servern sind zusätzliche Schritte erforderlich. Weitere Informationen finden Sie unter [auf Computern ohne Internetzugang installieren > Anwenden von kumulativen Updates](sql-ml-component-install-without-internet-access.md#apply-cu).

1. Beginnen Sie mit einer Baseline-Instanz, die bereits installiert: Erste Version von SQL Server 2016, SQL Server 2016 SP1 oder SQL Server 2016 SP 2.

2. Wechseln Sie zur Liste Kumulatives Update: [Updates für SQL Server 2016](https://sqlserverupdates.com/sql-server-2016-updates/)

3. Wählen Sie das neueste kumulative Update an. Eine ausführbare Datei wird automatisch heruntergeladen und extrahiert.

4. Führen Sie das Setup aus. Akzeptieren Sie die Lizenzbedingungen, und überprüfen Sie auf der Seite Funktionsauswahl, die Sie die Funktionen, die für die kumulativen Updates angewendet werden. Jede Funktion, die für die aktuelle Instanz, einschließlich der R Services installiert sind, sollte angezeigt werden. Die CAB-Dateien, die zum Aktualisieren aller Features von Setup heruntergeladen.

5. Weiterhin über den Assistenten, akzeptieren die Lizenzbedingungen für die R-Verteilung. 

<a name="bkmk_FollowUp"></a> 

## <a name="additional-configuration"></a>Zusätzliche Konfiguration

Wenn im externen Skript-Überprüfungsschritt erfolgreich war, können Sie die Python-Befehle ausführen, von SQL Server Management Studio, Visual Studio Code oder einem anderen Client, der T-SQL-Anweisungen an den Server senden kann.

Wenn Sie einen Fehler beim Ausführen des Befehls erhalten haben, überprüfen Sie die zusätzlichen Konfigurationsschritte in diesem Abschnitt. Möglicherweise müssen Sie zusätzliche geeignete Konfigurationen an den Dienst oder die Datenbank.

Auf Instanzebene kann zusätzliche Konfigurationsschritte Folgendes umfassen:

* [Konfiguration der Firewall für SQL Server Machine Learning Services](../../advanced-analytics/security/firewall-configuration.md)
* [Zusätzliche Netzwerkprotokolle aktivieren](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)
* [Aktivieren von Remoteverbindungen](../../database-engine/configure-windows/configure-the-remote-access-server-configuration-option.md)

<a name="bkmk_configureAccounts"></a>
<a name="bkmk_AllowLogon"></a>

In der Datenbank benötigen Sie möglicherweise die folgenden konfigurationsupdates:

* [Vergabe von Benutzerberechtigungen für SQL Server Machine Learning Services](../../advanced-analytics/security/user-permission.md)
* [Hinzufügen der SQLRUserGroup als Datenbankbenutzer](../../advanced-analytics/security/add-sqlrusergroup-to-database.md)

> [!NOTE]
> Nicht alle aufgeführten Änderungen sind erforderlich, und keine kann erforderlich sein. Anforderungen basieren auf Ihre Sicherheitsschema, auf dem SQL Server, und wie Sie erwarten, dass Benutzer eine Verbindung mit der Datenbank herstellen und Ausführen externer Skripts installiert. Weitere Tipps zur Problembehandlung finden Sie hier: [Häufig gestellte Fragen zu Upgrade und Installation](../r/upgrade-and-installation-faq-sql-server-r-services.md)

## <a name="suggested-optimizations"></a>Vorgeschlagenen Optimierungen

Nun, da Sie alles funktioniert haben, Sie können auch den Server zur Unterstützung von Machine Learning optimieren möchten, oder installieren pretrained Modelle.

### <a name="add-more-worker-accounts"></a>Fügen Sie weitere Konten hinzu.

Wenn Sie glauben, dass Sie R intensiv verwenden können, oder Sie erwarten, dass viele Benutzer gleichzeitig Skripts ausführen werden, können Sie die Anzahl der workerkonten erhöhen, die den Launchpad-Dienst zugewiesen sind. Weitere Informationen finden Sie unter [Ändern des benutzerkontenpools für SQL Server Machine Learning Services](../administration/modify-user-account-pool.md).

<a name="bkmk_optimize"></a>

### <a name="optimize-the-server-for-external-script-execution"></a>Optimieren des Servers für die Ausführung des externen Skripts

Die Standardeinstellungen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup dienen, den Saldo des Servers für eine Vielzahl von Diensten zu optimieren, die von der Datenbank-Engine unterstützt werden, einschließlich extrahieren, Transformieren und laden (ETL)-Prozesse, reporting, Überwachung, und Anwendungen, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Daten. Aus diesem Grund können die Standardeinstellungen finden Sie unter, dass Ressourcen für Machine Learning eingeschränkt oder, insbesondere für speicherintensive Vorgänge gedrosselt.

Um sicherzustellen, dass Machine Learning-Aufträge priorisiert und Ressourcen entsprechend zugewiesen sind, empfehlen wir, dass Sie SQL Server-Ressourcenkontrolle verwenden, um einen externen Ressourcenpool zu konfigurieren. Sie sollten auch die Menge an Arbeitsspeicher zu ändern, die zugeordnet wird, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank-Engine, oder erhöhen Sie die Anzahl der Konten, die unter ausgeführt werden soll. die [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] Service.

- Um einen Ressourcenpool für die Verwaltung von externen Ressourcen konfigurieren zu können, finden Sie unter [erstellen Sie einen externen Ressourcenpool](../../t-sql/statements/create-external-resource-pool-transact-sql.md).
  
- Um den reservierten Umfang an Arbeitsspeicher für die Datenbank zu ändern, finden Sie unter [Serverkonfigurationsoptionen für den Arbeitsspeicher](../../database-engine/configure-windows/server-memory-server-configuration-options.md).
  
- So ändern Sie die Anzahl der R-Konten, die durch gestartet werden kann [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], finden Sie unter [Ändern des benutzerkontenpools für Machine Learning](../administration/modify-user-account-pool.md).

Wenn Sie Standard Edition verwenden und nicht über Ressourcenkontrolle verfügen, können Sie dynamische Verwaltungssichten (DMVs) und erweiterte Ereignisse, als auch Windows-Ereignis überwachen, um die Server-Ressourcen zu verwalten, die von r verwendet werden Weitere Informationen finden Sie unter [überwachen und Verwalten von R Services](../r/managing-and-monitoring-r-solutions.md).

### <a name="install-additional-r-packages"></a>Installieren zusätzlicher R-Pakete

Die R-Lösungen, die Sie für SQL Server zu erstellen, können grundlegende R-Funktionen, Funktionen aus der proprietären Pakete, die mit SQL Server installiert, und R-Pakete von Drittanbietern kompatibel mit der Version von Open-Source-R-Installation von SQL Server aufrufen.

Pakete, die Sie von SQL Server verwenden möchten, müssen in der Standardbibliothek installiert sein, die von der Instanz verwendet wird. Wenn Sie eine separate Installation von R auf dem Computer, oder wenn Sie Pakete in benutzerbibliotheken installiert haben, nicht möglich, diese Pakete von T-SQL verwenden.

Der Prozess zum Installieren und Verwalten von R-Pakete ist in SQL Server 2016 und SQL Server 2017 anders. In SQL Server 2016 muss ein Datenbankadministrator R-Pakete installieren, die Benutzer benötigen. In SQL Server 2017 können Sie Benutzergruppen zum Freigeben von Paketen auf einer Ebene pro Datenbank einrichten oder konfigurieren Datenbankrollen, damit Benutzer ihre eigenen Pakete installieren können. Weitere Informationen finden Sie unter [Installieren neuer R-Pakete](../r/install-additional-r-packages-on-sql-server.md).

## <a name="next-steps"></a>Nächste Schritte

R-Entwickler können mit einigen einfachen Beispielen beginnen, und die Grundlagen der Funktionsweise von R mit SQL Server. Der nächste Schritt ist finden Sie in den folgenden Links:

+ [Tutorial: Run R in T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Tutorial: Datenbankinterne Analysen für R-Entwickler](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Beispiele für Machine Learning, die auf realen Szenarien basieren, finden Sie unter [Machine learning-Tutorials](../tutorials/machine-learning-services-tutorials.md).