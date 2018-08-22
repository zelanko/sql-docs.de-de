---
title: Installieren von SQL Server-Machine Learning-Dienste (Datenbankintern) für Windows | Microsoft-Dokumentation
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 8297d57ad1a29778e23d2ce02198c426825abf02
ms.sourcegitcommit: 9528843359cc43b9c66afac363f542ae343266e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "40437690"
---
# <a name="install-sql-server-machine-learning-services-in-database-on-windows"></a>Installieren von SQL Server-Machine Learning-Dienste (Datenbankintern) für Windows 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Ab SQL Server 2017 dient R und Python-Unterstützung für in-Database-Analyse in SQL Server Machine Learning Services, der Nachfolger von R Services-Funktion, die in SQL Server 2016 eingeführt wurde. Funktionsbibliotheken in R und Python verfügbar sind und als externes Skript auf eine Instanz der Datenbank-Engine ausgeführt. 

In diesem Artikel wird erläutert, wie zum Installieren der Machine Learning-Komponente mit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup-Assistenten zu finden und den aufforderungen auf dem Bildschirm.

## <a name="bkmk_prereqs"> </a> Checkliste für die vor der Installation

+ SQL Server 2017-Setup ist erforderlich, wenn Sie Machine Learning-Dienste mit Unterstützung für R, Python oder beides Sprachen installieren möchten. Wenn Sie SQL Server 2016-Installationsmedium installiert haben, können Sie installieren [SQL Server 2016 R Services (Datenbankintern)](sql-r-services-windows-install.md) zum Abrufen von R-sprachunterstützung.

+ Eine Instanz der Datenbank-Engine ist erforderlich. Sie können nicht nur R oder Python-Funktionen, nicht installieren, obwohl Sie inkrementell zu einer vorhandenen Instanz hinzufügen können.

+ Installieren Sie Machine Learning-Dienste nicht auf einem Failovercluster. Der Sicherheitsmechanismus, der zum Isolieren von R und Python-Prozessen verwendet, ist nicht mit einer Windows Server-Failoverclusterumgebung kompatibel.

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

1. Starten Sie den Setup-Assistenten für SQL Server 2017. Sie können herunterladen 
  
2. Auf der **Installation** Registerkarte **eigenständige neue SQL Server-Installation oder Hinzufügen von Funktionen zu einer vorhandenen Installation**.

   ![Installieren von Machine Learning-Dienste in-database](media/2017setup-installation-page-mlsvcs.PNG)
   
3. Wählen Sie diese Optionen auf der Seite **Funktionsauswahl** aus:
  
    -   
  **Datenbank-Engine-Dienste**
  
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

## <a name="bkmk_enableFeature"></a>Aktivieren der externen skriptausführung

1. Öffnen Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. 

    > [!TIP]
    > Sie können auch herunterladen und installieren Sie die entsprechende Version von dieser Seite: [Download SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
    > 
    > Sie können auch versuchen, sich die Preview-Version von [SQL Operations Studio](https://docs.microsoft.com/sql/sql-operations-studio/what-is), administrative Aufgaben und Abfragen für SQL Server unterstützt.
  
2. Verbinden mit der Instanz, in denen Sie Machine Learning-Dienste installiert haben, klicken Sie auf **neue Abfrage** , öffnen ein Abfragefenster, und führen den folgenden Befehl aus:

   ```SQL
   sp_configure
   ```

    Der Wert für die Eigenschaft `external scripts enabled` sollte an diesem Punkt **0** betragen. Der Grund ist die Funktion standardmäßig deaktiviert ist. Die Funktion muss explizit von einem Administrator aktiviert werden, bevor Sie R- oder Python-Skripts ausführen können.
    
3.  Um die Skripterstellung Feature "external" zu aktivieren, führen Sie die folgende Anweisung aus:
    
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
    
    Wenn Sie das Feature für die R-Sprache bereits aktiviert haben, führen Sie kein zweites Mal für Python konfigurieren. Die zugrunde liegende Erweiterbarkeitsplattform unterstützt beide Sprachen.

## <a name="restart-the-service"></a>Starten Sie den Dienst neu.

Wenn die Installation abgeschlossen ist, die Datenbank-Engine neu starten, vor dem Fortfahren mit der nächsten Ausführung des Skripts zu aktivieren.

Neustarten des Diensts auch automatisch neu gestartet wird das zugehörige [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] Service.

Können Sie den Dienst, mit der rechten Maustaste neu starten **neu starten** Befehl für die Instanz in SSMS oder mithilfe der **Services** Bereich in der Systemsteuerung oder mithilfe von [SQL Server-Konfigurations-Manager ](../../relational-databases/sql-server-configuration-manager.md).

## <a name="verify-installation"></a>Überprüfen der Installation

Verwenden Sie die folgenden Schritte aus, um sicherzustellen, dass alle Komponenten, die zum Starten von externen Skripts ausgeführt werden.

1. Öffnen Sie in SQL Server Management Studio ein neues Abfragefenster, und führen Sie den folgenden Befehl aus:
    
    ```SQL
    EXEC sp_configure  'external scripts enabled'
    ```

    Der Wert **Run_value** sollte jetzt auf 1 festgelegt werden.
    
2. Öffnen der **Services** Panel oder SQL Server-Konfigurations-Manager, und vergewissern Sie sich **SQL Server Launchpad-Dienst** ausgeführt wird. Sie sollten einen Dienst für jede Datenbank-Engine-Instanz, die R oder Python installiert sein. Weitere Informationen finden Sie unter [Komponenten zur Unterstützung der Integration von Python](../python/new-components-in-sql-server-to-support-python-integration.md). 
   
3. Wenn Launchpad ausgeführt wird, sollten Sie in der Lage, führen Sie einfache R und Python-Skripts, um sicherzustellen, dass externe Laufzeiten, die Skripts mit SQL Server kommunizieren können.

   Öffnen Sie ein neues **Abfrage** -Fensters im [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], und klicken Sie dann ein Skript wie dem folgenden ausführen:
    
    + Für R
    
    ```SQL
    EXEC sp_execute_external_script  @language =N'R',
    @script=N'
    OutputDataSet <- InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

    + Für Python
    
    ```SQL
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


> [!NOTE]
> Spalten oder Überschriften, die im Python-Skript verwendet werden, von nicht Entwurf zurückgegeben. Wenn Spaltennamen für die Ausgabe hinzufügen möchten, müssen Sie das Schema für die zurückgegebenen Daten Menge angeben. Dies erfolgt mithilfe des WITH RESULTS-Parameters der gespeicherten Prozedur, die Spalten benennen und Angeben des SQL-Datentyps.
> 
> Beispielsweise können Sie die folgende Zeile zum Generieren von eines beliebigen Spaltennamen hinzufügen: `WITH RESULT SETS ((Col1 AS int))`

## <a name="additional-configuration"></a>Zusätzliche Konfiguration

Wenn im externen Skript-Überprüfungsschritt erfolgreich war, können Sie die Python-Befehle ausführen, von SQL Server Management Studio, Visual Studio Code oder einem anderen Client, der T-SQL-Anweisungen an den Server senden kann.

Wenn Sie einen Fehler beim Ausführen des Befehls erhalten haben, überprüfen Sie die zusätzlichen Konfigurationsschritte in diesem Abschnitt. Möglicherweise müssen Sie zusätzliche geeignete Konfigurationen an den Dienst oder die Datenbank.

Allgemeine Szenarien, für die zusätzliche Änderungen erforderlich:

* [Konfigurieren Sie Windows-Firewall für eingehende Verbindungen](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)
* [Zusätzliche Netzwerkprotokolle aktivieren](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)
* [Aktivieren von Remoteverbindungen](../../database-engine/configure-windows/configure-the-remote-access-server-configuration-option.md)
* [Integrierte Berechtigungen für Remotebenutzer erweitern](#bkmk_configureAccounts)
* [Erteilen der Berechtigung zum Ausführen externer Skripts.](#permissions-external-script)
* [Gewähren des Zugriffs auf einzelne Datenbanken](#permissions-db)

> [!NOTE]
> Nicht alle aufgeführten Änderungen sind erforderlich, und keine kann erforderlich sein. Anforderungen basieren auf Ihre Sicherheitsschema, auf dem SQL Server, und wie Sie erwarten, dass Benutzer eine Verbindung mit der Datenbank herstellen und Ausführen externer Skripts installiert. Weitere Tipps zur Problembehandlung finden Sie hier: [häufig gestellte Fragen zu Upgrade und Installation](../r/upgrade-and-installation-faq-sql-server-r-services.md)

###  <a name="bkmk_configureAccounts"></a> Aktivieren der impliziten Authentifizierung für Launchpad-Kontogruppe

Beim Setup werden eine Anzahl neuer Windows-Benutzerkonten angelegt, um Aufgaben unter dem Sicherheitstoken des [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]-Dienstes ausführen zu können. Wenn ein Benutzer ein Python- oder R-Skript aus einem externen Client sendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ein verfügbares workerkonto aktiviert. Anschließend wird er die Identität des aufrufenden Benutzers zugeordnet, und führt das Skript im Auftrag des Benutzers.

Dies wird als bezeichnet *implizite Authentifizierung*, und ist ein Dienst, der die Datenbank-Engine. Dieser Dienst unterstützt die sichere Ausführung externer Skripts in SQL Server 2016 und SQL Server 2017.

Sie können diese Konten in der Windows-Benutzergruppe **SQLRUserGroup**anzeigen. Standardmäßig werden 20 workerkonten erstellt, ist in der Regel mehr als ausreichend für die Ausführung externen Skripts Aufträge.

> [!IMPORTANT]
> Die Worker-Gruppe heißt **SQLRUserGroup** unabhängig davon, ob Sie R- oder Python installiert. Es gibt eine einzelne Gruppe für jede Instanz ein.

Wenn Sie Skripts aus einem Data Science-Remoteclient ausführen müssen, und Sie die Windows-Authentifizierung verwenden, sind weitere Aspekte zu beachten. Diese Konten müssen die Berechtigung zur Anmeldung erteilt werden die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Instanz in Ihrem Namen.

1. In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]im Objekt-Explorer, erweitern Sie **Sicherheit**. Klicken Sie dann mit der rechten Maustaste **Anmeldungen**, und wählen Sie **NewLogin**.
2. In der **Anmeldung – neu** wählen Sie im Dialogfeld **Suche**.
3. Wählen Sie **Objekttypen**, und wählen Sie **Gruppen**. Deaktivieren Sie alle anderen aus.
4. In **Geben Sie den zu verwendenden Objektnamen**, Typ *SQLRUserGroup*, und wählen Sie **Namen überprüfen**.
5. Der Name der lokalen Gruppe, die zum Launchpad-Dienst der Instanz gehört, sollte in etwa wie folgt aufgelöst werden: *instancename\SQLRUserGroup*. Wählen Sie **OK**.
6. Wird standardmäßig die Gruppe zugewiesen wird die **öffentliche** Rolle, und über die Berechtigung zur Verbindung mit der Datenbank-Engine.
7. Wählen Sie **OK**.

> [!NOTE]
> Bei Verwendung einer **SQL-Anmeldung** zum Ausführen von Skripts in einem SQL Server-computekontext, dieser zusätzliche Schritt ist nicht erforderlich.

### <a name="permissions-external-script"></a> Vergabe von Benutzerberechtigungen zum Ausführen externer Skripts.

Wenn Sie installiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] selbst, und Sie in Ihrer eigenen Instanz R- oder Python-Skripts ausgeführt werden, die Sie Skripts in der Regel als Administrator ausführen. So können Sie implizite Berechtigung für verschiedene Vorgänge und alle Daten in der Datenbank.

Die meisten Benutzer haben jedoch nicht diese erhöhten Berechtigungen. Beispielsweise sind Benutzer in einer Organisation, die SQL-Benutzernamen verwenden, um Zugriff auf die Datenbank in der Regel nicht mit erhöhten Rechten berechtigt. Aus diesem Grund müssen für jeden Benutzer, die R- oder Python verwendet wird, Sie Benutzern von Machine Learning Services gewähren die Berechtigung zum Ausführen externer Skripts, die in jeder Datenbank, in denen die Sprache verwendet wird. So sieht wie:

```SQL
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]
```

> [!NOTE]
> Berechtigungen sind nicht spezifisch für die unterstützten Skriptsprache. Das heißt, sind es nicht separate Berechtigungsstufen für R-Skript im Vergleich zu Python-Skript. Wenn Sie separate Berechtigungen für diese Sprachen beibehalten möchten, installieren Sie R und Python auf separaten Instanzen.

### <a name="permissions-db"></a> Erteilen Sie Berechtigungen, die Ihre Benutzer Lese-, Schreib- oder Data Definition Language (DDL) für Datenbanken

Während ein Benutzer die Skripts ausgeführt wird, muss der Benutzer kann Daten aus anderen Datenbanken lesen. Der Benutzer müssen möglicherweise auch neue Tabellen zum Speichern der Ergebnisse und Schreiben von Daten in Tabellen erstellen.

Für jedes Windows-Benutzerkonto oder die SQL-Anmeldung, die R- oder Python-Skripts ausgeführt wird, stellen Sie sicher, dass sie die entsprechenden Berechtigungen für die betreffende Datenbank verfügt: `db_datareader`, `db_datawriter`, oder `db_ddladmin`.

Beispielsweise die folgenden [!INCLUDE[tsql](../../includes/tsql-md.md)] Anweisung bietet die SQL-Anmeldung *MySQLLogin* die Rechte zum Ausführen von T-SQL-Abfragen in der *ML_Samples* Datenbank. Um diese Anweisung auszuführen, muss die SQL-Anmeldung bereits im Sicherheitskontext des Servers vorhanden sein.

```SQL
USE ML_Samples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

Weitere Informationen zu den Berechtigungen in den einzelnen Rollen finden Sie unter [Datenbankrollen](../../relational-databases/security/authentication-access/database-level-roles.md).


### <a name="create-an-odbc-data-source-for-the-instance-on-your-data-science-client"></a>Erstellen einer ODBC-Datenquelle für die Instanz auf Ihrem Data Science-Client

Sie können ein Machine learning-Lösung auf einem Data Science-Clientcomputer erstellen. Wenn Sie Code mit dem SQL Server-Computer als Compute Context ausführen müssen, haben Sie zwei Optionen: Zugriff auf die Instanz unter Verwendung einer SQL-Anmeldung oder mithilfe einer Windows-Konto.

+ SQL-Anmeldung: Stellen Sie sicher, dass die erforderlichen Berechtigungen für die Datenbank verfügt, in dem Sie Daten lesen werden. Hierzu können Sie fügen *Herstellen einer Verbindung mit* und *wählen* Berechtigungen, oder durch Hinzufügen der Anmeldung bei der `db_datareader` Rolle. Um Objekte zu erstellen, weisen `DDL_admin` Rechte. Wenn Sie Daten in Tabellen speichern müssen, Hinzufügen der `db_datawriter` Rolle.

+ Für die Windows-Authentifizierung: Sie müssen möglicherweise eine ODBC-Datenquelle auf dem Data Science-Client zu erstellen, der den Namen der Instanz und andere Verbindungsinformationen angibt. Weitere Informationen finden Sie unter [ODBC-Datenquellenadministrator](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator).

## <a name="suggested-optimizations"></a>Vorgeschlagenen Optimierungen

Nun, da Sie alles funktioniert haben, Sie können auch den Server zur Unterstützung von Machine Learning optimieren möchten, oder installieren pretrained Modelle.

### <a name="add-more-worker-accounts"></a>Fügen Sie weitere Konten hinzu.

Wenn Sie erwarten, viele Benutzer gleichzeitig Skripts ausgeführt werden dass, können Sie die Anzahl der workerkonten erhöhen, die den Launchpad-Dienst zugewiesen sind. Weitere Informationen finden Sie unter [Ändern des benutzerkontenpools für SQL Server Machine Learning Services](../r/modify-the-user-account-pool-for-sql-server-r-services.md).

### <a name="optimize-the-server-for-script-execution"></a>Optimieren des Servers für die skriptausführung

Die Standardeinstellungen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup dienen, den Saldo des Servers für eine Vielzahl von Diensten zu optimieren, die von der Datenbank-Engine unterstützt werden, einschließlich extrahieren, Transformieren und laden (ETL)-Prozesse, reporting, Überwachung, und Anwendungen, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Daten. Aus diesem Grund können die Standardeinstellungen finden Sie unter, dass Ressourcen für Machine Learning eingeschränkt oder, insbesondere für speicherintensive Vorgänge gedrosselt.

Um sicherzustellen, dass Machine Learning-Aufträge priorisiert und Ressourcen entsprechend zugewiesen sind, empfehlen wir, dass Sie SQL Server-Ressourcenkontrolle verwenden, um einen externen Ressourcenpool zu konfigurieren. Sie sollten auch die Menge an Arbeitsspeicher zu ändern, die zugeordnet wird, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenbank-Engine, oder erhöhen Sie die Anzahl der Konten, die unter ausgeführt werden soll. die [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] Service.

- Um einen Ressourcenpool für die Verwaltung von externen Ressourcen konfigurieren zu können, finden Sie unter [erstellen Sie einen externen Ressourcenpool](../../t-sql/statements/create-external-resource-pool-transact-sql.md).
  
- Um den reservierten Umfang an Arbeitsspeicher für die Datenbank zu ändern, finden Sie unter [Serverkonfigurationsoptionen für den Arbeitsspeicher](../../database-engine/configure-windows/server-memory-server-configuration-options.md).
  
- So ändern Sie die Anzahl der R-Konten, die durch gestartet werden kann [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)], finden Sie unter [Ändern des benutzerkontenpools für Machine Learning](../r/modify-the-user-account-pool-for-sql-server-r-services.md).

Wenn Sie Standard Edition verwenden und nicht über Ressourcenkontrolle verfügen, können Sie dynamische Verwaltungssichten (DMVs) und erweiterte Ereignisse, als auch Windows-Ereignis überwachen, um die Server-Ressourcen zu verwalten. Weitere Informationen finden Sie unter [überwachen und Verwalten von R Services](../r/managing-and-monitoring-r-solutions.md) und [überwachen und Verwalten von Services für Python](../python/managing-and-monitoring-python-solutions.md).

### <a name="install-additional-r-packages"></a>Installieren zusätzlicher R-Pakete

Die R-Lösungen, die Sie für SQL Server zu erstellen, können grundlegende R-Funktionen, Funktionen aus der proprietären Pakete, die mit SQL Server installiert, und R-Pakete von Drittanbietern kompatibel mit der Version von Open-Source-R-Installation von SQL Server aufrufen.

Pakete, die Sie von SQL Server verwenden möchten, müssen in der Standardbibliothek installiert sein, die von der Instanz verwendet wird. Wenn Sie eine separate Installation von R auf dem Computer, oder wenn Sie Pakete in benutzerbibliotheken installiert haben, nicht möglich, diese Pakete von T-SQL verwenden.

Der Prozess zum Installieren und Verwalten von R-Pakete ist in SQL Server 2016 und SQL Server 2017 anders. In SQL Server 2016 muss ein Datenbankadministrator R-Pakete installieren, die Benutzer benötigen. In SQL Server 2017 können Sie Benutzergruppen zum Freigeben von Paketen auf einer Ebene pro Datenbank einrichten oder konfigurieren Datenbankrollen, damit Benutzer ihre eigenen Pakete installieren können. Weitere Informationen finden Sie unter [Installieren neuer R-Pakete in SQL Server](../r/install-additional-r-packages-on-sql-server.md).


## <a name="get-help"></a>Hilfe

Benötigen Sie Hilfe bei der Installation oder Aktualisierung? Finden Sie Antworten auf häufig gestellte Fragen und bekannte Probleme finden Sie im folgenden Artikel:

* [Upgrade und Installation – häufig gestellte Fragen – Machine Learning-Dienste](../r/upgrade-and-installation-faq-sql-server-r-services.md)

Versuchen Sie diese benutzerdefinierten Berichte, um den Installationsstatus der Instanz zu überprüfen und Behandeln häufig auftretender Probleme.

* [Benutzerdefinierte Berichte für SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>Nächste Schritte

R-Entwickler können mit einigen einfachen Beispielen beginnen, und die Grundlagen der Funktionsweise von R mit SQL Server. Der nächste Schritt ist finden Sie in den folgenden Links:

+ [Tutorial: Ausführen von R in T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Tutorial: Datenbankinterne Analysen für R-Entwickler](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Python-Entwickler erfahren, wie Python mit SQL Server verwenden, indem Sie die folgenden in diesen Tutorials:

+ [Tutorial: Ausführen von Python in T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Tutorial: Datenbankinterne Analysen für Python-Entwickler](../tutorials/sqldev-in-database-python-for-sql-developers.md)

Beispiele für Machine Learning, die auf realen Szenarien basieren, finden Sie unter [Machine learning-Tutorials](../tutorials/machine-learning-services-tutorials.md).
