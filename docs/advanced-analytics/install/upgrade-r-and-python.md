---
title: Aktualisieren von R-und python-Komponenten
description: Aktualisieren Sie R und python in SQL Server 2016-Diensten oder SQL Server 2017 Machine Learning Services, indem Sie sqlbindr. exe verwenden, um eine Bindung an Machine Learning Server herzustellen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: def007433075920e419f0bf77be5977d1145f793
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344959"
---
# <a name="upgrade-machine-learning-r-and-python-components-in-sql-server-instances"></a>Aktualisieren von Machine Learning-Komponenten (R und python) in SQL Server Instanzen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Die Integration von R und python in SQL Server umfasst Open Source-und Microsoft-proprietäre Pakete. Bei der Standard SQL Server Wartung werden Pakete gemäß dem SQL Server releasecycle aktualisiert, wobei Fehlerbehebungen für vorhandene Pakete mit der aktuellen Version, aber keine größeren Versions Upgrades ausgeführt werden. 

Viele Datenanalysten sind jedoch daran gewöhnt, mit neueren Paketen zu arbeiten, sobald Sie verfügbar werden. Sowohl für SQL Server 2017 Machine Learning Services (in-Database) als auch für SQL Server 2016 R Services (in-Database) können Sie [neuere Versionen von R und python](#version-map) durch *binden* an **Microsoft Machine Learning Server**erhalten. 

## <a name="what-is-binding"></a>Was ist Bindung?

Die Bindung ist ein Installationsvorgang, bei dem der Inhalt Ihrer R_SERVICES-und PYTHON_SERVICES-Ordner mit neueren ausführbaren Dateien, Bibliotheken und Tools aus [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/index)ausgecheckt wird.

Zusammen mit aktualisierten Komponenten ist ein Switch in den Wartungs Modellen. Anstelle des [SQL Server Produktlebenszyklus](https://support.microsoft.com/lifecycle/search?alpha=SQL%20Server%202017)mit [SQL Server kumulativen Updates](https://support.microsoft.com/help/4047329/sql-server-2017-build-versions)entsprechen die Dienst Updates jetzt der [Support Zeitachse für Microsoft R Server & Machine Learning Server](https://docs.microsoft.com/machine-learning-server/resources-servicing-support) im [modernen Lebenszyklus](https://support.microsoft.com/help/30881/modern-lifecycle-policy).

Mit Ausnahme von Komponenten Versionen und Dienst Updates ändert die Bindung nicht die Grundlagen der Installation: Die Integration von R und Python ist weiterhin Teil einer Datenbank-Engine-Instanz, die Lizenzierung bleibt unverändert (keine zusätzlichen Kosten im Zusammenhang mit der Bindung), und SQL Server Support Richtlinien bleiben weiterhin für die Datenbank-Engine. Im weiteren Verlauf dieses Artikels werden der Bindungs Mechanismus und seine Funktionsweise für jede Version von SQL Server erläutert.

> [!NOTE]
> Die Bindung gilt nur für Instanzen in der Datenbank, die an SQL Server Instanzen gebunden sind. Die Bindung ist für eine (eigenständige) Installation nicht relevant.

**Überlegungen zur SQL Server 2017-Bindung**

Bei SQL Server 2017 Machine Learning Services sollten Sie nur eine Bindung in Erwägung gezogen, wenn Microsoft Machine Learning Server zusätzliche Pakete oder neuere Versionen bereitstellt, die bereits vorhanden sind.

**Überlegungen zur SQL Server 2016-Bindung**

Bei SQL Server 2016 R Services-Kunden stellt die Bindung aktualisierte r-Pakete bereit, neue Pakete sind nicht Teil der ursprünglichen Installation ([microsoftml](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)) und [vorab trainierte Modelle](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models), die alle in jeder neuen Haupt-und neben Version von aktualisiert werden können. [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/index). Die Bindung bietet keine python-Unterstützung, was eine SQL Server 2017-Funktion ist. 

<a name="version-map"></a>

## <a name="version-map"></a>Versions Zuordnung

In der folgenden Tabelle finden Sie eine Versions Zuordnung, in der Paketversionen für releasefahrzeuge angezeigt werden, damit Sie mögliche Upgradepfade bei der Bindung an Microsoft Machine Learning Server (früher als R Server bezeichnet) bei der Bindung an (früher als "" bezeichnet) zum in MLS 9.2.1). 

Beachten Sie, dass die Bindung nicht die neueste Version von R oder Anaconda garantiert. Wenn Sie eine Bindung an Microsoft Machine Learning Server (MLS) herstellen, wird die R-oder python-Version über das-Setup installiert. Dies ist möglicherweise nicht die neueste Version, die im Web verfügbar ist.

[**SQL Server 2016 R-Dienste**](../install/sql-r-services-windows-install.md)

Komponente |Anfängliche Version | [R Server 9.0.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) | [R Server 9,1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) | [MLS 9.2.1](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) | [MLS 9,3](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) |
----------|----------------|----------------|--------------|---------|-------|
Microsoft r Open (MRO) über R | R 3.2.2     | R 3.3.2   |R 3.3.3   | R 3.4.1  | R 3.4.3 |
[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) | 8.0.3  | 9.0.1 |  9,1 |  9.2.1 |  9,3 |
[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)| Niederländische Antillen | 9.0.1 |  9,1 |  9.2.1 |  9,3 |
[vorab trainierte Modelle](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models)| Niederländische Antillen | 9.0.1 |  9,1 |  9.2.1 |  9,3 |
[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)| Niederländische Antillen | 1,0 |  1,0 |  1,0 |  1,0 |
[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | Niederländische Antillen | 1,0 |  1,0 |  1,0 |  1,0 |


[**SQL Server 2017 Machine Learning Services**](../install/sql-machine-learning-services-windows-install.md)

Komponente |Anfängliche Version | MLS 9,3 | | | |
----------|----------------|---------|-|-|-|-|
Microsoft r Open (MRO) über R | R 3.3.3 | R 3.4.3 | | | |
[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) |   9,2 |  9,3 | | | |
[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) | 9,2  | 9,3| | | |
[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)| 1,0 |  1,0 | | | |
[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | 1,0 |  1,0 | | | |
Anaconda 4,2 über python 3,5  | 4.2/3.5.2 | 4.2/3.5.2 | | | |
[revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9,2  | 9,3| | | |
 [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9,2  | 9,3| | | |
[vorab trainierte Modelle](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models) | 9,2 | 9,3| | | |

## <a name="how-component-upgrade-works"></a>Funktionsweise des Komponenten Upgrades 

R-und python-Bibliotheken und ausführbare Dateien werden aktualisiert, wenn Sie eine vorhandene Installation von R und python an Machine Learning Server binden. Die Bindung wird vom [Microsoft Machine Learning Server Installations](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) Programm ausgeführt, wenn Sie das Setup für eine vorhandene SQL Server Datenbank-Engine-Instanz ausführen, entweder 2016 oder 2017, mit R-oder python-Integration. Setup erkennt die vorhandenen Funktionen und fordert Sie zur erneuten Bindung an Machine Learning Server auf. 

Während der Bindung der Inhalt von c:\Programme\Microsoft SQL server\mssql14. MSSQLSERVER\R_SERVICES und \PYTHON_SERVICES werden mit den neueren ausführbaren Dateien und Bibliotheken von c:\programme\microsoft\ml Server\R_SERVER und \PYTHON_SERVER. überschrieben.

Gleichzeitig wird auch das Wartungs Modell von SQL Server Aktualisierungs Mechanismen in den häufigeren Haupt-und neben Versions Zyklen Microsoft Machine Learning Server gekippt. Das Wechseln von Unterstützungs Richtlinien ist eine attraktive Option für Data Science Teams, die R-und Python-Module der neueren Generation für ihre Lösungen benötigen. 

+ Ohne Bindung werden R-und Python-Pakete für Fehlerbehebungen gepatcht, wenn Sie eine SQL Server Service Pack oder ein kumulatives Update (Cu) installieren. 
+ Mit der Bindung können neuere Paketversionen unabhängig vom Cu-releasezeitplan in der [modernen Lebenszyklus Richtlinie](https://support.microsoft.com/help/30881/modern-lifecycle-policy) und den Releases von Microsoft Machine Learning Server auf Ihre Instanz angewendet werden. Die Support Richtlinie "Modern Lifecycle" bietet häufigere Updates für eine kürzere, einjährige Lebensdauer. Nach der Bindung verwenden Sie den MLS-Installer weiterhin für zukünftige Updates von R und Python, da diese auf Microsoft-Download Websites verfügbar werden.

Die Bindung gilt nur für R-und python-Features. Open-Source-Pakete für R-und Python-Funktionen (Microsoft R Open, Anaconda) und die proprietären Pakete revoscaler, revoscalepy usw. Durch die Bindung wird das Unterstützungs Modell für die Instanz der Datenbank-Engine nicht geändert, und die Version von SQL Server wird nicht geändert.

Die Bindung ist rückgängig. Sie können SQL Server Wartung wiederherstellen, indem Sie [die Bindung der Instanz](#bkmk_Unbind) aufheben und Ihre SQL Server Datenbank-Engine-Instanz neu zuweisen.

Zusammengefasst sind die Schritte für die Bindung wie folgt:

+ Beginnen Sie mit einer vorhandenen, konfigurierten Installation von SQL Server 2016 R Services (oder SQL Server 2017 Machine Learning Services).
+ Bestimmen Sie, welche Version von Microsoft Machine Learning Server die aktualisierten Komponenten enthält, die Sie verwenden möchten.
+ Sie können das Setup für diese Version herunterladen und ausführen. Setup erkennt die vorhandene Instanz, fügt eine Bindungs Option hinzu und gibt eine Liste der kompatiblen Instanzen zurück.
+ Wählen Sie die Instanz aus, die Sie binden möchten, und beenden Sie dann das Setup, um die Bindung auszuführen.

Im Hinblick auf die Benutzer Darstellung ist die Technologie und die Art und Weise, wie Sie damit arbeiten, unverändert. Der einzige Unterschied besteht darin, dass Pakete mit neueren Versionen und möglicherweise zusätzliche Pakete vorhanden sind, die ursprünglich nicht über SQL Server verfügbar waren (z. b. microsoftml für SQL Server 2016 R Services-Kunden).

## <a name="bkmk_BindWizard"></a>Binden an MLS mithilfe von Setup

Microsoft Machine Learning Setup erkennt die vorhandenen Features und SQL Server Version und ruft ein Hilfsprogramm mit dem Namen sqlbindr. exe auf, um die Bindung zu ändern. Intern wird sqlbindr mit dem Setup verkettet und indirekt verwendet. Später können Sie sqlbindr direkt von der Befehlszeile aus anrufen, um bestimmte Optionen zu üben.

1. Führen `SELECT @@version` Sie in SSMS aus, um sicherzustellen, dass der Server die Mindestanforderungen für den Build erfüllt 

   Bei SQL Server 2016 R-Diensten ist das Minimalwert [Service Pack 1](https://www.microsoft.com/download/details.aspx?id=54276) und [CU3](https://support.microsoft.com/help/4019916/cumulative-update-3-for-sql-server-2016-sp1).

1. Überprüfen Sie die Version der R-Basis-und revoscaler-Pakete, um zu bestätigen, dass die vorhandenen Versionen niedriger sind, als Sie durch Sie ersetzt werden sollen. Bei SQL Server 2016 r-Diensten ist das R-Basispaket 3.2.2, und revoscaler ist 8.0.3.

    ```sql
    EXECUTE sp_execute_external_script
    @language=N'R'
    ,@script = N'str(OutputDataSet);
    packagematrix <- installed.packages();
    Name <- packagematrix[,1];
    Version <- packagematrix[,3];
    OutputDataSet <- data.frame(Name, Version);'
    , @input_data_1 = N''
    WITH RESULT SETS ((PackageName nvarchar(250), PackageVersion nvarchar(max) ))
    ```

1. Schließen Sie SSMS und alle anderen Tools, die über eine geöffnete Verbindung zum SQL Server verfügen. Die Bindung überschreibt Programmdateien. Wenn SQL Server Sitzungen geöffnet hat, schlägt die Bindung mit dem Bindungs Fehlercode 6 fehl.

1. Laden Sie Microsoft Machine Learning Server auf den Computer herunter, auf dem sich die zu Aktualisier Ende Instanz befindet. Wir empfehlen die [neueste Version](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer).

1. Entpacken Sie den Ordner, und starten Sie die Datei "Serversetup. exe" unter MLSWIN93.

   ![Setup-Assistent für Microsoft Machine Learning Server](media/mls-921-installer-start.PNG)

1. Bestätigen Sie unter **Konfiguration der Installation**die zu aktualisierenden Komponenten, und überprüfen Sie die Liste der kompatiblen Instanzen. 

   Dieser Schritt ist sehr wichtig.

   Wählen Sie auf der linken Seite alle Features aus, die Sie beibehalten oder aktualisieren möchten. Einige Features können nicht aktualisiert werden. Ein leeres Kontrollkästchen entfernt dieses Feature, vorausgesetzt, es ist zurzeit installiert. Im Screenshot ist eine Instanz von SQL Server 2016 r Services (MSSQL13), r und der r-Version der vorab trainierten Modelle ausgewählt. Diese Konfiguration ist gültig, da SQL Server 2016 R, aber nicht python unterstützt.

   Wenn Sie ein Upgrade von Komponenten auf SQL Server 2016 R Services durchführen, wählen Sie die python-Funktion nicht aus. Sie können SQL Server 2016 R-Diensten python nicht hinzufügen.

   Aktivieren Sie auf der rechten Seite das Kontrollkästchen neben dem Instanznamen. Wenn keine Instanzen aufgelistet sind, haben Sie eine nicht kompatible Kombination. Wenn Sie keine Instanz auswählen, wird eine neue eigenständige Installation von Machine Learning Server erstellt, und die SQL Server Bibliotheken sind unverändert. Wenn Sie keine Instanz auswählen können, befindet Sie sich möglicherweise nicht bei [SP1 CU3](https://support.microsoft.com/help/4019916/cumulative-update-3-for-sql-server-2016-sp1). 

    ![Installationsschritt konfigurieren](media/mls-931-installer-mssql13.png)

1. Wählen Sie auf der Seite **Lizenzvertrag** die Option **Ich akzeptiere diese Bedingungen** aus, um die Lizenzbedingungen für Machine Learning Server zu akzeptieren. 

1. Geben Sie auf aufeinander folgenden Seiten den zusätzlichen Lizenzierungs Bedingungen für alle Open-Source-Komponenten an, die Sie ausgewählt haben, z. b. Microsoft R Open oder die python Anaconda-Distribution.

1. Notieren Sie sich auf der Seite **fast there** den Installationsordner. Der Standardordner ist "\programme\microsoft\ml Server".

    Wenn Sie den Installationsordner ändern möchten, klicken Sie auf **erweitert** , um zur ersten Seite des Assistenten zurückzukehren. Allerdings müssen Sie alle vorherigen Auswahlen wiederholen.

Während des Installationsvorgangs werden alle von SQL Server verwendeten R-oder python-Bibliotheken ersetzt, und Launchpad wird so aktualisiert, dass die neueren Komponenten verwendet werden. Wenn die Instanz zuvor Bibliotheken im Standardordner R_SERVICES verwendet hat, werden diese Bibliotheken nach dem Upgrade entfernt, und die Eigenschaften für den Launchpad-Dienst werden so geändert, dass die Bibliotheken am neuen Speicherort verwendet werden.

Die Bindung wirkt sich auf den Inhalt dieser Ordner aus: C:\Programme\Microsoft SQL server\mssql13. MSSQLSERVER\R_SERVICES\library wird durch den Inhalt von c:\programme\microsoft\ml Server\R_SERVER. ersetzt. Der zweite Ordner und sein Inhalt werden durch Microsoft Machine Learning Server-Setup erstellt. 

Wenn das Upgrade fehlschlägt, überprüfen Sie die [Fehlercodes von sqlbindr](#sqlbindr-error-codes) auf Weitere Informationen.

## <a name="confirm-binding"></a>Bindung bestätigen

Überprüfen Sie die Version von R und revoscaler, um zu bestätigen, dass neuere Versionen vorhanden sind. Verwenden Sie die mit den r-Paketen in der Datenbank-Engine-Instanz verteilte r-Konsole, um Paketinformationen zu erhalten:

```sql
EXECUTE sp_execute_external_script
@language=N'R'
,@script = N'str(OutputDataSet);
packagematrix <- installed.packages();
Name <- packagematrix[,1];
Version <- packagematrix[,3];
OutputDataSet <- data.frame(Name, Version);'
, @input_data_1 = N''
WITH RESULT SETS ((PackageName nvarchar(250), PackageVersion nvarchar(max) ))
```

Bei SQL Server 2016 r-Diensten, die an Machine Learning Server 9,3 gebunden sind, sollte das R-Basispaket 3.4.3 lauten, revoscaler muss 9,3 sein, und Sie sollten außerdem über microsoftml 9,3 verfügen. 

Wenn Sie die vorab trainierten Modelle hinzugefügt haben, werden die Modelle in die microsoftml-Bibliothek eingebettet, und Sie können Sie über microsoftml-Funktionen aufzurufen. Weitere Informationen finden Sie unter [R Samples for microsoftml](https://docs.microsoft.com/machine-learning-server/r/sample-microsoftml).

## <a name="offline-binding-no-internet-access"></a>Offline Bindung (kein Internet Zugriff)

Für Systeme ohne Internetverbindung können Sie die Installer-und CAB-Dateien auf einen mit dem Internet verbundenen Computer herunterladen und dann Dateien auf den isolierten Server übertragen. 

Das Installationsprogramm (Serversetup. exe) umfasst die Microsoft-Pakete (revoscaler, microsoftml, olapr, sqlrutils). Die CAB-Dateien stellen weitere Kernkomponenten bereit. Beispielsweise bietet das CAB "SRO" r Open, die Microsoft-Distribution von Open Source-r.

In den folgenden Anweisungen wird erläutert, wie Sie die Dateien für eine Offline Installation platzieren.

1. Laden Sie den MLS-Installer herunter. Es wird als einzelne ZIP-Datei heruntergeladen. Es wird empfohlen, die [neueste Version](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer)zu installieren, aber Sie können auch [frühere Versionen](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components)installieren.

1. CAB-Dateien herunterladen. Die folgenden Links gelten für die Version 9,3. Wenn Sie frühere Versionen benötigen, finden Sie weitere Links in [R Server 9,1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components). Denken Sie daran, dass python/Anaconda nur einer SQL Server 2017 Machine Learning Services-Instanz hinzugefügt werden kann. Vortrainierte Modelle sind für R und python vorhanden. die CAB-Anwendung stellt Modelle in den von Ihnen verwendeten Sprachen bereit.

    | Feature | Herunterladen |
    |---------|----------|
    | R       | [SRO_3.4.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=867186&clcid=1033) |
    | Python  | [SPO_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859054) | 
    | Vortrainierte Modelle | [MLM_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859053) |

1. Übertragen Sie ZIP-und CAB-Dateien auf den Zielserver.

1. Geben `%temp%` Sie auf dem-Server den Befehl ausführen ein, um den physischen Speicherort des temporären Verzeichnisses zu erhalten. Der physische Pfad variiert je nach Computer, aber er ist `C:\Users\<your-user-name>\AppData\Local\Temp`in der Regel.

1. Platzieren Sie die CAB-Dateien im Ordner "% Temp%".

1. Entpacken Sie das Installationsprogramm.

1. Führen Sie Serversetup. exe aus, und befolgen Sie die Anweisungen auf dem Bildschirm, um die Installation abzuschließen.

## <a name="bkmk_BindCmd"></a>Befehlszeilen Vorgänge

Nachdem Sie Microsoft Machine Learning Server ausgeführt haben, steht ein Befehlszeilenprogramm mit dem Namen sqlbindr. exe zur Verfügung, das Sie für weitere Bindungs Vorgänge verwenden können. Wenn Sie z. b. entscheiden, eine Bindung umzukehren, können Sie entweder das Setup erneut ausführen oder das Befehlszeilen-Hilfsprogramm verwenden. Außerdem können Sie dieses Tool verwenden, um die instanzkompatibilität und-Verfügbarkeit zu überprüfen.

> [!TIP]
> Sie können sqlbindr nicht finden? Sie haben das Setup wahrscheinlich nicht ausgeführt. Sqlbindr ist nur nach dem Ausführen Machine Learning Server Setup verfügbar.

1. Öffnen Sie als Administrator eine Eingabeaufforderung und navigieren Sie zum Ordner, der „sqlbindr.exe“ enthält. Der Standard Speicherort ist c:\programme\microsoft\mlserver\setup.

2. Geben Sie den folgenden Befehl ein, um eine Liste der verfügbaren Instanzen anzuzeigen: `SqlBindR.exe /list`
  
   Merken Sie sich den vollständigen aufgelisteten Namen der Instanz. Der Instanzname könnte beispielsweise MSSQL14 lauten. MSSQLSERVER für eine Standard Instanz oder etwas ähnliches wie Servername. MYNAMEDINSTANCE.

3. Führen Sie den Befehl **sqlbindr. exe** mit dem */Bind* -Argument aus, und geben Sie den Namen der Instanz an, die aktualisiert werden soll. verwenden Sie dazu den Instanznamen, der im vorherigen Schritt zurückgegeben wurde.

   Geben Sie z. b. Folgendes ein, um die Standard Instanz zu aktualisieren:`SqlBindR.exe /bind MSSQL14.MSSQLSERVER`

4. Wenn das Upgrade abgeschlossen ist, starten Sie den Launchpad-Dienst neu, der einer-Instanz zugeordnet ist, die geändert wurde.

## <a name="bkmk_Unbind"></a>Zurücksetzen oder Aufheben der Bindung einer Instanz

Sie können eine gebundene Instanz in einer Erstinstallation der R-und python-Komponenten wiederherstellen, die mit SQL Server-Setup eingerichtet wurden. Es gibt drei Teile, um auf die SQL Server Wartung zurückzukehren.

+ [Schritt 1: Bindung an Microsoft Machine Learning Server aufheben](#step-1-unbind)
+ [Schritt 2: Wiederherstellen des ursprünglichen Status der Instanz](#step-2-restore)
+ [Schritt 3: Installieren Sie alle Pakete neu, die Sie der Installation hinzugefügt haben.](#step-3-reinstall-packages)

<a name="step-1-unbind"></a> 

### <a name="step-1-unbind"></a>Schritt 1: Bindung

Sie haben zwei Möglichkeiten zum Rollback der Bindung: führen Sie Setup erneut aus, oder verwenden Sie das sqlbindr-Befehlszeilen-Hilfsprogramm.

#### <a name="bkmk_wizunbind"></a>Bindung mithilfe von Setup aufheben

1. Suchen Sie das Installationsprogramm für Machine Learning Server. Wenn Sie das Installationsprogramm entfernt haben, müssen Sie es möglicherweise erneut herunterladen oder von einem anderen Computer kopieren.
2. Stellen Sie sicher, dass Sie das Installationsprogramm auf dem Computer ausführen, auf dem sich die Instanz befindet, deren Bindung Sie aufheben möchten.
2. Das Installationsprogramm identifiziert lokale Instanzen, die Kandidaten für die Bindung sind.
3. Deaktivieren Sie das Kontrollkästchen neben der Instanz, die Sie auf die ursprüngliche Konfiguration zurücksetzen möchten.
4. Akzeptieren Sie den Lizenzvertrag. Sie müssen Ihre Zustimmung zu den Lizenzbedingungen auch bei der Installation von angeben.
5. Klicken Sie auf **Fertig stellen**. Der Prozess dauert eine Weile.

#### <a name="bkmk_cmdunbind"></a>Bindung mithilfe der Befehlszeile aufheben

1. Öffnen Sie eine Eingabeaufforderung, und navigieren Sie zu dem Ordner, der **sqlbindr.exe** enthält, wie im vorherigen Abschnitt beschrieben.

2. Führen Sie den Befehl **SqlBindR.exe** mit dem */unbind*-Argument aus, und geben Sie die Instanz an.

   Mit dem folgenden Befehl wird beispielsweise die Standard Instanz wieder hergestellt:
   
    `SqlBindR.exe /unbind MSSQL14.MSSQLSERVER`

<a name="step-2-restore"></a> 

###  <a name="step-2-repair-the-sql-server-instance"></a>Schritt 2: Reparieren der SQL Server Instanz

Führen Sie SQL Server-Setup aus, um die Datenbank-Engine-Instanz zu reparieren, die über die R-und Vorhandene Updates bleiben erhalten. Wenn Sie jedoch keine SQL Server Wartungsupdates für R-und Python-Pakete verpasst haben, werden diese Patches durch diesen Schritt angewendet.

Alternativ dazu können Sie auch die Datenbank-Engine-Instanz vollständig deinstallieren und erneut installieren und dann alle Dienst Updates anwenden.

<a name="step-3-reinstall-packages"></a> 

### <a name="step-3-add-any-third-party-packages"></a>Schritt 3: Pakete von Drittanbietern hinzufügen

Möglicherweise haben Sie der paketbibliothek andere Open Source-Pakete oder Drittanbieter Pakete hinzugefügt. Da durch Umkehren der Bindung der Speicherort der Standardpaket Bibliothek gewechselt wird, müssen Sie die Pakete in der Bibliothek, die von R und Python verwendet wird, neu installieren. Weitere Informationen finden Sie unter [Standard Pakete](../package-management/default-packages.md), [Installieren neuer R-Pakete](../r/install-additional-r-packages-on-sql-server.md)und [Installieren neuer Python-Pakete](../python/install-additional-python-packages-on-sql-server.md).

## <a name="sqlbindrexe-command-syntax"></a>Sqlbindr. exe-Befehlssyntax

### <a name="usage"></a>Verwendung

`sqlbindr [/list] [/bind <SQL_instance_ID>] [/unbind <SQL_instance_ID>]`

### <a name="parameters"></a>Parameter

|Name|Beschreibung|
|------|------|
|*list*| Zeigt eine Liste aller SQL-Datenbankinstanz-IDs auf dem aktuellen Computer an|
|*bind*| Aktualisiert die angegebene SQL-Datenbankinstanz auf die neueste Version von R Server und stellt sicher, dass die Instanz automatisch zukünftige Upgrades von R Server erhält|
|*unbind*|Die neueste Version von R Server wird auf der angegebenen SQL-Datenbankinstanz deinstalliert, und es wird verhindert, dass zukünftige R Server-Upgrades auf die Instanz angewandt werden|

<a name="sqlbindr-error-codes"><a/>

## <a name="binding-errors"></a>Bindungs Fehler

Der MLS-Installer und sqlbindr geben die folgenden Fehlercodes und Meldungen zurück.

|Fehlercode  | Meldung           | Details               |
|------------|-------------------|-----------------------|
|Bindungs Fehler 0 | OK (Erfolg) | Die Bindung wurde ohne Fehler erfolgreich durchgeführt. |
|Bindungs Fehler 1 | Ungültige Argumente | Syntax Fehler. |
|Bindungs Fehler 2 | Ungültige Aktion | Syntax Fehler. |
|Bindungs Fehler 3 | Ungültige Instanz. | Eine Instanz ist vorhanden, ist aber für die Bindung nicht gültig. |
|Bindungs Fehler 4 | Nicht binable | |
|Bindungs Fehler 5 | Bereits gebunden | Sie haben den *bind* -Befehl ausgeführt, die angegebene Instanz ist aber bereits gebunden. |
|Bindungs Fehler 6 | Fehler beim Binden. | Fehler beim Aufheben der Bindung der Instanz. Dieser Fehler kann auftreten, wenn Sie den MLS-Installer ausführen, ohne Features auszuwählen. Für die Bindung muss sowohl eine MSSQL-Instanz als auch R und python ausgewählt werden, vorausgesetzt, die Instanz ist SQL Server 2017. Dieser Fehler tritt auch auf, wenn sqlbindr nicht in den Ordner "Programme" schreiben konnte. Öffnen Sie Sitzungen oder Handles, um zu SQL Server führt zu diesem Fehler. Wenn Sie diesen Fehler erhalten, starten Sie den Computer neu, und wiederholen Sie die Bindungs Schritte, bevor Sie neue Sitzungen starten.|
|Bindungs Fehler 7 | Nicht gebunden | Die Instanz der Datenbank-Engine verfügt über R Services oder SQL Server Machine Learning Services. Die-Instanz ist nicht an Microsoft Machine Learning Server gebunden. |
|Bindungs Fehler 8 | Fehler beim Aufheben der Bindung | Fehler beim Aufheben der Bindung der Instanz. |
|Bindungs Fehler 9 | Keine Instanzen gefunden | Auf diesem Computer wurden keine Datenbank-Engine-Instanzen gefunden. |

## <a name="known-issues"></a>Bekannte Probleme

In diesem Abschnitt werden bekannte Probleme aufgelistet, die für die Verwendung des Hilfsprogramms sqlbindr. exe spezifisch sind, oder Upgrades von Machine Learning Server, die sich auf SQL Server Instanzen auswirken können.

### <a name="restoring-packages-that-were-previously-installed"></a>Wiederherstellen von zuvor installierten Paketen

Wenn Sie ein Upgrade auf Microsoft R Server 9.0.1 durchgeführt haben, konnte die Version von sqlbindr. exe für diese Version die ursprünglichen Pakete oder R-Komponenten nicht vollständig wiederherstellen. Dies erforderte, dass der Benutzer SQL Server Reparatur auf der Instanz ausführen, alle Dienst Releases anwenden und dann neu starten sollte. die-Instanz.

In einer neueren Version von sqlbindr werden die ursprünglichen r-Features automatisch wieder hergestellt, sodass keine Neuinstallation von r-Komponenten erforderlich ist oder der Server neu patcht werden muss. Sie müssen jedoch alle R-Paket Updates installieren, die möglicherweise nach der Erstinstallation hinzugefügt wurden.

Wenn Sie die Paket Verwaltungs Rollen zum Installieren und Freigeben von Paketen verwendet haben, ist dieser Task viel einfacher: Sie können R-Befehle verwenden, um installierte Pakete mithilfe von Datensätzen in der Datenbank mit dem Dateisystem zu synchronisieren (und umgekehrt). Weitere Informationen finden Sie unter [R Package Management for SQL Server](../r/install-additional-r-packages-on-sql-server.md).

### <a name="problems-with-multiple-upgrades-from-sql-server"></a>Probleme bei mehreren Upgrades von SQL Server

Wenn Sie zuvor eine Instanz von SQL Server 2016 R Services auf 9.0.1 aktualisiert haben, wird beim Ausführen des neuen Installers für Microsoft R Server 9.1.0 eine Liste aller gültigen-Instanzen angezeigt. Standardmäßig werden zuvor gebundene Instanzen ausgewählt. Wenn Sie den Vorgang fortsetzen, wird die Bindung der zuvor gebundenen Instanzen aufgehoben. Daher wird die frühere 9.0.1-Installation entfernt, einschließlich aller zugehörigen Pakete, aber die neue Version von Microsoft R Server (9.1.0) ist nicht installiert.

Um dieses Problem zu umgehen, können Sie die vorhandene R Server Installation wie folgt ändern:
1. Öffnen **Sie**in der Systemsteuerung die Option Software.
2. Suchen Sie Microsoft R Server, und klicken Sie auf **ändern/ändern**.
3. Wenn das Installationsprogramm gestartet wird, wählen Sie die Instanzen aus, die Sie an 9.1.0 binden möchten.

Microsoft Machine Learning Server 9.2.1 und 9,3 liegt dieses Problem nicht vor.

### <a name="binding-or-unbinding-leaves-multiple-temporary-folders"></a>Binden oder Aufheben der Bindung verlässt mehrere temporäre Ordner

Manchmal können die Bindungs-und die Bindungs Vorgänge keine temporären Ordner bereinigen.
Wenn Sie Ordner mit einem Namen wie diesem finden, können Sie Sie nach Abschluss der Installation entfernen: R_SERVICES_<guid>

> [!NOTE]
> Warten Sie, bis die Installation beendet ist. Das Entfernen von r-Bibliotheken, die einer Version zugeordnet sind, und anschließendes Hinzufügen der neuen r-Bibliotheken kann viel Zeit in Anspruch nehmen. Wenn der Vorgang abgeschlossen ist, werden temporäre Ordner entfernt.

## <a name="see-also"></a>Siehe auch

+ [Installieren von Machine Learning Server für Windows (Internet verbunden)](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
+ [Installieren von Machine Learning Server für Windows (offline)](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-offline)
+ [Bekannte Probleme in Machine Learning Server](https://docs.microsoft.com/machine-learning-server/resources-known-issues)
+ [Funktions Ankündigungen aus vorheriger Version von R Server](https://docs.microsoft.com/r-server/whats-new-in-r-server)
+ [Veraltete, nicht mehr unterstützte oder geänderte Features](https://docs.microsoft.com/machine-learning-server/resources-deprecated-features)
