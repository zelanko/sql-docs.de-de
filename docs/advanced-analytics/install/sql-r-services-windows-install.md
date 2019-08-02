---
title: Installieren von SQL Server 2016 R Services (datenbankintern)
description: Hinzufügen von Unterstützung für R-Programmiersprachen zu einer Datenbank-Engine auf SQL Server 2016 R-Diensten unter Windows.
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/03/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: =sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 61dd49191e85d9fd4685904ae01b72d754d43318
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68715811"
---
# <a name="install-sql-server-2016-r-services"></a>Installieren von SQL Server 2016 R-Diensten
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel wird erläutert, wie Sie **SQL Server 2016 R-Dienste**installieren und konfigurieren. Wenn Sie über SQL Server 2016 verfügen, installieren Sie diese Funktion, um die Ausführung von R-Code in SQL Server zu ermöglichen.

In SQL Server 2017 wird die R-Integration in [Machine Learning Services](../r/r-server-standalone.md)angeboten, was das Hinzufügen von python widerspiegelt. Wenn Sie R-Integration benötigen und SQL Server 2017-Installationsmedien haben, finden Sie weitere Informationen unter [Install SQL Server Machine Learning Services](sql-machine-learning-services-windows-install.md) , um das Feature hinzuzufügen. 

<a name="bkmk_prereqs"> </a> 

## <a name="pre-install-checklist"></a>Prüfliste vor der Installation

+ Eine Datenbank-Engine-Instanz ist erforderlich. Sie können nur R installieren, obwohl Sie es inkrementell zu einer vorhandenen-Instanz hinzufügen können.

+ Für die Geschäftskontinuität werden [Always on Verfügbarkeits Gruppen](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server) für R Services unterstützt. Sie müssen auf jedem Knoten R Services installieren und Pakete konfigurieren.

+ Installieren Sie R Services nicht auf einem Failovercluster. Der zum Isolieren von R-Prozessen verwendete Sicherheitsmechanismus ist mit einer Windows Server-Failoverclusterumgebung nicht kompatibel.

+ Installieren Sie R Services nicht auf einem Domänen Controller. Der R Services-Teil des Setups schlägt fehl.

+ Installieren Sie keine frei **gegebenen Funktionen** > **R Server (eigenständig)** auf dem gleichen Computer, auf dem eine Daten Bank Instanz ausgeführt wird. 

  Eine parallele Installation mit anderen Versionen von r und Python ist möglich, da die SQL Server Instanz eigene Kopien der Open-Source-Distributionen r und Anaconda verwendet. Das Ausführen von Code, der R und python auf dem SQL Server Computer außerhalb SQL Server verwendet, kann jedoch zu verschiedenen Problemen führen:
    
  + Sie verwenden eine andere Bibliothek und eine andere ausführbare Datei und erhalten andere Ergebnisse als bei der Ausführung in SQL Server.
  + R-und python-Skripts, die in externen Bibliotheken ausgeführt werden, können nicht SQL Server verwaltet werden, was zu Ressourcenkonflikten führt.
  
Wenn Sie frühere Versionen der Revolution Analytics-Entwicklungsumgebung oder der revoscaler-Pakete verwendet haben, oder wenn Sie vorab Versionen von SQL Server 2016 installiert haben, müssen Sie diese deinstallieren. Das Ausführen älterer und neuerer Versionen von revoscaler und anderen proprietären Paketen wird nicht unterstützt. Hilfe zum Entfernen vorheriger Versionen finden Sie unter Häufig gestellte Fragen zu [Upgrade und Installation für SQL Server Machine Learning Services](../r/upgrade-and-installation-faq-sql-server-r-services.md).

> [!IMPORTANT]
> Stellen Sie nach Abschluss des Setups sicher, dass Sie die in diesem Artikel beschriebenen zusätzlichen Schritte nach der Konfiguration ausführen. Diese Schritte umfassen das Aktivieren von SQL Server für die Verwendung externer Skripts und das Hinzufügen von Konten, die SQL Server zum Ausführen von R-Aufträgen in Ihrem Namen erforderlich sind. Konfigurationsänderungen erfordern im Allgemeinen einen Neustart der Instanz oder einen Neustart des Launchpad-Dienstanbieter.

## <a name="get-the-installation-media"></a>Abrufen der Installationsmedien

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

<a name="bkmk_ga_instalpatch"></a>

 ### <a name="install-patch-requirement"></a>Patch-Anforderung installieren 

Microsoft hat ein Problem bei der speziellen Version von Microsoft VC++ 2013 Runtime-Binärdateien erkannt, die von SQL Server als vorausgesetzte Komponenten installiert werden. Wenn dieses Update an den VC++ Runtime-Binärdateien nicht installiert wird, können bei SQL Server in bestimmten Szenarios Stabilitätsprobleme auftreten. Bevor Sie SQL Server installieren, sollten Sie entsprechend den Anweisungen unter [Versionsanmerkungen zu SQL Server](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch) vorgehen, um festzustellen, ob Ihr Computer einen Patch für die VC-Runtime-Binärdateien benötigt.  

<a name="bkmk2016top"></a>

## <a name="run-setup"></a>Ausführen von 'Setup'

Bei lokalen Installationen müssen Sie das Setup als Administrator ausführen. Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von einer Remotefreigabe installieren, müssen Sie ein Domänenkonto verwenden, das Lese- und Ausführungsberechtigungen auf der Remotefreigabe hat.

1. Starten Sie den Setup-Assistenten für SQL Server 2016.

2. Wählen Sie auf der Registerkarte **Installation** die **Option neu SQL Server eigenständige Installation aus, oder fügen Sie einer vorhandenen Installation Features hinzu**.
    
   ![Installieren von R Services (in-Database)](media/2016-setup-installation-rsvcs.png "Starten der Installation der Datenbank-Engine mit R Services")
   
3. Wählen Sie auf der Seite **Funktionsauswahl** die folgenden Optionen aus:

   - Wählen Sie **Datenbank-Engine Dienste**aus. Die Datenbank-Engine ist in jeder Instanz erforderlich, die Machine Learning verwendet.
   - Wählen Sie **R Services (in-Database) aus**. Installiert die Unterstützung für die datenbankbasierte Verwendung von R.
    
     ![R Services-Funktionsauswahl](media/2016setup-rsvcs-features.png "Wählen Sie diese Features für R Services in-Database aus") .

    > [!IMPORTANT]
    > Installieren Sie R Server und R Services nicht gleichzeitig. Normalerweise installieren Sie R Server (eigenständig), um eine Umgebung zu erstellen, die ein Daten Analyst oder Entwickler verwendet, um eine Verbindung mit SQL Server herzustellen und R-Lösungen bereitzustellen. Daher besteht keine Notwendigkeit beide auf demselben Computer zu installieren.

4.  Klicken Sie auf der Seite **Zustimmung zur Installation von Microsoft R Open** auf **annehmen**.
  
    Dieser Lizenzvertrag ist für das Herunterladen von Microsoft r Open erforderlich, das eine Verteilung der Open Source-r-Basispakete und-Tools sowie erweiterte r-Pakete und konnektivitätsanbieter aus dem Microsoft R-Entwicklungsteam umfasst.
  
5. Nachdem Sie den Lizenzvertrag akzeptiert haben, wird eine kurze Pause angezeigt, während das Installationsprogramm vorbereitet wird. Klicken Sie auf **weiter** , wenn die Schaltfläche verfügbar wird.

6. Überprüfen Sie auf der Seite **Installations bereit** , ob die folgenden Elemente enthalten sind, und wählen Sie dann **Installieren**aus.

   + -Datenbank-Engine-Dienste
   + R Services (In-Database)

    Notieren Sie sich den Speicherort des Ordners unter `..\Setup Bootstrap\Log` dem Pfad, in dem die Konfigurationsdateien gespeichert werden. Wenn das Setup fertiggestellt ist, können Sie die installierten Komponenten in der Zusammenfassungs Datei überprüfen.

7. Wenn Sie nach Abschluss des Setups aufgefordert werden, den Computer neu zu starten, führen Sie den Vorgang jetzt durch. Wenn Sie den Setupvorgang abgeschlossen haben, sollten Sie unbedingt die vom Installations-Assistenten angezeigte Meldung lesen. Weitere Informationen finden Sie unter [View and Read SQL Server Setup Log Files](https://docs.microsoft.com/sql/database-engine/install-windows/view-and-read-sql-server-setup-log-files).

## <a name="set-environment-variables"></a>Umgebungsvariablen festlegen

Für die Integration von R-Funktionen sollten Sie die **MKL_CBWR** -Umgebungsvariable festlegen, um [eine konsistente Ausgabe](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr) von MKL-Berechnungen (Intel Math Kernel Library) sicherzustellen.

1. Klicken Sie in der Systemsteuerung auf **System-und Sicherheits** > **System** > **Erweiterte Systemeinstellungen** > **Umgebungsvariablen**.

2. Erstellen Sie eine neue Benutzer-oder System Variable. 

  + Variablenname festlegen auf`MKL_CBWR`
  + Legen Sie den Variablen Wert auf fest.`AUTO`

Für diesen Schritt ist ein Neustart des Servers erforderlich. Wenn Sie im Begriff sind, die Skriptausführung zu aktivieren, können Sie den Neustart anhalten, bis die gesamte Konfigurations Arbeit abgeschlossen ist.

<a name="bkmk_enableFeature"></a>

##  <a name="enable-script-execution"></a>Skriptausführung aktivieren

1. Öffnen Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. 

    > [!TIP]
    > Sie können die entsprechende Version von dieser Seite herunterladen und installieren: [Herunterladen von SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)
    > 
    > Sie können auch das Vorschau Release von [Azure Data Studio](../../azure-data-studio/what-is.md)ausprobieren, das administrative Aufgaben und Abfragen für SQL Server unterstützt.
  
2. Stellen Sie eine Verbindung mit der Instanz her, auf der Sie Machine Learning Services installiert haben, klicken Sie auf **neue Abfrage** , um ein Abfragefenster zu öffnen

   ```sql
   sp_configure
   ```
    Der Wert für die Eigenschaft `external scripts enabled` sollte an diesem Punkt **0** betragen. Dies liegt daran, dass die Funktion standardmäßig deaktiviert ist. Die Funktion muss explizit von einem Administrator aktiviert werden, bevor Sie R-oder python-Skripts ausführen können.
     
3. Führen Sie die folgende Anweisung aus, um die Funktion für die externe Skripterstellung zu aktivieren:
  
    ```sql
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
## <a name="restart-the-service"></a>Starten Sie den Dienst neu.

Starten Sie nach Abschluss der Installation die Datenbank-Engine neu, bevor Sie mit der nächsten fortfahren, und aktivieren Sie die Skriptausführung.

Wenn Sie den Dienst neu starten, wird der zugehörige [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] Dienst ebenfalls automatisch neu gestartet.

Sie können den Dienst neu starten, indem Sie den Befehl mit der rechten Maustaste auf den Befehl **neu starten** für die Instanz in SSMS oder den Bereich **Dienste** in der Systemsteuerung oder [SQL Server-Konfigurations-Manager](../../relational-databases/sql-server-configuration-manager.md)verwenden.

## <a name="verify-installation"></a>Überprüfen der Installation

Überprüfen Sie den Installationsstatus der Instanz mithilfe von [benutzerdefinierten Berichten](../r/monitor-r-services-using-custom-reports-in-management-studio.md).

Gehen Sie folgendermaßen vor, um zu überprüfen, ob alle zum Starten eines externen Skripts verwendeten Komponenten ausgeführt werden.

1. Öffnen Sie in SQL Server Management Studio ein neues Abfragefenster, und führen Sie den folgenden Befehl aus:
    
    ```sql
    EXEC sp_configure  'external scripts enabled'
    ```

    Der Wert **Run_value** sollte jetzt auf 1 festgelegt werden.

2. Öffnen Sie den Bereich **Dienste** , oder SQL Server-Konfigurations-Manager, und überprüfen Sie, ob **SQL Server-Launchpad Dienst** ausgeführt wird. Sie sollten über einen Dienst für jede Datenbank-Engine-Instanz verfügen, auf der R oder python installiert ist. Weitere Informationen zum-Dienst finden Sie unter [Extensibility Framework](../concepts/extensibility-framework.md).

7. Wenn Launchpad ausgeführt wird, sollten Sie eine einfache R ausführen können, um zu überprüfen, ob externe Skript Laufzeiten mit SQL Server kommunizieren können. 

    Öffnen Sie in ein neues Abfrage [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]Fenster, und führen Sie dann ein Skript wie den folgenden aus:
    
    ```sql
    EXEC sp_execute_external_script  @language =N'R',
    @script=N'
    OutputDataSet <- InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

    Die Ausführung des Skripts kann einige Zeit in Anspruch nehmen, wenn die externe Skript Laufzeit zum ersten Mal geladen wird. Die Ergebnisse sollten in etwa wie folgt aussehen:

    | Hello |
    |----|
    | 1|

<a name="apply-cu"></a>

## <a name="apply-updates"></a>Anwenden von Updates

Es wird empfohlen, dass Sie das neueste kumulative Update sowohl auf die Datenbank-Engine als auch auf die Machine Learning-Komponenten anwenden.

Auf Geräten, die mit dem Internet verbunden sind, werden kumulative Updates in der Regel über Windows Update angewendet, aber Sie können auch die nachfolgenden Schritte für kontrollierte Updates verwenden. Wenn Sie das Update für die Datenbank-Engine anwenden, werden die kumulativen Updates für R-Bibliotheken, die Sie auf der gleichen-Instanz installiert haben, von Setup abgerufen. 

Auf getrennten Servern sind zusätzliche Schritte erforderlich. Weitere Informationen finden Sie unter [Installieren von auf Computern ohne Internet Zugriff > kumulative Updates anwenden](sql-ml-component-install-without-internet-access.md#apply-cu).

1. Beginnen Sie mit einer bereits installierten Baseline-Instanz: SQL Server 2016-erste Release, SQL Server 2016 SP 1 oder SQL Server 2016 SP 2.

2. Wechseln Sie zur Liste der kumulativen Updates: [SQL Server 2016 Updates](https://sqlserverupdates.com/sql-server-2016-updates/)

3. Wählen Sie das neueste kumulative Update aus. Eine ausführbare Datei wird automatisch heruntergeladen und extrahiert.

4. Führen Sie das Setup aus. Akzeptieren Sie die Lizenzbedingungen, und überprüfen Sie auf der Seite Funktionsauswahl die Funktionen, für die kumulative Updates angewendet werden. Es sollte jede installierte Funktion für die aktuelle Instanz, einschließlich R Services, angezeigt werden. Setup lädt die CAB-Dateien herunter, die zum Aktualisieren aller Features erforderlich sind.

5. Fahren Sie mit dem Assistenten fort, und akzeptieren Sie die Lizenzbedingungen für die R-Verteilung. 

<a name="bkmk_FollowUp"></a> 

## <a name="additional-configuration"></a>Zusätzliche Konfiguration

Wenn der Schritt für die externe Skript Überprüfung erfolgreich war, können Sie python-Befehle von SQL Server Management Studio, Visual Studio Code oder einem beliebigen anderen Client ausführen, der T-SQL-Anweisungen an den Server senden kann.

Wenn beim Ausführen des Befehls ein Fehler aufgetreten ist, überprüfen Sie die zusätzlichen Konfigurationsschritte in diesem Abschnitt. Möglicherweise müssen Sie für den Dienst oder die Datenbank zusätzliche geeignete Konfigurationen vornehmen.

Auf Instanzebene kann eine zusätzliche Konfiguration Folgendes umfassen:

* [Firewallkonfiguration für SQL Server Machine Learning Services](../../advanced-analytics/security/firewall-configuration.md)
* [Aktivieren zusätzlicher Netzwerkprotokolle](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)
* [Aktivieren von Remote Verbindungen](../../database-engine/configure-windows/configure-the-remote-access-server-configuration-option.md)
* [Verwalten](https://docs.microsoft.com/windows/desktop/fileio/managing-disk-quotas) von Datenträger Kontingenten, um externe Skripts zu vermeiden, die Aufgaben ausführen

<a name="bkmk_configureAccounts"></a>
<a name="bkmk_AllowLogon"></a>

In der-Datenbank benötigen Sie möglicherweise die folgenden Konfigurations Updates:

* [Erteilen Sie Benutzern die Berechtigung zum SQL Server Machine Learning Services](../../advanced-analytics/security/user-permission.md)
* [Hinzufügen der SQLRUserGroup als Datenbankbenutzer](../../advanced-analytics/security/create-a-login-for-sqlrusergroup.md)

> [!NOTE]
> Nicht alle aufgeführten Änderungen sind erforderlich, und keine ist möglicherweise erforderlich. Die Anforderungen hängen vom Sicherheits Schema ab, in dem Sie SQL Server installiert haben, und wie Sie erwarten, dass Benutzer eine Verbindung mit der Datenbank herstellen und externe Skripts ausführen. Weitere Tipps zur Problembehandlung finden Sie hier: [Häufig gestellte Fragen zu Upgrade und Installation](../r/upgrade-and-installation-faq-sql-server-r-services.md)

## <a name="suggested-optimizations"></a>Empfohlene Optimierungen

Nachdem Sie nun alles funktioniert haben, möchten Sie möglicherweise auch den Server für die Unterstützung von Machine Learning optimieren oder vorab trainierte Modelle installieren.

### <a name="add-more-worker-accounts"></a>Weitere workerkonten hinzufügen

Wenn Sie der Meinung sind, dass Sie R stark verwenden oder wenn Sie davon ausgehen, dass viele Benutzer Skripts gleichzeitig ausführen, können Sie die Anzahl der workerkonten erhöhen, die dem Launchpad-Dienst zugewiesen sind. Weitere Informationen finden Sie unter [Ändern des Benutzerkonten Pools für SQL Server Machine Learning Services](../administration/modify-user-account-pool.md).

<a name="bkmk_optimize"></a>

### <a name="optimize-the-server-for-external-script-execution"></a>Optimieren des Servers für die Ausführung externer Skripts

Die Standardeinstellungen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] das Setup dienen dazu, den Saldo des Servers für eine Vielzahl von Diensten zu optimieren, die von der Datenbank-Engine unterstützt werden. Hierzu zählen u. a. ETL-Prozesse (extrahieren, Transformieren und laden), Berichte, Überwachungen und Anwendungen, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Daten verwenden. Daher können Sie unter den Standardeinstellungen feststellen, dass die Ressourcen für Machine Learning manchmal eingeschränkt oder gedrosselt sind, insbesondere bei speicherintensiven Vorgängen.

Um sicherzustellen, dass Machine Learning-Aufträge priorisiert und ordnungsgemäß bereitgestellt werden, wird empfohlen, dass Sie SQL Server Resource Governor verwenden, um einen externen Ressourcenpool zu konfigurieren. Möglicherweise möchten Sie auch die Menge an Arbeitsspeicher ändern, die der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank-Engine zugeordnet ist, oder die Anzahl der Konten erhöhen, die unter dem [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] Dienst ausgeführt werden.

- Informationen zum Konfigurieren eines Ressourcenpools für die Verwaltung externer Ressourcen finden Sie unter [Erstellen eines externen Ressourcenpools](../../t-sql/statements/create-external-resource-pool-transact-sql.md).
  
- Informationen zum Ändern der für die Datenbank reservierten Arbeitsspeicher Menge finden Sie unter [Konfigurationsoptionen](../../database-engine/configure-windows/server-memory-server-configuration-options.md)für den Server Arbeitsspeicher.
  
- Informationen zum Ändern der Anzahl von R-Konten, die von [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]gestartet werden können, finden Sie unter [Ändern des Benutzerkonten Pools für Machine Learning](../administration/modify-user-account-pool.md).

Wenn Sie die Standard Edition verwenden und keine Resource Governor haben, können Sie dynamische Verwaltungs Sichten (DMVs) und erweiterte Ereignisse sowie die Windows-Ereignisüberwachung verwenden, um die von R verwendeten Server Ressourcen zu verwalten. Weitere Informationen finden Sie unter über [wachen und Verwalten von R Services](../r/managing-and-monitoring-r-solutions.md).

### <a name="install-additional-r-packages"></a>Installieren zusätzlicher R-Pakete

Die r-Lösungen, die Sie für SQL Server erstellen, können grundlegende R-Funktionen, Funktionen aus den proprietären Paketen, die mit SQL Server installiert werden, sowie r-Pakete von Drittanbietern, die mit der von SQL Server installierten Open Source-Version kompatibel sind, abrufen.

Pakete, die Sie von SQL Server verwenden möchten, müssen in der Standardbibliothek installiert sein, die von der Instanz verwendet wird. Wenn Sie über eine separate Installation von R auf dem Computer verfügen oder Pakete in Benutzer Bibliotheken installiert haben, können Sie diese Pakete nicht aus t-SQL verwenden.

Der Prozess zum Installieren und Verwalten von R-Paketen unterscheidet sich in SQL Server 2016 und SQL Server 2017. In SQL Server 2016 muss ein Datenbankadministrator R-Pakete installieren, die von den Benutzern benötigt werden. In SQL Server 2017 können Sie Benutzergruppen für die Freigabe von Paketen auf Datenbankebene einrichten oder Daten bankrollen so konfigurieren, dass Benutzer ihre eigenen Pakete installieren können. Weitere Informationen finden Sie unter [Installieren neuer R-Pakete](../r/install-additional-r-packages-on-sql-server.md).

## <a name="next-steps"></a>Nächste Schritte

R-Entwickler können mit einigen einfachen Beispielen beginnen und die Grundlagen der Funktionsweise von R mit SQL Server kennenlernen. Informationen zu den nächsten Schritten finden Sie unter den folgenden Links:

+ [Tutorial: Ausführen von R in T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Tutorial: Daten bankübergreifende Analysen für R-Entwickler](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Beispiele für Machine Learning, die auf realen Szenarios basieren, finden Sie unter [Machine Learning-Tutorials](../tutorials/machine-learning-services-tutorials.md).