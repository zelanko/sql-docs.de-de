---
title: Installieren von Machine Learning Server (eigenständig)
description: In diesem Artikel erfahren Sie, wie Sie einen eigenständigen Machine Learning-Server für Python und R einrichten. Ein per SQL Server-Setup installierter, eigenständiger Server stimmt funktionell mit nicht-SQL-Versionen von Microsoft Machine Learning Server überein.
ms.prod: sql
ms.technology: machine-learning
ms.date: 01/03/2020
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: e614579b3d4e64a73e5896c1be946cdb38d21dcf
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2020
ms.locfileid: "81118313"
---
# <a name="install-machine-learning-server-standalone-or-r-server-standalone-using-sql-server-setup"></a>Installieren von Machine Learning Server (eigenständig) oder R Server (Standalone) mithilfe des SQL Server-Setups
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
Das SQL Server-Setup umfasst eine Option für **freigegebene Features** zum Installieren eines eigenständigen Machine Learning-Servers, der außerhalb von SQL Server ausgeführt wird. Dieses Feature heißt **Machine Learning Server (eigenständig)** und umfasst R und Python. 
::: moniker-end
::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Das SQL Server-Setup umfasst eine Option für **freigegebene Features** zum Installieren eines eigenständigen Machine Learning-Servers, der außerhalb von SQL Server ausgeführt wird. In SQL Server 2016 heißt dieses Feature **R Server (Standalone)** .  
::: moniker-end

Ein per SQL Server-Setup installierter eigenständiger Server stimmt funktionell mit nicht-SQL-Versionen von [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/what-is-machine-learning-server) überein und unterstützt dieselben Anwendungsfälle und Szenarios, einschließlich der folgenden:

+ Remoteausführung mit Wechsel zwischen der lokalen und der Remotesitzung in derselben Konsole
+ Operationalisierung mit Web- und Computeknoten
+ Webdienstbereitstellung: die Möglichkeit wird geboten, R- und Python-Skripts in Webdienste einzufügen.
+ Eine vollständige Sammlung der R- und Python-Funktionsbibliotheken

Da es sich um einen von SQL Server getrennten unabhängigen Server handelt, erfolgen Konfiguration, Sicherung und Zugriff auf R- und Python-Umgebungen mithilfe des zugrunde liegenden Betriebssystems und der Tools des eigenständigen Servers und nicht mit SQL Server.

Ein eigenständiger Server eignet sich zur Ergänzung von SQL Server, wenn Sie leistungsfähige Machine Learning-Lösungen entwickeln müssen, die Remotecomputekontexte unterstützter Datenplattformen in vollem Umfang ausschöpfen können. Sie können die Ausführung vom lokalen Server auf einen Machine Learning-Remoteserver auf einem Spark-Cluster oder in einer andere SQL Server-Instanz migrieren.

<a name="bkmk_prereqs"> </a>

## <a name="pre-install-checklist"></a>Prüfliste vor der Installation

Wenn Sie eine frühere Version installiert haben, z. B. SQL Server 2016 R Server (Standalone) oder Microsoft R Server, deinstallieren Sie diese vorhandene Installation, bevor Sie fortfahren.

Grundsätzlich wird empfohlen, dass Sie instanzabhängige eigenständige Server- und Datenbank-Engine-Installationen als sich gegenseitig ausschließend behandeln, um Ressourcenkonflikte zu vermeiden. Wenn Sie jedoch über ausreichende Ressourcen verfügen, spricht nichts dagegen, beide Installationen auf dem gleichen physischen Computer zu installieren.

Sie können nur über einen eigenständigen Server auf einem Computer verfügen: entweder SQL Server Machine Learning Server (eigenständig) oder SQL Server R Server (Standalone). Stellen Sie sicher, dass Sie eine Version deinstallieren, bevor Sie eine neue hinzufügen.

::: moniker range="=sql-server-2016"
<a name="bkmk_ga_instalpatch"></a> 

 ###  <a name="install-patch-requirement"></a>Installieren einer Patchanforderung 

Nur für SQL Server 2016: Microsoft hat ein Problem bei der speziellen Version von Microsoft VC++ 2013 Runtime-Binärdateien erkannt, die von SQL Server als vorausgesetzte Komponenten installiert werden. Wenn dieses Update an den VC++ Runtime-Binärdateien nicht installiert wird, können bei SQL Server in bestimmten Szenarios Stabilitätsprobleme auftreten. Bevor Sie SQL Server installieren, sollten Sie entsprechend den Anweisungen unter [Versionsanmerkungen zu SQL Server](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch) vorgehen, um festzustellen, ob Ihr Computer einen Patch für die VC-Runtime-Binärdateien benötigt.  
::: moniker-end

## <a name="get-the-installation-media"></a>Abrufen der Installationsmedien

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
## <a name="run-setup"></a>Ausführen von 'Setup'

Bei lokalen Installationen müssen Sie das Setup als Administrator ausführen. Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von einer Remotefreigabe installieren, müssen Sie ein Domänenkonto verwenden, das Lese- und Ausführungsberechtigungen auf der Remotefreigabe hat.

1. Starten Sie den Installations-Assistenten.

2. Wählen Sie die Registerkarte **Installation** und dann **Neue Installation von Machine Learning Server (eigenständig)** aus.
    
   ::: moniker-end
   ::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
   ![Installieren von Machine Learning Server (eigenständig)](media/2017setup-installation-page-mlsvr.png "Beginnen der Installation von Machine Learning Server (eigenständig)")
   ::: moniker-end
   ::: moniker range="=sql-server-ver15||=sqlallproducts-allversions"
   ![Installieren von Machine Learning Server (eigenständig)](media/2019setup-installation-page-mlsvr.png "Beginnen der Installation von Machine Learning Server (eigenständig)")
   ::: moniker-end
   ::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"

3. Akzeptieren Sie nach Abschluss der Regelüberprüfung die SQL Server-Lizenzbedingungen, und wählen Sie eine neue Installation aus.

4. Auf der Seite **Featureauswahl** sollten die folgenden Optionen bereits aktiviert sein:

    - **Microsoft Machine Learning Server (eigenständig)**

    - **R** und **Python** sind beide standardmäßig ausgewählt. Sie können beide Sprachen abwählen, jedoch wird empfohlen, dass Sie mindestens eine der unterstützten Sprachen installieren.

   ::: moniker-end
   ::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
   ![Auswählen der R- oder Python-Features](media/2017setup-features-page-mlsvr-rpy.png "Beginnen der Installation von Machine Learning Server (eigenständig)")
   ::: moniker-end
   ::: moniker range="=sql-server-ver15||=sqlallproducts-allversions"
   ![Auswählen der R- oder Python-Features](media/2019setup-features-page-mlsvr-rpy.png "Beginnen der Installation von Machine Learning Server (eigenständig)")
   ::: moniker-end
   ::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
    
   Alle anderen Optionen sollten ignoriert werden. 
    
   > [!NOTE]
   > Vermeiden Sie es, die **freigegebenen Features** zu installieren, wenn Machine Learning Services für datenbankinterne SQL Server-Analysen bereits auf dem Computer installiert ist. Dadurch werden Bibliotheken doppelt erstellt.
   > 
   > Obwohl R- und Python-Skripts, die in SQL Server ausgeführt werden, von SQL Server verwaltet werden, damit keine Konflikte mit von anderen Datenbank-Engine-Diensten genutztem Arbeitsspeicher entstehen, bestehen keine solche Einschränkungen für Skripts auf eigenständigen Machine Learning-Servern, und sie können andere Datenbankvorgänge beeinträchtigen. Letztlich wird der Remotezugriff über eine RDP-Sitzung, der oft für die Operationalisierung verwendet wird, standardmäßig von Datenbankadministratoren blockiert.
   > 
   > Aus diesen Gründen wird im Allgemeinen empfohlen, dass Sie Machine Learning Server (eigenständig) auf einem anderen Computer als SQL Server-Machine Learning Services installieren.

5. Akzeptieren Sie die Lizenzbedingungen für das Herunterladen und Installieren von Basissprachverteilungen. Wenn die Schaltfläche **Annehmen** deaktiviert wird, können Sie auf **Weiter**klicken. 

6. Überprüfen Sie Ihre Auswahl auf der Seite **Installationsbereit** , und klicken Sie anschließend auf **Installieren**.
::: moniker-end

::: moniker range="=sql-server-2016"
## <a name="run-setup"></a>Ausführen von 'Setup'

Bei lokalen Installationen müssen Sie das Setup als Administrator ausführen. Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von einer Remotefreigabe installieren, müssen Sie ein Domänenkonto verwenden, das Lese- und Ausführungsberechtigungen auf der Remotefreigabe hat.

1. Starten Sie den Installations-Assistenten.

2. Klicken Sie auf der Registerkarte **Installation** auf **Neue R Server-Installation (Standalone)** .
    
   ![Starten des Setups von R Server (Standalone)](media/2016-setup-installation-rsvr.png "Starten des Setups von R Server (Standalone)")

3. Akzeptieren Sie nach Abschluss der Regelüberprüfung die SQL Server-Lizenzbedingungen, und wählen Sie eine neue Installation aus.

4. Auf der Seite **Feature selection** (Funktionsauswahl) sollte die folgende Option bereits aktiviert sein:
    
   - **R Server (eigenständig)**  
    
   ![Featureauswahl für R Server (Standalone)](media/2016setup-rserver-features.png "Featureauswahl für R Server (Standalone)")
    
   Alle anderen Optionen können ignoriert werden. 
    
   > [!NOTE]
   > Vermeiden Sie es, die **freigegebenen Features** zu installieren, wenn Sie das Setup auf einem Computer durchführen, auf dem R Services für datenbankinterne SQL Server-Analysen bereits installiert ist. Dadurch werden Bibliotheken doppelt erstellt.
   > 
   > Obwohl R-Skripts, die in SQL Server ausgeführt werden, von SQL Server verwaltet werden, damit keine Konflikte mit von anderen Datenbank-Engine-Diensten genutztem Arbeitsspeicher entstehen, bestehen keine solche Einschränkungen für Skripts auf eigenständigen R-Servern, und sie können andere Datenbankvorgänge beeinträchtigen.
   > 
   > Im Allgemeinen wird empfohlen, dass Sie R Server (Standalone) auf einem anderen Computer als SQL Server R Services (datenbankintern) installieren.

5. Akzeptieren Sie die Lizenzbedingungen für das Herunterladen und Installieren von Basissprachverteilungen. Wenn die Schaltfläche **Annehmen** deaktiviert wird, können Sie auf **Weiter**klicken. 

6. Überprüfen Sie Ihre Auswahl auf der Seite **Installationsbereit** , und klicken Sie anschließend auf **Installieren**.
::: moniker-end

## <a name="set-environment-variables"></a>Festlegen von Umgebungsvariablen

Wenn Sie nur das R-Feature integrieren möchten, sollten Sie die Umgebungsvariable **MKL_CBWR** über die Intel Math Kernel Library-Berechnungen auf [ensure consistent output](https://software.intel.com/articles/introduction-to-the-conditional-numerical-reproducibility-cnr) (Konsistente Ausgabe sicherstellen) festlegen.

1. Klicken Sie in der Systemsteuerung auf **System und Sicherheit** > **System** > **Erweiterte Systemeinstellungen** > **Umgebungsvariablen**.

2. Erstellen Sie eine neue Benutzer- oder Systemvariable. 

  + Legen Sie den Variablenname auf `MKL_CBWR` fest.
  + Legen Sie den Variablenwert auf `AUTO` fest.

3. Starten Sie den Server neu.

<a name="install-path"></a>

### <a name="default-installation-folders"></a>Standardinstallationsordner

Bei der R- und Python-Entwicklung ist es üblich, dass mehrere Versionen auf demselben Computer vorhanden sind. Bei der Installation mit dem SQL Server-Setup wird die Basisverteilung in einem Ordner installiert, der mit der SQL Server-Version verknüpft ist, die Sie für das Setup verwendet haben.

In der folgenden Tabelle werden die Pfade für R- und Python-Verteilungen aufgeführt, die von Microsoft-Installationsprogrammen erstellt werden. Der Vollständigkeit halber enthält die Tabelle Pfade, die vom SQL Server-Setup und vom eigenständigen Installationsprogramm für Microsoft Machine Learning Server generiert werden.

|Version| Installationsmethode | Standardordner|
|----|----|----|
|SQL Server 2019 Machine Learning Server (eigenständig) |  SQL Server 2019-Setup-Assistent |`C:\Program Files\Microsoft SQL Server\150\R_SERVER` <br/>`C:\Program Files\Microsoft SQL Server\150\PYTHON_SERVER`|
|SQL Server 2017 Machine Learning Server (eigenständig) |  SQL Server 2017-Setup-Assistent |`C:\Program Files\Microsoft SQL Server\140\R_SERVER` <br/>`C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`|
|Microsoft Machine Learning Server (eigenständig) |  Eigenständiges Windows.Installationsprogramm |`C:\Program Files\Microsoft\ML Server\R_SERVER`<br/>`C:\Program Files\Microsoft\ML Server\PYTHON_SERVER`|
|SQL Server-Machine Learning Services (datenbankintern) |SQL Server 2019-Setup-Assistent mit R-Sprachoption|`C:\Program Files\Microsoft SQL Server\MSSQL15.<instance_name>\R_SERVICES`  <br/>`C:\Program Files\Microsoft SQL Server\MSSQL15.<instance_name>\PYTHON_SERVICES` |
|SQL Server-Machine Learning Services (datenbankintern) |SQL Server 2017-Setup-Assistent mit R-Sprachoption|`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES`  <br/>`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\PYTHON_SERVICES` |
|SQL Server 2016 R Server (Standalone) |  SQL Server 2016-Setup-Assistent |`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|SQL Server 2016 R Services (datenbankintern) |SQL Server 2016-Setup-Assistent|`C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\R_SERVICES`|

<a name="apply-cu"></a>

## <a name="apply-updates"></a>Anwenden von Updates

Es wird empfohlen, dass Sie das neueste kumulative Update sowohl auf die Datenbank-Engine als auch auf die Machine Learning-Komponenten anwenden. Kumulative Updates werden über das Setupprogramm installiert. 

Auf mit dem Internet verbundenen Geräten können Sie eine sich selbst entpackende ausführbare Datei herunterladen. Beim Durchführen von Updates für die Datenbank-Engine werden kumulative Updates für vorhandene R- und Python-Features automatisch abgerufen. 

Auf getrennten Servern sind zusätzliche Schritte erforderlich. Sie müssen das kumulative Update für die Datenbank-Engine sowie für die CAB-Dateien für Machine Learning-Features selbstständig abrufen. Alle Dateien müssen manuell auf den isolierten Server übertragen und angewendet werden.

1. Beginnen Sie mit einer Baselineinstanz. Sie können kumulative Updates nur auf vorhandene Installationen anwenden:

  + Machine Learning Server (eigenständig) aus dem ursprünglichen Release von SQL Server 2019
  + Machine Learning Server (eigenständig) aus dem ursprünglichen Release von SQL Server 2017
  + R Server (Standalone) aus dem ursprünglichen Release von SQL Server 2016, SQL Server 2016 SP1 oder SQL Server 2016 SP2

2. Schließen Sie alle offenen R- oder Python-Sitzungen, und beenden Sie alle Prozesse, die noch auf dem System ausgeführt werden.

3. Wenn Sie die Ausführung der Operationalisierung als Web- und Computeknoten für Webdienstbereitstellungen aktiviert haben, legen Sie vorsichtshalber eine Sicherung der Datei **AppSettings.json** an. Durch Anwendung von SQL Server 2017 CU13 wird diese Datei überarbeitet, daher sollten Sie möglicherweise eine Sicherungskopie anlegen, um die ursprüngliche Version beizubehalten.

4. Laden Sie auf einem mit dem Internet verbundenen Computer das neueste kumulative Update für Ihre Version von der Website [Neueste Updates für Microsoft SQL Server](https://docs.microsoft.com/sql/database-engine/install-windows/latest-updates-for-microsoft-sql-server) herunter.

5. Laden Sie das neueste kumulative Update herunter. Dabei handelt es sich um eine ausführbare Datei.

6. Doppelklicken Sie auf einem mit dem Internet verbundenen Gerät auf die EXE-Datei, um das Setup auszuführen und den Assistenten zu durchlaufen, um die Lizenzbedingungen zu akzeptieren, betroffene Features zu überprüfen und den Fortschritt bis zum Abschluss zu überwachen.

7. Vorgehensweise für Server ohne Internetverbindung:

   + Rufen Sie entsprechende CAB-Dateien für R und Python ab. Downloadlinks finden Sie unter [CAB-Dateidownloads für kumulative Updates für SQL Server-Instanzen für datenbankinterne Analysen](sql-ml-cab-downloads.md).

   + Übertragen Sie alle Dateien, die ausführbare Hauptdatei und CAB-Dateien, in einen Ordner auf dem Offlinecomputer.

   + Doppelklicken Sie auf die EXE-Datei, um das Setup auszuführen. Beim Installieren eines kumulativen Updates auf einem Server ohne Internetverbindung werden Sie dazu aufgefordert, den Speicherort der CAB-Dateien für R und Python auszuwählen.

8. Bearbeiten Sie nach der Installation die Datei **AppSettings.json** auf einem Server, für den Sie die Bereitstellung mit Web- und Computeknoten aktiviert haben, und fügen Sie einen Eintrag „MMLResourcePath“ direkt unter „MMLNativePath“ hinzu. Beispiel:

    ```json
    "ScorerParameters": {
        "MMLNativePath": "C:\Program Files\Microsoft SQL Server\140\R_SERVER\library\MicrosoftML\mxLibs\x64\",
        "MMLResourcePath": "C:\Program Files\Microsoft SQL Server\140\R_SERVER\library\MicrosoftML\mxLibs\x64\"
    }
    ```

9. [Führen Sie das Hilfsprogramm für die Administrator-CLI aus](https://docs.microsoft.com/machine-learning-server/operationalize/configure-admin-cli-launch), um die Web- und Computeknoten neu zu starten. Informationen zu den Schritten und der Syntax finden Sie unter [Überwachen, Starten und Stoppen von Web- und Computeknoten](https://docs.microsoft.com/machine-learning-server/operationalize/configure-admin-cli-stop-start).

## <a name="development-tools"></a>Entwicklungstools

Im Rahmen des Setups wird keine integrierte Entwicklungsumgebung installiert. Weitere Informationen zum Konfigurieren einer Entwicklungsumgebung finden Sie unter [Einrichten von R-Tools](../r/set-up-a-data-science-client.md) und [Einrichten von Python-Tools](../python/setup-python-client-tools-sql.md).

## <a name="next-steps"></a>Nächste Schritte

R-Entwickler können mit einigen einfachen Beispielen loslegen und die Grundlagen der Funktionen von R unter SQL Server kennenlernen. Informationen zu den nächsten Schritten finden Sie unter den folgenden Links:

+ [Schnellstart: Ausführen von R in T-SQL](../tutorials/quickstart-r-create-script.md)
+ [Tutorial: Datenbankinterne Analysen für R-Entwickler](../tutorials/sqldev-in-database-r-for-sql-developers.md)

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
Python-Entwickler können in den folgenden Tutorials erfahren, wie Python mit SQL Server verwendet werden kann:

+ [Python-Tutorial: Bereitstellen eines linearen Regressionsmodells in SQL Server Machine Learning Services](../tutorials/python-ski-rental-linear-regression-deploy-model.md)
+ [Python-Tutorial: Kategorisieren von Kunden mithilfe von K-Means-Clustering mit SQL Server Machine Learning Services](../tutorials/python-clustering-model.md)
::: moniker-end