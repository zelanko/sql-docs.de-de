---
title: Installieren von SQL Server-Spracherweiterungen unter Windows
titleSuffix: SQL Server Language Extensions
description: Schritte für das Installieren von Spracherweiterungen für SQL Server 2019 unter Windows.
author: dphansen
ms.author: davidph
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: bc9baf6f5360c82ec27a3c243b840b2d38ed1d56
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73589064"
---
# <a name="install-sql-server-language-extensions-on-windows"></a>Installieren von SQL Server-Spracherweiterungen unter Windows

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Ab SQL Server 2019 werden Spracherweiterungen und Java-Unterstützung bereitgestellt. In diesem Artikel wird erläutert, wie Sie die Komponente „Spracherweiterungen“ durch Ausführen des Setup-Assistenten für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installieren.

> [!NOTE]
> Dieser Artikel behandelt die Installation von SQL Server-Spracherweiterungen unter Windows. Informationen für Linux finden Sie unter [Installieren von SQL Server 2019-Spracherweiterungen (Java) unter Linux](https://docs.microsoft.com/sql//linux/sql-server-linux-setup-language-extensions).

<a name="prerequisites"></a> 

## <a name="pre-install-checklist"></a>Prüfliste vor der Installation

+ Um die Unterstützung für Spracherweiterungen zu installieren, benötigen Sie SQL Server 2019-Setup.

+ Es ist eine Datenbank-Engine-Instanz erforderlich. Sie können nicht ausschließlich die Funktionen der Spracherweiterungen installieren, können diese aber einer vorhandenen Instanz inkrementell hinzufügen.

+ Für die Aufrechterhaltung der Geschäftskontinuität werden [Always On-Verfügbarkeitsgruppen](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server) für Spracherweiterungen unterstützt. Sie müssen auf jedem Knoten Spracherweiterungen installieren und Pakete konfigurieren.

+ Die Installation von Spracherweiterungen in einem Failovercluster wird in SQL Server 2019 unterstützt.

+ Installieren Sie SQL Server-Spracherweiterungen nicht auf einem Domänencontroller. Ansonsten schlägt derjenige Teil des Setups, der die Spracherweiterungen betrifft, fehl.

+ Spracherweiterungen und [Machine Learning Services](../../advanced-analytics/index.yml) werden standardmäßig auf Big Data-Clustern für SQL Server installiert. Wenn Sie Big Data-Cluster verwenden, müssen Sie die Schritte in diesem Artikel nicht ausführen. Weitere Informationen finden Sie unter [Verwenden von Machine Learning Services (Python und R) in Big Data-Clustern](../../big-data-cluster/machine-learning-services.md).

> [!IMPORTANT]
> Stellen Sie nach Abschluss des Setups sicher, dass Sie die in diesem Artikel beschriebenen Schritte nach der Konfiguration durchführen. Zu diesen Schritten gehören das Aktivieren von SQL Server für die Verwendung von externem Code und das Hinzufügen von Konten, die SQL Server für das Ausführen Ihres Java-Codes benötigt. Konfigurationsänderungen erfordern in der Regel einen Neustart der Instanz oder einen Neustart des Launchpad-Diensts.

<a name="java-jre-jdk"></a>

## <a name="java-jre-or-jdk"></a>Java JRE oder JDK

In SQL Server 2019 Release Candidate 1 gibt es zwei Möglichkeiten, Java mit SQL Server zu installieren und zu verwenden:

1. Verwenden Sie die Java-Standardruntime, Zulu Open JRE Version 11.0.3. Diese Runtime wird unterstützt und ist in der SQL Server-Installation enthalten.

1. Verwenden Sie Ihre bevorzugte Java-Verteilung anstelle der Java-Standardruntime.

    Java 11 ist die derzeit unterstützte Version unter Windows. Die Java Runtime Environment (JRE) ist die Mindestanforderung, aber das Java Development Kit (JDK) ist nützlich, wenn Sie den Java-Compiler und die Entwicklungspakete benötigen. Da das JDK alles beinhaltet, ist die JRE bei der Installation des JDK nicht erforderlich. Unter Windows empfiehlt es sich, das JDK nach Möglichkeit unter dem Standardordner `/Program Files/` zu installieren. Andernfalls ist eine zusätzliche Konfiguration erforderlich, um ausführbare Dateien Berechtigungen zu erteilen. Weitere Informationen finden Sie im Abschnitt über das [Erteilen von Berechtigungen (Windows)](#perms-nonwindows) in diesem Dokument.

    > [!NOTE]
    > Da Java abwärtskompatibel ist, funktionieren frühere Versionen möglicherweise, die unterstützte und getestete Version für Release Candidate 1 ist jedoch Java 11.
    
## <a name="get-the-installation-media"></a>Abrufen der Installationsmedien

Die Vorschauversion von SQL Server 2019 steht auf der [Installationssite für SQL Server 2019 ](https://www.microsoft.com/sql-server/sql-server-2019#Install) zur Verfügung.

<!-- We can use this include statement, once SQL Server 2019 is in GA
[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]
-->
## <a name="run-setup"></a>Ausführen von 'Setup'

Bei lokalen Installationen müssen Sie das Setup als Administrator ausführen. Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von einer Remotefreigabe installieren, müssen Sie ein Domänenkonto verwenden, das Lese- und Ausführungsberechtigungen auf der Remotefreigabe hat.

1. Starten Sie den Setup-Assistenten für SQL Server 2019. 
  
2. Klicken Sie auf der Registerkarte **Installation** auf **Neue eigenständige SQL Server-Installation oder Hinzufügen von Funktionen zu einer vorhandenen Installation**.

    ![SQL Server 2019-Installation](../media/sql-install.png) 

3. Wählen Sie diese Optionen auf der Seite **Funktionsauswahl** aus:
  
    - **Datenbank-Engine-Dienste**
  
        Sie müssen eine Instanz der Datenbank-Engine installieren, um Spracherweiterungen mit SQL Server verwenden zu können. Sie können entweder eine Standardinstanz oder eine benannte Instanz verwenden.
  
    - **Machine Learning-Dienste und -Spracherweiterungen**
  
        Mit dieser Option wird die Spracherweiterungskomponente installiert, die die Java-Codeausführung unterstützt.

        - Wenn Sie die Java-Standardruntime, Zulu Open JRE 11.0.3, installieren möchten, wählen Sie **Machine Learning-Dienste und -Spracherweiterungen** sowie **Java** aus.

        - Wenn Sie Ihre eigene Java-Runtime verwenden möchten, wählen Sie **Machine Learning-Dienste und -Spracherweiterungen** aus. Wählen Sie nicht „Java“ aus.

        Wenn Sie R und Python verwenden möchten, finden Sie Informationen unter [Installieren von SQL Server Machine Learning Services unter Windows](https://docs.microsoft.com/sql/advanced-analytics/install/sql-machine-learning-services-windows-install).

    ![Featureoptionen für Spracherweiterungen](../media/sql-install-feature-selection.png)

4. Wenn Sie im vorherigen Schritt **Java** ausgewählt haben, um die Java-Standardruntime zu installieren, wird die Seite **Java-Installationsspeicherort** angezeigt.

    Wählen Sie **In dieser Installation enthaltene Open JRE-Version 11.0.3 installieren** aus.

    ![Auswählen des Java-Installationsspeicherorts](../media/sql-install-openjdk.png)

    > [!NOTE]
    > Die Option **Speicherort einer anderen Version angeben, die auf diesem Computer installiert ist** wird für Spracherweiterungen nicht verwendet.

5. Stellen Sie auf der Seite **Installationsbereit** sicher, dass die folgenden Auswahlmöglichkeiten aktiviert sind, und klicken Sie auf **Installieren**.
  
    + -Datenbank-Engine-Dienste
    + Machine Learning-Dienste und -Spracherweiterungen

    Notieren Sie sich den Speicherort des Ordners unter dem Pfad `..\Setup Bootstrap\Log`, in dem die Konfigurationsdateien gespeichert werden. Nach Abschluss des Setups können Sie die installierten Komponenten in der Zusammenfassungsdatei überprüfen.

6. Wenn Sie nach Abschluss des Setups dazu aufgefordert werden, starten Sie jetzt den Computer neu. Wenn Sie den Setupvorgang abgeschlossen haben, sollten Sie unbedingt die vom Installations-Assistenten angezeigte Meldung lesen. Weitere Informationen finden Sie unter [View and Read SQL Server Setup Log Files](https://docs.microsoft.com/sql/database-engine/install-windows/view-and-read-sql-server-setup-log-files).

## <a name="add-the-jre_home-variable"></a>Hinzufügen der Variablen JRE_HOME

`JRE_HOME` ist eine Systemumgebungsvariable, die den Speicherort des Java-Interpreters angibt. In diesem Schritt erstellen Sie hierfür in Windows eine Systemumgebungsvariable.

1. Suchen und kopieren Sie den JRE-Basispfad.

    Für die standardmäßige Java-Runtime Zulu JRE 11.0.3 lautet der JRE-Basispfad beispielsweise `C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\MSSQL\Binn\AZUL-OpenJDK-JRE\`.

    Der JDK- oder JRE-Speicherort kann sich von dem oben genannten Beispielpfad unterscheiden. Dies hängt von Ihrem SQL Server-Installationspfad oder davon ab, ob Sie eine andere Java-Runtime ausgewählt haben. Selbst wenn Sie ein JDK installiert haben, erhalten Sie häufig im Rahmen dieser Installation einen JRE-Unterordner. Zeigen Sie in einem solchen Fall auf den JRE-Ordner. Die Java-Erweiterung versucht, die `jvm.dll` aus dem Pfad `%JRE_HOME%\bin\server` zu laden.

2. Öffnen Sie in der Systemsteuerung **System und Sicherheit**, öffnen Sie **System**, und klicken Sie auf **Erweiterte Systemeigenschaften**.

3. Klicken Sie auf **Umgebungsvariablen**.

4. Erstellen Sie eine neue Systemvariable für `JRE_HOME` mit dem Wert des JDK-/JRE-Pfads (aus Schritt 1).

5. Starten Sie [Launchpad](../concepts/extensibility-framework.md#launchpad) neu.

    1. Öffnen Sie den [SQL Server-Konfigurations-Manager](../../relational-databases/sql-server-configuration-manager.md).

    2. Klicken Sie unter „SQL Server-Dienste“ mit der rechten Maustaste auf „SQL Server-Launchpad“, und wählen Sie **Neu starten** aus.

<a name="perms-nonwindows"></a>

## <a name="grant-access-to-non-default-jre-folder"></a>Gewähren des Zugriffs auf einen nicht standardmäßigen JRE-Ordner

Wenn Sie nicht die standardmäßige Zulu Open JRE installiert haben, die in SQL Server enthalten ist, und das JDK bzw. die JRE nicht unter „Programme“ installiert haben, müssen Sie die folgenden Schritte ausführen. Führen Sie die **icacls**-Befehle von einer Befehlszeile mit *erhöhten Rechten* aus, um für den JRE-Zugriff Zugriff auf die **SQLRUsergroup** und die SQL Server-Dienstkonten (in **ALL_APPLICATION_PACKAGES**) zu gewähren. Die Befehle gewähren rekursiv Zugriff auf alle Dateien und Ordner unter dem angegebenen Verzeichnispfad.

1. Vergeben Sie SQLRUserGroup-Berechtigungen.

    Hängen Sie für eine benannte Instanz den Namen der Instanz an SQLRUsergroup an (z. B. `SQLRUsergroupINSTANCENAME`).

    ```cmd
    icacls "<PATH to JRE>" /grant "SQLRUsergroup":(OI)(CI)RX /T
    ```
    
    Sie können diesen Schritt überspringen, wenn Sie das JDK/die JRE in Windows im Standardordner unter „Programme“ installiert haben.

2. Vergeben Sie AppContainer-Berechtigungen.

    ```cmd
    icacls "<PATH to JRE>" /grant "ALL APPLICATION PACKAGES":(OI)(CI)RX /T
    ```
    
## <a name="enable-script-execution"></a>Aktivieren der Skriptausführung

1. Öffnen Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. 

    > [!TIP]
    > Sie können die entsprechende Version von folgender Seite herunterladen und installieren: [Herunterladen von SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)
    > 
    > Sie können auch [Azure Data Studio](../../azure-data-studio/what-is.md) verwenden, das administrative Aufgaben und Abfragen für SQL Server unterstützt.
  
2. Stellen Sie eine Verbindung mit der Instanz her, auf der Sie die Spracherweiterungen installiert haben. Klicken Sie auf **Neue Abfrage**, um ein Abfragefenster zu öffnen, und führen Sie den folgenden Befehl aus:

    ```sql
    sp_configure
    ```

    Der Wert für die Eigenschaft `external scripts enabled` sollte an diesem Punkt **0** betragen. Diese Funktion ist standardmäßig deaktiviert. Sie muss explizit von einem Administrator aktiviert werden, damit Sie Java-Code ausführen können.
    
3.  Führen Sie die folgende Anweisung aus, um die externe Funktion für die Skripterstellung zu aktivieren:
    
    ```sql
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
    
    Führen Sie RECONFIGURE kein zweites Mal für Spracherweiterungen aus, wenn Sie die Funktion bereits für Machine Learning Services aktiviert haben. Die zugrunde liegende Erweiterungsplattform unterstützt beides.

## <a name="restart-the-service"></a>Starten Sie den Dienst neu.

Starten Sie nach Abschluss der Installation die Datenbank-Engine neu, bevor Sie mit dem nächsten Schritt fortfahren, und aktivieren Sie die Skriptausführung.

Durch den Neustart des Diensts wird auch der zugehörige SQL Server-Launchpad-Dienst automatisch neu gestartet.

Sie können den Dienst neu starten, indem Sie mit der rechten Maustaste auf den Befehl **Neu starten** für die Instanz in SSMS klicken, den Bereich **Dienste** in der Systemsteuerung oder den [SQL Server-Konfigurations-Manager](../../relational-databases/sql-server-configuration-manager.md) verwenden.

<a name="register_external_language"></a>

## <a name="register-external-language"></a>Registrieren einer externen Sprache

Für jede Datenbank, in der Sie Spracherweiterungen verwenden möchten, müssen Sie die externe Sprache über den Befehl [CREATE EXTERNAL LANGUAGE](https://docs.microsoft.com/sql/t-sql/statements/create-external-language-transact-sql) registrieren.

Im folgenden Beispiel wird eine externe Sprache mit dem Namen Java einer Datenbank auf SQL Server unter Windows hinzugefügt.

```SQL
CREATE EXTERNAL LANGUAGE Java
FROM (CONTENT = N'<path-to-zip>', FILE_NAME = 'javaextension.dll');
GO
```

Weitere Informationen finden Sie unter [CREATE EXTERNAL LANGUAGE](https://docs.microsoft.com/sql/t-sql/statements/create-external-language-transact-sql).

## <a name="verify-installation"></a>Überprüfen der Installation

Überprüfen Sie den Installationsstatus der Instanz in den Setupprotokollen.

Gehen Sie folgendermaßen vor, um zu überprüfen, ob alle zum Starten eines externen Skripts verwendeten Komponenten ausgeführt werden.

1. Öffnen Sie in SQL Server Management Studio oder in Azure Data Studio ein neues Abfragefenster, und führen Sie die folgende Anweisung aus:
    
    ```sql
    EXEC sp_configure  'external scripts enabled'
    ```

    Der **run_value-** ist nun auf 1 festgelegt.
    
2. Öffnen Sie den Bereich **Dienste** oder den SQL Server-Konfigurations-Manager, und überprüfen Sie, ob der **SQL Server-Launchpad-Dienst** ausgeführt wird. Sie sollten über einen Dienst für jede Datenbank-Engine-Instanz verfügen, auf der Spracherweiterungen installiert sind. Weitere Informationen zu dem Dienst finden Sie unter [Erweiterbarkeitsframework](../concepts/extensibility-framework.md). 
   
## <a name="additional-configuration"></a>Zusätzliche Konfiguration

Wenn der Überprüfungsschritt erfolgreich war, können Sie Java-Code aus SQL Server Management Studio, Azure Data Studio, Visual Studio Code oder einem anderen Client ausführen, der T-SQL-Anweisungen an den Server senden kann.

Überprüfen Sie die zusätzlichen Konfigurationsschritte in diesem Abschnitt, wenn beim Ausführen des Befehls ein Fehler aufgetreten ist. Möglicherweise müssen Sie für den Dienst oder die Datenbank zusätzliche geeignete Konfigurationen vornehmen.

Auf Instanzebene kann eine zusätzliche Konfiguration Folgendes umfassen:

* [Firewallkonfiguration für SQL Server- Machine Learning Services](../../advanced-analytics/security/firewall-configuration.md)
* [Aktivieren zusätzlicher Netzwerkprotokolle](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)
* [Aktivieren von Remoteverbindungen](../../database-engine/configure-windows/configure-the-remote-access-server-configuration-option.md)
* [Erstellen von Anmeldeinformationen für SQLRUserGroup](../../advanced-analytics/security/create-a-login-for-sqlrusergroup.md)

<a name="bkmk_configureAccounts"></a> 
<a name="permissions-external-script"></a> 

Für die Datenbank benötigen Sie möglicherweise die folgenden Konfigurationsupdates:

* [Benutzern die Berechtigung für SQL Server-Machine Learning Services erteilen](../../advanced-analytics/security/user-permission.md)
* [Benutzern die Berechtigung zum Ausführen einer bestimmten Sprache erteilen](https://docs.microsoft.com/sql/t-sql/statements/create-external-language-transact-sql#permissions)

> [!NOTE]
> Ob eine zusätzliche Konfiguration erforderlich ist, hängt vom Sicherheitsschema, in dem Sie SQL Server installiert haben, sowie von Ihren Erwartungen bezüglich des Herstellens einer Verbindung mit der Datenbank und dem Ausführen externer Skripts seitens der Benutzer ab.

## <a name="suggested-optimizations"></a>Empfohlene Optimierungen

Da nun alles funktioniert, möchten Sie möglicherweise auch den Server für die Unterstützung von Spracherweiterungen optimieren.

### <a name="optimize-the-server-for-language-extensions"></a>Optimieren des Servers für Spracherweiterungen

Die Standardeinstellungen für das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Setup dienen zur Optimierung des Lastenausgleichs des Servers für eine Vielzahl von Diensten, die von der Datenbank-Engine unterstützt werden, einschließlich ETL-Prozesse (Extrahieren, Transformieren und Laden), Reporting, Überwachung und Anwendungen, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Daten verwenden. Daher können in den Standardeinstellungen Ressourcen für Spracherweiterungen eingeschränkt oder gedrosselt sein, insbesondere für speicherintensive Vorgänge.

Es wird empfohlen, dass Sie zum Konfigurieren eines externen Ressourcenpools den SQL Server-Resource Governor verwenden, um sicherzustellen, dass Spracherweiterungsaufgaben über die entsprechende Priorität und die nötigen Ressourcen verfügen. Eventuell ist es auch sinnvoll, die Größe des Speichers zu ändern, der der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank-Engine zugewiesen ist, oder die Anzahl der Konten zu erhöhen, die unter dem [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]-Dienst ausgeführt werden.

- Informationen zum Konfigurieren eines Ressourcenpools zum Verwalten externer Ressourcen finden Sie unter [Erstellen eines externen Ressourcenpools](../../t-sql/statements/create-external-resource-pool-transact-sql.md).
  
- Informationen zum Ändern des für die Datenbank reservierten Arbeitsspeichers finden Sie unter [Konfigurationsoptionen für den Serverarbeitsspeicher](../../database-engine/configure-windows/server-memory-server-configuration-options.md).
  
Wenn Sie die Standard Edition verwenden und nicht über den Resource Governor verfügen, können Sie zum Verwalten von Serverressourcen dynamische Verwaltungssichten (DMVs) und erweiterte Ereignisse sowie die Windows-Ereignisüberwachung verwenden.

## <a name="next-steps"></a>Nächste Schritte

Java-Entwickler können mit einigen einfachen Beispielen loslegen und die Grundlagen der Funktionen von Java unter SQL Server kennenlernen. Informationen zum nächsten Schritt finden Sie unter dem folgenden Link:

+ [Tutorial: Reguläre Ausdrücke in Java](../tutorials/search-for-string-using-regular-expressions-in-java.md)
