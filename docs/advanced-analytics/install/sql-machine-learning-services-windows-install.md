---
title: Installieren von SQL Server Machine Learning Services (python, R) unter Windows
titleSuffix: ''
description: In diesem Artikel wird erläutert, wie Sie SQL Server Machine Learning Services unter Windows installieren. Sie können Machine Learning Services verwenden, um Python-und R-Skripts in der-Datenbank auszuführen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/20/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 28e4681808348df97e61709745e9b59e0a44d3be
ms.sourcegitcommit: 632ff55084339f054d5934a81c63c77a93ede4ce
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "69634557"
---
# <a name="install-sql-server-machine-learning-services-on-windows"></a>Installieren von SQL Server Machine Learning Services unter Windows

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel wird erläutert, wie Sie SQL Server Machine Learning Services unter Windows installieren. Sie können Machine Learning Services verwenden, um Python-und R-Skripts in der-Datenbank auszuführen.

## <a name="bkmk_prereqs"></a> Prüfliste vor der Installation

+ SQL Server 2017 (oder höher) ist erforderlich, wenn Sie Machine Learning Services mit der R-oder python-Sprachunterstützung installieren möchten. Wenn Sie stattdessen über SQL Server 2016-Installationsmedium verfügen, können Sie [SQL Server R Services (in-Database)](sql-r-services-windows-install.md) installieren, um die R-Sprachunterstützung zu erhalten.

+ Eine Datenbank-Engine-Instanz ist erforderlich. Sie können nicht nur R-oder python-Funktionen installieren, Sie können Sie jedoch inkrementell zu einer vorhandenen-Instanz hinzufügen.

+ Für die Geschäftskontinuität werden [Always on Verfügbarkeits Gruppen](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server) für Machine Learning Services unterstützt. Sie müssen auf jedem Knoten Machine Learning Services installieren und Pakete konfigurieren.

+ Das Installieren von Machine Learning Services wird in einem Failovercluster in SQL Server 2017 *nicht unterstützt* . Dies wird jedoch mit SQL Server 2019 *unterstützt* . 
 
+ Installieren Sie Machine Learning Services nicht auf einem Domänen Controller. Der Machine Learning Services Teil des-Setups schlägt fehl.

+ Installieren Sie keine frei **gegebenen Funktionen** > **Machine Learning Server (eigenständig)** auf dem gleichen Computer, auf dem eine Daten Bank Instanz ausgeführt wird. Ein eigenständiger Server wird mit den gleichen Ressourcen konkurrieren und die Leistung beider Installationen untergraben.

+ Eine parallele Installation mit anderen Versionen von R und python wird unterstützt, wird jedoch nicht empfohlen. Dies wird unterstützt, da SQL Server Instanz eigene Kopien der Open Source-Distributionen R und Anaconda verwendet. Dies wird jedoch nicht empfohlen, da das Ausführen von Code, der R und python auf dem SQL Server Computer außerhalb SQL Server verwendet, zu unterschiedlichen Problemen führen kann:
    
  + Sie verwenden eine andere Bibliothek und eine andere ausführbare Datei und erhalten andere Ergebnisse als bei der Ausführung in SQL Server.
  + R-und python-Skripts, die in externen Bibliotheken ausgeführt werden, können nicht SQL Server verwaltet werden, was zu Ressourcenkonflikten führt.
  
> [!IMPORTANT]
> Stellen Sie nach Abschluss des Setups sicher, dass Sie die Schritte nach der Konfiguration durchführen, die in diesem Artikel beschrieben werden. Zu diesen Schritten gehören das Aktivieren von SQL Server für die Verwendung externer Skripts und das Hinzufügen von Konten, die für SQL Server erforderlich sind, um R-und python-Aufträge für Konfigurationsänderungen erfordern im Allgemeinen einen Neustart der Instanz oder einen Neustart des Launchpad-Dienstanbieter.

## <a name="get-the-installation-media"></a>Abrufen der Installationsmedien

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

## <a name="run-setup"></a>Ausführen von 'Setup'

Bei lokalen Installationen müssen Sie das Setup als Administrator ausführen. Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von einer Remotefreigabe installieren, müssen Sie ein Domänenkonto verwenden, das Lese- und Ausführungsberechtigungen auf der Remotefreigabe hat.

1. Starten Sie den Setup-Assistenten für SQL Server 2017. 
  
2. Wählen Sie auf der Registerkarte **Installation** die **Option neu SQL Server eigenständige Installation aus, oder fügen Sie einer vorhandenen Installation Features hinzu**.

   ![Neue SQL Server eigenständige Installation](media/2017setup-installation-page-mlsvcs.PNG)
   
3. Wählen Sie diese Optionen auf der Seite **Funktionsauswahl** aus:
  
    -   **Datenbank-Engine-Dienste**
  
         Zum Verwenden von R und Python mit SQL Server müssen Sie eine Instanz der Datenbank-Engine installieren. Sie können entweder eine Standard Instanz oder eine benannte Instanz verwenden.
  
    -   **Machine Learning Services (datenbankintern)**
  
         Mit dieser Option werden die Datenbankdienste installiert, die die Skriptausführung von R und python unterstützen

    -   **R**

        Aktivieren Sie diese Option, um die Microsoft r-Pakete, den Interpreter und Open Source-r hinzuzufügen. 

    -   **Python**

        Aktivieren Sie diese Option, um die Microsoft Python-Pakete, die ausführbare Datei von Python 3,5 hinzuzufügen und Bibliotheken aus der Anaconda-Distribution auszuwählen.
        
        ![Funktions Optionen für R und python](media/2017setup-features-page-mls-rpy.png "Setup Optionen für python")

        > [!NOTE]
        > 
        > Wählen Sie nicht die Option für **Machine Learning Server (eigenständig)** aus. Die Option zum Installieren von Machine Learning Server unter "frei **gegebene Features** " ist für die Verwendung auf einem separaten Computer vorgesehen.

4. Wählen Sie auf der Seite **Zustimmung zur Installation von R** die Option **annehmen**aus. Diese Lizenzvereinbarung umfasst Microsoft R Open, das eine Verteilung der Open-Source-r-Basispakete und-Tools sowie erweiterte r-Pakete und konnektivitätsanbieter vom Microsoft-Entwicklungsteam umfasst.

5. Wählen Sie auf der Seite **Zustimmung zur Installation von python** die Option **annehmen**aus. Der Open-Source-Lizenzierungs Vertrag von python umfasst auch Anaconda und verwandte Tools sowie einige neue python-Bibliotheken vom Microsoft-Entwicklungsteam.
     
     ![Vertrag zur python-Lizenz](media/2017setup-python-license.png "Lizenzvertrag für python")
  
    > [!NOTE]
    >  Wenn der von Ihnen verwendete Computer nicht über Internet Zugriff verfügt, können Sie das Setup an dieser Stelle anhalten, um die Installationsprogramme separat herunterzuladen. Weitere Informationen finden Sie unter [Installieren von Machine Learning-Komponenten ohne Internetzugang](../install/sql-ml-component-install-without-internet-access.md).
  
     Wählen Sie **annehmen**aus, warten Sie, bis die Schaltfläche **weiter** aktiviert ist, und klicken Sie dann auf **weiter**.
  
6. Vergewissern Sie sich auf der Seite **Installations bereit** , dass diese Optionen eingeschlossen sind, und wählen Sie **Installieren**aus.
  
    + -Datenbank-Engine-Dienste
    + Machine Learning-Dienste (datenbankintern)
    + R oder python oder beides

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

## <a name="enable-script-execution"></a>Skriptausführung aktivieren

1. Öffnen Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. 

    > [!TIP]
    > Sie können die entsprechende Version von dieser Seite herunterladen und installieren: [Herunterladen von SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)
    > 
    > Sie können auch [Azure Data Studio](../../azure-data-studio/what-is.md)verwenden, das administrative Aufgaben und Abfragen für SQL Server unterstützt.
  
2. Stellen Sie eine Verbindung mit der Instanz her, auf der Sie Machine Learning Services installiert haben, klicken Sie auf **neue Abfrage** , um ein Abfragefenster zu öffnen

    ```sql
    sp_configure
    ```

    Der Wert für die Eigenschaft `external scripts enabled` sollte an diesem Punkt **0** betragen. Dies liegt daran, dass die Funktion standardmäßig deaktiviert ist. Die Funktion muss explizit von einem Administrator aktiviert werden, bevor Sie R-oder python-Skripts ausführen können.
    
3.  Führen Sie die folgende Anweisung aus, um die Funktion für die externe Skripterstellung zu aktivieren:
    
    ```sql
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
    
    Wenn Sie die Funktion für die Sprache R bereits aktiviert haben, führen Sie für python nicht neu konfigurieren aus. Die zugrunde liegende Erweiterbarkeits Plattform unterstützt beide Sprachen.

## <a name="restart-the-service"></a>Starten Sie den Dienst neu.

Starten Sie nach Abschluss der Installation die Datenbank-Engine neu, bevor Sie mit der nächsten fortfahren, und aktivieren Sie die Skriptausführung.

Wenn Sie den Dienst neu starten, wird der zugehörige [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] Dienst ebenfalls automatisch neu gestartet.

Sie können den Dienst neu starten, indem Sie den Befehl mit der rechten Maustaste auf den Befehl **neu starten** für die Instanz in SSMS oder den Bereich **Dienste** in der Systemsteuerung oder [SQL Server-Konfigurations-Manager](../../relational-databases/sql-server-configuration-manager.md)verwenden.

## <a name="verify-installation"></a>Überprüfen der Installation

Überprüfen Sie den Installationsstatus der Instanz in [benutzerdefinierten Berichten](../r/monitor-r-services-using-custom-reports-in-management-studio.md) oder Setup Protokollen.

Gehen Sie folgendermaßen vor, um zu überprüfen, ob alle zum Starten eines externen Skripts verwendeten Komponenten ausgeführt werden.

1. Öffnen Sie in SQL Server Management Studio ein neues Abfragefenster, und führen Sie den folgenden Befehl aus:
    
    ```sql
    EXEC sp_configure  'external scripts enabled'
    ```

    Der Wert **Run_value** sollte jetzt auf 1 festgelegt werden.
    
2. Öffnen Sie den Bereich **Dienste** , oder SQL Server-Konfigurations-Manager, und überprüfen Sie, ob **SQL Server-Launchpad Dienst** ausgeführt wird. Sie sollten über einen Dienst für jede Datenbank-Engine-Instanz verfügen, auf der R oder python installiert ist. Weitere Informationen zum-Dienst finden Sie unter [Extensibility Framework](../concepts/extensibility-framework.md). 
   
3. Wenn Launchpad ausgeführt wird, sollten Sie einfache R-und python-Skripts ausführen können, um zu überprüfen, ob externe Skript Laufzeiten mit SQL Server kommunizieren können.

   Öffnen Sie in ein neues Abfrage [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]Fenster, und führen Sie dann ein Skript wie den folgenden aus:
    
    + Für R
    
    ```sql
    EXEC sp_execute_external_script  @language =N'R',
    @script=N'
    OutputDataSet <- InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

    + Für python
    
    ```sql
    EXEC sp_execute_external_script  @language =N'Python',
    @script=N'
    OutputDataSet = InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

    **Ergebnisse**

    Die Ausführung des Skripts kann einige Zeit in Anspruch nehmen, wenn die externe Skript Laufzeit zum ersten Mal geladen wird. Die Ergebnisse sollten in etwa wie folgt aussehen:

    | Hello |
    |----|
    | 1|

> [!NOTE]
> Spalten oder Überschriften, die im Python-Skript verwendet werden, werden nicht Entwurfs bedingt zurückgegeben. Um Spaltennamen für Ihre Ausgabe hinzuzufügen, müssen Sie das Schema für das Rückgabe DataSet angeben. Verwenden Sie hierzu den with results-Parameter der gespeicherten Prozedur, benennen Sie die Spalten, und geben Sie den SQL-Datentyp an.
> 
> Beispielsweise können Sie die folgende Zeile hinzufügen, um einen beliebigen Spaltennamen zu generieren:`WITH RESULT SETS ((Col1 AS int))`

<a name="apply-cu"></a>

## <a name="apply-updates"></a>Anwenden von Updates

Es wird empfohlen, dass Sie das neueste kumulative Update sowohl auf die Datenbank-Engine als auch auf die Machine Learning-Komponenten anwenden.

Auf Geräten, die mit dem Internet verbunden sind, werden kumulative Updates in der Regel über Windows Update angewendet, aber Sie können auch die nachfolgenden Schritte für kontrollierte Updates verwenden. Wenn Sie das Update für die Datenbank-Engine anwenden, ruft das Setup kumulative Updates für alle R-oder python-Funktionen ab, die Sie auf derselben Instanz installiert haben. 

Auf getrennten Servern sind zusätzliche Schritte erforderlich. Weitere Informationen finden Sie unter [Installieren von auf Computern ohne Internet Zugriff > kumulative Updates anwenden](sql-ml-component-install-without-internet-access.md#apply-cu).

1. Beginnen Sie mit einer bereits installierten Baseline-Instanz: SQL Server 2017-erste Version

2. Wechseln Sie zur Liste der kumulativen Updates: [SQL Server 2017 Updates](https://sqlserverupdates.com/sql-server-2017-updates/)

3. Wählen Sie das neueste kumulative Update aus. Eine ausführbare Datei wird automatisch heruntergeladen und extrahiert.

4. Führen Sie das Setup aus. Akzeptieren Sie die Lizenzbedingungen, und überprüfen Sie auf der Seite Funktionsauswahl die Funktionen, für die kumulative Updates angewendet werden. Es sollte jede installierte Funktion für die aktuelle Instanz angezeigt werden, einschließlich Machine Learning-Features. Setup lädt die CAB-Dateien herunter, die zum Aktualisieren aller Features erforderlich sind.

  ![Zusammenfassung installierter Features](media/cumulative-update-feature-selection.png)

5. Fahren Sie mit dem Assistenten fort, und akzeptieren Sie die Lizenzbedingungen für R-und python-Distributionen. 

## <a name="additional-configuration"></a>Zusätzliche Konfiguration

Wenn der Schritt für die externe Skript Überprüfung erfolgreich war, können Sie R-oder python-Befehle von SQL Server Management Studio, Visual Studio Code oder einem beliebigen anderen Client ausführen, der T-SQL-Anweisungen an den Server senden kann.

Wenn beim Ausführen des Befehls ein Fehler aufgetreten ist, überprüfen Sie die zusätzlichen Konfigurationsschritte in diesem Abschnitt. Möglicherweise müssen Sie für den Dienst oder die Datenbank zusätzliche geeignete Konfigurationen vornehmen.

Auf Instanzebene kann eine zusätzliche Konfiguration Folgendes umfassen:

* [Firewallkonfiguration für SQL Server Machine Learning Services](../../advanced-analytics/security/firewall-configuration.md)
* [Aktivieren zusätzlicher Netzwerkprotokolle](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)
* [Aktivieren von Remote Verbindungen](../../database-engine/configure-windows/configure-the-remote-access-server-configuration-option.md)
* [Erstellen eines Anmelde namens für "sqlrusergroup"](../../advanced-analytics/security/create-a-login-for-sqlrusergroup.md)
* [Verwalten](https://docs.microsoft.com/windows/desktop/fileio/managing-disk-quotas) von Datenträger Kontingenten, um externe Skripts zu vermeiden, die Aufgaben ausführen

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"
In SQL Server 2019 unter Windows hat sich der Isolations Mechanismus geändert. Dies wirkt sich auf **sqlrusergroup**, Firewallregeln, die Datei Berechtigung und die implizite Authentifizierung aus. Weitere Informationen finden Sie unter [Isolations Änderungen für Machine Learning Services](sql-server-machine-learning-services-2019.md).
::: moniker-end

<a name="bkmk_configureAccounts"></a> 
<a name="permissions-external-script"></a> 

In der-Datenbank benötigen Sie möglicherweise die folgenden Konfigurations Updates:

* [Erteilen Sie Benutzern die Berechtigung zum SQL Server Machine Learning Services](../../advanced-analytics/security/user-permission.md)

> [!NOTE]
> Ob eine zusätzliche Konfiguration erforderlich ist, hängt vom Sicherheits Schema ab, in dem Sie SQL Server installiert haben, und wie Sie davon ausgehen, dass Benutzer eine Verbindung mit der Datenbank herstellen und externe Skripts ausführen.

## <a name="suggested-optimizations"></a>Empfohlene Optimierungen

Nachdem Sie nun alles funktioniert haben, möchten Sie möglicherweise auch den Server für die Unterstützung von Machine Learning optimieren oder vorab trainierte Modelle installieren.

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
### <a name="add-more-worker-accounts"></a>Weitere workerkonten hinzufügen

Wenn Sie erwarten, dass viele Benutzer Skripts gleichzeitig ausführen, können Sie die Anzahl der workerkonten erhöhen, die dem Launchpad-Dienst zugewiesen sind. Weitere Informationen finden Sie unter [Ändern des Benutzerkonten Pools für SQL Server Machine Learning Services](../administration/modify-user-account-pool.md).
::: moniker-end

### <a name="optimize-the-server-for-script-execution"></a>Optimieren des Servers für die Skriptausführung

Die Standardeinstellungen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] das Setup dienen dazu, den Saldo des Servers für eine Vielzahl von Diensten zu optimieren, die von der Datenbank-Engine unterstützt werden. Hierzu zählen u. a. ETL-Prozesse (extrahieren, Transformieren und laden), Berichte, Überwachungen und Anwendungen, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Daten verwenden. Daher können Sie unter den Standardeinstellungen feststellen, dass die Ressourcen für Machine Learning manchmal eingeschränkt oder gedrosselt sind, insbesondere bei speicherintensiven Vorgängen.

Um sicherzustellen, dass Machine Learning-Aufträge priorisiert und ordnungsgemäß bereitgestellt werden, wird empfohlen, dass Sie SQL Server Resource Governor verwenden, um einen externen Ressourcenpool zu konfigurieren. Möglicherweise möchten Sie auch die Menge an Arbeitsspeicher ändern, die der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank-Engine zugeordnet ist, oder die Anzahl der Konten erhöhen, die unter dem [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] Dienst ausgeführt werden.

- Informationen zum Konfigurieren eines Ressourcenpools für die Verwaltung externer Ressourcen finden Sie unter [Erstellen eines externen Ressourcenpools](../../t-sql/statements/create-external-resource-pool-transact-sql.md).
  
- Informationen zum Ändern der für die Datenbank reservierten Arbeitsspeicher Menge finden Sie unter [Konfigurationsoptionen](../../database-engine/configure-windows/server-memory-server-configuration-options.md)für den Server Arbeitsspeicher.
  
- Informationen zum Ändern der Anzahl von R-Konten, die von [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]gestartet werden können, finden Sie unter [Ändern des Benutzerkonten Pools für Machine Learning](../administration/modify-user-account-pool.md).

Wenn Sie die Standard Edition verwenden und keine Resource Governor haben, können Sie die Server Ressourcen mithilfe dynamischer Verwaltungs Sichten (DMVs) und erweiterter Ereignisse sowie der Windows-Ereignisüberwachung verwalten. Weitere Informationen finden Sie unter über [wachen und Verwalten von R Services](../r/managing-and-monitoring-r-solutions.md) und über [wachen und Verwalten von python-Diensten](../python/managing-and-monitoring-python-solutions.md).

### <a name="install-additional-r-packages"></a>Installieren zusätzlicher R-Pakete

Die r-Lösungen, die Sie für SQL Server erstellen, können grundlegende R-Funktionen, Funktionen aus den proprietären Paketen, die mit SQL Server installiert werden, sowie r-Pakete von Drittanbietern, die mit der von SQL Server installierten Open Source-Version kompatibel sind, abrufen.

Pakete, die Sie von SQL Server verwenden möchten, müssen in der Standardbibliothek installiert sein, die von der Instanz verwendet wird. Wenn Sie über eine separate Installation von R auf dem Computer verfügen oder Pakete in Benutzer Bibliotheken installiert haben, können Sie diese Pakete nicht aus t-SQL verwenden.

Zum Installieren und Verwalten von R-Paketen können Sie Benutzergruppen für die Freigabe von Paketen auf Datenbankebene einrichten oder Daten bankrollen so konfigurieren, dass Benutzer ihre eigenen Pakete installieren können. Weitere Informationen finden Sie unter [Installieren neuer R-Pakete in SQL Server](../r/install-additional-r-packages-on-sql-server.md).

## <a name="next-steps"></a>Nächste Schritte

R-Entwickler können mit einigen einfachen Beispielen loslegen und die Grundlagen der Funktionen von R unter SQL Server kennenlernen. Informationen zu den nächsten Schritten finden Sie unter den folgenden Links:

+ [Tutorial: Ausführen von R in T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Tutorial: Datenbankinterne Analysen für R-Entwickler](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Python-Entwickler können in den folgenden Tutorials erfahren, wie Python mit SQL Server verwendet werden kann:

+ [Tutorial: Ausführen von Python in T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Tutorial: Datenbankinterne Analysen für Python-Entwickler](../tutorials/sqldev-in-database-python-for-sql-developers.md)

Praxisbeispiele für die Verwendung von Machine Learning finden Sie unter [Tutorials für Machine Learning](../tutorials/machine-learning-services-tutorials.md).
