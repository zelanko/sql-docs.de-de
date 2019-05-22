---
title: 'Installieren Sie SQL Server Machine Learning Services (Datenbankintern) unter Windows: SQLServer Machine Learning'
description: R in SQL Server oder Python auf SQL Server-Installationsschritte für SQL Server 2017 Machine Learning Services auf Windows.
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/22/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 6cb30c306c5cd2b426976aba4a873475639e4ba5
ms.sourcegitcommit: be09f0f3708f2e8eb9f6f44e632162709b4daff6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "65994217"
---
# <a name="install-sql-server-machine-learning-services-on-windows"></a>Installieren von SQL Server Machine Learning-Dienste auf Windows

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Ab SQL Server 2017, R und Python Unterstützung für in-Database-Analyse in bereitgestellt **SQL Server Machine Learning Services**, der Nachfolger von [SQL Server R Services](../r/sql-server-r-services.md) in SQL Server 2016 eingeführt wurde. Funktionsbibliotheken in R und Python verfügbar sind und als externes Skript auf eine Instanz der Datenbank-Engine ausgeführt. 

In diesem Artikel wird erläutert, wie zum Installieren der Machine Learning-Komponente mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup-Assistenten zu finden und den aufforderungen auf dem Bildschirm.

## <a name="bkmk_prereqs"> </a> Checkliste für die vor der Installation

+ SQL Server 2017 (oder höher)-Setup ist erforderlich, wenn Sie Machine Learning-Dienste mit R oder Python-sprachunterstützung installieren möchten. Wenn Sie SQL Server 2016-Installationsmedium installiert haben, können Sie installieren [SQL Server 2016 R Services (Datenbankintern)](sql-r-services-windows-install.md) zum Abrufen von R-sprachunterstützung.

+ Eine Instanz der Datenbank-Engine ist erforderlich. Sie können nicht nur R oder Python-Funktionen, nicht installieren, obwohl Sie inkrementell zu einer vorhandenen Instanz hinzufügen können.

+ Für die Geschäftskontinuität [Always On Availability Groups](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server) für Machine Learning Services unterstützt werden. Sie müssen Machine Learning Services installieren und Konfigurieren von Paketen, auf den einzelnen Knoten.

+ Installieren von Machine Learning Services ist *nicht unterstützt* auf einem Failovercluster in SQL Server 2017. Allerdings es *wird unterstützt* mit SQL Server-2019. 
 
+ Machine Learning-Dienste nicht auf einem Domänencontroller installiert werden. Der Machine Learning-Dienste Teil der Installation schlägt fehl.

+ Installieren Sie nicht **gemeinsam genutzte Funktionen** > **Machine Learning Server (eigenständig)** auf demselben Computer eine in der Datenbank-Instanz ausführen. Ein eigenständigen Server konkurrieren um dieselben Ressourcen, die Leistung der beiden Installationen unterminieren.

+ Seite-an-Seite-Installation mit anderen Versionen von R und Python wird unterstützt jedoch nicht empfohlen. Da SQL Server-Instanz, eine eigene Kopien der Open-Source-R "und" Anaconda-Distributionen verwendet wird unterstützt. Aber es wird nicht empfohlen, da Code, R und Python, auf dem SQL Server-Computer außerhalb von SQL Server verwendet, ausgeführt zu verschiedenen Problemen führen kann:
    
  + Sie verwenden eine andere Bibliothek und andere ausführbare Datei, und unterschiedliche Ergebnisse zu erhalten, als Sie tun, wenn Sie in SQL Server ausgeführt werden.
  + R und Python-Skripts in externen Bibliotheken können nicht von SQL Server, vorangestellte zu Ressourcenkonflikten verwaltet werden.
  
> [!IMPORTANT]
> Nachdem Setup abgeschlossen ist, achten Sie darauf, dass Sie zum Ausführen nach der Konfiguration in diesem Artikel beschriebenen Schritte. Diese Schritte umfassen SQL Server zur Verwendung externer Skripts aktivieren und Hinzufügen von Konten, die für SQL Server zum Ausführen von R und Python-Aufträgen in Ihrem Namen erforderlich sind. Konfigurationsänderungen erfordern in der Regel ein Neustart der Instanz oder einen Neustart des Launchpad-Diensts.

## <a name="get-the-installation-media"></a>Abrufen der Installationsmedien

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

## <a name="run-setup"></a>Ausführen von 'Setup'

Bei lokalen Installationen müssen Sie das Setup als Administrator ausführen. Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von einer Remotefreigabe installieren, müssen Sie ein Domänenkonto verwenden, das Lese- und Ausführungsberechtigungen auf der Remotefreigabe hat.

1. Starten Sie den Setup-Assistenten für SQL Server 2017. 
  
2. Auf der **Installation** Registerkarte **eigenständige neue SQL Server-Installation oder Hinzufügen von Funktionen zu einer vorhandenen Installation**.

   ![Neue eigenständige SQL Server-installation](media/2017setup-installation-page-mlsvcs.PNG)
   
3. Wählen Sie diese Optionen auf der Seite **Funktionsauswahl** aus:
  
    -   **Datenbank-Engine-Dienste**
  
         Um R und Python mit SQL Server verwenden möchten, müssen Sie eine Instanz der Datenbank-Engine installieren. Sie können entweder eine Standardinstanz oder eine benannte Instanz verwenden.
  
    -   **Machine Learning Services (datenbankintern)**
  
         Diese Option installiert die Datenbankdienste, die Unterstützung von R und Python-skriptausführung.

    -   **R**

        Aktivieren Sie diese Option zum Hinzufügen der Microsoft R-Pakete, -Interpreter und Open-Source-R. 

    -   **Python**

        Aktivieren Sie diese Option, die Microsoft-Python-Pakete, ausführbare Datei der Python 3.5 hinzuzufügen, und wählen Sie Bibliotheken, in die Anaconda-Distribution.
        
        ![Optionen für R und Python Feature](media/2017setup-features-page-mls-rpy.png "Setup-Optionen für Python")

        > [!NOTE]
        > 
        > Aktivieren Sie nicht die Option für **Machine Learning Server (eigenständig)**. Die Option zum Installieren von Machine Learning-Server unter **gemeinsam genutzte Funktionen** dient zur Verwendung auf einem separaten Computer.

4. Auf der **Zustimmung zur Installation von R** Seite **Accept**. Die Lizenzbedingungen umfasst Microsoft R Open eine Verteilung der Open-Source-R-Basispakete und Tools, einschließlich der erweiterten R-Paketen und Konnektivitätsanbietern von Microsoft-Entwicklungsteam umfasst.

5. Auf der **Zustimmung zum Installieren von Python** Seite **Accept**. Die Python-Open-Source-Lizenzvertrag behandelt auch Anaconda und verwandte Tools sowie einige neuen Python-Bibliotheken von Microsoft-Entwicklungsteam.
     
     ![Vereinbarung zum Python-Lizenz](media/2017setup-python-license.png "-Lizenzvertrag für Python")
  
    > [!NOTE]
    >  Wenn der Computer, den Sie verwenden nicht über Internetzugriff verfügt, können Sie Setup aus, an diesem Punkt, um die Installationsprogramme getrennt herunterladen anhalten. Weitere Informationen finden Sie unter [Machine Learning-Komponenten ohne Internetzugang installieren](../install/sql-ml-component-install-without-internet-access.md).
  
     Wählen Sie **Accept**, warten Sie, bis die **Weiter** wird aktiv, und wählen Sie dann die Schaltfläche **Weiter**.
  
6. Auf der **Installationsbereit** Seite, stellen Sie sicher, dass die Auswahl eingeschlossen werden, werden, und wählen Sie **installieren**.
  
    + -Datenbank-Engine-Dienste
    + Machine Learning-Dienste (datenbankintern)
    + R oder Python oder beides

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

## <a name="enable-script-execution"></a>Skriptausführung aktivieren

1. Öffnen Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. 

    > [!TIP]
    > Sie können die herunterladen und installieren die entsprechende Version von dieser Seite: [Herunterladen von SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)
    > 
    > Sie können auch [Studio für Azure Data](../../azure-data-studio/what-is.md), administrative Aufgaben und Abfragen für SQL Server unterstützt.
  
2. Verbinden mit der Instanz, in denen Sie Machine Learning-Dienste installiert haben, klicken Sie auf **neue Abfrage** , öffnen ein Abfragefenster, und führen den folgenden Befehl aus:

    ```sql
    sp_configure
    ```

    Der Wert für die Eigenschaft `external scripts enabled` sollte an diesem Punkt **0** betragen. Der Grund ist die Funktion standardmäßig deaktiviert ist. Die Funktion muss explizit von einem Administrator aktiviert werden, bevor Sie R- oder Python-Skripts ausführen können.
    
3.  Um die Skripterstellung Feature "external" zu aktivieren, führen Sie die folgende Anweisung aus:
    
    ```sql
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
    
    Wenn Sie das Feature für die R-Sprache bereits aktiviert haben, führen Sie kein zweites Mal für Python konfigurieren. Die zugrunde liegende Erweiterbarkeitsplattform unterstützt beide Sprachen.

## <a name="restart-the-service"></a>Starten Sie den Dienst neu.

Wenn die Installation abgeschlossen ist, die Datenbank-Engine neu starten, vor dem Fortfahren mit der nächsten Ausführung des Skripts zu aktivieren.

Neustarten des Diensts auch automatisch neu gestartet wird das zugehörige [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] Service.

Können Sie den Dienst, mit der rechten Maustaste neu starten **neu starten** Befehl für die Instanz in SSMS oder mithilfe der **Services** Bereich in der Systemsteuerung oder mithilfe von [SQL Server-Konfigurations-Manager ](../../relational-databases/sql-server-configuration-manager.md).

## <a name="verify-installation"></a>Überprüfen der Installation

Überprüfen Sie den Installationsstatus für die Instanz im [benutzerdefinierte Berichte](../r/monitor-r-services-using-custom-reports-in-management-studio.md) oder Setupprotokolle.

Verwenden Sie die folgenden Schritte aus, um sicherzustellen, dass alle Komponenten, die zum Starten von externen Skripts ausgeführt werden.

1. Öffnen Sie in SQL Server Management Studio ein neues Abfragefenster, und führen Sie den folgenden Befehl aus:
    
    ```sql
    EXEC sp_configure  'external scripts enabled'
    ```

    Der Wert **Run_value** sollte jetzt auf 1 festgelegt werden.
    
2. Öffnen der **Services** Panel oder SQL Server-Konfigurations-Manager, und vergewissern Sie sich **SQL Server Launchpad-Dienst** ausgeführt wird. Sie sollten einen Dienst für jede Datenbank-Engine-Instanz, die R oder Python installiert sein. Weitere Informationen zum Dienst finden Sie unter [Erweiterungsframework](../concepts/extensibility-framework.md). 
   
3. Wenn Launchpad ausgeführt wird, sollten Sie in der Lage, führen Sie einfache R und Python-Skripts, um sicherzustellen, dass externe Laufzeiten, die Skripts mit SQL Server kommunizieren können.

   Öffnen Sie ein neues **Abfrage** -Fensters im [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], und klicken Sie dann ein Skript wie dem folgenden ausführen:
    
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

    + Für Python
    
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

    Das Skript kann etwas dauern, während der erstmaligen Ausführung der externen Skript-Laufzeit geladen wird. Die Ergebnisse sollten in etwa wie folgt aussehen:

    | Hello |
    |----|
    | 1|


<!--  The preceding 'hello' table is NOT rendering properly on live Docs.
Instead, the RAW markdown for the table is being displayed.  Probable bug in this markdown source,
due to stricter rules imposed by 'markdig' engine (replaced 'DFM').
I will inform HeidiSteen  [GeneMi, 2019/01/17]
-->


> [!NOTE]
> Spalten oder Überschriften, die im Python-Skript verwendet werden, von nicht Entwurf zurückgegeben. Wenn Spaltennamen für die Ausgabe hinzufügen möchten, müssen Sie das Schema für die zurückgegebenen Daten Menge angeben. Dies erfolgt mithilfe des WITH RESULTS-Parameters der gespeicherten Prozedur, die Spalten benennen und Angeben des SQL-Datentyps.
> 
> Beispielsweise können Sie die folgende Zeile zum Generieren von eines beliebigen Spaltennamen hinzufügen: `WITH RESULT SETS ((Col1 AS int))`

<a name="apply-cu"></a>

## <a name="apply-updates"></a>Anwenden von updates

Es wird empfohlen, dass Sie das neueste kumulative Update für die Datenbank-Engine und Machine learning-Komponenten anwenden.

Auf dem Internet verbundene Geräte kumulative Updates werden in der Regel über Windows Update angewendet, aber Sie können auch die unten beschriebenen Schritte verwenden, für kontrollierte Updates. Wenn Sie das Update für die Datenbank-Engine anwenden, zieht Setup kumulativen Updates für alle R oder Python-Funktionen, die auf derselben Instanz installiert. 

Auf getrennten Servern sind zusätzliche Schritte erforderlich. Weitere Informationen finden Sie unter [auf Computern ohne Internetzugang installieren > Anwenden von kumulativen Updates](sql-ml-component-install-without-internet-access.md#apply-cu).

1. Beginnen Sie mit einer Baseline-Instanz, die bereits installiert: Erste Version von SQL Server 2017

2. Wechseln Sie zur Liste Kumulatives Update: [SQL Server 2017-updates](https://sqlserverupdates.com/sql-server-2017-updates/)

3. Wählen Sie das neueste kumulative Update an. Eine ausführbare Datei wird automatisch heruntergeladen und extrahiert.

4. Führen Sie das Setup aus. Akzeptieren Sie die Lizenzbedingungen, und überprüfen Sie auf der Seite Funktionsauswahl, die Sie die Funktionen, die für die kumulativen Updates angewendet werden. Jede Funktion, die für die aktuelle Instanz, einschließlich Machine Learning-Features installiert sind, sollte angezeigt werden. Die CAB-Dateien, die zum Aktualisieren aller Features von Setup heruntergeladen.

  ![Zusammenfassung der installierten features](media/cumulative-update-feature-selection.png)

5. Weiterhin über den Assistenten, akzeptieren die Lizenzbedingungen für die Verteilung von R und Python. 

## <a name="additional-configuration"></a>Zusätzliche Konfiguration

Wenn im externen Skript-Überprüfungsschritt erfolgreich war, können Sie R- oder Python-Befehle ausführen, von SQL Server Management Studio, Visual Studio Code oder einem anderen Client, der T-SQL-Anweisungen an den Server senden kann.

Wenn Sie einen Fehler beim Ausführen des Befehls erhalten haben, überprüfen Sie die zusätzlichen Konfigurationsschritte in diesem Abschnitt. Möglicherweise müssen Sie zusätzliche geeignete Konfigurationen an den Dienst oder die Datenbank.

Auf Instanzebene kann zusätzliche Konfigurationsschritte Folgendes umfassen:

* [Konfiguration der Firewall für SQL Server Machine Learning Services](../../advanced-analytics/security/firewall-configuration.md)
* [Zusätzliche Netzwerkprotokolle aktivieren](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)
* [Aktivieren von Remoteverbindungen](../../database-engine/configure-windows/configure-the-remote-access-server-configuration-option.md)
* [Erstellen eines Anmeldenamens für SQLRUserGroup](../../advanced-analytics/security/create-a-login-for-sqlrusergroup.md)
* [Verwalten von Datenträgerkontingenten](https://docs.microsoft.com/windows/desktop/fileio/managing-disk-quotas) Vermeiden von externen Skripts, Ausführen von Aufgaben, die Speicherplatz auf dem Datenträger erschöpft

<a name="bkmk_configureAccounts"></a> 
<a name="permissions-external-script"></a> 

In der Datenbank benötigen Sie möglicherweise die folgenden konfigurationsupdates:

* [Vergabe von Benutzerberechtigungen für SQL Server Machine Learning Services](../../advanced-analytics/security/user-permission.md)

> [!NOTE]
> Ob zusätzliche Konfiguration erforderlich ist, hängt von Ihrer Sicherheitsschema, auf dem SQL Server, und wie Sie erwarten, dass Benutzer eine Verbindung mit der Datenbank herstellen und Ausführen externer Skripts installiert ab.

## <a name="suggested-optimizations"></a>Vorgeschlagenen Optimierungen

Nun, da Sie alles funktioniert haben, Sie können auch den Server zur Unterstützung von Machine Learning optimieren möchten, oder installieren pretrained Modelle.

### <a name="add-more-worker-accounts"></a>Fügen Sie weitere Konten hinzu.

Wenn Sie erwarten, viele Benutzer gleichzeitig Skripts ausgeführt werden dass, können Sie die Anzahl der workerkonten erhöhen, die den Launchpad-Dienst zugewiesen sind. Weitere Informationen finden Sie unter [Ändern des benutzerkontenpools für SQL Server Machine Learning Services](../administration/modify-user-account-pool.md).

### <a name="optimize-the-server-for-script-execution"></a>Optimieren des Servers für die skriptausführung

Die Standardeinstellungen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup dienen, den Saldo des Servers für eine Vielzahl von Diensten zu optimieren, die von der Datenbank-Engine unterstützt werden, einschließlich extrahieren, Transformieren und laden (ETL)-Prozesse, reporting, Überwachung, und Anwendungen, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Daten. Aus diesem Grund können die Standardeinstellungen finden Sie unter, dass Ressourcen für Machine Learning eingeschränkt oder, insbesondere für speicherintensive Vorgänge gedrosselt.

Um sicherzustellen, dass Machine Learning-Aufträge priorisiert und Ressourcen entsprechend zugewiesen sind, empfehlen wir, dass Sie SQL Server-Ressourcenkontrolle verwenden, um einen externen Ressourcenpool zu konfigurieren. Sie sollten auch die Menge an Arbeitsspeicher zu ändern, die zugeordnet wird, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank-Engine, oder erhöhen Sie die Anzahl der Konten, die unter ausgeführt werden soll. die [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] Service.

- Um einen Ressourcenpool für die Verwaltung von externen Ressourcen konfigurieren zu können, finden Sie unter [erstellen Sie einen externen Ressourcenpool](../../t-sql/statements/create-external-resource-pool-transact-sql.md).
  
- Um den reservierten Umfang an Arbeitsspeicher für die Datenbank zu ändern, finden Sie unter [Serverkonfigurationsoptionen für den Arbeitsspeicher](../../database-engine/configure-windows/server-memory-server-configuration-options.md).
  
- So ändern Sie die Anzahl der R-Konten, die durch gestartet werden kann [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], finden Sie unter [Ändern des benutzerkontenpools für Machine Learning](../administration/modify-user-account-pool.md).

Wenn Sie Standard Edition verwenden und nicht über Ressourcenkontrolle verfügen, können Sie dynamische Verwaltungssichten (DMVs) und erweiterte Ereignisse, als auch Windows-Ereignis überwachen, um die Server-Ressourcen zu verwalten. Weitere Informationen finden Sie unter [überwachen und Verwalten von R Services](../r/managing-and-monitoring-r-solutions.md) und [überwachen und Verwalten von Services für Python](../python/managing-and-monitoring-python-solutions.md).

### <a name="install-additional-r-packages"></a>Installieren zusätzlicher R-Pakete

Die R-Lösungen, die Sie für SQL Server zu erstellen, können grundlegende R-Funktionen, Funktionen aus der proprietären Pakete, die mit SQL Server installiert, und R-Pakete von Drittanbietern kompatibel mit der Version von Open-Source-R-Installation von SQL Server aufrufen.

Pakete, die Sie von SQL Server verwenden möchten, müssen in der Standardbibliothek installiert sein, die von der Instanz verwendet wird. Wenn Sie eine separate Installation von R auf dem Computer, oder wenn Sie Pakete in benutzerbibliotheken installiert haben, nicht möglich, diese Pakete von T-SQL verwenden.

Der Prozess zum Installieren und Verwalten von R-Pakete ist in SQL Server 2016 und SQL Server 2017 anders. In SQL Server 2016 muss ein Datenbankadministrator R-Pakete installieren, die Benutzer benötigen. In SQL Server 2017 können Sie Benutzergruppen zum Freigeben von Paketen auf einer Ebene pro Datenbank einrichten oder konfigurieren Datenbankrollen, damit Benutzer ihre eigenen Pakete installieren können. Weitere Informationen finden Sie unter [Installieren neuer R-Pakete in SQL Server](../r/install-additional-r-packages-on-sql-server.md).


## <a name="next-steps"></a>Nächste Schritte

R-Entwickler können mit einigen einfachen Beispielen beginnen, und die Grundlagen der Funktionsweise von R mit SQL Server. Der nächste Schritt ist finden Sie in den folgenden Links:

+ [Tutorial: Run R in T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Tutorial: Datenbankinterne Analysen für R-Entwickler](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Python-Entwickler erfahren, wie Python mit SQL Server verwenden, indem Sie die folgenden in diesen Tutorials:

+ [Tutorial: Ausführen von Python in T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Tutorial: Datenbankinterne Analysen für Python-Entwickler](../tutorials/sqldev-in-database-python-for-sql-developers.md)

Beispiele für Machine Learning, die auf realen Szenarien basieren, finden Sie unter [Machine learning-Tutorials](../tutorials/machine-learning-services-tutorials.md).
