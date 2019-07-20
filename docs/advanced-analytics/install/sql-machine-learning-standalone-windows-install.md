---
title: Installieren von R Server oder Machine Learning Server (eigenständig) mit SQL Server Setup
description: Richten Sie mithilfe von revoscaler, revoscalepy, microsoftml und anderen Paketen einen nicht instanzfähigen eigenständigen Machine Learning-Server für die R-und Python-Entwicklung ein.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/28/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 0abf14fa61d9408f8403a493b7559148f0f5a775
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344980"
---
# <a name="install-machine-learning-server-standalone-or-r-server-standalone-using-sql-server-setup"></a>Installieren von Machine Learning Server (eigenständig) oder R Server (eigenständig) mit SQL Server Setup
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

SQL Server Setup enthält eine Option für frei **gegebene Funktionen** zum Installieren eines nicht instanzabhängigen, eigenständigen Machine Learning-Servers, der außerhalb von SQL Server ausgeführt wird. In SQL Server 2016 wird diese Funktion **R Server (eigenständig)** genannt. In SQL Server 2017 heißt Sie **Machine Learning Server (eigenständig)** und umfasst R und python. 

Ein eigenständiger Server, der von SQL Server-Setup installiert wird, ist funktional äquivalent zu den nicht-SQL-Branding-Versionen von [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server)und unterstützt dieselben Anwendungsfälle und Szenarien wie die folgenden:

+ Remote Ausführung, wechseln zwischen lokalen und Remote Sitzungen in derselben Konsole
+ Operationalisierung mit webknoten und Computeknoten
+ Webdienst Bereitstellung: die Möglichkeit, R-und python-Skripts in Webdienste zu verpacken
+ Umfassende Sammlung von R-und python-Funktionsbibliotheken

Als unabhängiger Server, der von SQL Server entkoppelt ist, wird die R-und python-Umgebung konfiguriert, gesichert und der Zugriff erfolgt über das zugrunde liegende Betriebssystem und die Tools SQL Server, die auf dem eigenständigen Server bereitgestellt werden.

Als Ergänzung zu SQL Server ist ein eigenständiger Server nützlich, wenn Sie hochleistungsfähige Machine Learning-Lösungen entwickeln müssen, die remotecomputekontexte für alle unterstützten Daten Plattformen verwenden können. Sie können die Ausführung vom lokalen Server auf eine Remote Machine Learning Server in einem Spark-Cluster oder auf einer anderen SQL Server Instanz verlagern.

<a name="bkmk_prereqs"> </a>

## <a name="pre-install-checklist"></a>Prüfliste vor der Installation

Wenn Sie eine frühere Version installiert haben, z. b. SQL Server 2016 R Server (eigenständig) oder Microsoft R Server, deinstallieren Sie die vorhandene Installation, bevor Sie fortfahren.

Als allgemeine Regel empfiehlt es sich, eigenständige Server-und Datenbank-Engine-Installationen als gegenseitig ausschließende Installationen zu behandeln, um Ressourcenkonflikte zu vermeiden. Wenn Sie jedoch über ausreichende Ressourcen verfügen, besteht keine Sperre gegen die Installation beider Komponenten auf der gleicher physischer Computer.

Auf dem Computer kann nur ein eigenständiger Server vorhanden sein: entweder SQL Server 2017 Machine Learning Server oder SQL Server 2016 R Server (eigenständig). Stellen Sie sicher, dass Sie eine Version deinstallieren, bevor Sie einen neuen hinzufügen.

::: moniker range="=sql-server-2016"
<a name="bkmk_ga_instalpatch"></a> 

 ###  <a name="install-patch-requirement"></a>Patch-Anforderung installieren 

Nur für SQL Server 2016: Microsoft hat ein Problem bei der speziellen Version von Microsoft VC++ 2013 Runtime-Binärdateien erkannt, die von SQL Server als vorausgesetzte Komponenten installiert werden. Wenn dieses Update an den VC++ Runtime-Binärdateien nicht installiert wird, können bei SQL Server in bestimmten Szenarios Stabilitätsprobleme auftreten. Bevor Sie SQL Server installieren, sollten Sie entsprechend den Anweisungen unter [Versionsanmerkungen zu SQL Server](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch) vorgehen, um festzustellen, ob Ihr Computer einen Patch für die VC-Runtime-Binärdateien benötigt.  
::: moniker-end

## <a name="get-the-installation-media"></a>Abrufen der Installationsmedien

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
## <a name="run-setup"></a>Ausführen von 'Setup'

Bei lokalen Installationen müssen Sie das Setup als Administrator ausführen. Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von einer Remotefreigabe installieren, müssen Sie ein Domänenkonto verwenden, das Lese- und Ausführungsberechtigungen auf der Remotefreigabe hat.

1. Starten Sie den-Installations-Assistenten.

2. Klicken Sie auf die Registerkarte **Installation** , und wählen Sie **neu Machine Learning Server Installation (eigenständig)** aus.
    
     ![Installieren von Machine Learning Server eigen] ständig (media/2017setup-installation-page-mlsvr.png "Installation von eigenständigem Machine Learning Server starten")

3. SQL Server akzeptieren Sie nach Abschluss der Regelüberprüfung die Lizenzbedingungen, und wählen Sie eine neue Installation aus.

4. Auf der Seite **Funktionsauswahl** sollten die folgenden Optionen bereits ausgewählt sein:

    - Microsoft Machine Learning Server (eigenständig)

    - R und python sind beide standardmäßig ausgewählt. Sie können beide Sprachen deaktivieren, es wird jedoch empfohlen, mindestens eine der unterstützten Sprachen zu installieren.

     ![R-oder python-Features auswählen](media/2017setup-features-page-mlsvr-rpy.png "Installation von eigenständigem Machine Learning Server starten")
    
    Alle anderen Optionen sollten ignoriert werden. 
    
    > [!NOTE]
    > Vermeiden Sie die Installation der frei **gegebenen Funktionen** , wenn auf dem Computer bereits Machine Learning Services für SQL Server datenbankübergreifende Analyse installiert ist. Dadurch werden doppelte Bibliotheken erstellt.
    > 
    > Auch wenn R-oder python-Skripts, die in SQL Server ausgeführt werden, von SQL Server verwaltet werden, damit kein Konflikt mit dem von anderen Datenbank-Engine-Diensten verwendeten Arbeitsspeicher besteht, weist der eigenständige Machine Learning-Server keine Einschränkungen auf und kann andere Daten Bank Vorgänge beeinträchtigen. . Schließlich wird der Remote Zugriff über die RDP-Sitzung, die häufig für die Operationalisierung verwendet wird, in der Regel von Datenbankadministratoren blockiert.
    > 
    > Aus diesen Gründen wird im Allgemeinen empfohlen, dass Sie Machine Learning Server (eigenständig) auf einem anderen Computer als SQL Server Machine Learning Services installieren.

5.  Akzeptieren Sie die Lizenzbedingungen für das herunterladen und Installieren von Basis Sprachen Verteilungen. Wenn die Schaltfläche **Annehmen** deaktiviert wird, können Sie auf **Weiter**klicken. 

     ![Python-Lizenzvertrag](media/2017setup-python-license.png "Python-Lizenzvertrag")

6.  Überprüfen Sie Ihre Auswahl auf der Seite **Installationsbereit** , und klicken Sie anschließend auf **Installieren**.

Wenn die Installation abgeschlossen ist, finden Sie weitere Informationen unter [benutzerdefinierte Berichte für SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md) Hilfe zu Fehlern oder Warnungen finden Sie unter Häufig gestellte Fragen zu [Upgrade und Installation Machine Learning Services](../r/upgrade-and-installation-faq-sql-server-r-services.md).
::: moniker-end

::: moniker range="=sql-server-2016"
## <a name="run-setup"></a>Ausführen von 'Setup'

Bei lokalen Installationen müssen Sie das Setup als Administrator ausführen. Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von einer Remotefreigabe installieren, müssen Sie ein Domänenkonto verwenden, das Lese- und Ausführungsberechtigungen auf der Remotefreigabe hat.

1. Starten Sie den-Installations-Assistenten.

2. Klicken Sie auf der Registerkarte **Installation** auf **neu R Server Installation (eigenständig)** .
    
     ![Setup von R Server eigenständig starten](media/2016-setup-installation-rsvr.png "Setup von R Server eigenständig starten")

3. SQL Server akzeptieren Sie nach Abschluss der Regelüberprüfung die Lizenzbedingungen, und wählen Sie eine neue Installation aus.

4.  Auf der Seite **Feature selection** (Funktionsauswahl) sollte die folgende Option bereits aktiviert sein:
    
    **R Server (eigenständig)**  
    
    ![Funktionsauswahl für eigenständige R Server](media/2016setup-rserver-features.png "Funktionsauswahl für eigenständige R Server")
    
    Alle anderen Optionen können ignoriert werden. 
    
    > [!NOTE]
    > Vermeiden Sie die Installation der frei **gegebenen Funktionen** , wenn Sie Setup auf einem Computer ausführen, auf dem R Services bereits für SQL Server in-Database-Analyse installiert wurde. Dadurch werden doppelte Bibliotheken erstellt.
    > 
    > Während R-Skripts, die in SQL Server ausgeführt werden, von SQL Server verwaltet werden, damit kein Konflikt mit dem von anderen Datenbank-Engine-Diensten verwendeten Arbeitsspeicher vorliegt, verfügt der eigenständige R Server nicht über derartige Einschränkungen und kann andere Daten Bank Vorgänge beeinträchtigen.
    > 
    > Im Allgemeinen wird empfohlen, dass Sie R Server (eigenständig) auf einem separaten Computer von SQL Server R Services (in-Database) installieren.

5.  Akzeptieren Sie die Lizenzbedingungen für das herunterladen und Installieren von Basis Sprachen Verteilungen. Wenn die Schaltfläche **Annehmen** deaktiviert wird, können Sie auf **Weiter**klicken. 

6.  Überprüfen Sie Ihre Auswahl auf der Seite **Installationsbereit** , und klicken Sie anschließend auf **Installieren**.

Wenn die Installation abgeschlossen ist, finden Sie weitere Informationen unter [benutzerdefinierte Berichte für SQL Server R Services](../r/monitor-r-services-using-custom-reports-in-management-studio.md) Hilfe zu Fehlern oder Warnungen finden Sie unter Häufig gestellte Fragen zu [Upgrade und Installation Machine Learning Services](../r/upgrade-and-installation-faq-sql-server-r-services.md).
::: moniker-end

## <a name="set-environment-variables"></a>Umgebungsvariablen festlegen

Für die Integration von R-Funktionen sollten Sie die **MKL_CBWR** -Umgebungsvariable festlegen, um [eine konsistente Ausgabe](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr) von MKL-Berechnungen (Intel Math Kernel Library) sicherzustellen.

1. Klicken Sie in der Systemsteuerung auf **System-und Sicherheits** > **System** > **Erweiterte Systemeinstellungen** > **Umgebungsvariablen**.

2. Erstellen Sie eine neue Benutzer-oder System Variable. 

  + Variablenname festlegen auf`MKL_CBWR`
  + Legen Sie den Variablen Wert auf fest.`AUTO`

3. Starten Sie den Server neu.

<a name="install-path"></a>

### <a name="default-installation-folders"></a>Standard Installationsordner

Bei der Entwicklung von R und Python ist es üblich, dass mehrere Versionen auf demselben Computer vorhanden sind. Gemäß der Installation durch SQL Server-Setup wird die basisverteilung in einem Ordner installiert, der der SQL Server Version zugeordnet ist, die Sie für das Setup verwendet haben.

In der folgenden Tabelle sind die Pfade für R-und python-Distributionen aufgelistet, die von Microsoft Installer erstellt wurden. Der Vollständigkeit halber enthält die Tabelle Pfade, die von SQL Server-Setup generiert werden, sowie das eigenständige Installationsprogramm für Microsoft Machine Learning Server.

|Version| Installationsmethode | Standardordner|
|----|----|----|
|SQL Server 2017 Machine Learning Server (eigenständig) |  Setup-Assistent für SQL Server 2017 |`C:\Program Files\Microsoft SQL Server\140\R_SERVER` <br/>`C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`|
|Microsoft Machine Learning Server (eigenständig) |  Eigenständiges Windows Installer |`C:\Program Files\Microsoft\ML Server\R_SERVER`<br/>`C:\Program Files\Microsoft\ML Server\PYTHON_SERVER`|
|SQL Server 2017 Machine Learning Services (in-Database) |Setup-Assistent für SQL Server 2017, mit R-Sprachoption|`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES`  <br/>`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\PYTHON_SERVICES` |
|SQL Server 2016 R Server (eigenständig) |  Setup-Assistent für SQL Server 2016 |`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|SQL Server 2016 R Services (in-Database) |Setup-Assistent für SQL Server 2016|`C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\R_SERVICES`|

<a name="apply-cu"></a>

## <a name="apply-updates"></a>Anwenden von Updates

Es wird empfohlen, dass Sie das neueste kumulative Update sowohl auf die Datenbank-Engine als auch auf die Machine Learning-Komponenten anwenden. Kumulative Updates werden über das-Setup Programm installiert. 

Auf Geräten mit Internetverbindung können Sie eine selbst extrahierende ausführbare Datei herunterladen. Wenn Sie ein Update für die Datenbank-Engine anwenden, werden kumulative Updates für vorhandene R-und Python-Funktionen automatisch abgerufen. 

Auf getrennten Servern sind zusätzliche Schritte erforderlich. Sie müssen das kumulative Update für die Datenbank-Engine sowie die CAB-Dateien für Machine Learning-Features abrufen. Alle Dateien müssen auf den isolierten Server übertragen und manuell angewendet werden.

1. Beginnen Sie mit einer Baseline-Instanz. Sie können nur kumulative Updates auf vorhandene Installationen anwenden:

  + Machine Learning Server (eigenständig) aus SQL Server 2017-anfangs Version
  + R Server (eigenständig) aus SQL Server 2016-anfangs Version, SQL Server 2016 SP 1 oder SQL Server 2016 SP 2

2. Schließen Sie alle geöffneten R-oder python-Sitzungen, und beenden Sie alle Prozesse, die noch im System ausgeführt werden.

3. Wenn Sie die Operationalisierung als webknoten und Computeknoten für Webdienst Bereitstellungen ausgeführt haben, sichern Sie die Datei " **appSettings. JSON** " als Vorsichtsmaßnahme. Wenn Sie SQL Server 2017 CU13 oder höher anwenden, wird diese Datei erneut überprüft, sodass Sie eine Sicherungskopie verwenden können, um die ursprüngliche Version beizubehalten.

4. Klicken Sie auf einem mit dem Internet verbundenen Gerät auf den Link kumulativer Update für Ihre Version von SQL Server.

  + [SQL Server 2017 Updates](https://sqlserverupdates.com/sql-server-2017-updates/)
  + [SQL Server 2016 Updates](https://sqlserverupdates.com/sql-server-2016-updates/)

5. Laden Sie das neueste kumulative Update herunter. Dabei handelt es sich um eine ausführbare Datei.

6. Doppelklicken Sie auf einem mit dem Internet verbundenen Gerät auf die exe-Datei, um das Setup auszuführen, und durchlaufen Sie den Assistenten, um die Lizenzbedingungen zu akzeptieren, betroffene Features zu überprüfen und den Fortschritt zu überwachen

7. Auf einem Server ohne Internet Konnektivität:

   + Sie erhalten entsprechende CAB-Dateien für R und python. Download Links finden Sie unter [CAB-Downloads für kumulative Updates auf SQL Server in-Database-Analyse Instanzen](sql-ml-cab-downloads.md).

   + Übertragen Sie alle Dateien, die ausführbare Hauptdatei und die CAB-Dateien, in einen Ordner auf dem Offline Computer.

   + Doppelklicken Sie auf die exe-Datei, um das Setup auszuführen. Wenn Sie ein kumulationsupdate auf einem Server ohne Internetverbindung installieren, werden Sie aufgefordert, den Speicherort der CAB-Dateien für R und python auszuwählen.

8. Bearbeiten Sie nach der Installation auf einem Server, für den Sie die Operationalisierung mit webknoten und Computeknoten aktiviert haben, **appSettings. JSON**, und fügen Sie den Eintrag "mmlresourcepath" direkt unter "mmlnativepath" hinzu:

    ```json
    "ScorerParameters": {
        "MMLNativePath": "C:\Program Files\Microsoft SQL Server\140\R_SERVER\library\MicrosoftML\mxLibs\x64\",
        "MMLResourcePath": "C:\Program Files\Microsoft SQL Server\140\R_SERVER\library\MicrosoftML\mxLibs\x64\"
    }
    ```

9. [Führen Sie das CLI-Hilfsprogramm admin](https://docs.microsoft.com/machine-learning-server/operationalize/configure-admin-cli-launch) aus, um die Web-und Compute-Knoten neu Schritte und die Syntax finden Sie unter [überwachen, starten und Abbrechen von Web-und Compute-Knoten](https://docs.microsoft.com/machine-learning-server/operationalize/configure-admin-cli-stop-start).

## <a name="development-tools"></a>Entwicklungs Tools

Eine Entwicklungs-IDE wird nicht als Teil des-Setups installiert. Weitere Informationen zum Konfigurieren einer Entwicklungsumgebung finden Sie unter [Einrichten von R-Tools](../r/set-up-a-data-science-client.md) und [Einrichten von python-Tools](../python/setup-python-client-tools-sql.md).

## <a name="next-steps"></a>Nächste Schritte

R-Entwickler können mit einigen einfachen Beispielen beginnen und die Grundlagen der Funktionsweise von R mit SQL Server kennenlernen. Informationen zu den nächsten Schritten finden Sie unter den folgenden Links:

+ [Tutorial: Ausführen von R in T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [Tutorial: Daten bankübergreifende Analysen für R-Entwickler](../tutorials/sqldev-in-database-r-for-sql-developers.md)

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
Python-Entwickler können mit den folgenden Tutorials erfahren, wie Sie python mit SQL Server verwenden:

+ [Tutorial: Ausführen von python in T-SQL](../tutorials/run-python-using-t-sql.md)
+ [Tutorial: Daten bankübergreifende Analysen für python-Entwickler](../tutorials/sqldev-in-database-python-for-sql-developers.md)
::: moniker-end

Beispiele für Machine Learning, die auf realen Szenarios basieren, finden Sie unter [Machine Learning-Tutorials](../tutorials/machine-learning-services-tutorials.md).
