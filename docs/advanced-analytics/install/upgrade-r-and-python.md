---
title: Upgrade von R- und Python-Komponenten
description: Führen Sie ein Upgrade von R- und Python-Komponenten in SQL Server Machine Learning Services oder SQL Server R Services mit sqlbindr.exe aus, um diese an Machine Learning Server zu binden.
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/30/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: abc14f78a969abd4adbbb2dcf12b4ee316614d23
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "69634553"
---
# <a name="upgrade-machine-learning-r-and-python-components-in-sql-server-instances"></a>Upgrade von Machine Learning-Komponenten (R und Python) in SQL Server-Instanzen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Die Integration von R und Python in SQL Server umfasst Open-Source- und proprietäre Microsoft-Pakete. Im Rahmen der Standardwartung von SQL Server werden die Pakete entsprechend dem SQL Server-Releasezyklus aktualisiert, mit Bugfixes für vorhandene Pakete in der aktuellen Version, aber ohne Hauptversionsupgrades. 

Viele Data Scientists sind es jedoch gewohnt, mit neueren Paketen zu arbeiten, sobald diese verfügbar sind. Sowohl für SQL Server Machine Learning Services (datenbankintern) als auch für SQL Server R Services (datenbankintern) können Sie [neuere Versionen von R und Python](#version-map) erhalten, indem Sie sie an **Microsoft Machine Learning Server***binden*. 

## <a name="what-is-binding"></a>Was ist eine Bindung?

Die Bindung ist ein Installationsprozess, bei dem der Inhalt der Ordner R_SERVICES und PYTHON_SERVICES gegen neuere ausführbare Dateien, Bibliotheken und Tools von [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/index) ausgetauscht wird.

Mit den aktualisierten Komponenten geht ein Wechsel der Wartungsmodelle einher. Anstelle des [SQL Server-Produktlebenszyklus](https://support.microsoft.com/lifecycle/search?alpha=SQL%20Server%202017) mit [kumulativen SQL Server-Updates](https://support.microsoft.com/help/4047329/sql-server-2017-build-versions) entsprechen die Dienstupdates nun den [Supportablauffristen für Microsoft R Server und Machine Learning Server](https://docs.microsoft.com/machine-learning-server/resources-servicing-support) für den [modernen Lebenszyklus](https://support.microsoft.com/help/30881/modern-lifecycle-policy).

Abgesehen von Komponentenversionen und Dienstupdates ändert die Bindung nichts an den Grundlagen der Installation: Die R- und Python-Integration ist immer noch Teil einer Datenbank-Engine-Instanz, die Lizenzierung ist unverändert (keine zusätzlichen Kosten für die Bindung) und für die Datenbank-Engine gelten weiterhin die SQL Server-Supportrichtlinien. Im weiteren Verlauf dieses Artikels wird der Bindungsmechanismus erklärt und wie er für die verschiedenen Versionen von SQL Server funktioniert.

> [!NOTE]
> Die Bindung gilt nur für (datenbankinterne) Instanzen, die an SQL Server-Instanzen gebunden sind. Für eine (eigenständige) Installation ist die Bindung nicht relevant.

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
**Überlegungen zur SQL Server 2017-Bindung**

Für SQL Server Machine Learning Services würden Sie eine Bindung nur dann in Betracht ziehen, wenn für Microsoft Machine Learning Server zusätzliche Pakete oder neuere Versionen angeboten werden, als Sie bereits haben.
::: moniker-end

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
**Überlegungen zur SQL Server 2016-Bindung**

Für SQL Server 2016 R Services-Kunden stellt die Bindung aktualisierte R-Pakete, neue Pakete, die nicht Teil der ursprünglichen Installation sind ([MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)), und [vorab trainierte Modelle](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models) bereit, die alle bei jeder neuen Haupt- und Nebenversion von [Microsoft Machine Learning Server](https://docs.microsoft.com/machine-learning-server/index) weiter aktualisiert werden können. Durch die Bindung erhalten Sie einen Python-Support, da es sich dabei um eine SQL Server 2017-Funktion handelt.
::: moniker-end

<a name="version-map"></a>

## <a name="version-map"></a>Versionsübersicht

Die folgende Tabelle zeigt eine Versionsübersicht, die Paketversionen über Releasewechsel hinweg auflistet, sodass Sie bei der Bindung an Microsoft Machine Learning Server (vor dem Hinzufügen von Python-Support ab MLS 9.2.1 bekannt als R-Server) mögliche Upgradepfade ermitteln können. 

Beachten Sie, dass die Bindung nicht garantiert, dass R oder Anaconda auf dem neuesten Stand sind. Bei der Bindung an Microsoft Machine Learning Server (MLS) wird die R- oder Python-Version über das Setup installiert, wobei es sich möglicherweise nicht um die neueste, online verfügbare Version handelt.

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
[**SQL Server 2016 R Services**](../install/sql-r-services-windows-install.md)

Komponente |Erstrelease | [R Server 9.0.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) | [R Server 9.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) | [MLS 9.2.1](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) | [MLS 9.3](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) |
----------|----------------|----------------|--------------|---------|-------|
Microsoft R Open (MRO) über R | R 3.2.2     | R 3.3.2   |R 3.3.3   | R 3.4.1  | R 3.4.3 |
[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) | 8.0.3  | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package)| k. A. | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[vortrainierte Modelle](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models)| k. A. | 9.0.1 |  9.1 |  9.2.1 |  9.3 |
[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)| k. A. | 1.0 |  1.0 |  1.0 |  1.0 |
[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | k. A. | 1.0 |  1.0 |  1.0 |  1.0 |
::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"
[**SQL Server Machine Learning Services**](../install/sql-machine-learning-services-windows-install.md)

Komponente |Erstrelease | MLS 9.3 | | | |
----------|----------------|---------|-|-|-|-|
Microsoft R Open (MRO) über R | R 3.3.3 | R 3.4.3 | | | |
[RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) |   9.2 |  9.3 | | | |
[MicrosoftML](https://docs.microsoft.com/machine-learning-server/r-reference/microsoftml/microsoftml-package) | 9.2  | 9.3| | | |
[sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils)| 1.0 |  1.0 | | | |
[olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | 1.0 |  1.0 | | | |
Anaconda 4.2 über Python 3.5  | 4.2/3.5.2 | 4.2/3.5.2 | | | |
[revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9.2  | 9.3| | | |
[microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9.2  | 9.3| | | |
[vortrainierte Modelle](https://docs.microsoft.com/machine-learning-server/install/microsoftml-install-pretrained-models) | 9.2 | 9.3| | | |
::: moniker-end

## <a name="how-component-upgrade-works"></a>Funktionsweise von Komponentenupgrades 

R- und Python-Bibliotheken sowie ausführbare Dateien werden aktualisiert, wenn Sie eine vorhandene Installation von R und Python an Machine Learning Server binden. Die Bindung wird vom [Microsoft Machine Learning Server-Installationsprogramm](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install) vorgenommen, wenn Sie das Setup auf einer vorhandenen SQL Server-Datenbank-Engine mit R- oder Python-Integration ausführen. Bei der Einrichtung werden die vorhandenen Funktionen erkannt, und Sie werden aufgefordert, erneut eine Bindung mit Machine Learning Server herzustellen. 

Beim Binden wird der Inhalt von `C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES` und `\PYTHON_SERVICES` mit den neueren ausführbaren Dateien und Bibliotheken von `C:\Program Files\Microsoft\ML Server\R_SERVER` und `\PYTHON_SERVER` überschrieben.

Gleichzeitig wird auch das Wartungsmodell von den SQL Server-Updatemechanismen auf den häufigeren Haupt- und Nebenreleasezyklus von Microsoft Machine Learning Server umgestellt. Der Wechsel der Supportrichtlinien ist eine attraktive Option für Data-Science-Teams, die für ihre Lösungen R- und Python-Module der neueren Generation benötigen. 

+ Ohne Bindung werden R- und Python-Pakete für Fehlerbehebungen gepatcht, wenn Sie ein SQL Server Service Pack oder ein kumulatives Update installieren. 
+ Durch die Bindung können neuere Paketversionen auf Ihre Instanz angewendet werden, unabhängig vom Releasezeitplan der kumulativen Updates und unter Berücksichtigung der [modernen Lebenszyklusrichtlinie](https://support.microsoft.com/help/30881/modern-lifecycle-policy) und der Releases von Microsoft Machine Learning Server. Die Supportrichtlinie für den modernen Lebenszyklus bietet häufigere Updates über eine kürzere, einjährige Lebensdauer. Nach der Bindung würden Sie das MLS-Installationsprogramm weiterhin für zukünftige Updates von R und Python verwenden, sobald diese auf den Microsoft-Websites als Download verfügbar sind.

Die Bindung betrifft nur R- und Python-Funktionen. Das sind insbesondere Open-Source-Pakete für R- und Python-Funktionen (Microsoft R Open, Anaconda) und proprietäre Pakete wie RevoScaleR oder revoscalepy. Die Bindung ändert weder das Supportmodell für die Datenbank-Engine-Instanz noch die Version der SQL Server-Instanz.

Die Bindung kann rückgängig gemacht werden. Sie können die SQL Server-Wartung wiederherstellen, indem Sie [die Bindung der Instanz aufheben](#bkmk_Unbind) und Ihre SQL Server-Datenbank-Engine-Instanz reparieren.

Zusammengefasst umfasst die Bindung folgende Schritte:

+ Beginnen Sie mit einer vorhandenen, konfigurierten Installation von SQL Server R Services oder SQL Server Machine Learning Services.
+ Stellen Sie fest, welche Version von Microsoft Machine Learning Server die aktualisierten Komponenten enthält, die Sie verwenden möchten.
+ Laden Sie das Setup für diese Version herunter, und führen Sie es aus. Bei der Einrichtung wird die vorhandene Instanz erkannt, eine Bindungsoption hinzugefügt und eine Liste der kompatiblen Instanzen zurückgegeben.
+ Wählen Sie die Instanz, die Sie binden möchten, und beenden Sie dann das Setup, um die Bindung auszuführen.

In puncto Benutzererfahrung ist die Technologie und deren Handhabung unverändert. Der einzige Unterschied besteht darin, dass es neuere und möglicherweise zusätzliche Pakete gibt, die ursprünglich nicht über SQL Server verfügbar waren.

## <a name="bind-to-mls-using-setup"></a><a name="bkmk_BindWizard"></a>Binden an MLS über das Setup

Beim Microsoft Machine Learning-Setup werden die vorhandenen Funktionen und die SQL Server-Version erkannt und ein Hilfsprogramm namens SqlBindR.exe aufgerufen, um die Bindung zu ändern. Intern ist SqlBindR an das Setup gekoppelt und wird indirekt verwendet. Später können Sie SqlBindR direkt über die Befehlszeile aufrufen, um bestimmte Optionen auszuführen.

1. Führen Sie in SSMS `SELECT @@version` aus, um sicherzustellen, dass der Server die Mindestanforderungen für die Erstellung erfüllt. 

   Bei SQL Server 2016 R Services ist die Mindestanforderung [Service Pack 1](https://www.microsoft.com/download/details.aspx?id=54276) und [CU3](https://support.microsoft.com/help/4019916/cumulative-update-3-for-sql-server-2016-sp1).

1. Überprüfen Sie die Version der R-Basisinstallation und RevoScaleR-Pakete, um sicherzustellen, dass die vorhandenen Versionen niedriger sind als die, durch die Sie sie ersetzen möchten. 

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

1. Schließen Sie SSMS und alle anderen Tools mit einer offenen Verbindung zu SQL Server. Beim Binden werden Programmdateien überschrieben. Wenn in SQL Server offene Sitzungen vorhanden sind, schlägt die Bindung mit dem Bindungsfehlercode 6 fehl.

1. Laden Sie Microsoft Machine Learning Server auf den Computer herunter, auf dem sich die Instanz befindet, die Sie aktualisieren möchten. Es wird die [aktuelle Version](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer) empfohlen.

1. Entpacken Sie den Ordner, und führen Sie die ServerSetup.exe-Datei aus, die sich unter MLSWIN93 befindet.

   ![Setup-Assistent für Microsoft Machine Learning Server](media/mls-921-installer-start.PNG)

1. Bestätigen Sie unter **Configure the installation** (Konfigurieren der Installation) die zu aktualisierenden Komponenten, und überprüfen Sie die Liste der kompatiblen Instanzen. 

   Dieser Schritt ist sehr wichtig.

   Wählen Sie auf der linken Seite alle Funktionen aus, die Sie behalten oder aktualisieren möchten. Einige Funktionen können nicht aktualisiert werden ohne auch andere zu aktualisieren. Durch ein leeres Kontrollkästchen wird diese Funktion entfernt, sofern sie aktuell installiert ist. In dem Screenshot einer Instanz von SQL Server 2016 R Services (MSSQL13) wird gezeigt, dass R und die R-Version der vorab trainierten Modelle ausgewählt sind. Diese Konfiguration ist gültig, da SQL Server 2016 zwar R, aber nicht Python unterstützt.

   Wenn Sie Komponenten in SQL Server 2016 R Services aktualisieren, dürfen Sie die Python-Funktion nicht auswählen. Python kann nicht zu SQL Server 2016 R Services hinzugefügt werden.

   Aktivieren Sie auf der rechten Seite das Kontrollkästchen neben dem Instanznamen. Wenn keine Instanzen aufgelistet sind, ist die Kombination nicht kompatibel. Wenn Sie keine Instanz auswählen, wird eine neue eigenständige Installation von Machine Learning Server erstellt, und die SQL Server-Bibliotheken bleiben unverändert. Wenn Sie eine Instanz nicht auswählen können, befindet sie sich möglicherweise nicht in [SP1 CU3](https://support.microsoft.com/help/4019916/cumulative-update-3-for-sql-server-2016-sp1). 

    ![Schritt zum Konfigurieren der Installation](media/mls-931-installer-mssql13.png)

1. Wählen Sie auf der Seite **License agreement** (Lizenzvereinbarung) **I accept these terms** (Ich akzeptiere diese Bedingungen) aus, um die Lizenzbedingungen für Machine Learning Server zu akzeptieren. 

1. Geben Sie auf den folgenden Seiten Ihre Zustimmung zu weiteren Lizenzbedingungen für alle von Ihnen ausgewählten Open-Source-Komponenten, wie Microsoft R Open oder die Python-Anaconda-Distribution.

1. Notieren Sie sich auf der Seite **Almost there** (Fast geschafft) den Installationsordner. Der Standardordner ist \Programme\Microsoft\ML Server.

    Wenn Sie den Installationsordner ändern möchten, klicken Sie auf **Advanced** (Erweitert), um zur ersten Seite des Assistenten zurückzukehren. Sie müssen jedoch die bisherige Auswahl wiederholen.

Während des Installationsvorgangs werden alle von SQL Server verwendeten R- oder Python-Bibliotheken ersetzt und Launchpad wird aktualisiert, damit die neueren Komponenten verwendet werden können. Wenn die Instanz zuvor Bibliotheken im Standardordner „R_SERVICES“ verwendet hat, werden diese nach dem Upgrade entfernt und die Eigenschaften für den Launchpad-Dienst geändert, sodass die Bibliotheken am neuen Speicherort verwendet werden.

Die Bindung wirkt sich auf den Inhalt dieser Ordner aus: C:\Programme\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library wird durch den Inhalt aus C:\Programme\Microsoft\ML Server\R_SERVER ersetzt. Der zweite Ordner und sein Inhalt werden beim Microsoft Machine Learning Server-Setup erstellt. 

Wenn das Upgrade nicht erfolgreich ist, finden Sie weitere Informationen in den [SqlBindR-Fehlercodes](#sqlbindr-error-codes).

## <a name="confirm-binding"></a>Bestätigen der Bindung

Überprüfen Sie die Version von R und RevoScaleR, um sicherzustellen, dass es sich um neuere Versionen handelt. Verwenden Sie die R-Konsole, die in den R-Paketen Ihrer Datenbank-Engine-Instanz enthalten ist, um Paketinformationen abzurufen:

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

Für SQL Server 2016 R Services mit Bindung an Machine Learning Server 9.3 sollte das R-Basispaket die Version 3.4.3 und RevoScaleR die Version 9.3 aufweisen. Außerdem sollten Sie auch über MicrosoftML 9.3 verfügen. 

Wenn Sie die vorab trainierten Modelle hinzugefügt haben, werden die Modelle in die MicrosoftML-Bibliothek eingebettet und Sie können sie über MicrosoftML-Funktionen aufrufen. Weitere Informationen finden Sie unter [R-Beispiele für MicrosoftML](https://docs.microsoft.com/machine-learning-server/r/sample-microsoftml).

## <a name="offline-binding-no-internet-access"></a>Offlinebindung (kein Internetzugang)

Bei Systemen ohne Internetverbindung können Sie das Installationsprogramm und die CAB-Dateien auf einen mit dem Internet verbundenen Computer herunterladen und die Dateien dann auf den isolierten Server übertragen. 

Das Installationsprogramm (ServerSetup.exe) enthält die Microsoft-Pakete (RevoScaleR, MicrosoftML, olapR, sqlRUtils). Die CAB-Dateien stellen weitere wichtige Komponenten bereit. So enthält beispielsweise die CAB-Datei „SRO“ R Open, die Microsoft-Version der Open-Source-Distribution von R.

In den folgenden Anweisungen wird beschrieben, wie Sie die Dateien für eine Offlineinstallation bereitstellen.

1. Laden Sie das MLS-Installationsprogramm herunter. Es wird als einzelne ZIP-Datei heruntergeladen. Es wird empfohlen, die [aktuelle Version](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install#download-machine-learning-server-installer) zu verwenden, aber Sie können auch [frühere Versionen](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components) installieren.

1. Laden Sie die CAB-Dateien herunter. Unter den folgenden Links finden Sie das Release 9.3. Wenn Sie frühere Versionen benötigen, finden Sie weitere Links unter [R Server 9.1](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows-offline#download-required-components). Denken Sie daran, dass Python/Anaconda nur einer SQL Server Machine Learning Services-Instanz hinzugefügt werden kann. Sowohl für R als auch für Python gibt es vorab trainierte Modelle. Die CAB-Dateien stellen Modelle in den Sprachen bereit, die Sie verwenden.

    | Funktion | Download |
    |---------|----------|
    | R       | [SRO_3.4.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=867186&clcid=1033) |
    | Python  | [SPO_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859054) | 
    | Vortrainierte Modelle | [MLM_9.3.0.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=859053) |

1. Übertragen Sie die ZIP- und CAB-Dateien auf den Zielserver.

1. Geben Sie auf dem Server in die Befehlszeile `%temp%` ein, um den physischen Speicherort des temporären Verzeichnisses aufzurufen. Der physische Pfad ist in der Regel `C:\Users\<your-user-name>\AppData\Local\Temp`, kann aber auch von Computer zu Computer variieren.

1. Platzieren Sie die CAB-Dateien im Ordner %Temp%.

1. Entpacken Sie das Installationsprogramm.

1. Führen Sie die ServerSetup.exe-Datei aus, und befolgen Sie die Anweisungen auf dem Bildschirm, um die Installation abzuschließen.

## <a name="command-line-operations"></a><a name="bkmk_BindCmd"></a>Befehlszeilenvorgänge

Nachdem Sie Microsoft Machine Learning Server ausgeführt haben, können Sie das Befehlszeilenprogramm „SqlBindR.exe“ für weitere Bindungsvorgänge verwenden. Wenn Sie sich beispielsweise entscheiden, eine Bindung aufzuheben, können Sie entweder das Setup erneut ausführen oder aber das Befehlszeilenprogramm verwenden. Außerdem können Sie dieses Tool verwenden, um die Kompatibilität und Verfügbarkeit der Instanz zu überprüfen.

> [!TIP]
> Sie können SqlBindR nicht finden? Dann haben Sie wahrscheinlich das Setup nicht ausgeführt. SqlBindR ist nur nach dem Ausführen des Machine Learning Server-Setups verfügbar.

1. Öffnen Sie als Administrator eine Eingabeaufforderung und navigieren Sie zum Ordner, der „sqlbindr.exe“ enthält. Der Standardspeicherort lautet C:\Programme\Microsoft\MLServer\Setup

2. Geben Sie den folgenden Befehl ein, um eine Liste der verfügbaren Instanzen anzuzeigen: `SqlBindR.exe /list`
  
   Merken Sie sich den vollständigen aufgelisteten Namen der Instanz. Beispielsweise kann der Instanzname für eine Standardinstanz MSSQL14.MSSQLSERVER oder etwas wie SERVERNAME.MYNAMEDINSTANCE sein.

3. Führen Sie den Befehl **SqlBindR.exe** mit dem */bind*-Argument aus, und geben Sie den Namen der zu aktualisierenden Instanz an, indem Sie den im vorherigen Schritt zurückgegebenen Instanznamen verwenden.

   Geben Sie beispielsweise Folgendes ein, um die Standardinstanz zu aktualisieren: `SqlBindR.exe /bind MSSQL14.MSSQLSERVER`

4. Wenn das Upgrade abgeschlossen ist, starten Sie den Launchpad-Dienst neu, der mit einer beliebigen aktualisierten Instanz verknüpft ist.

## <a name="revert-or-unbind-an-instance"></a><a name="bkmk_Unbind"></a>Wiederherstellen oder Aufheben der Bindung einer Instanz

Sie können eine gebundene Instanz in einer Erstinstallation von R- und Python-Komponenten wiederherstellen, die beim SQL Server-Setup eingerichtet wurden. Zum Wiederherstellen der SQL Server-Wartung sind drei Schritte erforderlich:

+ [Schritt 1: Aufheben der Bindung zu Microsoft Machine Learning Server](#step-1-unbind)
+ [Schritt 2: Wiederherstellen des ursprünglichen Status der Instanz](#step-2-restore)
+ [Schritt 3: Erneutes Installieren aller zur Installation hinzugefügten Pakete](#step-3-reinstall-packages)

<a name="step-1-unbind"></a> 

### <a name="step-1-unbind"></a>Schritt 1: Aufheben der Bindung

Es gibt zwei Möglichkeiten, um die Bindung aufzuheben: Sie können das Setup erneut ausführen oder das Befehlszeilenprogramm „SqlBindR“ verwenden.

#### <a name="unbind-using-setup"></a><a name="bkmk_wizunbind"></a> Aufheben der Bindung über das Setup

1. Navigieren Sie zum Installationsprogramm für Machine Learning Server. Wenn Sie das Installationsprogramm bereits entfernt haben, müssen Sie es ggf. wieder herunterladen oder von einem anderen Computer kopieren.
2. Stellen Sie sicher, dass Sie das Installationsprogramm auf dem Computer ausführen, auf dem sich die Instanz befindet, deren Bindung Sie aufheben möchten.
2. Das Installationsprogramm identifiziert die lokalen Instanzen, die für das Aufheben der Bindung in Frage kommen.
3. Deaktivieren Sie das Kontrollkästchen neben der Instanz, für die Sie die ursprüngliche Konfiguration wiederherstellen möchten.
4. Akzeptieren Sie die Lizenzbedingungen. Auch bei der Installation müssen Sie Ihre Zustimmung zu den Lizenzbedingungen geben.
5. Klicken Sie auf **Fertig stellen**. Der Prozess dauert eine Weile.

#### <a name="unbind-using-the-command-line"></a><a name="bkmk_cmdunbind"></a> Aufheben der Bindung über die Befehlszeile

1. Öffnen Sie eine Eingabeaufforderung, und navigieren Sie zu dem Ordner, der **sqlbindr.exe** enthält, wie im vorherigen Abschnitt beschrieben.

2. Führen Sie den Befehl **SqlBindR.exe** mit dem */unbind*-Argument aus, und geben Sie die Instanz an.

   Beispielsweise wird die Standardinstanz über folgenden Befehl wiederhergestellt:
   
    `SqlBindR.exe /unbind MSSQL14.MSSQLSERVER`

<a name="step-2-restore"></a> 

###  <a name="step-2-repair-the-sql-server-instance"></a>Schritt 2: Reparieren der SQL Server-Instanz

Führen Sie das SQL Server-Setup aus, um die Datenbank-Engine-Instanz mit den R- und Python-Funktionen zu reparieren. Vorhandene Updates werden beibehalten. Wenn Sie jedoch SQL Server-Wartungsupdates für R- und Python-Pakete verpasst haben, werden diese Patches in diesem Schritt angewendet.

Dies ist zwar aufwendiger, aber Sie können die Datenbank-Engine-Instanz auch vollständig deinstallieren, neu installieren und dann alle Wartungsupdates vornehmen.

<a name="step-3-reinstall-packages"></a> 

### <a name="step-3-add-any-third-party-packages"></a>Schritt 3: Hinzufügen von Drittanbieterpaketen

Möglicherweise haben Sie der Paketbibliothek andere Open-Source- oder Drittanbieterpakete hinzugefügt. Da durch das Umkehren der Bindung der Speicherort der Standardpaketbibliothek geändert wird, müssen Sie die Pakete in der Bibliothek neu installieren, die jetzt von R und Python verwendet wird. Weitere Informationen finden Sie unter [R-Paketinformationen](../package-management/r-package-information.md) und [Installation](../package-management/install-additional-r-packages-on-sql-server.md) sowie unter [Python-Paketinformationen](../package-management/python-package-information.md) und [Installation](../package-management/install-additional-python-packages-on-sql-server.md).

## <a name="sqlbindrexe-command-syntax"></a>SqlBindR.exe-Befehlssyntax

### <a name="usage"></a>Verwendung

`sqlbindr [/list] [/bind <SQL_instance_ID>] [/unbind <SQL_instance_ID>]`

### <a name="parameters"></a>Parameter

|Name|BESCHREIBUNG|
|------|------|
|*list*| Zeigt eine Liste aller SQL-Datenbankinstanz-IDs auf dem aktuellen Computer an|
|*bind*| Aktualisiert die angegebene SQL-Datenbankinstanz auf die neueste Version von R Server und stellt sicher, dass die Instanz automatisch zukünftige Upgrades von R Server erhält|
|*unbind*|Die neueste Version von R Server wird auf der angegebenen SQL-Datenbankinstanz deinstalliert, und es wird verhindert, dass zukünftige R Server-Upgrades auf die Instanz angewandt werden|

<a name="sqlbindr-error-codes"><a/>

## <a name="binding-errors"></a>Bindungsfehler

Das MLS-Installationsprogramm und SqlBindR geben beide die folgenden Fehlercodes und -meldungen zurück.

|Fehlercode  | `Message`           | Details               |
|------------|-------------------|-----------------------|
|Bindungsfehler 0 | OK (bei Erfolg) | Bindung ohne Fehler übergeben. |
|Bindungsfehler 1 | Ungültige Argumente | Syntaxfehler. |
|Bindungsfehler 2 | Ungültige Aktion | Syntaxfehler. |
|Bindungsfehler 3 | Ungültige Instanz | Es ist eine Instanz vorhanden, aber für die Bindung nicht zulässig. |
|Bindungsfehler 4 | Keine Bindung möglich | |
|Bindungsfehler 5 | Bereits gebunden | Sie haben den *bind* -Befehl ausgeführt, die angegebene Instanz ist aber bereits gebunden. |
|Bindungsfehler 6 | Fehler beim Binden | Beim Aufheben der Bindung der Instanz ist ein Fehler aufgetreten. Dieser Fehler kann auftreten, wenn Sie das MLS-Installationsprogramm ohne Auswahl von Funktionen ausführen. Für die Bindung muss sowohl eine MSSQL-Instanz als auch R und Python ausgewählt werden, vorausgesetzt, es handelt sich um eine SQL Server 2017-Instanz. Dieser Fehler tritt auch auf, wenn SqlBindR nicht in den Ordner „Programme“ schreiben konnte. Bei offenen Sitzungen oder Handles für SQL Server tritt dieser Fehler auf. Wenn Sie diese Fehlermeldung erhalten, starten Sie den Computer neu. Wiederholen Sie dann die Bindungsschritte, bevor Sie neue Sitzungen starten.|
|Bindungsfehler 7 | Nicht gebunden | Die Datenbank-Engine-Instanz verfügt über R Services oder SQL Server Machine Learning Services. Die Instanz ist nicht an Microsoft Machine Learning Server gebunden. |
|Bindungsfehler 8 | Fehler beim Aufheben der Bindung | Beim Aufheben der Bindung der Instanz ist ein Fehler aufgetreten. |
|Bindungsfehler 9 | Keine Instanzen gefunden | Auf diesem Computer wurden keine Datenbank-Engine-Instanzen gefunden. |

## <a name="known-issues"></a>Bekannte Probleme

In diesem Abschnitt werden bekannte Probleme aufgelistet, die für die Verwendung des SqlBindR.exe-Hilfsprogramms oder für Upgrades von Machine Learning Server, die ggf. SQL Server-Instanzen betreffen, spezifisch sind.

### <a name="restoring-packages-that-were-previously-installed"></a>Wiederherstellen von zuvor installierten Paketen

Wenn Sie ein Upgrade auf Microsoft R Server 9.0.1 durchgeführt haben, konnte die Version von SqlBindR.exe für diese Version die ursprünglichen Pakete oder R-Komponenten nicht vollständig wiederherstellen. Das bedeutet, dass der Benutzer die SQL Server-Reparatur für die Instanz ausführen, alle Wartungsreleases anwenden und die Instanz anschließend neu starten muss.

In der späteren Version von SqlBindR werden die ursprünglichen R-Funktionen automatisch wiederhergestellt, sodass keine Neuinstallation von R-Komponenten oder ein erneutes Patchen des Servers erforderlich ist. Sie müssen jedoch alle R-Paketupdates installieren, die möglicherweise nach der Erstinstallation hinzugefügt wurden.

Mit den Paketverwaltungsrollen zur Installation und Freigabe von Paketen ist diese Aufgabe viel einfacher: Mithilfe von R-Befehlen können Sie installierte Pakete über Datensätze in der Datenbank mit dem Dateisystem synchronisieren und umgekehrt. Weitere Informationen finden Sie unter [R-Paketverwaltung für SQL Server](../r/install-additional-r-packages-on-sql-server.md).

### <a name="problems-with-multiple-upgrades-from-sql-server"></a>Probleme bei mehreren Upgrades von SQL Server

Wenn Sie zuvor eine Instanz von SQL Server 2016 R Services auf 9.0.1 aktualisiert haben, zeigt das neue Installationsprogramm für Microsoft R Server 9.1.0 eine Liste aller gültigen Instanzen an und wählt dann standardmäßig zuvor gebundene Instanzen aus. Wenn Sie den Vorgang fortsetzen, wird die Bindung der zuvor gebundenen Instanzen aufgehoben. Infolgedessen wird die frühere Installation der Version 9.0.1 entfernt, einschließlich aller zugehörigen Pakete, aber die neue Version von Microsoft R Server (9.1.0) wird nicht installiert.

Um dieses Problem zu umgehen, können Sie die vorhandene R Server-Installation wie folgt ändern:
1. Öffnen Sie in der Systemsteuerung **Programme hinzufügen/entfernen**.
2. Wählen Sie Microsoft R Server aus, und klicken Sie auf **Ändern/Bearbeiten**.
3. Wenn das Installationsprogramm gestartet wird, wählen Sie die Instanzen aus, die Sie an 9.1.0 binden möchten.

Bei Microsoft Machine Learning Server 9.2.1 und 9.3 besteht dieses Problem nicht.

### <a name="binding-or-unbinding-leaves-multiple-temporary-folders"></a>Mehrere temporäre Ordner nach dem Binden bzw. Aufheben der Bindung

Manchmal werden die temporären Ordner nach dem Binden bzw. Aufheben von Bindungen nicht bereinigt.
Wenn Sie Ordner mit einem derartigen Namen vorfinden, können Sie sie nach Abschluss der Installation entfernen: R_SERVICES_<guid>

> [!NOTE]
> Warten Sie unbedingt, bis die Installation abgeschlossen ist. Es kann lange dauern, bis R-Bibliotheken, die einer Version zugeordnet sind, entfernt und dann die neuen R-Bibliotheken hinzugefügt werden. Sobald der Vorgang abgeschlossen ist, werden temporäre Ordner entfernt.

## <a name="see-also"></a>Weitere Informationen

+ [Install Machine Learning Server for Windows (Internet connected) (Installieren von Machine Learning Server für Windows (mit Internetzugang))](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install)
+ [Install Machine Learning Server for Windows (offline) (Installieren von Machine Learning Server für Windows (ohne Internetzugang))](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-offline)
+ [Known issues in Machine Learning Server (Bekannte Probleme in Machine Learning Server)](https://docs.microsoft.com/machine-learning-server/resources-known-issues)
+ [Feature announcements from previous release of R Server (Funktionsankündigungen aus vorherigem Release von R Server)](https://docs.microsoft.com/r-server/whats-new-in-r-server)
+ [Deprecated, discontinued or changed features (Veraltete, nicht mehr unterstützte oder geänderte Funktionen)](https://docs.microsoft.com/machine-learning-server/resources-deprecated-features)
