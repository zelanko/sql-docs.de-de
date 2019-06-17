---
title: Installieren von R Server oder SQL Server-Setup – SQL Server-Machine Learning mit Machine Learning Server (eigenständig)
description: Richten Sie einen nicht instanzabhängige eigenständige Machine Learning-Server, für die R und Python-Entwicklung, die mithilfe von RevoScaleR, Revoscalepy, MicrosoftML und andere Pakete.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/28/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 911086beaaaeb28a036a764e066402d7ba6f1da7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62747072"
---
# <a name="install-machine-learning-server-standalone-or-r-server-standalone-using-sql-server-setup"></a>Installieren von Machine Learning Server (eigenständig) oder R Server (eigenständig) mit SQL Server-Setup
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server-Setup enthält einen **freigegebene Funktion** -Option zum Installieren einer nicht instanzabhängige, eigenständige Machine Learning-Server, die außerhalb von SQL Server ausgeführt wird. In SQL Server 2016 kann dieses Feature heißt **R Server (eigenständig)** . In SQL Server 2017 heißt es **Machine Learning Server (eigenständig)** enthält R und Python. 

Ein eigenständigen Server, wie vom SQL Server-Setup installiert ist funktionell gleichwertig mit der nicht-SQL-Versionen unter dem Markennamen [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server), unterstützen die gleichen verwenden, Anwendungsfälle und Szenarien, einschließlich:

+ Remoteausführung, zwischen lokalen und Remotesitzungen in der gleichen Konsole wechseln
+ Operationalisierung mit Web- und Computeknoten
+ Web-Service-Bereitstellung: die Möglichkeit, R und Python-Skript in Webdienste Paket
+ Führen Sie die Sammlung von Bibliotheken für R und Python-Funktion

Als unabhängige-Server von SQL Server entkoppelt ist die R- und Python-Umgebung, gesicherte und zugegriffen, mit dem zugrunde liegenden Betriebssystem und auf dem eigenständigen Server, nicht auf SQL Server bereitgestellten Tools konfiguriert.

Als Ergänzung zum SQL Server ist ein eigenständiger Server nützlich, wenn Sie zum Entwickeln von High-Performance-Machine learning-Lösungen, die remotecomputekontexte auf den vollständigen Bereich der unterstützten Plattformen verwenden können, benötigen. Sie können die Ausführung vom lokalen Server mit einem Machine Learning-Remoteserver verlagern, auf einen Spark-Cluster oder auf eine andere SQL Server-Instanz.

<a name="bkmk_prereqs"> </a>

## <a name="pre-install-checklist"></a>Checkliste für die vor der Installation

Bei der Installation einer früheren Version, z. B. SQL Server 2016 R Server (eigenständig) oder Microsoft R Server, deinstallieren Sie die vorhandene Installation, bevor Sie fortfahren.

Als allgemeine Regel, wird empfohlen, Sie behandeln, eigenständigen Server und Datenbank-Engine instanzabhängigen Installationen als sich gegenseitig exklusiv, um Ressourcenkonflikte zu vermeiden, wenn Sie über ausreichende Ressourcen verfügen, keine Verbot besteht für die Installation von beidem jedoch auf die demselben physischen Computer.

Sie können nur ein eigenständiger Server verwenden, auf dem Computer: entweder SQL Server 2017-Machine-Learning-Server oder SQL Server 2016 R Server (eigenständig). Achten Sie darauf, dass Sie eine Version zu deinstallieren, bevor Sie einen neuen hinzufügen.

::: moniker range="=sql-server-2016"
<a name="bkmk_ga_instalpatch"></a> 

 ###  <a name="install-patch-requirement"></a>Installieren einer patchanforderung 

Nur für SQLServer 2016: Microsoft hat ein Problem bei der speziellen Version von Microsoft VC++ 2013 Runtime-Binärdateien erkannt, die von SQL Server als vorausgesetzte Komponenten installiert werden. Wenn dieses Update an den VC++ Runtime-Binärdateien nicht installiert wird, können bei SQL Server in bestimmten Szenarios Stabilitätsprobleme auftreten. Bevor Sie SQL Server installieren, sollten Sie entsprechend den Anweisungen unter [Versionsanmerkungen zu SQL Server](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch) vorgehen, um festzustellen, ob Ihr Computer einen Patch für die VC-Runtime-Binärdateien benötigt.  
::: moniker-end

## <a name="get-the-installation-media"></a>Abrufen der Installationsmedien

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
## <a name="run-setup"></a>Ausführen von 'Setup'

Bei lokalen Installationen müssen Sie das Setup als Administrator ausführen. Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von einer Remotefreigabe installieren, müssen Sie ein Domänenkonto verwenden, das Lese- und Ausführungsberechtigungen auf der Remotefreigabe hat.

1. Starten Sie den Installations-Assistenten.

2. Klicken Sie auf die **Installation** , und wählen Sie **neue Machine Learning Server (Standalone) Installation**.
    
     ![Installieren von Machine Learning Server (eigenständig)](media/2017setup-installation-page-mlsvr.png "Starten der Installation von Machine Learning Server (eigenständig)")

3. Nachdem die Überprüfung der Regeln abgeschlossen ist, akzeptieren Sie SQL Server-Lizenzbedingungen, und wählen Sie eine neue Installation.

4. Auf der **Funktionsauswahl** Seite die folgenden Optionen bereits ausgewählt sein sollte:

    - Microsoft Machine Learning Server (eigenständig)

    - R und Python sind standardmäßig ausgewählt. Sie können die beiden Sprachen deaktivieren, aber es wird empfohlen, mindestens eine der unterstützten Sprachen zu installieren.

     ![Wählen Sie die Funktionen von R oder Python](media/2017setup-features-page-mlsvr-rpy.png "Starten der Installation von Machine Learning Server (eigenständig)")
    
    Alle anderen Optionen sollten ignoriert werden. 
    
    > [!NOTE]
    > Vermeiden Sie die Installation der **gemeinsam genutzte Funktionen** verfügt der Computer bereits Machine Learning-Dienste, die für SQL Server in-Database-Analyse installiert. Dadurch wird die doppelte Bibliotheken erstellt.
    > 
    > Darüber hinaus während R oder Python-Skripts in SQL Server von SQL Server nicht in Konflikt mit von anderen Datenbank-Engine-Dienste verwendete Arbeitsspeicher verwaltet werden, die eigenständige Machine Learning-Server verfügt über keine solche Einschränkungen und kann bei anderen Datenbankvorgängen beeinträchtigen . Schließlich wird der Remotezugriff über RDP-Sitzung, die häufig für die operationalisierung verwendet wird, in der Regel von Datenbankadministratoren blockiert.
    > 
    > Aus diesen Gründen im Allgemeinen empfohlen, dass Sie Machine Learning Server (eigenständig) auf demselben Computer wie SQL Server Machine Learning Services installieren.

5.  Akzeptieren Sie die Lizenzbedingungen für das Herunterladen und installieren die Basissprache Verteilungen. Wenn die Schaltfläche **Annehmen** deaktiviert wird, können Sie auf **Weiter**klicken. 

     ![Python-Lizenzvertrag](media/2017setup-python-license.png "Python-Lizenzvertrag")

6.  Überprüfen Sie Ihre Auswahl auf der Seite **Installationsbereit** , und klicken Sie anschließend auf **Installieren**.

Wenn die Installation abgeschlossen ist, finden Sie unter [benutzerdefinierte Berichte für SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md) Hilfe Fehler oder Warnungen, finden Sie unter [Upgrade und Installation – häufig gestellte Fragen – Machine Learning Services](../r/upgrade-and-installation-faq-sql-server-r-services.md).
::: moniker-end

::: moniker range="=sql-server-2016"
## <a name="run-setup"></a>Ausführen von 'Setup'

Bei lokalen Installationen müssen Sie das Setup als Administrator ausführen. Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von einer Remotefreigabe installieren, müssen Sie ein Domänenkonto verwenden, das Lese- und Ausführungsberechtigungen auf der Remotefreigabe hat.

1. Starten Sie den Installations-Assistenten.

2. Auf der **Installation** auf **neue R Server (Standalone) Installation**.
    
     ![Starten Sie das Setup von R Server (eigenständig)](media/2016-setup-installation-rsvr.png "starten Sie das Setup von R Server (eigenständig)")

3. Nachdem die Überprüfung der Regeln abgeschlossen ist, akzeptieren Sie SQL Server-Lizenzbedingungen, und wählen Sie eine neue Installation.

4.  Auf der Seite **Feature selection** (Funktionsauswahl) sollte die folgende Option bereits aktiviert sein:
    
    **R Server (eigenständig)**  
    
    ![Die Funktionsauswahl für R Server (eigenständig)](media/2016setup-rserver-features.png "Funktionsauswahl für R Server (eigenständig)")
    
    Alle anderen Optionen können ignoriert werden. 
    
    > [!NOTE]
    > Vermeiden Sie die Installation der **gemeinsam genutzte Funktionen** Wenn Sie Setup auf einem Computer ausführen, bei der es dem R Services bereits für SQL Server in-Database-Analyse installiert wurde. Dadurch wird die doppelte Bibliotheken erstellt.
    > 
    > Während der R-Skripts in SQL Server von SQL Server nicht in Konflikt mit von anderen Datenbank-Engine-Dienste verwendete Arbeitsspeicher verwaltet werden, wird der eigenständigen R Servers verfügt über keine solche Einschränkungen, und bei anderen Datenbankvorgängen beeinträchtigen kann.
    > 
    > Wir empfehlen im allgemeinen Installation von R Server (eigenständig) auf einem separaten Computer von SQL Server R Services (Datenbankintern).

5.  Akzeptieren Sie die Lizenzbedingungen für das Herunterladen und installieren die Basissprache Verteilungen. Wenn die Schaltfläche **Annehmen** deaktiviert wird, können Sie auf **Weiter**klicken. 

6.  Überprüfen Sie Ihre Auswahl auf der Seite **Installationsbereit** , und klicken Sie anschließend auf **Installieren**.

Wenn die Installation abgeschlossen ist, finden Sie unter [benutzerdefinierte Berichte für SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md) Hilfe Fehler oder Warnungen, finden Sie unter [Upgrade und Installation – häufig gestellte Fragen – Machine Learning Services](../r/upgrade-and-installation-faq-sql-server-r-services.md).
::: moniker-end

## <a name="set-environment-variables"></a>Festlegen von Umgebungsvariablen

Sie sollten für die R-Funktionsintegration nur Festlegen der **MKL_CBWR** -Umgebungsvariable so fest, [sicherstellen von konsistenten Ausgabe](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr) von Intel Math Kernel Library (MKL) Berechnungen.

1. Klicken Sie in der Systemsteuerung auf **System und Sicherheit** > **System** > **Erweiterte Systemeinstellungen**  >   **Umgebungsvariablen**.

2. Erstellen Sie eine neue Variable für Benutzer- oder Systemkonto. 

  + Set-Variablennamen, um `MKL_CBWR`
  + Legen Sie den Wert den Variablen auf `AUTO`

3. Starten Sie den Server neu.

<a name="install-path"></a>

### <a name="default-installation-folders"></a>Standard-Installationsordner

Für R und Python-Entwicklung ist es üblich, mehrere Versionen auf demselben Computer zu verwenden. Wie von SQL Server-Setup installiert, ist die base-Verteilung installiert, in einem Ordner mit dem zugeordneten SQL Server-Version, die Sie bei der Installation verwendet.

Die folgende Tabelle enthält die Pfade für R und Python-Distributionen, die durch Microsoft Installationsprogramme erstellt. Der Vollständigkeit halber enthält die Tabelle klickpfade, die von SQL Server-Setup als auch auf dem eigenständigen Installer für Microsoft Machine Learning Server erstellt.

|Version| Installationsmethode | Standardordner|
|----|----|----|
|SQL Server 2017-Machine-Learning-Server (eigenständig) |  SQL Server 2017-Setup-Assistenten |`C:\Program Files\Microsoft SQL Server\140\R_SERVER` <br/>`C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`|
|Microsoft Machine Learning Server (eigenständig) |  Eigenständiger Installer für Windows |`C:\Program Files\Microsoft\ML Server\R_SERVER`<br/>`C:\Program Files\Microsoft\ML Server\PYTHON_SERVER`|
|SQL Server 2017-Machine-Learning-Services (Datenbankintern) |SQL Server 2017-Setup-Assistenten, mit der Option "R-Sprache"|`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES`  <br/>`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\PYTHON_SERVICES` |
|SQL Server 2016 R Server (eigenständig) |  SQL Server 2016-Setup-Assistenten |`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|SQL Server 2016 R Services (Datenbankintern) |SQL Server 2016-Setup-Assistenten|`C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\R_SERVICES`|

<a name="apply-cu"></a>

## <a name="apply-updates"></a>Anwenden von updates

Es wird empfohlen, dass Sie das neueste kumulative Update für die Datenbank-Engine und Machine learning-Komponenten anwenden. Kumulative Updates werden über das Setupprogramm installiert. 

Auf dem Internet verbundene Geräte verwenden können Sie eine selbstextrahierende EXE-Datei herunterladen. Automatisches Anwenden eines Updates für die Datenbank-Engine ruft kumulativen Updates für vorhandene Features von R und Python. 

Auf getrennten Servern sind zusätzliche Schritte erforderlich. Sie müssen das kumulative Update für die Datenbank-Engine sowie die CAB-Dateien für Machine Learning-Features abrufen. Alle Dateien müssen auf den isolierten Server übertragen und manuell angewendet werden.

1. Beginnen Sie mit einer Baseline-Instanz. Sie können nur kumulative Updates auf vorhandene Installationen anwenden:

  + Machine Learning Server (eigenständig) aus der ersten Version von SQL Server 2017
  + R Server (eigenständig) aus der ersten Version von SQL Server 2016, SQL Server 2016 SP1 oder SQL Server 2016 SP 2

2. Schließen Sie alle geöffneten Sitzungen, die R- oder Python, und beenden Sie alle weiterhin auf dem System ausgeführten Prozesse.

3. Wenn Sie operationalisierung zur Ausführung als Web und Computeknoten für Bereitstellungen für Web-Dienst aktiviert haben, Sichern Sie die **"appSettings.JSON"** Datei als Vorsichtsmaßnahme. Daher sollten Sie eine Sicherungskopie die ursprüngliche Version beibehalten CU13 für SQL Server 2017 oder höher im Verlauf dieser Datei angewendet werden soll.

4. Klicken Sie auf den Link Kumulatives Update für Ihre Version von SQL Server, auf einem verbundenen Gerät Internet.

  + [SQL Server 2017-updates](https://sqlserverupdates.com/sql-server-2017-updates/)
  + [Updates für SQL Server 2016](https://sqlserverupdates.com/sql-server-2016-updates/)

5. Laden Sie das neueste kumulative Update herunter. Es ist eine ausführbare Datei.

6. Doppelklicken Sie auf einem Gerät mit Internetzugang auf der .exe zum Ausführen von Setup und Schritt im Assistenten auf die Lizenzbedingungen akzeptieren, prüfen die betroffenen Features und Fortschritt bis zur Fertigstellung zu überwachen.

7. Auf einem Server ohne Internetverbindung:

   + Erhalten Sie entsprechende CAB-Dateien für R und Python. Downloadlinks finden Sie unter [CAB-downloads für kumulative Updates auf SQL Server in-Database-Analyse für Instanzen](sql-ml-cab-downloads.md).

   + Übertragen Sie alle Dateien, die zentrale ausführbare Datei und die CAB-Dateien in einen Ordner auf dem Offlinecomputer.

   + Doppelklicken Sie auf die .exe aus, um Setup auszuführen. Wenn Sie ein kumulatives Update auf einem Server ohne Internetverbindung zu installieren, werden Sie aufgefordert, um den Speicherort der CAB-Dateien für R und Python auszuwählen.

8. Bearbeiten Sie nach der Installation auf einem Server, Sie haben für die operationalisierung mit Web-Knoten und Compute-Knoten aktiviert **"appSettings.JSON"** , einen Eintrag "MMLResourcePath" direkt unter "MMLNativePath" hinzufügen:

    ```json
    "ScorerParameters": {
        "MMLNativePath": "C:\Program Files\Microsoft SQL Server\140\R_SERVER\library\MicrosoftML\mxLibs\x64\",
        "MMLResourcePath": "C:\Program Files\Microsoft SQL Server\140\R_SERVER\library\MicrosoftML\mxLibs\x64\"
    }
    ```

9. [Führen Sie das Admin-CLI-Hilfsprogramm](https://docs.microsoft.com/machine-learning-server/operationalize/configure-admin-cli-launch) neu starten im Web, und compute-Knoten. Schritte und Syntaxelemente, finden Sie unter [überwachen, Start- und Stop-web- und compute-Knoten](https://docs.microsoft.com/machine-learning-server/operationalize/configure-admin-cli-stop-start).

## <a name="development-tools"></a>Entwicklungstools

Eine integrierte Entwicklungsumgebung ist nicht als Teil des Setups installiert. Weitere Informationen zum Konfigurieren einer Entwicklungsumgebung finden Sie unter [Einrichten von R-Tools](../r/set-up-a-data-science-client.md) und [Python-Tools einrichten](../python/setup-python-client-tools-sql.md).

## <a name="next-steps"></a>Nächste Schritte

R-Entwickler können mit einigen einfachen Beispielen beginnen, und die Grundlagen der Funktionsweise von R mit SQL Server. Der nächste Schritt ist finden Sie in den folgenden Links:

+ [Tutorial: Run R in T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Tutorial: Datenbankinterne Analysen für R-Entwickler](../tutorials/sqldev-in-database-r-for-sql-developers.md)

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
Python-Entwickler erfahren, wie Python mit SQL Server verwenden, indem Sie die folgenden in diesen Tutorials:

+ [Tutorial: Ausführen von Python in T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Tutorial: Datenbankinterne Analysen für Python-Entwickler](../tutorials/sqldev-in-database-python-for-sql-developers.md)
::: moniker-end

Beispiele für Machine Learning, die auf realen Szenarien basieren, finden Sie unter [Machine learning-Tutorials](../tutorials/machine-learning-services-tutorials.md).
